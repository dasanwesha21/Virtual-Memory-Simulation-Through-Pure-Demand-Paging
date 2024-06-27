# Virtual-Memory-Simulation-Through-Pure-Demand-Paging
We simulated a demand-paged virtual memory in this project.

In a typical multiprogramming environment, processes arrive in the system and they are scheduled by the scheduler. Once a process is allocated to CPU, it starts execution and hence CPU starts generating the virtual addresses. The sequence in which the virtual addresses are generated, is known as the page reference string.

Once a virtual address (page number) is generated, it is given to the Memory Management Unit (MMU) to determine the corresponding physical address (frame number). In order to determine the frame number, it consults the page table. If the page reference is illegal, the current process gets terminated, whereas if the page is present in the main memory, the current process can continue its execution.

Otherwise a page-fault occurs. At that point of time, an I/O request needs to be initiated to bring the page from disk to main memory. As a result, the scheduler then takes the CPU away from current process and schedules another process. 

Meanwhile the page-fault handler routine of MMU performs the following activities to bring the requested page into main memory. First, it checks if there is any free frame in main memory. If so, then it loads the page into this frame. Otherwise it identifies a victim page using LRU page-replacement algorithm and brings in the new page. 

Once the page fault is handled, the process comes out of the waiting state and gets added to the ready queue so that it can be scheduled again by the scheduler.

We simulate these activities using four modules
(a) Master is responsible for creating other modules as well as for the initialization of the required data structures.

(b) Scheduler is responsible for scheduling various processes using FCFS algorithm.

(c) MMU translates the page number to frame number and handles page faults.

(d) Process generates the page number from reference string.

After Process completes execution, Scheduler notifies Master. Master terminates Scheduler, MMU, and finally itself.
