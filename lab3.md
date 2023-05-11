# Lab Report 3 - Researching Commands (find)
The find command is a powerful utility for searching for files and directories within a given path. In this report, we explore four interesting command-line options or alternate ways to use the find command.

## Option 1: Find Files by Name
One common use case of find is to search for files based on their name. The -name option allows you to search for files that match a specific pattern.

Before beginning, the full path for ./technical is as follows: ```/home/linux/ieng6/cs15lsp23/cs15lsp23eq/stringsearch/stringsearch-data/technical```

Example 1: Find All .txt Files in /home/linux/ieng6/cs15lsp23/cs15lsp23eq/stringsearch/stringsearch-data/technical/911report
To find all files in the 911report directory that have a .txt extension,I used the following command:
```find 911report -type f -name "*.txt"```

Note: command ran from "technical" directory

Output:
```
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-12.txt
911report/chapter-13.1.txt
911report/chapter-13.2.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-2.txt
911report/chapter-3.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt
```

Example 2: Find a File/Files with a Specific Name in ./technical/plos
To find the file/files in the ./technical/plos directory that has the name "pmed.0010046.txt", you can use the following command:

```find plos -type f -name "pmed.0010046.txt"```

Note: command ran from "technical" directory

Output:
```
plos/pmed.0010046.txt
```


## Option 2: Find Directories by Name
In addition to searching for files, find can also be used to search for directories based on their name. The -type option can be used to specify that we are searching for directories (d) instead of files (f).

Example 1: Find All Directories with "r" in their Name within ./technical
To find all directories in the ./technical directory and its subdirectories that have the word "folder" in their name, you can use the following command:
```
find technical -type d -name "*r*"
```
Note: command ran from "stringsearch-data" directory

Output:
```
technical/911report
technical/government
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
```

Example 2: Find a specific directory within ./technical
To find a specific directory/directories in the ./technical directory and its subdirectories that have the name "Media", you can use the following command:
```
find technical -type d -name "Media"
```

Note: command ran from "stringsearch-data" directory

Output:
```
technical/government/Media
```

## Option 3: Find Files by Modification Time
Another useful feature of find is the ability to search for files based on their modification time. The -mtime option allows you to search for files that were modified within a specified time range.

Example 1: Find Files Modified in the Last 10 Days within ./technical/911report
To find all files in the ./technical directory and its subdirectories that were modified in the last 7 days, you can use the following command:
```
find 911report -type f -mtime -10
```

Note: command ran from "technical" directory

Output:
```
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-12.txt
911report/chapter-13.1.txt
911report/chapter-13.2.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-2.txt
911report/chapter-3.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt
```

Example 2: Finding files modified between 1 and 5 days ago
Suppose we want to find all files in the ./technical/911report directory and its subdirectories that have been modified between 1 and 5 days ago. We can use the following command:

```find technical -mtime +1 -mtime -5```

Note: command ran from "technical" directory

Output: there is no output because no files were modified within this time period

## Option 4: Using the -exec option to perform actions on files found by find
The -exec option allows us to perform a command on the files found by find. The basic syntax is find <directory> -exec <command> {} \;. The {} is a placeholder for the found file(s) and \; indicates the end of the command. Here are two examples:

Example 1: Using cp to copy files found by find to a new directory within ./technical
Suppose we want to copy all .txt files found in the ./technical/911report directory and its subdirectories to a new directory called ./new. We can use the following command:

```find 911report -name "*.txt" -exec cp {} ./new \;```
  
Note: command ran from "technical" directory
  
Output: After running the ls command within ./technical, we now get

``` 911report  biomed  government  new  plos ```
  
  This shows that the new directory has been created 

Example 2: Using rm to delete files found by find within ./technical/new
Suppose we want to delete all .txt files found in the ./technical/new directory and its subdirectories. We can use the following command:

```
find new -name "*.txt" -exec rm {} \;
```
Output: There is no output, but the .txt files in new are removed

## Conclusion
In this report, we explored various command-line options and alternate ways to use the find command. We learned how to search for files by their name and type, directories, performing actions on files found by find, and how to find files based on their modification time.

## Sources used
[find command in Linux with examples](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)
  
ChatGPT
