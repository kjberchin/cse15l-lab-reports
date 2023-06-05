# Edstem Post

## What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?

Windows, vscode bash terminal

## Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.

When I try to use the terminal to run my program to create a new java file with 3 samples of text, I am receiving the following error in the screenshots below, I have the proper main file, I am in the right directory that the code is referencing but I cant find the file despite the error.

Here is my code


![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/ec5a22e9-d92c-4eaf-bde5-2ea1a9e3c2ab)


Here is my terminal

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/2c91faa8-a1c8-4554-aadd-f4fdb6499e77)


## Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.

I am running no commands other than using the javac and java commands to run my programs `main` method.  The input from the command line argument is just the 3 strings "racecar" " = " "racecar".  The working directory is in the screenshots above.

# TA response

If you think your command has successfully created the file, try using the `find` command to search your directory, also think about find command specifics such as `*` to search all files in a parent directory if its not in the one you think

If you still cannot find your file, it is possible that the error did not create your file, in which case, try editting your code and just creating a file without specifying your directory by removing the `directoryPath` variable and just a file in the current directory.

# Student response to TA

When I try to use the `find` command I recieve the following output

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/5698e220-d442-4ccb-9e22-6ba312868e50)

However when I changed the code by removing the specific directory that worked as it produced a new outcome with the following code and terminal

Code

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/6b99ac1c-e621-4f40-9b09-fe1828afb45c)

Terminal

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/ef822d00-ff22-45ce-bef2-2d7d3f0226eb)

# Setup information
## 1.

Directory for terminal commands and code file:

`/c/Users/nerdb/Desktop/CSE-stuff/CSE15L/lab-report-5/wavelet`

## 2. Code contents of before/after fix

Before

`import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
public class Anagram {
    public static void main(String[] args){
        String fileName = "lab5.txt";
        String directoryPath = "/c/Users/nerdb/Desktop/CSE-stuff/CSE15L/lab-report-5/wavelet";

        try {
            
            FileWriter fileWriter = new FileWriter(directoryPath + fileName);

            
            BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

            
            bufferedWriter.write(args[0]);
            bufferedWriter.newLine(); 
            bufferedWriter.write(args[1]);
            bufferedWriter.newLine();
            bufferedWriter.write(args[2]);

            
            bufferedWriter.close();
            fileWriter.close();

            System.out.println("File created and lines added successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}`

After

`import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
public class Anagram {
    public static void main(String[] args){
        String fileName = "lab5.txt";

        try {
            
            FileWriter fileWriter = new FileWriter(fileName);

            
            BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

            
            bufferedWriter.write(args[0]);
            bufferedWriter.newLine(); 
            bufferedWriter.write(args[1]);
            bufferedWriter.newLine();
            bufferedWriter.write(args[2]);

            
            bufferedWriter.close();
            fileWriter.close();

            System.out.println("File created and lines added successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
`

## Command Line Arguments Ran (in order)

`$ javac Anagram.java`

`$ java Anagram racecar = racecar`

Additional argument ran to find file during error

`$ find lab5.txt`

## Edit to fix bug

Remove the `directoryPath` variable seen in the screenshot, in order to create the file directly in the current-nonspecified directory.

# Reflection Part 2

The coolest thing for me was the ssh into a computer, and learning how to use vim for 2 reasons.  First, the sshing into the computer because honestly it made me feel like a hacker, it sort of sparked that fun energetic feeling from learning something new in cs
more than any other topic really and I also appreciated it because it seemed like the most applicable skill.  Secondly, I appreciated vim because when I got accepted into my major I joined a meme page about CS memes and one that kept coming up was about it being impossible to exit vim, so when
it was first introduced I remember the first thing I wanted to see was how to exit vim to see what the memes were all about so that part made me smile.
