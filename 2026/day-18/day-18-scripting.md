## Day 18 – Shell Scripting: Functions & Slightly Advanced Concepts

### Task 1: Basic Functions
```bash
#!/bin/bash

greet(){
        echo "Hello, $1"
}

add(){
        echo "Sum: $(($1 + $2))"
}
greet "Damian"
add 12 14
```
Output: 
```txt
ubuntu-os:~/devops$ ./functions.sh
Hello, Damian
Sum: 26
```

### Task 2: Functions with Return Values
```bash
#!/bin/bash

check_disk(){
        echo "=====Disk usage=====" 
        df -h /
}

check_memory(){
        echo "=====Memory used====="
        free -h
}

main(){
        check_disk
        echo ""
        check_memory
}
main
```
Output:
```txt
ubuntu-os:~/devops$ ./disk_check.sh
=====Disk usage=====
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p3  225G   71G  143G  34% /

=====Memory used=====
               total        used        free      shared  buff/cache   available
Mem:            15Gi       4.2Gi       6.4Gi       667Mi       4.9Gi       9.3Gi
Swap:           19Gi          0B        19Gi
```

### Task 3: Strict Mode — set -euo pipefail
```bash
#!/bin/bash

set -euo pipefail
name="Priyanka"
echo "value: $name"

# mkdir strict_file
# echo "done"

#set -o pipefail
#set -e
ls missing_file.txt | wc -l
echo "Exit code: $?"
echo "After"
```
Output: 
```txt
ubuntu-os:~/devops$ ./strict_demo.sh
value: Priyanka
ls: cannot access 'missing_file.txt': No such file or directory
0
```
* set -e → Exit the script immediately if any command fails.
* set -u → Exit the script if you use an undefined (unset) variable.
* set -o pipefail → In a pipeline (a | b | c), fail if any command fails (not just the last one).

### Task 4: Local Variables
```bash
#!/bin/bash

name="Leaf"

my_local(){
        local name="Damian"
        #echo "$num"
}

my_global(){
        name="Anya"
}
echo "Before calling local function"
echo "$name"
my_local
echo "After calling local function"
echo "$name"

echo ""
echo "Before calling global function"
echo "$name"
my_global
echo "After calling global function"
echo "$name"
```
Output:
```txt
ubuntu-os:~/devops$ ./local_demo.sh
Before calling local function
Leaf
After calling local function
Leaf

Before calling global function
Leaf
After calling global function
Anya
```

### Task 5: Build a Script — System Info Reporter
```bash
#!/bin/bash

set -euo pipefail

my_host(){
        echo "Hostname: $(hostname)"
        echo "OS: $(. /etc/os-release && echo "$PRETTY_NAME")"
}

os_time(){
        uptime -p
}

disk_usage(){
        du -h --max-depth=1 / 2>/dev/null | sort -hr | head -n 5 || true
}

memory_usage(){
        if command -v free >/dev/null 2>&1; then
        free -h || true
        else
                echo "free command not found. Showing /proc/meminfo:"
                head -n 10 /proc/meminfo || true
        fi
}

check_process(){
        ps -eo pid,comm,%cpu --sort=-%cpu | head -n 6
}

main(){
        echo "=====SYSTEM INFO REPORT====="
        echo ""

        echo "Hostname & OS Info"
        my_host
        echo ""

        echo "Uptime"
        os_time
        echo ""

        echo "Disk Usage"
        disk_usage
        echo ""

        echo "Memory Usage"
        memory_usage
        echo ""

        echo "Top 5CPU processes"
        check_process
        echo ""
}
main
```
Output:
```txt
ubuntu-os:~/devops$ ./system_info.sh
=====SYSTEM INFO REPORT=====

Hostname & OS Info
Hostname: pop-os
OS: Pop!_OS 22.04 LTS

Uptime
up 4 hours, 23 minutes

Disk Usage
71G	/
52G	/home
17G	/usr
1.3G	/var
378M	/opt

Memory Usage
               total        used        free      shared  buff/cache   available
Mem:            15Gi       4.3Gi       6.2Gi       682Mi       5.0Gi       9.2Gi
Swap:           19Gi          0B        19Gi

Top 5CPU processes
    PID COMMAND         %CPU
   5345 chrome           6.5
  14910 chrome           5.2
   7230 chrome           4.7
  13751 firefox-bin      4.0
   9588 chrome           3.7
```

#### Day-18 Done


