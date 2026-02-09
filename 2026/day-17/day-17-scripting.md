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

