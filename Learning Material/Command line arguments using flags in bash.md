# Command line arguments in bash
In the previous article we created a simple bash script let's modify it a bit to accept command line arguments.
We will accept the name of directory which needs to be created and the path of dicrectory whose files we have to list.
We will use flags to take input i.e `-i` for name of input directory whose contents will be listed and `-o` for output directory.

This is our current code:
```bash
#!/usr/bin/bash
# Script to create a directory in home with given name and a file containing list of files present in /var/www/html
NAME="Aastha"
mkdir ~/$NAME
echo `ls /var/www/html` > ~/$NAME/file_list.txt
```
# Getting arguments using `getopts`
We will use get `getopts` function which returns a list of options(flags) with respective argument. 
We will use a `while` to iterate through `getopts`
```bash
while getopts i:o: flag 
do
```
Here are we are specifying list of valid options as `i:o:` the `:` represents that an option need to be followed by a value.You can read more about `getopts` [here](https://www.mkssoftware.com/docs/man1/getopts.1.asp).
`flag` is the iterator variable here. In bash  the `do` followed  by `while` statement specifies starting of block which contains satement to be executed by `while`. The ending of block is specified by `done`.

# Storing argument values in variables
We will use switch `case` to assign values, based on options.
```bash
case "${flag}" in
                i) infolder=${OPTARG}
                        ;;
                o) outfolder=${OPTARG}
                         ;;
                *) echo "Invalid option: -$flag" ;;
        esac
done
```
The above will comapare `$flag` with `i`,`o` and `*` where `*` can be any thing other than `i` and `o`. The `;;` indicates the end of a `case`. The `${OPTARG}` contains the argument supplied for `$flag` option.
The `esac` indicates the end of the whole switch `case` block.

# Replacing hard-coded values with new variables
```bash
mkdir ~/$outfolder 
ls $infolder > ~/$outfolder/file_list.txt
```

## Final code
```bash
#!/usr/bin/bash
# Script to create a directory in home with name `$outfolder` and a file containing list of files present in`$infolder`
while getopts i:o: flag

do
        case "${flag}" in
                i) infolder=${OPTARG}
                        ;;
                o) outfolder=${OPTARG}
                         ;;
                *) echo "Invalid option: -$flag" ;;
        esac
done
mkdir ~/$outfolder 
ls $infolder > ~/$outfolder/file_list.txt
```

