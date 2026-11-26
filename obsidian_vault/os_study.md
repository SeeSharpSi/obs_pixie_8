---
type: study
topic: school
---

#school #study #CS3502 
# Deadlocks
* Mutual Exclusion - Only one process at a time can use a resource
* Hold and wait - a process holding at least one resource is waiting to acquire additional resources held by other processes
* No preemption - a resource can be released only voluntarily by the process holding it, after that process has completed its task
* Circular Wait - There exists a set {P_0, P_1, . . ., P_n} of waiting processes such that P_0 is waiting for a resource that is held by P_2, . . ., P_n-1 is waiting for a resource that is held by P_n, and P_n is waiting for a resource that is held by P_0

# Resource Allocation Graphs
* A set of vertices V and a set of edges E
* V is partitioned into two types:
	* P = {P_1, P_2, . . ., P_n}, the set consisting of all the processes in the system
	* R = {R_1, R_2, . . ., R_m}, the set consisting of all resource types in the system
* request edge - directed edge P_1 -> R_j
* assignment edge - directed edge R_j -> P_i
![[Pasted image 20231024141204.png | 200]]

# Identify Atomic Methods
* Cannot be interrupted

# Identify Mutual Exclusion / Identify Bounded Waiting / Critical Section, Race Conditions
* Mutual Exclusion - If process P_i is executing in its critical section, then no other processes can be executing in their critical sections
* Bounded waiting - A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted
* Two approaches depending in if kernel is preemptive or non-preemptive
	* Preemptive - allows preemption of process when running in kernel mode
	* Non-preemptive - runs until exists kernel mode, blocks, or voluntarily yields CPU
	* Essentially free of race conditions in kernel mode
* If two thing want same then how decide which go
# Advantages/Disadvantages of Preemptive Kernels
A preemptive kernel allows a process to interrupt another running process allowing
it to run, whereas a non-preemptive kernel requires a process to exit kernel mode before other processes can run. This means that preemptive kernels are better for fast/guaranteed response times, while non-preemptive kernels are easier to use.
# Characteristics Advantages/Disadvantages of spinlocks
A spinlock is called such because it's a lock that puts threads waiting on it in a loop that continuously checks the lock's state. One advantage of spinlocks is their low overhead. That said, it wouldn't be a good idea to use them for tasks that would have them be blocked for long periods because they can keep other threads from running. This means that using a spinlock on a 10Mb transfer is not a good idea (though I do wonder how long 10Mb will be "large" in the context of OS calls).

# Counting Semaphores and binary semaphores
![[Pasted image 20231024162308.png | 400]]
![[Pasted image 20231024162539.png | 400]]

# Characteristics of and differences between scheduling algorithms

# Reader-Writer First Reader
![[Pasted image 20231024170130.png]]

# CPU Scheduling, CPU Utilization

# CPU Throughput

# CPU Turnaround

# Waiting Time

# Response Time

# Memory Stall