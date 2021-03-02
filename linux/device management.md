---
Title: device management
Description:
Date: 2021-03-02 18:53
References:
Tags: #linux
---

# device management


## Device files

- **Block device**
Programs access data from a block in fixed chunks. e.g. sda1 is a disk device a type of block device. Disks can be easily split up into blocks of data. Because a block device's total size is fixed and easy to index, processes have random access to any block in the device with thelp of the kernel. 

- **Character device**
Character devices work with data streams. You can only read characters from or write characters to character devices. E.g. /dev/null is a character device. Character devices don't have a size. When you read from or write one, the kernel usually performs a read or write operation on the device. It's important to note that during character device interaction, the kernel cannot back up and re-examine the data stream after it has passed data to the device or process. 

- **Pipe device**
Named pipes are like character devices, with another process at the other end of the I/O stream instead of a kernel driver.

- **Socket device**
Sockets are special purpose interfaces that are frequently used for interprocess communication. They're often found outside of the /dev directory. **Socket files represent Unix domain sockets. **

## udev