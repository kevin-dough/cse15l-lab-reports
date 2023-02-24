## Week 5 Lab Report
> By Kevin Do

### "Done Quick" Lab Task

The way I did the task was by using a bash script (I didn't know we weren't supposed to...).

So my process for doing the lab was:

1. <^V> (`this would paste the ssh command to log into ieng6`)
2. &lt;enter>
3. bash kevin.sh
4. &lt;enter>

bash script `kevin.sh`
```bash
git clone git@github.com:kevin-dough/lab7.git

javac -cp .:lab7/lib/hamcrest-core-1.3.jar:lab7/lib/junit-4.13.2.jar lab7/*.java

cd lab7

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples

sed -i '43s/index1/index2/g' ListExamples.java

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples

git add ListExamples.java
git commit -m "Updated"
git push
```

The bash `sed` (streamline editor) was used to replace `index1` on line `43` with `index2`.
The `-i` would edit the file in place instead of outputting the edited file to the command line.

If I did the steps manually, my steps would be here:

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
