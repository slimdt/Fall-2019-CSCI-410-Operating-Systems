# CSCI 410 Operating Systems
# Fall 2019
# Dr. Ning Zhang

# Lecutre 1: Course Overview 08/22/2019

## [Syllabus](https://zhangningsau.github.io/CSCI410/Fall2019/Syllabus.html)
## Topics to be covered
### Overview (Ch 1-2)
1. Fetures of OS
2. Tasks of OS
### Process Management (Ch 3-6)
A process is
1. the heart of OS,
2. the unit of work in OS.
Types of process:
1. OS processes,
2. user processes.
Topics to be covered:
1. process scheduling, 
2. interprocess communication, 
3. process synchronization,
4. deadlock handling,
5. threads
6. issues related to multicore systems and parallel programming.
### Memory management (Ch 7-8)
Task: the management of main memory during the execution of a process
Goal: to improve both the utilization of the CPU and the speed of its response to its users
Topics: different memory-management schemes
### Storage management (Ch 9-12)
Topics:
1. mass storage
2. file system
3. I/O
### Protection and security (Ch 13-14)
Protection is a mechanism for **controlling** the access of programs, processes, or users to computer-system resources.

## Programming
[Linux virtual machine](http://people.westminstercollege.edu/faculty/ggagne/osc/vm/index.html)


## Chapter 1: Introduction
1. OS is an intermediary between users and computer hardwares.
2. OS is software.
3. The goal of OS should be well-defined before the design begins (OS vary in diffrent tasks).
### Computer system
![](../Images/Fig1.1.png)
#### 1. hardwares
1). CPU/Central Processing Unit
![](https://o.aolcdn.com/images/dims?quality=85&image_uri=https%3A%2F%2Fo.aolcdn.com%2Fimages%2Fdims%3Fcrop%3D1600%252C953%252C0%252C99%26quality%3D85%26format%3Djpg%26resize%3D1600%252C953%26image_uri%3Dhttp%253A%252F%252Fo.aolcdn.com%252Fhss%252Fstorage%252Fmidas%252F391002b78e506e85c77fc661aea99892%252F205545457%252FIntel%252BCore%252BX%252Bseries%252Bgallery%252B21.jpg%26client%3Da1acac3e1b3290917d92%26signature%3D99ebc799dc4b1de8cba48077268995444b23a29e&client=amp-blogside-v2&signature=0881674cb86de0036c65e97d988df67634c06309)
2). Memory
![](https://pixfeeds.com/images/technology/storage/1280-471770087-memory-cards.jpg)
3). I/O devices (monitor,mouse,keyborad,printer,touch screen,etc)

#### 2. OS
1). Windows
2). MAC OS
3). Linux
4). Android
5). iOS
6). for IoT(Internet of Things)
Fuchsia OS

Harmony OS
#### 3. application programs
![](https://steamcdn-a.akamaihd.net/steam/apps/578080/header.jpg?t=1564606217)
![](http://9.pic.pc6.com/thumb/up/2012-12/20121212111044247821_600_0.jpg)
#### 4. users

### Two different views to understand the role of OS
#### 1. User view
ease of use
#### 2. System view
Resource utilization/Resouce allocator
1). CPU time 
2). memory space
3). file storage space
4). I/O devices

#### Definition of OS
1. no completely adequate definition
2. no universally accepted definition of what is part of the operating system
3. Kernel: OS is the one program running at all times on the computer.
    Besides kernel, there are system programs(part of OS, but not associated with kernel) and user programs.

