# CSCI 410 Operating Systems
# Fall 2019
# Chapter 1: Introduction

# Topics
+ What Operating Systems Do
+ Computer-System Organization
+ Computer-System Architecture
+ Operating-System Structure
+ Operating-System Operations
+ Process Management
+ Memory Management
+ Storage Management
+ Protection and Security
+ Distributed Systems
+ Special-Purpose Systems
+ Computing Environments
+ Open-Source Operating Systems
# Objectives
+ To provide a grand tour of the major operating systems components
  - Chapter 1 is broad coverage but shallow
+ To provide coverage of basic computer system organization

# What is an Operating System?
+ A program that acts as an intermediary between a user of a computer and the computer hardware

+ Operating system goals:
  - Execute user programs (Safely!)
  - Make the computer system convenient to use
  - Use the computer hardware in an efficient manner

# Computer System Structure
Computer system can be divided into four components:
+ Hardware – provides basic computing resources
  - CPU, memory, I/O devices
+ Operating system
  - Controls and coordinates use of hardware among various applications and users
+ Application programs – Software to solve computing problems of users
  - Word processors, compilers, web browsers, database systems, video games
+ Users
  - People, machines, other computers

![4components](../Images/ch1-4components.png)
# What Operating Systems Do
+ Depends on point of view
+ Users want convenience, ease of use
  - Don’t care about resource utilization
+ Shared computers such as mainframe or minicomputer must keep all users happy
+ Users of dedicate systems such as workstations have dedicated resources
  - Still share among processes
+ Handheld computers are resource poor,  optimized for usability and battery life
+ Some computers have little or no user interface, such as embedded computers in devices and automobiles

# Operating System Definition
+ No universally accepted definition
+ OS is a resource allocator
  - Manages all resources
  - Decides between conflicting requests for efficient and fair resource use

+ OS is a control program
  - Controls execution of programs to prevent errors and improper use of the computer

+ “Everything a vendor ships when you order an operating system” is good approximation
  - But varies wildly

+ “The one program running at all times on the computer” is the kernel.  Everything else is either a system program (ships with the operating system) or an application program.

# Computer Startup
+ bootstrap program is loaded at power-up or reboot
  - Typically stored in ROM or EPROM, generally known as firmware
  - Initializes all aspects of system
  - Loads operating system kernel and starts execution
# Computer System Organization
## Computer-system operation
+ One or more CPUs, device controllers connect through common bus providing access to shared memory
+ Concurrent execution of CPUs and devices competing for memory cycles
![a modern computer system](../Images/ch1-computer_system.png)

+ I/O devices and the CPU can execute concurrently

+ Each device controller is in charge of a particular device type

+ Each device controller has a local buffer (RAM)

+ CPU moves data from/to main memory to/from local buffers

+ I/O is from the device to local buffer of a controller

+ Device controller informs CPU that it has finished its operation by causing an interrupt

### Common Functions of Interrupts
+ Interrupt transfers control to the interrupt service routine generally, through the interrupt vector, which contains the addresses of all the service routines

+ Interrupt architecture must save the address of the interrupted instruction

+ Incoming interrupts are disabled while another interrupt is being processed to prevent a lost interrupt

+ A **trap** is a software-generated interrupt caused either by an error or a user request

+ An operating system is interrupt driven

### Interrupt Handling
+ The operating system preserves the state of the CPU by storing registers and the program counter

+ Determines which type of interrupt has occurred:
  - polling
  - vectored interrupt system

+ Separate segments of code determine what action should be taken for each type of interrupt

### Interrupt Timeline
![interrupt_timeline](../Images/ch1-interrupt_timeline)


# I/O Structure Types
+ After I/O starts, control returns to user program only upon I/O completion
  - Wait instruction idles the CPU until the next interrupt
  - Wait loop (contention for memory access)
  - At most one I/O request is outstanding at a time, no simultaneous I/O processing

+ After I/O starts, control returns to user program without waiting for I/O completion
  - System call – request to the operating system to allow user to wait for I/O completion
  - Device-status table contains entry for each I/O device indicating its type, address, and state
  - Operating system indexes into I/O device table to determine device status and to modify table entry to include interrupt
## Direct Memory Access Structure
+ Used for high-speed I/O devices able to transmit information at close to memory speeds

+ Device controller transfers blocks of data from buffer storage directly to main memory without CPU intervention

+ Only one interrupt is generated per block, rather than the one interrupt per byte

# Storage Structure
## Notation Review
+ Computer storage, along with most computer throughput, is generally measured and manipulated in bytes and collections of bytes.
  - bit is a 0/1; byte is 8 bits (nibble is 4 bits!)
  - Word depends on CPU register size (native data unit size: 16 bit, 32 bit, 64, bit)
  - kilobyte, or KB, is 1,024 bytes
  - megabyte, or MB, is 1,0242 bytes
  - gigabyte, or GB, is 1,0243 bytes
  - terabyte, or TB, is 1,0244 bytes 
  - petabyte, or PB, is 1,0245 bytes
  - exabyte, EB, is 1,0246 bytes (zeta, yota, xenotta, Shilentno, domegemegrotte) (Internet traffic will reach 1.3 ZB in 2016)
+ NOTE: Network throughput is usually measured in powers of 10.
  - 10mbps is 10,000,000 bits per second
## 
+ Main memory – only large storage media that the CPU can access directly
  - Random access
  - Typically volatile
+ Secondary storage – extension of main memory that provides large nonvolatile storage capacity
  - Hard disks – rigid metal or glass platters covered with magnetic recording material 
    1. Disk surface is logically divided into tracks, which are subdivided into sectors
    2. The disk controller determines the logical interaction between the device and the computer 
  - Solid-state disks – faster than hard disks, nonvolatile
    1. Various technologies
    2. Becoming more popular
