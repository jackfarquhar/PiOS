# PiOS
OS Project on Raspberry Pi
by Jack Farquhar
Student ID: 200407242

This is my project for CS330 Assignment 5. 

I have made a very simple OS designed for a Raspberry Pi model 2. It is based on a few tutorials online, and class content. It is related to Operating systems in that it is a standalone operating system. Granted, it is an operating system that, in its current state, does not do very much of anything at all. It uses a non-standard version of the gcc comiler that compiles for ARM systems (such as the Raspberry Pi), and all of my tests have been done using an emulator called qemu, which emulates most of the funtionality of the Raspberry Pi model 2. I have not ported it to my Pi yet to test. 

Most of the code for the project is written in C, but there is some assembly as well for a few of the more basic functions such as the boot file, part of the interrupt handling, process management, and a small part of the locking/mutex mechanism. These assembly files are based heavily on online tutorials, and I cannot fully explain how they work. The rest of the files are written in C, and use many of the concepts that were taught in class such as processes, threads, locks/mutexes, memory management, and standard IO. I did have to learn some other topics such as GPU and graphics handling, as well as some things that are specific to the Raspberry Pi such as the mailbox peripheral. 

In doing this project I learned that there is a lot that goes into even the most simple of operating systems, and mine barely scratches the surface of usability. It is more of a baseline off of which a more complex operating system could be build. It has no system calls, and it cannot yet be interacted with other than direct modification to code in the kernel_main() in kernel.c. 

Some of the challenges that I came across while making the PiOS are as follows:
The timer does not really seem to work. I'm not sure if my implementation is bad, or what really the issue is. As far as I can tell, my code is fine, and it compiles, but when I try to use the timer to set delays or use it at all, it causes the program to stop. It does not give any errors either, so it is possible that it is getting hung up somewhere during runtime, and I have not been able to solve the issue. Because of this the udelay is commented out in kernel_main(). 
Another issue is that my mutex lock is probably not implemented perfectly, as I have had test cases where it appears to get caught in a deadlock, and others where it seems to work properly. 

Reproduction:
In order to reproduce this project you would need to install the qemu emulator. I use version 3 on linux. You would also need to install the GNU Arm embedded toolchain gcc compiler for linux. I am using the July 2018 updated version. With these two things, the code can be easily compiled using the Makefile provided in the build folder. 
