TARGET DECK
Home::Misc::Operating System Basics

https://www.youtube.com/watch?v=9GDX-IyZ_C8
*Brian Will*
# Operating System <!--fc-->
Manages the hardware and running programs
<!--ID: 1721856562045-->


## Basic tasks an operating system performs <!--fc-->
- load and manage programs
- provide interfaces to hardware via system calls
- provide a filesystem
- provide a basic user interface
<!--ID: 1721856562050-->


# Device Driver <!--fc-->
Plug-in module of the OS that handles the functionality of IO devices.
![[Pasted image 20240724152248.png]]
<!--ID: 1721856562055-->


# Running multiple processes at a time <!--fc-->
The time spent on processes on a particular CPU core are split between the process(es) themselves and OS activities. Two cores will not run the same process at the same time
![[Pasted image 20240724152503.png]]
<!--ID: 1721856562059-->


## Pre-emptive multitasking <!--fc-->
A scheduler runs after each process to see if any OS work should be done, and which process should run next. Running processes are stopped with hardware interrupts, which then defers to the scheduler.
- CPU receives interrupt
- Interrupt stores program counter
- Interrupt invokes handler
- Handler saves rest of state of the CPU for the process
- Handler does its business
- Handler invokes the scheduler
- Scheduler selects process to run
- Scheduler restores state of the CPU for that process
- Scheduler jumps execution to that process.
<!--ID: 1721856562064-->

## Ensuring Scheduler runs <!--fc-->
To ensure the scheduler runs on a regular basis, a clock device on the board regularly sends an interrupt (10, 20 ms). This guarantees the process changes regularly.
<!--ID: 1721868653803-->



# System Memory <!--fc-->
It is the OS's job to makes sure multiple processes don't trespass on memory space used by other processes and to OS itself
![[Pasted image 20240724153805.png]]
This restriction is enforced by the hardware, but processes need to be able to make system calls so there needs to be a workaround.
<!--ID: 1721868653807-->


## System Calls <!--fc-->
Processes can invoke a special instruction (*usually called `syscall`*) in which the process specifies a system call number
When this instruction is invoked, the processor looks in the system call table for the address of the routine corresponding to that number, and jumps to its instruction. The OS controls this table.
<!--ID: 1721868653813-->


## Privilege Levels <!--fc-->
The CPU runs in two different privilege levels.
- When OS code is run, the CPU is put into a privilege level that allows access of IO devices and any address of memory
- When processes are run, the CPU is put into a privilege level that triggers a hardware exception when the code attempts to access the IO devices or addresses not allowed for that process. Processes are supposed to touch only their own memory
<!--ID: 1721868653817-->


# How Processes use Memory <!--fc-->
Each process uses a portion for it's memory for its
- Text (the code (binary instructions))
- Call Stack (local variables)
- Heap (everything else)
![[Pasted image 20240724155957.png]]
<!--ID: 1721868653821-->


## The stack <!--fc-->
A contiguous array of memory that starts out unused. When the first function is called, its local variables are stored on its *frame*.
Any functions called from this are stored on another frame on top with the return address to the previous function.
When the function returns, the stack pointer goes back to the previous frame.
- Frames don't need to be deleted, they can be overwritten when needed
![[Pasted image 20240725151033.png]]
<!--ID: 1721952266892-->


### Stack boundary <!--fc-->
Keeps track of the size of the stack. When the stack space passes this, a hardware exception is triggered and the stack space is increased. In some cases the stack space may be too large and the process will be terminated (i.e.: stack overflow)
<!--ID: 1721952266896-->


## Common Memory layout for a process
- Stack at the top
- Text (code) at the bottom
- Space left in between for heap allocation
![[Pasted image 20240725152146.png]]

## Heap allocation <!--fc-->
Done with system calls. The OS decides where these chunks of memory are allocated, they won't necessarily be adjacent. When a process is done with the heap, the space is given back to the OS with a deallocate
As more heap space is allocated, the allowed space per heap chunk will get smaller (*memory leak*), as each one needs to be contiguous. To avoid this, be sure to deallocate memory when not needed.
<!--ID: 1721952266900-->


## Address space to system memory <!--fc-->
Address space isn't actually contiguous, chunks of the address space are mapped to RAM by the OS
![[Pasted image 20240725165024.png]]
When the OS runs a process, it lists these mappings in a table. It uses this table to map addresses.
- Each process has it's own address space, a separate table is used for each process. Thus each process can only access its own memory. *Pages*
<!--ID: 1721952266909-->


### Swapped pages <!--fc-->
To free up RAM, the OS may decide to swap out pages of a process to storage (hard drive). In the table, these pages would be marked *swapped*.
An attempt by the process to access this page will trigger an exception, at which point the OS will copy the swapped page back to RAM and adjust the memory table accordingly.
<!--ID: 1721952266915-->



# Lifecyle of a Process <!--fc-->
In its lifecycle, a process moves through a few major states
- The OS does what it needs at the point of process *creation*
- The process then moves into the *waiting* state
- When the scheduler selects the process to run, it moves to the *running* state, then back to *waiting*
- When the process ends, it enters its final state; *terminated*
![[Pasted image 20240725171130.png]]
<!--ID: 1721952266921-->


## Blocked state <!--fc-->
![[Pasted image 20240725171155.png]]
In the blocked state, the process is waiting for some external event in the system before before it can proceed rather than waiting to be scheduled.
- Most commonly, a process will be in the blocked state when invoking certain system calls, such as reading files
Once the external event takes place, the process is put back into the waiting state so the scheduler can consider it again.
**Only in the waiting state will the scheduler select the process to run**
<!--ID: 1721952266926-->



# The File System <!--fc-->
Operating systems provide a layer of abstraction for storage devices called the *file system*, which presents storage space as a hierarchy of directories with files stored in those directories.
This way, you don't have to worry about the particulars of each type of storage device.
<!--ID: 1721952266931-->


## Partitions <!--fc-->
The storage area of each drive is divided into one or more contiguous chunks known as *partitions*
![[Pasted image 20240725174812.png]]
<!--ID: 1721952266936-->


## Identifiers <!--fc-->
In most partition formats used today, each file and directory in a partition is known by an identifier number unique within that partition
![[Pasted image 20240725175030.png]]
*e.g.; there can only be one file known as 35, and no directories can be 35 within this particular partition*
<!--ID: 1721952266941-->


## How are files stored? <!--fc-->
Files are a contiguous sequence of bytes
Files on disc may actually be stored out of order, it is the file system's job to make sure a file's *logical order* is reconstructed when the file data is sent to a program.
<!--ID: 1721952266949-->


## The root directory <!--fc-->
When a partition is created, it will have nothing in it but the *root directory*, which cannot be deleted.
<!--ID: 1721952266956-->


## File paths <!--fc-->
A file path is a string of text denoting where a file or directory is on the system
![[Pasted image 20240725175657.png]]*Partitions are denoted by letters in Windows*
*Not in Unix, `/whatever` denotes the root directory there*
<!--ID: 1721952266961-->


# IPC (Interprocess Communication) <!--fc-->
An umbrella term for any mechanism of the CPU that facilitates communication between processes.
- e.g.: Files can be read and written by multiple processes, thus can be used as a method of communication between them
![[Pasted image 20240725180320.png]]
<!--ID: 1721952266967-->
