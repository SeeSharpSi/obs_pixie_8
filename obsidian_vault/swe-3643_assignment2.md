---
type: assignment
topic: school
---

# Assignment 2
* Silas Tompkins
* SWE 3643
* 6-16-2024

# Part 1 

### Test Cases

| ID# | Input Data                                                          | Statements Covered          | Expected Output | Actual Output      | Pass/Fail | % Coverage |
| --- | ------------------------------------------------------------------- | --------------------------- | --------------- | ------------------ | --------- | ---------- |
| 1   | incomeList []<br>childList[]<br>parentList[]                        | 1-3, 7-8, 16-17, 31-33      | 0               | 0                  | Pass      | 30.3%      |
| 2   | incomeList[40001]<br>childList[20, 17, 17, 17]<br>parentList[61]    | 1-5, 9-10, 16-30, 37-41     | 0               | -4399.93           | Fail<br>  | 81.81%     |
| 3   | incomeList[40000, 50000]<br>childList[19]<br>parentList[59, 61, 60] | 1-5, 11-12, 16-30, 37-41    | 12400           | 12400              | Pass      | 81.81%     |
| 4   | incomeList[120001]<br>childList[20]<br>parentList[59]               | 1-5, 13-15, 16-30, 37-41    | 28800.17        | 28800.170000000002 | Pass      | 81.81%     |
| 5   | incomeList[]<br>childList[10]<br>parentList[61]                     | 1-5, 7-8,  16-30, 31, 34-35 | 0               | 0                  | Pass      | 75.75%     |

The textbook states "when we consider a two-way decision construct like the if statement, then to cover all the statements, we should also cover the then and else parts of the if statement. This means we should have, for each if then else, (at least) one test case to test the Then part and (at least) one test case to test the else part" (3.3.2.1, paragraph 6). This is why there are several cases of duplicate statement coverage; to cover the if-else parts of the statement.
I also counted 32 statements, which is how I made my calculations for the % coverage. 
The outputs show that the function to cap tax exemption subtracts too much tax and causes the amount to be negative.

<div class="pb"></div>

# Part 2
### Flow chart:
![[Pasted image 20240616173425.png|550]]

<div class="pb"></div>

### Test Cases

