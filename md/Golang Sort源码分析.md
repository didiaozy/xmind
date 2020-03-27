# Golang Sort源码分析



### Interface接口

想要使用Sort.Sort对数据进行排序，需要提前实现Len、Less、Swap这三个接口。

```go
// A type, typically a collection, that satisfies sort.Interface can be
// sorted by the routines in this package. The methods require that the
// elements of the collection be enumerated by an integer index.
type Interface interface {
	// Len is the number of elements in the collection.
	Len() int
	// Less reports whether the element with
	// index i should sort before the element with index j.
	Less(i, j int) bool
	// Swap swaps the elements with indexes i and j.
	Swap(i, j int)
}
```

**Len**：返回数据长度。

**Less**：数据**i**是否需要排在数据**j**的前面。由于源码**quickSort**函数中**Swap**是发生在**Less**为**true**时，所以当**i** < **j**实现的是升序，**i** > **j**实现的是降序。

**Swap**：数据交换。



### Sort排序

**Sort**函数实际是调用的**quickSort**实现的排序，而该排序实现不是稳定排序。

```go
// a: 待排序序列首索引、 b: 待排序序列尾索引、 maxDepth: 表示排序方式转为堆排序的阈值（2*lg(n+1))
func quickSort(data Interface, a, b, maxDepth int) {
    // 切片元素大于12时，maxDepth==0使用堆排序，否则使用快排
    // 切片元素小于等于12时，使用希尔排序
	for b-a > 12 { // Use ShellSort for slices <= 12 elements
		if maxDepth == 0 {
			heapSort(data, a, b)
			return
		}
		maxDepth--
		mlo, mhi := doPivot(data, a, b)
		// Avoiding recursion on the larger subproblem guarantees
		// a stack depth of at most lg(b-a).
		if mlo-a < b-mhi {
			quickSort(data, a, mlo, maxDepth)
			a = mhi // i.e., quickSort(data, mhi, b)
		} else {
			quickSort(data, mhi, b, maxDepth)
			b = mlo // i.e., quickSort(data, a, mlo)
		}
	}
    
    // 使用增量6对切片进行一次希尔排序，使部分有序后再调用插入排序。并未持续缩减增量进行希尔排序的原因是数据量总体并不大（b-a<=12）
	if b-a > 1 {
		// Do ShellSort pass with gap 6
		// It could be written in this simplified form cause b-a <= 12
		for i := a + 6; i < b; i++ {
			if data.Less(i, i-6) {
				data.Swap(i, i-6)
			}
		}
		insertionSort(data, a, b)
	}
}
```



为了满足稳定排序的需要，Sort包提供了**Stable**函数。

```go
func Stable(data Interface) {
	stable(data, data.Len())
}

func stable(data Interface, n int) {
	blockSize := 20 // must be > 0
	a, b := 0, blockSize
	for b <= n {
		insertionSort(data, a, b)
		a = b
		b += blockSize
	}
	insertionSort(data, a, n)

	for blockSize < n {
		a, b = 0, 2*blockSize
		for b <= n {
			symMerge(data, a, a+blockSize, b)
			a = b
			b += 2 * blockSize
		}
		if m := a + blockSize; m < n {
			symMerge(data, a, m, n)
		}
		blockSize *= 2
	}
}
```

