The Find Command will be analyzed here

# Command line option 1 -- case insensitive searching

Source Found

[Source](https://adamtheautomator.com/bash-find/#:~:text=The%20Bash%20find%20Command%20101,-Finding%20a%20file&text=The%20find%20command%20allows%20you,a%20folder%20on%20your%20computer.)

![Screenshot 2023-05-19 171604](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/b643c851-1a09-4a27-b589-76c77744e8c1)

input

`find 911report -iname "Preface.txt"`

output

`911report/preface.txt`

![Screenshot 2023-05-19 171702](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/da424e84-b1a5-4ab4-8188-1a385f0c174f)

input

`find 911report -name "Preface.txt"`

output

`NULL`

We can see in the first image that when in the directory, we can use the find command paired with the command line argument of `iname` as opposed to just  `name` to remove the case sensitivity from our search, thus when we do `-iname` and search for `"Preface.txt"` despite being `"preface.txt"` we get the desired file despite having a different first letter case 

However in the second image, when we just use `-name` and use the exact same search, we can see that the file is not found as in the standard find command we are looking for files that match our search parameter exactly, including case, thus when we make a case error, nothing appears.  

# Command line option 2 -- searching for files over x size

Source Found

Chat GPT suggestion

![image](https://user-images.githubusercontent.com/130321865/236344670-4028f8d0-39f7-4d0d-9fe8-c62c9f682066.png)

input

`find 911report -size +10M`

output

`NULL`

![image](https://user-images.githubusercontent.com/130321865/236344710-63b52c06-6061-437a-9416-3c029ad73260.png)

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

# Command line option 3 -- searching for files created/modified within x time

Source Found

Chat GPT suggestion

![image](https://user-images.githubusercontent.com/130321865/236344752-b83f6bc4-08f2-409b-9f1c-a0670a2b416b.png)

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

![image](https://user-images.githubusercontent.com/130321865/236344790-b9f8640e-7a18-4370-9894-77a269afce0b.png)

input 

`find 911report -mtime -0.000001`

output

`NULL`

We can see in the first image that the find command is looking for anything with the name or in the directory 911report that was created within the last 5 days.  Notably, this not only includes all files within it as I created them less than 3 hours prior to running the command, but also the directory 911report itself, which was also created in that time.

In the second image, we can see that when changing the time check to be 0.000001 days, no results turn up as none of the files or the directory itself have been modified in the last 0.000001 days which is approximately 1.5 minutes prior to the command being run

It is important to note that if you were to change the input in the first image from `find 911report -mtime -5` to `find 911report -mtime +5` it would change the search parameter to search for files in that directory that were created outside of the past 5 days as opposed to within 5 days when the `-5` argument was used

# Command line option 4 -- searching for empty directories 

Source Found

Chat GPT suggestion

![image](https://user-images.githubusercontent.com/130321865/236344832-5f1f26b1-cec6-4724-a273-3057beda3a2e.png)

input

`find technical -type d -empty`

output

`NULL`

![image](https://user-images.githubusercontent.com/130321865/236344868-28dbe56c-d5a3-46f5-b94e-779bceea88d8.png)

input

`find 911report -type d -empty`

output

`911report`

We can see in the first image that the find command is looking for empty directories within the technical directory and because each directory in technical originally has text files, no directories are returned and we recieve a null (empty) return

However in the second image, we performed `rm *` in the 911report directory and cleared all of its files, and re-ran the same find command in the technical directory, we now have the 911report directory returned as it is not empty.  

# References

Method 1

[Method 1](https://adamtheautomator.com/bash-find/#:~:text=The%20Bash%20find%20Command%20101,-Finding%20a%20file&text=The%20find%20command%20allows%20you,a%20folder%20on%20your%20computer.)

Method 2-4

Chat GPT suggestion
