# Day 16 - Bash Scripting Tasks

## Task 1

```bash
#!/bin/bash
echo "Hello, DevOps!"
```
**Output:**
```txt
Hello, DevOps!
```
Note:
If a script lacks a shebang, the shell you are currently using (the "parent shell," e.g., bash, zsh) may interpret the script.

### Task 2
```bash
#!/bin/bash

NAME="Priyanka"
ROLE="DevOps engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```
**Output:** 
```txt
Hello, I am Priyanka and I am a DevOps engineer
```
Note:
Putting single quotes (' ') prevents the shell from expanding variables inside the text.

### Task 3
```bash
#!/bin/bash

read -p "Enter your name: " NAME
read -p "What is your favourite tool? " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```
**Output:** 
```txt
Enter your name: Leaf
What is your favourite tool? Shell
Hello Leaf, your favourite tool is Shell
```
### Task 4

a. To check if a number is positive, negative or zero
```bash
#!/bin/bash

read -p "Enter a number: " num

if ! [[ "$num" =~ ^-?[0-9]+$ ]]
then
        echo "Invalid input"
        exit 1
fi

if [ $num -gt 0 ]
then
        echo "$num is a positive number"
elif [ $num -lt 0 ]
then
        echo "$num is a negative number"
else
        echo "Number entered is zero"
fi
```
**Output:** 
```txt
Enter a number: 32
32 is a positive number
```
Note:
Do not forget spaces in conditions and handle errors properly (especially for negative numbers).

b. To check if the file exists or not
```bash
#!/bin/bash

read -p "enter a filename: " filename

if [ -f $filename ]
then
        echo "File $filename exists"
else
        echo "File not found"
fi
```
**Output:**
```txt
enter a filename: install_packages.sh
File install_packages.sh exists
```
### Task 5
```bash
#!/bin/bash

read -p "Enter a service: " service

read -p "Do you want to check the service status(y/n)? " user_input

if [[ "$user_input" == "y" || "$user_input" == "Y" ]]
then
        echo "=====Service status====="
        systemctl status "$service"

        echo "=====Active/Inactive====="
        systemctl is-active "$service"

else
        echo "skipped"
fi
```
**Output:**
<img width="918" height="508" alt="image" src="https://github.com/user-attachments/assets/daf4803e-b79d-4dba-abeb-380b93cb77f0" />

### Day 16 Outputs
<img width="1600" height="773" alt="image" src="https://github.com/user-attachments/assets/1b61c947-3475-4b5a-bdbd-76e69ff4d110" />

### Day 16 done












