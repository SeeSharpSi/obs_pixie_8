---
type: assignment
topic: school
---

#school #CS3502
- Always submit within this document file.
- You may include your freehand drawing/image and handwritten scans in the submission. However, the writing and images must be clearly legible.  If I notice them as illegible to me prior to the due date I will let you know to provide clearer version.  This will not change the due date.  It is best to present non-handwritten submissions, generally, as is done in the professional setting.
- Show all work/calculations.
- **Please complete your entire work in a single Word Document and Save the file as: yournetid_CS3502_Assignment01.docx; otherwise, 25% points will be deducted. For instance, I would save my file as: cmcmanu2_CS3502_Assignment02.docx. Then upload your file in D2L.**
- Please observe the submission due date and time. After the due date there is a 50% penalty for the next 24 hours. Any submission after 24 hours of the due date will be graded at 0%.
- If you include a reference or an image taken from other sources, please cite them appropriately. APA is preferred, but cite them so they can be found.
- If you resubmit, please make sure to attach the file again. Your latest submission before the due date will be graded. 
- **There is NO extended deadline for this assignment.**

# Q-1
What are the three requirements of a solution to the Critical Section Problem? Provide their definitions.

* Mutual Exclusion - If a process is executing in its critical section, then no other processes can be executing in their critical sections
* Progress - If no process is executing in its critical section and there exist some processes that wish to enter their critical section, then the selection of the processes that will enter the critical section next cannot be postponed indefinitely.
* Bounded waiting - A bound must exist on the number of times that other processes are allowed to enter its critical section and before that request is granted.

# Q-2
What does the preemption in kernels do for Process Synchronization vs. non-preemptive kernels?

A preemptive kernel allows a process to interrupt another running process allowing it to run, whereas a non-preemptive kernel requires a process to exit kernel mode before other processes can run. This means that preemptive kernels are better for fast/guaranteed response times, while non-preemptive kernels are easier to use.

# Q-3
What is one advantage of using a spinlock? Would it be a good idea to have a process hold with a spinlock (such as compare and swap() or test_and_set()) while waiting on a process or thread that is waiting on a 10Mb transfer from the hard drive?

A spinlock is called such because it's a lock that puts threads waiting on it in a loop that continuously checks the lock's state. One advantage of spinlocks is their low overhead. That said, it wouldn't be a good idea to use them for tasks that would have them be blocked for long periods because they can keep other threads from running. This means that using a spinlock on a 10Mb transfer is not a good idea (though I do wonder how long 10Mb will be "large" in the context of OS calls).

# Q-4
**Define what an atomic operation is.   Give one example of an operation that is atomic given in Chapter 5.**

An atomic operation is an operation that is either completed or not executed at all, meaning it cannot be interrupted by other operations. The wait() operation is given as an example; weight() decrements the value of a semaphore.

# Q-5
* Process 111: s1 becomes -2, *list stays the same
* Process 91: s1 becomes -1, *list stays the same
* Process 110: s1 becomes -2, *list becomes { 100, 101, 105, 110}
* Process 93: s1 becomes -1, *list stays the same
* Process 95: s1 becomes 0, *list stays the same
* Process 113: s1 becomes 1, 100 is awoken from the list
* Process 105: s1 becomes 2, 105 is in the list, so *list stays the same

# Q-6
What is the readers-writers problem? There are two variations referred to as first and second readers, what new problem does the solution to first and second readers problem introduce?

The readers-writers problem is the issue of how to allow two readers to read the same data at the same time. Two variations of the solution are first and second readers. Both suffer from "starvation" issues, meaning writers take last priority.

# Q-7
Gantt charts (created using the drawing tool Excalidraw)
Shortest job first without preemption:
![[Pasted image 20231018230945.png]]
Shortest Job First with preemption based on remaining run time:
![[Pasted image 20231018231707.png]]
The average wait time for 1) is (18+0+0+8)/4= 6.5ms
The average wait time for 2) is (18+0+5+0)/4= 5.75ms

# Q-8
What benefit does Round Robin provide over First Come First Serve for scheduling? What computing environment is better suited for Round Robin?

Round Robin has far better response than First Come First Server. Especially in multi-tasking; think of watching YouTube while writing a document. First Come First Server would require the video to finish before key presses register in your document. Whereas Round Robin would allow both to run at the "same time" (yes, you can multithread without Round Robin. It's just for demonstration). This is because Round Robin is starvation free.
Round Robin is best for environments that need high response; namely Operating Systems and Cloud Computing.

# Q-9
What technique can be used to remediate starvation in a scheduling algorithm?

Aging can be used to remediate starvation in queues because it adds priority to processes that have been in queue for longer.