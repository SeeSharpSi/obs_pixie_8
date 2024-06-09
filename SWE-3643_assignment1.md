# Q4

If we have a program that adds two two-digit integers, would it be exhaustively testable? If so, how many test cases would be required?
To start, we must decide whether our two-digit integers include 0-9 (in the form of 00-09). Since including them is worst case, we will. That gives us 100 * 100 (10,000) possible inputs, each with a known corresponding output. This is exhaustively testable, though it may not be practically testable.
Assuming each test case takes 1 seconds to run, this application would take 10,000 seconds (~2.7778 hours) to test. This is not practical for local, per-commit testing, but it may be practical for pre-merge and pre-production testing.
Note: chapter 1.2 of our textbook states that "exhaustive testing is impossible." This is odd, as it is definitely possible to test every input of this test 

# Q5 
*  In his article discussing Software Metrics, Kan discusses using Lines of Code (LOC) to assess product quality. Is this a good metric? Why or Support your answer with material from the article.

## article 
* Counting tools can cause significant differences in final count of LOC. Several variations are: 
	1. Count only executable lines 
	2. Count executable lines plus data definitions 
	3. Count executable lines, data definitions, comments, and job control language 
	4. Count lines as physical lines on an input screen 
	5. Count lines as terminated by logical delimiters 
*  In _Software Engineering Metrics and Models_ by Conte et al. (1986), LOC is defined as follows: 
	* A line of code is any line of program text that is not a comment or blank line, regardless of the number of statements or fragments of statements on the line. This specifically includes all lines containing program headers, declarations, and executable and non-executable statements. (p. 35)
	* **Counter example: js ternary operator** 
* 

# discussion 2
* List and briefly describe in your own words at least five key qualities that software engineering is concerned with.
* Now, order the qualities of importance in your SWE projects that you complete for school. Give a brief explanation of your order. Do you think your opinion would align with the goals of a business? Why or why not?

Simply put, software engineering is the activity of applying engineering practices to software. This highlights (but is not limited to): 
1. Iteration on design 
2. Implementation of software 
3. Testing of software
4. Maintenance of software
5. Research before development 

In my software projects for school, these fall into most-least important order as:
1. Research before development 
2. Iteration on design 
3. Implementation of software 
4. Testing of software 
5. Maintenance of software 

The order I place these in my school projects doesn't reflect my opinion on how real-world development should be done, but it gives good insight into my mentality. 
If "coding" was on the list it would take precedent. That said, research is very important. Reading the manual, textbooks, etc. on frameworks and languages is invaluable. When learning a language I generally have some documentation open while using my terminal (Vim btw) to practice what I read.
Iteration on design is also important, though primarily from a coding standpoint (with my projects at least). Do something, see if it works (testing), change it. Testing is right there with this, so they're interchangable in my book.
Maintenance is something I can't really comment on as I've never done customer facing changes after a full release. Still, it's on my initial list as I've encountered maintenance problems from third parties and how easy they are to implement says a lot about a company.
Overall, my opinions don't reflect many decisions made by businesses (except possibly Netflix). Most businesses like to spend long periods planning, drawing, and finalizing designs before they touch code. This is understandable, but not my approach to software.