---
type: assignment
topic: school
---

# Q1
* Draw the control flow graph for the printPrimes() method 
* Control flow graph: ![[Pasted image 20240721162024.png]]

# Q2 
* For printPrimes(), find a test case such that the corresponding test path visits the edge that connects the beginning of the while statement to the for statement that appears after the while loop, without going through the body of the while loop 
* the test case would have an input of 2 

| Input | Expected Output |
| ----- | --------------- |
| 1     | 2               |

# Q3 
* Write a (set of) test path(s) that (as a set, if you listed more than one) achieve Edge Coverage but not Prime Path Coverage on the graph. For each of them identify the input(s) that will allow its execution. Suggestions: (1) Start by identifying the TRs for both criteria; (2) more simple test paths will make your job easier when you have to identify the correspondent input than a single complex path 

TRs: { (1, 2), (1, 3), (2, 9), (2, 4), (3, 5), (3, 6), (5, 7), (5, 1), (6, 8), (7, 1), (8, 1) }

| Input | Edges Covered                                                                          | Expected Output | Test Path                               |
| ----- | -------------------------------------------------------------------------------------- | --------------- | --------------------------------------- |
| 3     | (1, 2), (1, 3), (2, 9), (2, 4), (3, 5), (3, 6), (5, 7), (5, 1), (6, 8), (7, 1), (8, 1) | 2 3 5           | [1, 3, 5, 7, 1, 3, 6, 8, 1, 2, 4, 2, 9] |

# Q4 
* Create effective Junit test cases (i.e., check for the correct output condition) for the values questions 2 and 3 

![[Pasted image 20240721182802.png]]