---
type: assignment
topic: school
---

# Equivalence Partitioning

---
# Benefits 
* Less tests for more coverage (as opposed to other methods) 
* Easy to identify

--- 
# Partition
* Consists of a set of at least one input value 
* Has one expected output/behavior

In other words, inputs are grouped by their outputs

---
# Tests
Testing based on equivalence partitions involves selecting one member value from each partition to write a test case for

--- 
# Example
| Height       | Roller Coaster # |
| ------------ | ---------------- |
| Under 4 feet | 3                |
| 4-5 feet     | 5                |
| 5-6 feet     | 7                |
| Over 6 feet  | 10               |

---
### Partitions:
* Shorter than 4 feet (valid input) 
* Between 4 and 5 feet (valid input) 
* Between 5 and 6 feet (valid input) 
* Over 6 feet (valid input)
* 0 feet (invalid input) 
* Negative feet (invalid input) 

---
### Test Cases 
| Validity | Inputs   | Expected Output |
| -------- | -------- | --------------- |
| valid    | 2, 3     | 3               |
| valid    | 4, 4.2   | 5               |
| valid    | 5.3, 5.9 | 7               |
| valid    | 6.5, 8   | 10              |
| invalid  | 0        | Error           |
| invalid  | -2,-5    | Error           |

---

* Equivalence partitioning is a software testing technique that involves identifying a small set of representative input values that produce as many different output conditions as possible
* The set of input values that generate one single expected output is called a _partition_
	* When the behavior of the software is the same for a set of values, then the set is termed as an _equivalance class_ or a _partition_
---
testing

---
# this is how it's done

---
