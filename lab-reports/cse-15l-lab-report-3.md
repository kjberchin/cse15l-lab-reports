FOR THIS REPORT WE WILL BE ANALYZING THE "FIND" COMMAND

Command line option 1 -- searching for files by name

![Image](cse15l-lab-reports/Screenshot 2023-05-04 142009)

input

`find 911report/preface.txt`

output

`911report/preface.txt`

![Image](cse15l-lab-reports/Screenshot 2023-05-04 142138)

input

`find 911report/preface_not_present.txt`

output

`find: ‘911report/preface_not_present.txt’: No such file or directory`

We can see in the first image that when in the directory, we can use the find command to loop through sub directories looking for if a file exists.  In the first image, we are looking for an existing file, while in the second image we are looking for a nonexistant file.  

We can see clearly that the find command informs us when a file does not exist within a sub directory, by searching through said directory for file names that match the input we provided it, and then returning that path back to us if it does exist, telling us that it is not present

Command line option 2 -- searching for files over x size

![Image](cse15l-lab-reports/Screenshot 2023-05-04 143326)

input

`find 911report -size +10M`

output

`NULL`

![Image](cse15l-lab-reports/Screenshot 2023-05-04 143345)

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

Command line option 3 -- searching for files created/modified within x time

![Image](cse15l-lab-reports/Screenshot 2023-05-04 144613)

input

`find 911report -mtime -5`

output

`911report
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
911report/preface.txt`

![Image](cse15l-lab-reports/Screenshot 2023-05-04 144624)

input 

`find 911report -mtime -0.000001`

output

`NULL`

We can see in the first image that the find command is looking for anything with the name or in the directory 911report that was created within the last 5 days.  Notably, this not only includes all files within it as I created them less than 3 hours prior to running the command, but also the directory 911report itself, which was also created in that time.

In the second image, we can see that when changing the time check to be 0.000001 days, no results turn up as none of the files or the directory itself have been modified in the last 0.000001 days which is approximately 1.5 minutes prior to the command being run

Command line option 4 -- searching for empty directories

![Image](cse15l-lab-reports/Screenshot 2023-05-04 150125)

input

`find technical -type d -empty`

output

`NULL`

![Image](cse15l-lab-reports/Screenshot 2023-05-04 150206)

input

`find 911report -type d -empty`

output

`911report`

We can see in the first image that the find command is looking for empty directories within the technical directory and because each directory in technical originally has text files, no directories are returned and we recieve a null (empty) return

However in the second image, we performed `rm *` in the 911report directory and cleared all of its files, and re-ran the same find command in the technical directory, we now have the 911report directory returned as it is not empty.  
