---
type: assignment
topic: school
---

# Question 1
## Zip Codes: 00600-98000 inclusive 
Equivalence Partitions:
* value < 00600 (invalid input) 
* 00600 <= value <= 98000 (valid input) 
* value < 0 (invalid input) 
* value > 98000 (invalid input) 

Test cases:

| Partition Type | Partition Description   | Test Cases     |
| -------------- | ----------------------- | -------------- |
| invalid        | value < 00600           | 30, 800        |
| valid          | 00600 <= value <= 98000 | 00600, 40000   |
| invalid        | value < 0               | -1, -500       |
| invalid        | value > 98000           | 100000, 101000 |

## States: AL-WY
Equivalence Partitions:
* AL <= value <= WY (valid input) 
* value != state (invalid input) 
* value < 2 letters (invalid input)
* value > 2 letters (invalid input)

Test cases:

| Partition Type | Partition Description | Test Cases |
| -------------- | --------------------- | ---------- |
| valid          | AL <= value <= WY     | CA, DE     |
| invalid        | value != state        | ZZ, LM     |
| invalid        | value < 2 letters     | M, P       |
| invalid        | value > 2 letters     | MOP, PAN   |
<div class="pb"></div>

## Last Name: One through twelve characters (alphabetic, space and hyphen)
Equivalence Partitions:
* value includes number (invalid input) 
* value < 1 length (invalid input) 
* value > 12 length (invalid input) 
* 1 <= value <= 12 length, only letters/spaces/hyphens (valid input) 

Test cases:

| Partition Type | Partition Description                                | Test Cases    |
| -------------- | ---------------------------------------------------- | ------------- |
| invalid        | value includes number                                | add4, alij1   |
| invalid        | value < 1 length                                     |               |
| invalid        | value > 12 length                                    | qwertyuiopadf |
| valid          | 1 <= value <= 12 length, only letters/spaces/hyphens | hello world   |

## User ID: Eight characters, at least two of which are not alphabetic (numeric, special characters)
Equivalence Partitions:
* value > 8 length (invalid input)
* value < 8 length (invalid input)
* value contains < 2 non-alphabetic chars (invalid input) 
* value = 8 length, has >= 2 non-alphabetic chars 

Test cases:

| Partition Type | Partition Description                           | Test Cases         |
| -------------- | ----------------------------------------------- | ------------------ |
| invalid        | value > 8 length                                | asd12fgji          |
| invalid        | value < 8 length                                | 12ef               |
| invalid        | value has < 2 non-alphabetic chars              | 1abdhgir           |
| valid          | value = 8 length, has >= 2 non-alphabetic chars | 12erty3o, 12fjahwu |
<h2 class="pb"</h2>

# Question 2
Equivalent Partitions:
* Between 90 and 100, inclusive (valid input)
* Between 80 and 89, inclusive (valid input)
* Between 70 and 79, inclusive (valid input)
* Between 60 and 69, inclusive (valid input)
* 59 and below (valid input)
* Above 100 (invalid input) 
* Below 0 (invalid input)

The test cases given below use the boundaries of n-1, n, n+1

| Test Case # | Input | Expected Output |
| ----------- | ----- | --------------- |
| 1           | 101   | Error           |
| 2           | 100   | A               |
| 3           | 99    | A               |
| 4           | 91    | A               |
| 5           | 90    | A               |
| 6           | 89    | B               |
| 7           | 88    | B               |
| 8           | 81    | B               |
| 9           | 80    | B               |
| 10          | 79    | C               |
| 11          | 78    | C               |
| 11          | 70    | C               |
| 12          | 69    | D               |
| 13          | 68    | D               |
| 14          | 61    | D               |
| 15          | 60    | D               |
| 16          | 59    | F               |
| 17          | 58    | F               |
| 18          | 1     | F               |
| 19          | 0     | F               |
| 20          | -1    | F               |

![[Pasted image 20240707001205.png]]