| ID# | Input Data                                                              | Paths Covered                 | Expected Output | Actual Output | Pass/Fail | % Coverage |
| --- | ----------------------------------------------------------------------- | ----------------------------- | --------------- | ------------- | --------- | ---------- |
| 1   | incomeList[]<br>childList[]<br>parentList[]                             | A-C-J-N-Q-S                   | 0               | 0             | Pass      | 2.63%      |
| 2   | incomeList[]<br>childList[17,19]<br>parentList[]                        | A-C-I-K-L-J-N-Q-T             | 0               | 0             | Pass      | 2.63%      |
| 3   | incomeList[]<br>childList[19, 17,17,17,17,17]<br>parentList[]           | A-C-I-K-L-J-N-R               | 0               | -8000         | Fail      | 2.63%      |
| 4   | incomeList[]<br>childList[17,19]<br>parentList[59,61]                   | A-C-I-K-L-J-M-O-P-N-Q-T       | 0               | 0             | Pass      | 2.63%      |
| 5   | incomeList[]<br>childList[17,19]<br>parentList[59,61,61]                | A-C-I-K-L-J-M-O-P-N-R         | 0               | 0             | Pass      | 2.63%      |
| 6   | incomeList[]<br>childList[]<br>parentList[59,61]                        | A-C-J-M-O-P-N-Q-T             | 0               | 0             | Pass      | 2.63%      |
| 7   | incomeList[]<br>childList[]<br>parentList[59,61,61,61]                  | A-C-J-M-O-P-N-R               | 0               | 0             | Pass      | 2.63%      |
| 8   | incomeList[39000]<br>childList[]<br>parentList[]                        | B-A-C-J-N-Q-S                 | 780             | 780           | Pass      | 2.63%      |
| 9   | incomeList[79000]<br>childList[]<br>parentList[]                        | B-A-D-E-J-N-Q-S               | 6330            | 6330          | Pass      | 2.63%      |
| 10  | incomeList[119000]<br>childList[]<br>parentList[]                       | B-A-D-F-G-J-N-Q-S             | 17880           | 17880         | Pass      | 2.63%      |
| 11  | incomeList[121000]<br>childList[]<br>parentList[]                       | B-A-D-F-H-J-N-Q-S             | 28970           | 28970         | Pass      | 2.63%      |
| 12  | incomeList[39000]<br>childList[19,17]<br>parentList[]                   | B-A-C-I-K-L-J-N-Q-S           | 0               | 0             | Pass      | 2.63%      |
| 13  | incomeList[100]<br>childList[19,17]<br>parentList[]                     | B-A-C-I-K-L-J-N-Q-T           | 0               | 0             | Pass      | 2.63%      |
| 14  | incomeList[39000]<br>childList[19,17,17,17,17,17]<br>parentList[]       | B-A-C-I-K-L-J-N-R             | 0               | 0             | Pass      | 2.63%      |
| 15  | incomeList[79000]<br>childList[17]<br>parentList[]                      | B-A-D-E-I-K-L-J-N-Q-S         | 0               | 0             | Pass      | 2.63%      |
| 16  | incomeList[79000]<br>childList[17,17,17,17,17,19]<br>parentList[]       | B-A-D-E-I-K-L-J-N-R           | 6330            | -1670         | Fail      | 2.63%      |
| 17  | incomeList[119000]<br>childList[19,17]<br>parentList[]                  | B-A-D-F-G-I-K-L-J-N-Q-S       | 13880           | 13880         | Pass      | 2.63%      |
| 18  | incomeList[119000]<br>childList[19,17,17,17,17,17]<br>parentList[]      | B-A-D-F-G-I-K-L-J-N-R         | 9880            | 9880          | Pass      | 2.63%      |
| 19  | incomeList[121000]<br>childList[19,17]<br>parentList[]                  | B-A-D-F-H-I-K-L-J-N-Q-S       | 24970           | 24970         | Pass      | 2.63%      |
| 20  | incomeList[121000]<br>childList[19,17,17,17,17,17]<br>parentList[]      | B-A-D-F-H-I-K-L-J-N-R         | 20970           | 20970         | Pass      | 2.63%      |
| 21  | incomeList[100]<br>childList[19,17]<br>parentList[59,61]                | B-A-C-I-K-L-J-M-O-P-N-Q-S     | 0               | 0             | Pass      | 2.63%      |
| 22  | incomeList[100]<br>childList[19,17]<br>parentList[59,61]                | B-A-C-I-K-L-J-M-O-P-N-Q-T     | 0               | 0             | Pass      | 2.63%      |
| 23  | incomeList[39000]<br>childList[19,17,17,17,17,17]<br>parentList[59,61]  | B-A-C-I-K-L-J-M-O-P-N-R       | 0               | -7220         | Fail      | 2.63%      |
| 24  | incomeList[41000]<br>childList[]<br>parentList[]                        | B-A-D-E-I-K-L-J-M-O-P-N-Q-S   | 820             | 820           | Pass      | 2.63%      |
| 25  | incomeList[79000]<br>childList[19,17]<br>parentList[59,61,61]           | B-A-D-E-I-K-L-J-M-O-P-N-R     | 0               | 0             | Pass      | 2.63%      |
| 26  | incomeList[119000]<br>childList[19,17]<br>parentList[59,61]             | B-A-D-F-G-I-K-L-J-M-O-P-N-Q-S | 11880           | 11880         | Pass      | 2.63%      |
| 27  | incomeList[119000]<br>childList[19,17,17,17,17,17]<br>parentList[59,61] | B-A-D-F-G-I-K-L-J-M-O-P-N-R   | 9880            | 9880          | Pass      | 2.63%      |
| 28  | incomeList[121000]<br>childList[19,17]<br>parentList[59,61]             | B-A-D-F-H-I-K-L-J-M-O-P-N-Q-S | 22970           | 22970         | Pass      | 2.63%      |
| 29  | incomeList[121000]<br>childList[19,17,17,17,17,17]<br>parentList[59,61] | B-A-D-F-H-I-K-L-J-M-O-P-N-R   | 20970           | 20970         | Pass      | 2.63%      |
| 30  | incomeList[39000]<br>childList[]<br>parentList[59,61]                   | B-A-C-J-M-O-P-N-Q-S           | 0               | 0             | Pass      | 2.63%      |
| 31  | incomeList[100]<br>childList[]<br>parentList[59,61]                     | B-A-C-J-M-O-P-N-Q-T           | 0               | 0             | Pass      | 2.63%      |
| 32  | incomeList[100]<br>childList[]<br>parentList[59,61,61,61,61,61]         | B-A-C-J-M-O-P-N-R             | 0               | -7998         | Fail      | 2.63%      |
| 33  | incomeList[79000]<br>childList[]<br>parentList[59,61]                   | B-A-D-E-J-M-O-P-N-Q-S         | 4330            | 4330          | Pass      | 2.63%      |
| 34  | incomeList[79000]<br>childList[]<br>parentList[59,61,61,61,61,61]       | B-A-D-E-J-M-O-P-N-R           | 0               | -1669         | Fail      | 2.63%      |
| 35  | incomeList[119000]<br>childList[]<br>parentList[59,61]                  | B-A-D-F-G-J-M-O-P-N-Q-S       | 15880           | 15880         | Pass      | 2.63%      |
| 36  | incomeList[119000]<br>childList[]<br>parentList[59,61,61,61,61,61]      | B-A-D-F-G-J-M-O-P-N-R         | 17880           | 9880          | Pass      | 2.63%      |
| 37  | incomeList[121000]<br>childList[]<br>parentList[59,61]                  | B-A-D-F-H-J-M-O-P-N-Q-S       | 26970           | 26970         | Pass      | 2.63%      |
| 38  | incomeList[121000]<br>childList[]<br>parentList[59,61,61,61,61,61]      | B-A-D-F-H-J-M-O-P-N-R         | 28970           | 20970         | Fail      | 2.63%      |

