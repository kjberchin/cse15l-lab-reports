Step 1: reset your password/find your specific account name
  I. Login to https://sdacs.ucsd.edu/~icc/index.php to find your account name
  II. Follow the directions on https://drive.google.com/file/d/17IDZn8Qq7Q0RkYMxdiIR0o6HJ3B5YqSW/view to reset your password from account lookup
  III. Wait a few minutes to hours for password reset to take place, can take up to 12 hours to initiate new password

Step 2: download/install visual studio code
  I. follow the instructions on  https://code.visualstudio.com/ to install visual studio code

Step 3: install Git
  I. follow the instructions on https://gitforwindows.org/ to install Git

Step 4: set bash as the default terminal in visual studio code
  I. follow the instructions on 
     https://stackoverflow.com/questions/42606837/how-do-i-use-bash-on-windows-from-the-visual-studio-code-integrated-terminal/50527994#50527994 
     to set bash as the default terminal

Step 5: connect to the assigned cse basement computer by ssh'ing your course username
  I. once selected, access the terminal and then input the following
     ssh cs15lsp23zz@ieng6.ucsd.edu
     but replace the zz with the corresponding letters in your CSE15l course specific account name
  II. If this is your first time logging in, select yes when asked if you want to continue connecting
  III. Input the password you selected as your reset password in step 1 II.

Step 6: input your commands
  I. use commands such as
      cd ~
      cd
      ls -lat
      ls -a
      ls <directory> where <directory> is /home/linux/ieng6/cs15lsp23/cs15lsp23abc, where the abc corresponds to another user's course specific ID tag
      cp /home/linux/ieng6/cs15lsp23/public/hello.txt ~/
      cat /home/linux/ieng6/cs15lsp23/public/hello.txt
      these commands will allow you to navigate and interface with both your own commuter, and the lab computer for which you have been assigned.  
