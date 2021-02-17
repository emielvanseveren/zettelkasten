---
Title: Sysinternals
Description: What is sysinternals?
Date: 06-07-2020
Tags: #windows
References:
Editor: markdown
---

# SysInternal Tools

## General
The sysinternals website was created in 1996 by Mark Russinovich to host his advanced system utilities and technical information. Whether you are an IT Pro or a developer, you'll find Sysinternals utilities to help you manage, troubleshoot and diagnose your Windows systems and applications. see [sysinternal](https://docs.microsoft.com/en-us/sysinternals/).

## Possible usage for QA

### Cpustres 
[Download](https://docs.microsoft.com/en-us/sysinternals/downloads/cpustres) - Cpustres is a utility can be used to simulate CPU activity by running up to 64 threads in a thight loop. Each thread can be started, paused or stopped independently and can be configured with the following parameters:

Activity Level This can be Low, Meidcum, Busy or Maximum which controls how long the thread sleeps between cycles. Setting this value to Maximum causes the thread to run continuously. Priority this controls the thread priority. To be used with caution see [simulate cpu, memory, disk load](https://blog.msdn.microsoft.com/vijaysk/2012/10/26/tools-to-simulate-cpu-memory-disk-load/)

### Process Explorer
[Download](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer) - Shows you information about which handles and DLLs processes have openen or loaded. 

### Testlimit
[Download](https://docs.microsoft.com/en-us/sysinternals/downloads/testlimit) - Testlimit is a command-line utility that can be used to stress-test your PC and/or applicationns by simulating low resource conditions for memory, handles, processes, thread and other system objects.

### VMMap
[Download](https://docs.microsoft.com/en-us/sysinternals/downloads/vmmap) - VMMap is a process virutal and physical memory analysis utility. It shows a breakdown of a process's committed virtual memory types as well as th eamount of physical memory (working set) assigned by the operaitng system to those types. Besides graphical representations of memory usage, vMMap also shows summary information and a detailed process memory map. Powerful filtering and refresh capabilities allow you to identify the sources of process memory usage and the memory cost of application features. 
