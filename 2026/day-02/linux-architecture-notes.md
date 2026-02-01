## Day 02: Linux Architecture, Processes and Systemd
### How Linux works under the Hood?
Linux is a whole system. It is free and an open source software operating system.
It has 3 main parts:
- Kernel
- User Space
- Init/Systemd

#### 1. kernel
Kernel is the brain of linux which decides:
- who will use the cpu
- how memory will be allocated
- how disk will be used for data transfer
- how to interaction happens with hardware
One cannot communicate with kernel directly so we use commands.

#### 2. User Space
It is the space where we actually do work. It can be:
- terminal
- Commands
- Apps
- Scripts
We stay in the user space while kernel works in the background.

#### 3. Init/Systemd (My Fav. Special Process)
**Init vs Systemd**

Init: Earlier it was an old school initialization method used by linux. It starts services one by one during system boot.
It is simple but slow and does not handle service failures well.

Systemd: It is the modern system initialization system. It starts services in parallel, manages dependencies, and can automatically restart services if they fail.

In Devops:
whenever server downs,service stopped then systemd is checked first.

**Why systemd is my Fav. Special process?**
- Because it is the parent of almost all processes. Every process is born from it.
- It's PID is 1
- It is the guard of restart and caretaker of recovery.
- Killing this process will crash the whole system and will break the entire boot cycle.

**Killing random processes can be dangerous.**

### Process States
1. Running (R): The process is either using cpu or ready to run.
2. Sleeping (S): The process is waiting for an event ie., Input, io or resource.
3. Uninterruptible Sleep (D): The process is waiting for hardware or disk I/O and cannot be interrupted.
4. Stopped (T): The process is paused by a signal or user action.
5. Zombie (Z): The process has finished execution but still has an entry in the process table.
6. Dead (X): The process has completely terminated and is removed from the system.

### Day 02 Task Done






