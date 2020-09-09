# Getting started with Shell Scripting
Shell scripting is a simple yet powerful way of performing some task using shell. A shell script is just like any program file which contains sequence of statements. Shell scripts can be useful when you want to execute a same set of commands everytime say for installing dependencies on multiple systems. What makes a shell script so powerfull is that you can directly write your shell commands as statements which allows you to do a lot of things ranging from linkinking two files for e.g getting some value from say a python script and supplying  it as an input to say a php file, to monitoring the entire system. All this is possible because you are working on the system level. 
Now that we know what can we do using shell script let's try to make one of our own.

Let's try to create a directory and list all the files in a specific directory.

## Creating bash script step by step

### 1. Open your terminal and create a new script file.
Let's call our script file `list_file.sh`, every bash script has extension `.sh`.
```bash
vi list_files.sh
```
Press `I` to insert.

### 2. Specifying executable binary 
The first line of the script contains the absolute path of the program by which it is executed.

**Note:** Although it is not necessary to specify program it is followed as a good practice.

Since we are creating a bash script the path will be `/usr/bin/bash`
Enter the following line:
```bash
#!/usr/bin/bash
```
### 3. Adding comments 
You can add comments by adding `#` followed by comment in a bash script
```bash
# Script to create a directory in home with given name and a file containing list of files present in /var/www/html
```
### 4. Declaring variable
Now let's create a variable which contains name of the folder which we are going to create:
```bash
NAME="Aastha"
```
You can create variables just by writing `variable_name = value`, no need to specify data type.
### 5. Creating folder
Now let's create a folder in home directory:
```bash
mkdir ~/$NAME
```
Notice that `NAME` is preceeded by `$`, here `$NAME` represents value stored in `NAME` variable.

### 6. Generating file with list of files present in /var/www/html
We can use `echo` followed by text, to print some text on stdout(Standard Outoput) but we can also use it to add some text in a specified file using `>` operator like this:
```bash
echo `ls /var/www/html` > ~/$NAME/file_list.txt
```
Here `~/$NAME/file_list.txt` is the name of out put file which contains result of `ls /var/www/html`.
The **``** denotes that echo will first evaluate the expression and then use its value.

The whole file will look like this:
```bash
#!/usr/bin/bash
# Script to create a directory in home with given name and a file containing list of files present in /var/www/html
NAME="Aastha"
mkdir ~/$NAME
echo `ls /var/www/html` > ~/$NAME/file_list.txt
```
### 7. Saving the file
We are done with all the statements, let's save and close the file. Press `Esc` then type `:wq` that is write and quit and press enter.

### 8. Executing the script
To execute the script first we will need to change its permissions by:
```bash
chmod +x list_files.sh 
```
Which will grant executing permissions to all.

Now let's execute the script:
```bash
./list_files.sh 
```

And that's it! You can see a file is created in the specified directory.