The textbook does not specify, so I am assuming that a test case that goes over multiple paths is still considered a singular path, and that the sub paths still need crossed (e.g. a test case going over A-B-D would not negate the need for a test case to go over A-D if B is possible to skip). This resulted in a lot of test cases, because conditionals add a multiplicative amount of test cases.
Still, many test cases were deleted because the pathing was not possible. For example, several paths would need to invoke the condition that income was greater than $120k and not invoke the tax exemption loops, meaning the condition that tax was less than zero was not possible to invoke.
Just like the last set of test cases, the outputs show that the function to cap tax exemption subtracts too much tax and causes the amount to be negative. Unlike the last test, there is a lot more to go off of.

<div class="pb"></div>

# Part 3
### Test Cases

| ID# | Input Data                                   | Loops Covered | Expected Output | Actual Output | Pass/Fail | % Coverage |
| --- | -------------------------------------------- | ------------- | --------------- | ------------- | --------- | ---------- |
| 1   | incomeList[]<br>childList[]<br>parentList[]  | N/A           | 0               | 0             | Pass      | 0%         |
| 2   | incomeList[1]<br>childList[]<br>parentList[] | 4             | 0.02            | 0.02          | Pass      | 33.33%     |
| 3   | incomeList[]<br>childList[1]<br>parentList[] | 18            | 0               | 0             | Pass      | 33.33%     |
| 4   | incomeList[]<br>childList[]<br>parentList[1] | 25            | 0               | 0             | Pass      | 33.33%     |

The program has three loops (total income, child tax deductible, parent tax deductible). Each loop has three boundaries: n-1, n, n+1 (as stated by the textbook). That said, coverage will be calculated as a portion of three, one for each loop gone through, because if it was calculated out of nine it would be 100% each time. The textbook doesn't specify testing the different cases of if-statements inside of each loop so I'm assuming it's not required here, though that would be useful for future testing (and was covered in path testing anyways).
This specific program does not have an upper bound on each for loop, meaning that, while testing for n-1 is possible, n+1 is not.