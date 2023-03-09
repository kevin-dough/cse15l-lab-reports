## Week 9 Lab Report
> By Kevin Do

### "Done Quick" Lab Task with a Bash Script



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