---
type: assignment
topic: school
---

# Assignment 1 
* Silas Tompkins 
* SWE 3643
* June 9, 2024


## Question 2	
	Dijkstra asserts that “Program testing can be used to show the presence of bugs, but never to show their absence!”  Explain this statement.  Provide one real world example that is not related to computing.

Dijkstra's statement that "program testing can be used to show the presence of bugs, but never to show their absence" is pivotal for a tester's mindset and gives us insight to testing at a philosophical level.

Essentially, while testing can assert the positive of defects's existence in a program, it cannot assert the negative that is their non-existence. This means that, while the days needed for defect fixing and outstanding defects may be zero, testers should always, continuously, be testing throughout different stages of the product lifecycle whether or not defects are found. This can be tedious but can save a system from longterm failure.

To give one example of Dijkstra's statement (and where it may be derived from), it's especially relevant to the world of philosophy and provides a lot of debate. While many people claim that "you cannot prove a negative," this in itself is a negative claim, causing it to become paradoxical. Besides, negative claims have positive counterparts. For example, the claim "no-one in the store is older than 30" is equivalent to "everyone in the store is younger than 30." Along with this, philosophers often agree that inductive reasoning can be used to prove a negative (such as "unicorns don't exist"). Which, to that point, means that Dijkstra's statement is actually false.

For example, take a system that converts one byte into a corresponding ANSI character. This is exhaustively testable, as the program only has 256 inputs (ignoring bugs that can arise from I/O calls, which highlights the "inductive" function of this proposition). Having the correct output surface from all 256 inputs would mean the system has zero bugs. But this is a small program that has one function, which most applications aren't. So while Dijkstra's statement may not be absolutely true, it's an extremely good principle.

All this to say, Dijkstra's point is very good: testers/developers should always assume defects are possible/present, and be prepared to hunt for them and find them.
<div class="pb"></div>

## Question 3
	What is Software Quality?  How do you know when the software provided is considered good software?  And how do you know that an update is better than the previous version?

The success of a piece of software is often tied to its quality, making software quality extremely important. But what dictates quality is often debated and can show a team's overarching goals.
Personally, it seems software quality is directly tied to two things:
1. Meeting stakeholder needs and
2. The general perception of the released product 

The first is self explanatory, but the second point is confusing. So, like all good articles, we will start with a quote from Steve Jobs from his interview at the All Things Digital Conference: "things are packages of emphasis. Some things are emphasized in a product, some things are not done as well in a product" (Jobs, 2010). The customer will want something, and they will make it a requirement. Whether the product comes across as polished depends on what is emphasized. For Apple, the emphasis is chassis design and flashy software. For Linus Torvalds it is a better way to connect to I/O.

Now to go backwards: point one may seem self explanatory, but getting the needs (requirements) of the stakeholders can be a hard task. This means that a product can fail if it does not know what to emphasize and what to deliver. This task falls on requirements engineers, and even goes hand-in-hand with customer-facing testing (like AB testing).

Overall, software quality is a target that will change per company, per niche, per team, per customer. The variables that dictate quality differ widely, meaning a concrete definition is hard to come across. This makes the term "quality" somewhat transcendental in the software world, and thus makes it a form of art. Still, this should not take us away from the engineering aspects of software and the tried and true paths that lead to success, even if there are not many.
<div class="pb"></div>

## Question 4
	You are assigned the task of creating a program that adds two two-digit integers.  Can you test the program exhaustively?  If so, how many test cases are required?  Assuming that each test case can be executed and analyzed in one second, how long would it take for you to run all of the tests?  Fully explain your answer, along with all assumptions.  No credit will be given for answers that simply show a calculation.

If we have a program that adds two two-digit integers, would it be exhaustively testable? If so, how many test cases would be required? 

To start, we must decide whether our two-digit integers include 0-9 (in the form of 00-09). Since including them is worst case, we will. That gives us 100 * 100 (10,000) possible inputs, each with a known corresponding output. This is exhaustively testable, though it may not be practically testable. Assuming each test case takes 1 seconds to run, this application would take 10,000 seconds (~2.7778 hours) to test. This is not practical for local, per-commit testing, but it may be practical for pre-merge and pre-production testing. 

Note: chapter 1.2 of our textbook explains that exhaustive testing is impossible. This is odd, as it is definitely possible to test every input of this test. But if this is theoretically true the simple answer to Q4 is "no, it's not exhaustively testable."
<div class="pb"></div>

## Question 5 
	In his article discussing Software Metrics, Kan discusses using Lines of Code (LOC) to assess product quality.  Is this a good metric?  Why or why not? Make sure your answer is not opinion. Support your answer with material from the article.

The idea of counting lines of code as a metric is not bad. It can help developers measure runtime, coding efficiency, estimate package size, and so on. That said, using it as a _target_ metric does not make sense and should generally be avoided, even if the target is only implied by correlating defects with LOC.

There are several reasons why, but we will start from the text itself. As the book _Metrics and Models in Software Quality Engineering_ puts it: "Furthermore, as discussed in Chapter 3, some companies may use the straight LOC count (whatever LOC counting method is used) as the denominator for calculating defect rate. . . So far, very little research on this topic has been published" (Kan, 2002, p. 89). To demonstrate why this does not make sense, let us take this example written in Go 1.21: 
```go
func main() {
    var prints []func()
    for i := 1; i <= 3; i++ {
        prints = append(prints, func() { fmt.Println(i) })
    }
    for _, print := range prints {
        print()
    }
}
```

In this code, the variable `prints` is defined as an array of functions. The for-loop iterates three times, each time appending a function to the array that prints the value of `i` from the for-loop to `stdout`. It then goes through each function in `prints` and runs it.

On paper, this would seem to output `123`. Instead, it outputs `333`. The fix for this adds the line `temp_int := i` and looks like this:
```go
func main() {
    var prints []func()
    for i := 1; i <= 3; i++ {
		temp_int := i
        prints = append(prints, func() { fmt.Println(temp_int) })
    }
    for _, print := range prints {
        print()
    }
}
```

This is a commonly overlooked attribute of for loops found in Go and JavaScript applications that often goes undetected until extensive performance tests are run (though, the most recent version of Go changed this). But this presents an issue: LOC reasoning would discard the second function because it adds a line of executable code.

We can also look at JavaScript ternaries (JavaScript is not compiled to Assembly, meaning you cannot count lines that way): 
```js
function getFee(isMember) {
  return isMember ? '$2.00' : '$10.00';
}

console.log(getFee(true));
// Expected output: "$2.00"

console.log(getFee(false));
// Expected output: "$10.00"

console.log(getFee(null));
// Expected output: "$10.00"
```

Many developers dislike ternaries for good reason. But if using LOC as a target and ratio for defects, developers will be swayed to use them. Having to use something that is less readable when its counterpart isn't slower seems odd.
<div class="pb"></div>

## References 
* Jobs, Steve (2010). D8 Conference. https://www.youtube.com/watch?v=XmRNIGqzuRI 
* Pike, Rob (2012). _Go at Google: Language Design in the Service of Software Engineering_. https://go.dev/talks/2012/splash.article 
* Kan, Stephen (2002). _Metrics and Models in Software Quality Engineering_, 89 
