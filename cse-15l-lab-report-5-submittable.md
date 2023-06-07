# Edstem Post

## What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?

Windows, vscode bash terminal

## Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.

When I try to use the terminal to run my program to create a new java file with 3 samples of text, I am receiving the following error in the screenshots below, I have the proper main file, I am in the right directory that the code is referencing but I cant find the file despite the error.  I believe that the likely error is that the file has been created in another directory and that the intended directory path is being substituted as the file name.

Here is my error message

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/38fcfffb-b227-46a9-a29a-890400430ff1)

and my code

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/09d23142-fd4e-47d7-8011-9d6263c62050)

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/642a13e8-1e55-4fe0-b0f8-07e62d08bfa2)

## Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.

I am running no commands other than using the `bash Anagram_script.sh` command to run `javac Anagram.java` and `java Anagram racecar = racecar` to run the program's `main` method.  The input from the command line argument in the `java Anagram` command is just the 3 strings "racecar" " = " "racecar".  The working directory is in the screenshots above.

# TA response

If you think your command has successfully created the file, try using the `find` command to search your directory, also think about find command specifics such as `*` to search all files in a parent directory if its not in the one you think

If you still cannot find your file, it is possible that the error did not create your file, in which case, try editting your code and just creating a file without specifying your directory by removing the `directoryPath` variable and just a file in the current directory.

# Student response to TA

When I try to use the `find` command I recieve the following output

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/5698e220-d442-4ccb-9e22-6ba312868e50)

However when I changed the code by removing the specific directory that worked as it produced a new outcome with the following code and terminal

Code

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/a9566baf-da6a-4501-8541-86061f0b9f60)

Terminal

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/03ce7a40-6173-46e7-8af6-ed8e3445dd00)

# Setup information
## 1.

Directory for terminal commands and code file:

Directory

`/c/Users/nerdb/Desktop/CSE-stuff/CSE15L/lab-report-5/wavelet`

Directory and file structure screenshot

![image](https://github.com/kjberchin/cse15l-lab-reports/assets/130321865/0178ba06-91bc-4e7d-9cf4-3ad021dc2fc3)

(directory is at the bottom of screenshot, file structure on screen left side)

## 2. Code contents of before/after fix

Before

java code

```
import java.io.BufferedWriter;
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
}
```

bash script(unchanged before and after)

```
javac Anagram.java

if [ $? -eq 0 ]; then
    echo "Compilation successful. Running the Java program..."
    echo ""


    java Anagram racecar = racecar
else
    echo "Compilation failed. Please check the Java source code and try again."
fi
```

After

```
import java.io.BufferedWriter;
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
```

## Command Line Arguments Ran (in order)

commands ran in bash script

`$ javac Anagram.java`

`$ java Anagram racecar = racecar`

bash script 

`$ bash Anagram_script.sh`

Additional argument ran to find file during error

`$ find lab5.txt`

## Edit to fix bug

Remove the `directoryPath` variable in the java file seen in the screenshot, in order to create the file directly in the current-nonspecified directory.

# Reflection Part 2

The coolest thing for me was the ssh into a computer, and learning how to use vim for 2 reasons.  First, the sshing into the computer because honestly it made me feel like a hacker, it sort of sparked that fun energetic feeling from learning something new in cs
more than any other topic really and I also appreciated it because it seemed like the most applicable skill.  Secondly, I appreciated vim because when I got accepted into my major I joined a meme page about CS memes and one that kept coming up was about it being impossible to exit vim, so when
it was first introduced I remember the first thing I wanted to see was how to exit vim to see what the memes were all about so that part made me smile.
