# I/O Redirection
we can redirect the output of many commands to files, devices, and even to the input of other commands.

## Standard Output
Standard output directs its contents to the display. To redirect standard output to a file, the ">" character is used like this:
```bash
[me@linuxbox me]$ ls > file_list.txt
```
If you want the new results to be appended to the file instead, use ">>" like this:
```bash
[me@linuxbox me]$ ls >> file_list.txt
```

## Standard Input
Many commands can accept input from a facility called standard input. By default, standard input gets its contents from the keyboard, but like standard output, it can be redirected.
```bash
[me@linuxbox me]$ sort < file_list.txt
```

you can use "<" and ">" at same time.
```bash
[me@linuxbox me]$ sort < file_list.txt > sorted_file_list.txt
```

## Pipelines
You can connect multiple commands together with what are called **pipelines**
```
me@linuxbox me]$ ls -l | less
```

## Filter
One kind of program frequently used in pipelines is called filters. Filters take standard input and perform an operation upon it and send the results to standard output. In this way, they can be combined to process information in powerful ways. 

Common filter commands
|**program**|What it does|
|:--|:--|
|sort|Sorts standard input then outputs the sorted result on standard output|
|uniq|Given a sorted stream of data from standard input, it removes duplicate lines of data|
|grep|Examines each line of data it receives from standard input and outputs every line that contains a specified pattern of characters.|
|fmt|Reads text from standard input, then outputs formatted tet on standard output.|
|pr|Takes text input from standard input and splits the data into pages with page breaks, headers and footers in preparation for printing.|
|head|Outputs the first few lines of its input. Useful for getting the header of a file.|
|tail|Outputs the last few lines of its input. Useful for things like getting the most recent entries from a log file.|
|tr|Translates characters. Can be used to perform tasks such as upper/lowercase conversions or changing line termination characters from one type to another.|
|sed|Stream editor. Can perform more sophisticated text translations than tr.|
|awk|An entire programming language designed for constructing filters. Extremely powerful.|

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM4MDU2MjU1M119
-->