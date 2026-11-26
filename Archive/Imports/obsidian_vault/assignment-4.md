---
type: assignment
topic: school
---

#IT4823 
Assignment #4

Software Security &

Buffer Overflow Concepts

**Part 1: Software Security [70 points]**

|   |   |
|---|---|
|**1.**    **[10 points] Explain the difference between Dynamic and Static code analysis**<br><br>[**https://www.overops.com/blog/static-vs-dynamic-code-analysis-how-to-choose-between-them/**](https://www.overops.com/blog/static-vs-dynamic-code-analysis-how-to-choose-between-them/)<br><br>**2.**     **[50 points] Below is a list of Software Application Security tools. Research 2 tools of your choice (One from each group below)**<br><br>(a)   One from this group<br><br>a.     Rapid7<br><br>b.    Klocwork<br><br>c.     SonarQube<br><br>(b)   One from this group<br><br>a.     Veracode<br><br>b.    HCL AppScan<br><br>c.     Checkmarx<br><br>**Document in the matrix below what each tool can do in relation to typical software security scanning and vulnerabilities [25 points x 2].**  <br><br>**1.**    **Tool 1**<br><br>**a.**     **Overview**<br><br>**b.**    **Dynamic vs Static Code Analyzer (or both)**<br><br>**c.**     **Vulnerabilities identified (SQLi, etc.)**<br><br>**d.**    **Software Languages, supported. Tools, etc. supported**<br><br>**e.**    **Costs**<br><br>**f.**      **Other advantages or disadvantages**<br><br>**2.**    **Tool 2**<br><br>**a.**     **Overview**<br><br>**b.**    **Dynamic vs Static Code Analyzer (or both)**<br><br>**c.**     **Vulnerabilities Identified (SQLi, etc.)**<br><br>**d.**    **Software Languages. Tools, etc. supported**<br><br>**e.**    **Costs**<br><br>**f.**      **Other advantages or disadvantages**<br><br>\|   \|   \|   \|<br>\|---\|---\|---\|<br>\|**Area to Compare**\|**Tool 1**\|**Tool 2**\|<br>\|Overview\|<br>\|Dynamic vs Static Code Analyzer (or both)\|<br>\|Vulnerabilities Identified (SQLi, etc.)\|<br>\|Software Languages. Tools, etc. supported\|<br>\|Costs\|<br>\|Other\|<br><br>**3.**    **Which would you recommend of the two and why?  [10 points]**||
|||

**Part 2: Buffer Overflow      [30 points]**

**Question 1:  Draw and explain a function stack . Be sure to communicate what is happening and what will happen when the strcpy occurs.**  Use the following C code to depict the stack/heap like the slides 15 in the buffer overflow teaching materials. [**20 point**]

int main () //think of main like P

{

int returnedvalue.

/* In C, a function can return values */

/* Now you are passing a string into buffered */

/* the function buffered returns a value */

returnedvalue =  buffered (“12345678910”);

/* think of bof as Q; don’t forget your parameters */

return 0;

}

int buffered (char *str)

{

char mybuffer [10];  strcpy (mybuffer, str); return 1;

}

**Answer:**

**Question 2:** Is this following code segment safe? **Explain** **why or why not**? [**10 points**]

/* Assume this function can be called from a C program */

 int bof (char *str, int size) {

char *buffer = (char *) malloc (size); strcpy (buffer, str);

return 1;

}

Notes: malloc is a C library function that allocates space of a specific size