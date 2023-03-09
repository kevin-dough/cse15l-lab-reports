## Week 9 Lab Report
> By Kevin Do

### "Done Quick" Lab Task with a Bash Script

### Manual Steps:

#### Log into ieng6

```bash
ssh cs15lwi23als@ieng6.ucsd.edu
```
> logs into my ieng6 account

![image](https://user-images.githubusercontent.com/54718041/221057637-928cb4cc-89ee-4f75-b611-bea33acc11e0.png)


#### Clone your fork of the repository from your Github account

```bash
git clone git@github.com:kevin-dough/lab7.git
```
> clones from my forked repository of lab7

![image](https://user-images.githubusercontent.com/54718041/221057931-2922845c-d7e8-48c1-8913-3863138d2a3c.png)

#### Run the tests, demonstrating that they fail

```bash
cd lab7
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```
> changes into the lab7 directory, compiles, and runs the tester file

![image](https://user-images.githubusercontent.com/54718041/221058649-d50da2d6-d0c5-4f3c-a958-1cb39ca49b78.png)

#### Edit the code file to fix the failing test

```bash
nano ListExamples.java
```
then hold down arrow key to find the last "`index1`" and replace with "`index2`"

> opens a nano editor with the `ListExamples.java` file and then I manually replace
> ^O &lt;enter> and ^X to save and exit

![image](https://user-images.githubusercontent.com/54718041/221058721-f7d32efe-4bfa-4121-82d8-a8f53054d62e.png)

#### Run the tests, demonstrating that they now succeed

```bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore 
```
> compiles and runs the tester file again

![image](https://user-images.githubusercontent.com/54718041/221059245-ef1411d6-09ce-4f92-97a2-07a2994d6d18.png)


#### Commit and push the resulting change to your Github account

```bash
git add ListExamples.java
git commit -m "Updated"
git push
```
> stages the changes in `ListExamples.java`, commits them with the message "`Updated`" and pushes them to the repository

![image](https://user-images.githubusercontent.com/54718041/221059776-16226181-3689-4407-8ac8-ef00a03b489c.png)

### Using a bash script

Using the bash script would decrease the amount of actions the user would have to do in order to clone, run tests, fix code, rerun tests, and commit changes to the Github repository. I did not include the logging into the ieng6 account as part of the script because it is like a "different" terminal" and I don't think the bash commands would be able to execute locally and in the remote host after.

The bash script is located inside of the remote server and is ran from inside the remote server.

The first step of executing the comands for the lab task is to log into the ieng6 account. This was done quickly by having ssh keys on my computer. This allows me to only have to type the ssh command without having to enter my password.

After logging into ieng6, I only have to type `bash kevin.sh` and run that. The command will do all the tasks including changing the code. My first version of the script was unable to change the code and would simply open up to the nano editor. By using the `sed` command, I was able to change the code and reduce the runtime by at least 5 seconds.

A problem I ran into while writing the script was being able to compile and run the java files from outside of the lab7 directory. Although, I just changed directories and was able to compile and run. I probably just incorrectly wrote the directories for the junit files since there was a problem with finding it previously.

bash script `kevin.sh`
```bash
# clones the github repository using ssh
git clone git@github.com:kevin-dough/lab7.git

# compiles the code (all java files)
javac -cp .:lab7/lib/hamcrest-core-1.3.jar:lab7/lib/junit-4.13.2.jar lab7/*.java

# changes directory into the lab7 directory
cd lab7

# runs the code and tester
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples

# changes index1 on line 43 to index2 and writes it to the file
sed -i '43s/index1/index2/g' ListExamples.java

# compiles the code
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

# runs code again
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples

# staging, committing, and pushing the code to the github repo
git add ListExamples.java
git commit -m "Updated"
git push
```