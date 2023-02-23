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

#### Clone your fork of the repository from your Github account

```bash
git clone git@github.com:kevin-dough/lab7.git
```
> clones from my forked repository of lab7

#### Run the tests, demonstrating that they fail

```bash
cd lab7
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```
> changes into the lab7 directory, compiles, and runs the tester file

#### Edit the code file to fix the failing test

```bash
nano ListExamples.java
```
then hold down arrow key to find the last "`index1`" and replace with "`index2`"

> opens a nano editor with the `ListExamples.java` file and then I manually replace

#### Run the tests, demonstrating that they now succeed

```bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore 
```
> compiles and runs the tester file again

#### Commit and push the resulting change to your Github account

```bash
git add ListExamples.java
git commit -m "Updated"
git push
```
> stages the changes in `ListExamples.java`, commits them with the message "`Updated`" and pushes them to the repository