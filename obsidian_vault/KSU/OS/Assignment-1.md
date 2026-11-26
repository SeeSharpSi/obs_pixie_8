---
type: assignment
topic: school
---

1. The kernel is used to interface between software and hardware (i.e. file writing). This differs from software because software only interacts with itself (and other capable software) but needs the kernel to make system level calls and to do memory management.
2. Software in kernel mode has the capability to directly interface and execute binary on a computer's hardware. Kernel mode is generally reserved for a computer's trusted functions (and some programs like task manager). Crashes in kernel mode will also crash the entire system because of direct interfacing with the hardware. This is directly adverse to user mode, which requires apis and abstraction to interface with the hardware.
3. 
* Mainframes - these are computers specially designed to handle lots of transactions and data. Generally, several can be linked together.
* Personal Computers - this is an at-home computer that is used for personal reasons like web browsing and day-to-day file operations.
* Embedded System - these are computers with an extremely niche use case. They generally consist of a circuit board with minimal software.
* Parallel systems - these are computers that deal with several of the same hardware. Think one computer with two processors are one motherboard with three graphics cards (like a rendering station).
4. A process control block is a data structure that stores information about a process (i.e. memory allocation). It's used to control the flow, order, and execution of processes.
5. The two models of interprocess communication are Shared Memory and Message Passing. The main difference between the two is memory; Shared Memory processes share a memory buffer and often share variables. Message Passing processes don't share variables or memory. Rather, Message Passing is the way processes that aren't in shared memory communicate; by passing "sends" and "receives" to each other. 
6. A process is a task to be completed, a thread is a type of process that can be managed by a schedular. Typically, threads run in a shared memory space, meaning systems like Windows can find ways to run them "simultaneously." Moreover, threads (the process) can run on several threads (the hardware), meaning they can actually run simultaneously (though this can lead to syncing issues; they've mostly been overcome).

Calculate the speedup using Amdahl’s law if a process, due to data dependency, runs serially for 20% but can be parallelized by 80% running on N=4 cores. Show all work including the math formula.

s = n = 4
p = 80% = 0.80
S = 1 / (1 - p + p/s)
S = 1 / (1 - 0.8 + 0.8/4)
S = 2.5

The base formula for Amdahl's Law is S = 1 / (1 - p + p/s), where…

- S is the speedup of a process
- p is the proportion of a program that can be made parallel, and
- s is the speedup factor of the parallel portion

**How this assignment will be evaluated**

1.      Answers to questions should be in your own words, not copied and pasted from other sources.

2.      Answers to questions should demonstrate understanding and knowledge about the concepts and principles related to the question.

3.      Answers to questions should show appropriate use of scientific/technical terms (instead of casual words).

4.  Answers to questions should be well-structured.

5.  Answers to questions should be fairly or reasonably complete. If questions have several sub-questions, those sub-questions should also be answered.

6.  Answers to questions should be well articulated. Answers should be clear and correctly written using good grammar and spelling.

7.      All work and calculations should be shown for questions involving mathematical work.

8.      If references or images are taken from other sources they should be cited appropriately. APA is preferred, but references must be cited so they can be found.

9.       The assignment should be typed instead of hand-written.

10.   The assignment should be legible and typed in Arial or Times New Roman font.

11.   Any graphs required in the assignment should be constructed with an appropriate tool (instead of hand-drawn)

**Submission Guidelines:**

·        No handwritten submission is accepted, always submit within this document file.  Fonts should not be decorative. Use Arial or Times New Roman fonts.

·         You may include your freehand drawing/image and handwritten scans in the submission. However, the writing and images must be clearly legible.  If I notice them as illegible to me prior to the due date I will let you know to provide clearer version.  This will not change the due date.  It is best to present non-handwritten submissions, generally, as is done in the professional setting.

·         Show all work/calculations.

·         **Please include your last name, first name, and section number at the top of your completed assignment; otherwise, 20% points will be deducted.**

·         Please observe the submission due date and time. After the due date there is a 50% penalty for the next 24 hours. Any submission after 24 hours of the due date will be graded at 0%.

·         If you include a reference or an image taken from other sources, please cite them appropriately. APA is preferred, but cite them so they can be found.

·        If you resubmit, please make sure to attach the file again. Your latest submission before the due date will be graded. 

·         **Please complete your entire work in a single Word Document and Save the file as: yournetid_CS3502_Assignment01.docx; otherwise, 10% points will be deducted. For instance, I would save my file as: cmcmanu2_CS3502_Assignment01.docx. Then upload your file in D2L.**

·        **There is NO extended deadline for this assignment.**

