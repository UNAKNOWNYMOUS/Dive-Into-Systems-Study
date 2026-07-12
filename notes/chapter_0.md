---
id: chapter_0
aliases: []
tags: []
---

# 0. Introduction
- Understanding what a computer system is and how it runs your programs can help you design code that runs efficiently and that can make the best use of the power of the underlying system.
## What Is a Computer System?
- A computer system combines the computer hardware and special system software that together make the computer usable by users and programs.
- Specifically, a computer system has the following components:
  - Input/output (IO) ports enable the computer to take information from its environment and display it back to the user in some meaningful way.
  - A central processing unit (CPU) runs instructions and computes data and memory addresses.
  - Random access memory (RAM) stores data and instructions of running programs. The data and instructions in RAM are typically lost when the computer system loses power.
  - Secondary storage devices like hard disks store programs and data even when the power is not actively being provided to the computer.
  - An operating system (OS) software layer lies between the hardware of the computer and the software that a user runs on the computer. The OS implements programming abstractions and interfaces that enable users to easily run and interact with programs on the system. It also manages the underlying hardware resources and controls how and when programs execute. The OS implements abstractions, policies, and mechanisms to ensure that multiple programs can simultaneously run on the system in an efficient, protected, and seamless manner.
- "Figure 1"
- We focus specifically on computer systems that have the following qualities:
  - They are general purpose, meaning that their function is not tailored to any specific application.
  - They are reprogrammable, meaning that they support running a different program without modifying the computer hardware or system software.
## What Do Modern Computer Systems Look Like?
- "Figure 2"
- If computer components overheat, they can become permanently damaged.
- A single-board computer (SBC) is a device in which the entirety of the computer is printed on a single circuit board.
- "Figure 3"
- The Raspberry Pi SBC contains a system-on-a-chip (SoC) processor with integrated RAM and CPU, which encompasses much of the laptop and desktop hardware shown in Figure 2.
- The SoC technology found on the Raspberry Pi is also commonly found in smartphones.
  - In fact, the smartphone is another example of a computer system.
- All aforementioned computer systems (Raspberry Pi and smartphones included) have multicore processors.
  - In other words, their CPUs are capable of executing multiple programs simultaneously.
    - We refer to this simultaneous execution as parallel execution.
- All of these different types of computer hardware systems can run one more general purpose operating systems, such as macOS, Windows, or Unix.
- A general-purpose operating system manages the underlying computer hardware and provides an interface for users to run any program on the computer.
- Together these different types of computer hardware running different general-purpose operating systems make up a computer system.
## What You Will Learn In This Book
- By the end of this book, you will know the following:
  - How a computer runs a program.
  - How to evaluate systems costs associated with a program's performance.
  - How to leverage the power of parallel computer with parallel programming.
## Getting Started with This Book
### Linux, C, and the GNU Compiler
- C is less abstracted from the underlying computer systems than many other high-level languages.
  - As a result, C is the language of choice for programmers who want more control over how their program executes on the computer system.
## Other Types of Notation and Callouts
### The origins of Linux, GNU, and the Free Open Source Software (FOSS) movement
### How to do the readings in this book
### This book contains puns
