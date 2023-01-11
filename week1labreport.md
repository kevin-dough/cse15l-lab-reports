## Week 1 Lab Report
> By Kevin Do

### VS Code
Install VS Code by downloading it from the website ([`code.visualstudio.com`](https://code.visualstudio.com/)) and following the instructions to install.

After opening the application, open the terminal by clicking `Terminal` on the menu bar and selecting `New Terminal`.

![image](https://user-images.githubusercontent.com/54718041/211928277-dc5a9e8b-3322-4e72-af2b-d14c97ca6788.png)

If you are using Windows,
- make sure you have git installed by typing `git --version`
   - if a version shows, then you have git installed
   - if not, download and install git ([`gitforwindows.org`](https://gitforwindows.org/))
- once git is installed, go back to VS Code and type `Select Default Profile` and select `Git Bash`
- in the terminal window, press the `+` to open a new terminal, which will be in Git Bash

### Remote Connection
Use the following command to connect with the computers in the CSE Basement.
```
$ ssh cs15lwi23___@ieng6.ucsd.edu
```
> replace the blank with your account letters, which can be found by following the instructions on [`sdacs.ucsd.edu/~icc/index.php`](https://sdacs.ucsd.edu/~icc/index.php)

After entering your password, you will see an output similar to this:

![image](https://user-images.githubusercontent.com/54718041/211933231-58403ea5-8662-4937-93c8-ea293a01eb60.png)

### Running Commands
After connecting remotely with the host, you can run commands.

Use `pwd` to print the current working directory.

Use `cd` to change directories.

Use `ls` to list the files in the current directory.

Here is a list of commands I ran and their results:

![image](https://user-images.githubusercontent.com/54718041/211933311-15fa8d5b-45ae-4cd1-8507-9c298bcb52c9.png)

![image](https://user-images.githubusercontent.com/54718041/211933350-b2fad641-d706-40c1-83ed-c48c175e105f.png)


To exit the remote server you can either use `Ctrl + D` or type `exit`.