### Computer-system organization
![A modern computer system](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter1/1_2_ModernSystem.jpg)
+ CPU and controllers compete for memory cycles.
#### What will happen if you push the power button?
**Bootstrap program** will be run and it
    <li>is stored in ROM or EEPROM</li>
    ![rom](https://www.thoughtco.com/thmb/0kUhsdYcFITCzmyVm2E9RjDdIKw=/768x0/filters:no_upscale():max_bytes(150000):strip_icc()/Amiga_1200_Kickstart_3.0_ROMs-56b429575f9b5829f82c66bd.jpg)
    <li>initilize the system</li>
    <li>locate and load kernel</li>
    <li> some system programs</li>
now, your computer is ready.
#### Interrupt organization
How is the computing resource/CPU is utilized?

**interrupt**
    <li>hardware interrupt by sending a signal to CPU</li>
    <li>software interrupt by executing a system call </li>
    
#### Storage organization
![](https://camo.githubusercontent.com/a32f325851f11af2810abe9d64f04d7e94c35bb4/687474703a2f2f7777772e63732e7569632e6564752f7e6a62656c6c2f436f757273654e6f7465732f4f7065726174696e6753797374656d732f696d616765732f43686170746572312f315f345f53746f726167654465766963654869657261726368792e6a7067)
1. Memory
CPU can load instructions only from memory, so any program to run must be store there.
    + ROM: read-only-memory, can not be changed
    + EEPROM: erasable programmable ROM, can be changed, but not frequently
    + RAM: random-access-memory, the main memory, can be changed frequently
 2. secondary storage: other storages under main memory
 
**volatile** storage:
loses content without power
**non-volatile** storage:
the data is always there.

### IO Structure
A device **controller** is responsible for moving data between a device or several same-type devices and the local buffer.
![](http://www.expertsmind.com/CMSImages/690_Devices%20using%20Device%20Controller.png)

![](https://slideplayer.com/slide/2406777/8/images/12/Device+controller+A+device+controller+has+registers+that+control+operation..jpg)

A device **driver** understands the a device or same-type devices and provides the rest of the OS with a uniform interface to the device(s).

![](https://slideplayer.com/slide/5120224/16/images/25/Device+Drivers+Logical+position+of+device+drivers+is+shown+here.jpg)

+ interrupt-driven I/O for small amounts of data
+ direct memory access for block data

### Computer-system architecture
#### Single processor systems
#### Multiple processor systems
1. asymmetric multiprocessing
boss-workers relationship
+ A boss controls the system.
+ The other processors either look to the boss or have predefined task.
2. symmetric multiprocessing
All are peers.
![](http://download.oracle.com/docs/cd/A57673_01/DOC/server/doc/SPS73/image019.gif)

multiprocessor vs multicore

multicore: multiple cores on a single chip

They can be more efficient than multiple chips with single cores because on-chip communication is faster than between-chip communication. In addition, one chip with multiple cores uses significantly less power than multiple single-core chips.

![](https://slideplayer.com/slide/5832436/19/images/3/Multi-Core+vs.+Multi-Processor.jpg)


**advantages of multiprocessors**
+ Increased throughput. By increasing the number of processors, we expect to get more work done in less time. The speed-up ratio with N processors is not N, however; rather, it is less than N. 
+ Economy of scale. Multiprocessor systems can cost less than equivalent multiple single-processor systems.
+ Increased reliability. If functions can be distributed properly among several processors, then the failure of one processor will not halt the system, only slow it down.


#### blade server
[wikipeida](https://en.wikipedia.org/wiki/Blade_server)

Blade servers have many components removed to save space, minimize power consumption and other considerations, while still having all the functional components to be considered a computer.

#### cluster systems

![cluster](../Images/ch1-cluster.png)

### 1.4 OS structure
An OS provides an environment within which programs are executed.
#### multiprogramming
1. job pool
    + The jobs(code and data) are kept in the job pool on the disk.
2. subset of job pool
    + The OS keep a subset of the jobs in the memory(memory is not large enough for all jobs).
3. The cpu switches to another job if the current job has to wait for some task.
#### multitasking/time-sharing
1. multitasking/time-sharing is an extension of multiprogramming.
2. cpu switches jobs so frequently.
3. multitasking/time-sharing requires an interactive computer system(keyborad, mouse, touch screen...).
4. concept of **clock**.

#### job-scheduling
How to choose the subset of jobs in the job pool to memory?(chapter 6)
#### memory management
How to arrange the jobs in memory?(chapters 7,8)
#### CPU-scheduling
Which job in memory will run first?(chapter 6)
#### swapping/virtual memory
How to swap processes in and out memory?

How to run programs that are larger than the memory?





