## Practice Loops, commandline arguments, package installation

### Task 1
a. To print the list of fruits using for loop
```bash
#!/bin/bash

list=("Apple" "mango" "Orange" "Grapes" "Banana")
for item in ${list[@]};
do
        echo "$item"
done
```
Output:
```txt
dev@pop-os:~/devops$ ./for_loop.sh
Apple
mango
Orange
Grapes
Banana
```

b. To count the number from 1 to 10
```bash
#!/bin/bash

for i in {1..10};
do
        echo "$i"
done
```
Output:
```txt
dev@pop-os:~/devops$ ./count.sh
1
2
3
4
5
6
7
8
9
10
```
### Task 2
Take a number from user and print it down till 0 using for loop. Print done at the end.
```bash
#!/bin/bash

read -p "Enter a number: " number

while [ "$number" -ge 0 ];
do
        echo "$number"
        ((number--))
done

echo "done"
```
output:
```txt
dev@pop-os:~/devops$ ./countdown.sh
Enter a number: 15
15
14
13
12
11
10
9
8
7
6
5
4
3
2
1
0
done
```
### Task 3
Command line arguments
1. Create a script greet.sh
```bash
#!/bin/bash
name=$1
if [ $1 ]
then
        echo "Hello, $name!"
else
        echo "Usage: ./greet2.sh"
fi
```
Output:
```txt
dev@pop-os:~/devops$ ./greet2.sh
Usage: ./greet2.sh
dev@pop-os:~/devops$ ./greet2.sh Lufy
Hello, Lufy!
```
2. Create a script args_demo.sh
```bash
#!/bin/bash

echo "Total number of arguments: " $#

echo "All arguments: " $@

echo "Script name: " $0
```
Output:
```txt
dev@pop-os:~/devops$ sh args_demo.sh Hello Linux nginx git docker aws
Total number of arguments:  6
All arguments:  Hello Linux nginx git docker aws
Script name:  args_demo.sh
```

### Task 4
Installing packages via script
```bash
#!/bin/bash

list=("nginx" "curl" "wget" "docker")

sudo apt-get update

for package in ${list[@]};
do
        echo "Checking if $package is installed or not"

        if dpkg -s "$package" >/dev/null 2>&1; then
                echo "$package is already installed"

        else
                echo "=====continue installing====="
                sudo apt install "$package" -y
        fi

        if dpkg -s "$package" >/dev/null 2>&1; then
                echo "$package : Installed Successfully"
        else
                echo " $package : Installation Failed"
        fi
done
```

### Task 5
```bash
#!/bin/bash

set -e

read -p "Directory path: " dir_path

mkdir "$dir_path" || echo "directory already exists"
echo "Hello, this is my new file." > hello.txt
cat hello.txt
cd "$dir_path"
pwd
```
Output:
```txt
dev@pop-os:~/devops$ ./safe_script.sh
Directory path: /tmp/devops-test
mkdir: cannot create directory ‘/tmp/devops-test’: File exists
directory already exists
Hello, this is my new file.
/tmp/devops-test
dev@pop-os:~/devops$ ./safe_script.sh
Directory path: /tmp/hello_test
Hello, this is my new file.
/tmp/hello_test
```




