## Shell Scripting Practice

### Task 1 
#!/bin/bash (shebang)
echo "Hello, DevOps!"

**Output:** Hello, devOps!
It falls back to the Parent Shell: When a script lacks a shebang, the shell you are currently using (the "parent shell," e.g., bash, zsh) assumes responsibility for interpreting the script.

### Task 2
#!/bin/bash

NAME="Priyanka"
ROLE="DevOps engineer"

echo "Hello, I am $NAME and I am a $ROLE"

**Output:** Hello, I am Priyanka and i am a DevOps engineer
Putting single quotes (' ') prevents the shell from interpreting special characters or expanding variables within the text

### Task 3
#!/bin/bash

read -p "Enter your name: " NAME
read -p "What is your favourite tool? " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"

**Output:** 
Enter your name: Leaf
What is your favourite tool? Shell
Hello Leaf, your favourite tool is Shell

### Task 4
a. To check if a number is positive, negative or zero
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

**Output:** 
Enter a number: 32
32 is a positive number

- Do not forget the spaces and condition to handle the error especially for negative numbers

b. To check if the file exists or not
#1/bin/bash

read -p "enter a filename: " filename

if [ -f $filename ]
then
        echo "File $filename exists"
else
        echo "File not found"
fi

**Output:**
enter a filename: install_packages.sh
File install_packages.sh exists

### Task 5
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

<img width="918" height="508" alt="image" src="https://github.com/user-attachments/assets/daf4803e-b79d-4dba-abeb-380b93cb77f0" />

### Day 16 Outputs
<img width="1600" height="773" alt="image" src="https://github.com/user-attachments/assets/1b61c947-3475-4b5a-bdbd-76e69ff4d110" />

### Day 16 done












