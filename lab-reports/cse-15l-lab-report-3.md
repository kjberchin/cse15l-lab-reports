FOR THIS REPORT WE WILL BE ANALYZING THE "FIND" COMMAND

I. command line option 1 -- searching for files by directory

![Image](Screenshot 2023-05-04 142009)

input

`find 911report/preface.txt`

output

`911report/preface.txt`

![Image](Screenshot 2023-05-04 142138)

input

`find 911report/preface_not_present.txt`

output

`find: ‘911report/preface_not_present.txt’: No such file or directory`

We can see in the first image that when in the directory, we can use the find command to loop through sub directories looking for if a file exists.  In the first image, we are looking for an existing file, while in the second image we are looking for a nonexistant file.  

We can see clearly that the find command informs us when a file does not exist within a sub directory, by searching through said directory for file names that match the input we provided it, and then returning that path back to us if it does exist, telling us that it is not present

II. command line option 2 -- searching for files over x size

![Image](Screenshot 2023-05-04 143326)

input

`find 911report -size +10M`

output

`NULL`

![Image](Screenshot 2023-05-04 143345)

input

`find 911report -size +1k`

output

`911report/chapter-1.txt
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
911report/preface.txt`

We can see in the first image that the find command is looking for any files in the 911report directory that are over 10 megabytes.  As the directory contains only a few text files of moderate size, none would be near that large.

However, when we look in the second image and change the size of our search from 10 megabytes to 1 kilobyte, that all files within 911report are that large and thus it shows us the path from the directory we are in, to those files.
