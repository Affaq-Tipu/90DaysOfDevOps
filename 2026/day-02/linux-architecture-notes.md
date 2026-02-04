# Day 02 – Linux Architecture, Processes, and systemd

  **How Linux work**

 **.....The core components of Linux....**
The core components of a Linux operating system are the kernel, the user space (composed of the shell, system libraries, and utilities), and the init system (like systemd) which manages their initialization and interaction
**Kernel:** This is the core of the operating system, directly interacting with the hardware. It manages system resources, handles memory management, facilitates process creation and scheduling, and provides file system control
**User Space:** The kernel manages the hardware, but users and applications interact with the system through the user space. This includes:
**System Libraries:** Standardized routines that applications use to interact with the kernel
**Shell:** A command-line interface (e.g., Bash) that translates user commands into instructions for the kernel
System Utilities & Applications: The programs and tools that run on the system (e.g., file editors, networking tools, etc.)
**Init System (systemd):** The first process launched by the kernel during boot-up (it always has a Process ID of 1). Its primary role is to initialize the rest of the system, start all necessary services and daemons, and manage the system throughout its lifecycle.
   **How Processes Are Created and Managed**
 -  Everything in a linux is a process
 - Everything start with a process
   If you run top,htop,tocuh or every command  it becomes a process
   everything that runs ( programs, scripts, daemons ) is a process

Linux mainly usess two system calls to create processes
(a) fork()
       This is the primary mechanism for creating a new process. When a process calls fork() the kernel creates an almost identical copy of the calling (parent) process. The child process inherits a copy of the parent's memory space, open file descriptors, and CPU register states.
(b) exec()
        Often, the child process needs to run a different program than its parent. The exec() family of system calls (e.g., execlp(), execve()) replaces the current process's memory space, code, and data with that of a new program. The PID of the process remains the same, but it begins executing the new program from its entry point.


**Process Management**
  The Linux kernel manages processes using a data structure called the task_struct (process descriptor) which stores all relevant information about a process, including its PID, state, memory map, and list of open files. 

  **What systemd does and why it matters** 
  

     Systemd is the default system and service manager for most modern Linux distributions, acting as the PID 1 initialization system to bootstrap user space and manage processes. It provides fast, parallelized service startup, manages system resources via control groups, controls services, mounts, and devices, and provides logging, networking, and login management. 

  **why  matters??**
         Systemd matters because it is the modern, standardized system and service manager used by nearly all major Linux distributions. It replaced older, slower methods by introducing features like parallel service startup, integrated logging, and consistent management tools, which significantly improved performance and streamlined system administration. 


**Process States**
         **Running/Runnable (R):** The process is either currently using the CPU or is in the run queue waiting for its turn.
**Sleeping (S/D):** The process is inactive, waiting for a resource, timer, or event to complete.
**Interruptible Sleep (S):** Waiting for a resource; can be woken up by signals.
**Uninterruptible Sleep (D):** Waiting for hardware I/O; cannot be interrupted.
**Zombie (Z):** The process has finished execution (terminated), but still has an entry in the process table. The parent process has not yet called wait() to read its exit status.
**Stopped (T):** The process has been suspended, usually by a signal (e.g., SIGSTOP or Ctrl+Z).
**Dead/Terminated (X):** The final state, where the process is being removed from the system. 


# List 5 commands you would use daily
- touch : This command is use to create file
       touch <file name >
- mkdir  : This command is use to create directory ( folder )
       mkdir <directory name>
- top  : This command is use to check running active processes
- cp   : This command is use  for copy file or directory
          cp <source>  <destination>
- ping : This commad is used to check  connectivity
            ping google.com
