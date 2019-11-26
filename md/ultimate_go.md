[Ultimate Go中记载的编程哲学](https://github.com/ardanlabs/gotraining/blob/master/topics/go/README.md)



## Reading Code

“If most computer people lack understanding and knowledge, then what they will select will also be lacking.” - Alan Kay*



*"The software business is one of the few places we teach people to write before we teach them to read." - Tom Love (inventor of Objective C)*



*"Code is read many more times than it is written." - Dave Cheney*



*"Programming is, among other things, a kind of writing. One way to learn writing is to write, but in all other forms of writing, one also reads. We read examples both good and bad to facilitate learning. But how many programmers learn to write programs by reading programs?" - Gerald M. Weinberg*



*"Skill develops when we produce, not consume." - Katrina Owen*



## Legacy Software

*"There are two kinds of software projects: those that fail, and those that turn into legacy horrors." - Peter Weinberger (inventor of AWK)*



*"Legacy software is an unappreciated but serious problem. Legacy code may be the downfall of our civilization." - Chuck Moore (inventor of Forth)*



*"Few programmers of any experience would contradict the assertion that most programs are modified in their lifetime. Why then do we rarely find a program that contains any evidence of having been written with an eye to subsequent modification. - Gerald M. Weinberg"*



*"We think awful code is written by awful devs. But in reality, it's written by reasonable devs in awful circumstances." - Sarah Mei*



*"There are many reasons why programs are built the way they are, although we may fail to recognize the multiplicity of reasons because we usually look at code from the outside rather than by reading it. When we do read code, we find that some of it gets written because of machine limitations, some because of language limitations, some because of programmer limitations, some because of historical accidents, and some because of specifications—both essential and inessential. - Gerald M. Weinberg"*



## Correctness vs Performance

*"Make it correct, make it clear, make it concise, make it fast. In that order." - Wes Dyer*



*"Good engineering is less about finding the "perfect" solution and more about understanding the tradeoffs and being able to explain them." - JBD*



*"Choosing the right limitations for a certain problem domain is often much more powerful than allowing anything." - Jason Moiron*



*"The correctness of the implementation is the most important concern, but there is no royal road to correctness. It involves diverse tasks such as thinking of invariants, testing and code reviews. Optimization should be done, but not prematurely." - Al Aho (inventor of AWK)*



*"The basic ideas of good style, which are fundamental to write clearly and simply, are just as important now as they were 35 years ago. Simple, straightforward code is just plain easier to work with and less likely to have problems. As programs get bigger and more complicated, it's even more important to have clean, simple code." - Brian Kernighan*



*"Problems can usually be solved with simple, mundane solutions. That means there's no glamorous work. You don't get to show off your amazing skills. You just build something that gets the job done and then move on. This approach may not earn you oohs and aahs, but it lets you get on with it." - Jason Fried*



## Rules

- Rules have costs.
- Rules must pull their weight - Don’t be clever (high level).
- Value the standard, don’t idolize it.
- Be consistent!
- Semantics convey ownership.



*"An architecture isn't a set of pieces, it's a set of rules about what you can expect of them." - Michael Feathers*



## Senior vs Junior Developers

*"You are personally responsible for the software you write." - Stephen Bourne (Bourne shell)*



*"And the difference between juniors+seniors to those who are in-between, is the confidence to ask "dumb" questions." - Natalie Pistunovich*



*"Mistakes are an inevitable consequence of doing something new and, as such, should be seen as valuable; without them, we'd have no originality." - Ed Catmull (President of Pixar)*



*"It takes considerable knowledge just to realize the extent of your own ignorance." - Thomas Sowell*



*"If you don’t make mistakes, you’re not working on hard enough problems." - Frank Wilczek*



## Code Reviews

You can't look at a piece of code, function or algorithm and determine if it smells good or bad without a design philosophy. These four major categories are the basis for code reviews and should be prioritized in this order: Integrity, Readability, Simplicity and then Performance. You must consciously and with great reason be able to explain the category you are choosing.



------

### Integrity

There have been studies that have researched the number of bugs you can expect to have in your software. The industry average is around 15 to 50 bugs per 1000 lines of code. One simple way to reduce the number of bugs, and increase the integrity of your software, is to **write less code**.



Bjarne Stroustrup stated that writing more code than you need results in `Ugly`, `Large` and `Slow` code:

- `Ugly`: Leaves places for bugs to hide.
- `Large`: Ensures incomplete tests.
- `Slow`: Encourages the use of shortcuts and dirty tricks.



*"Failure is expected, failure is not an odd case. Design systems that help you identify failure. Design systems that can recover from failure." - JBD*



*"Product excellence is the difference between something that only works under certain conditions, and something that only breaks under certain conditions". - Kelsey Hightower*



*"Instability is a drag on innovation." - Yehudah Katz*



------

### Readability

**We must structure our systems to be more comprehensible.**



 **Code Must Never Lie**

We have all been here if you have been programming long enough. At this point it doesn't matter how fast the code might be if no one can understand or maintain it moving forward.



*"This is a cardinal sin amongst programmers. If code looks like it’s doing one thing when it’s actually doing something else, someone down the road will read that code and misunderstand it, and use it or alter it in a way that causes bugs. That someone might be you, even if it was your code in the first place." - Nate Finch*



**Average Developer**

You must be aware of who you are on your team. When hiring new people, you must be aware of where they fall. The code must be written for the average developer to comprehend. If you are below average, you have the responsibility to come up to speed. If you are the expert, you have the responsibility to reduce being clever.



*"Can you explain it to the median user (developer)? as opposed to will the smartest user (developer) figure it out?" - Peter Weinberger (inventor of AWK)*



**Real Machine**

In Go, the underlying machine is the real machine rather than a single abstract machine. The model of computation is that of the computer. Here is the key, Go gives you direct access to the machine while still providing abstraction mechanisms to allow higher-level ideas to be expressed.



*"Making things easy to do is a false economy. Focus on making things easy to understand and the rest will follow." - Peter Bourgon*



------

### Simplicity

**We must understand that simplicity is hard to design and complicated to build.**



**Complexity Sells Better**

*"Simplicity is a great virtue but it requires hard work to achieve it and education to appreciate it. And to make matters worse: complexity sells better." - Edsger W. Dijkstra*



*"Everything should be made as simple as possible, but not simpler." - Albert Einstein*



*"You wake up and say, I will be productive, not simple, today." - Dave Cheney*



------

### Performance



**We must compute less to get the results we need.**



*"Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%." — Donald E. Knuth*



*"I don't trust anything until it runs... In fact, I don't trust anything until it runs twice." - Andrew Gelman (one of the greatest living statisticians at Columbia University).*