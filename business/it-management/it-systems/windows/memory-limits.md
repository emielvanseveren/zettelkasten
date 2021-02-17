---
Title: Memory limits
Description: 
Date: 06-07-2020
Tags: #windows
References:
Editor: markdown
---

# Memory limits in Windows

out of memory can happen on various levels. Here is some more information about which memory limits exist in Windows.

**Operating system level**
Windows can run out of memory when the address space is full, or when both RAM and the page fill are full. Today, with 64 bit operating sytems, it's unlikely you will address too much memory. When the RAM is full, Windows starts using the page file. This will have a negative impact on the performance of the server since Windows starts to use the disk as memory which is a lot slower. This will also have a negative impact on the disk busyu time. But it doe snot immediately cause an out of memory condition, unless your page file is limited and that limit has been reached. 

**Process level**
The memory limitations of a process is the most common cause of out of memory errors (like CMemoryException), especially when it concerns a 32 bit processes.  32 bit means only 4GB of memory can be addressed, in other words when you reach 4GB, out of memory errors will happen. This is assuming the process is running on a 64 bit OS, if it would run on a 32 bit OS, only half of it would be available for the process. 

The 4GB limit can not only be reached by parameters like 'Memory Usage' or 'VM Size', but also 'Virtual bytes', should be checked. Virtual bytes is memory which is allocated when creating a thread, but not immediately used and can therefore reach the 4GB a lot faster than other memory parameters.

**Deep Dive**
If you want a deep dive on how memory is managed in windows, have a look at these videos by [Mark Russinovich](https://en.wikipedia.org/wiki/Mark_russinovich).

https://www.youtube.com/watch?v=TrFEgHr72Yg - Mysteries of Memory Management Revealed (1/2)
https://www.youtube.com/watch?v=RsQyc4xiJeo - Mysteries of Memory Management Revealed (2/2)


