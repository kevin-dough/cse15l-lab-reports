## Week 3 Lab Report
> By Kevin Do

## Part 1

### `StringServer.java`
```java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {

    ArrayList<String> strings = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return lineBreaker(strings);
        } else {
            if (url.getPath().contains("add-message")) {
                String[] params = url.getQuery().split("=");
                if (params[0].equals("s")) {
                    strings.add(params[1]);
                    return String.format("\"%s\" was added.", params[1]);
                }
            }
            return "404 Not Found!";
        }
        
    }

    public String lineBreaker(ArrayList<String> strings) {
        if (strings.size() == 0) return "Add some words!";
        String combined = "";
        for (String str : strings) {
            combined = combined.concat(str + "\n");
        }
        return combined;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

### Image 1

![image](https://user-images.githubusercontent.com/54718041/215361255-36897b84-aa2c-4098-9134-8d2eeb772f9e.png)

![image](https://user-images.githubusercontent.com/54718041/215361266-528baa70-5725-463d-8a19-c5ce8a4e4d0b.png)

The first method that is called is the `handleRequest` method, which takes the URI as a parameter. Since the path does not equal "`/`", the method will then check if the path contains "`/add-message`", which it does. It will then split the query string around "`=`" which will separate "`s`" and the string that will be inputted. Such string is then added to my ArrayList. To output the ArrayList, I created a method called `lineBreaker` that adds a linebreak in between each string in the ArrayList.

### Image 2

![image](https://user-images.githubusercontent.com/54718041/215361308-53085aa7-7254-4d2b-861a-4e7b81c67f04.png)

![image](https://user-images.githubusercontent.com/54718041/215361311-baa2eafe-06d1-4d1a-9709-b70e15a8867e.png)

When another message is added to the list of Strings, the same process happens with the `handleRequest` method. The URI will be different since there is a different query. The path and querys are checked again except this time `params[1]` will be "`HEHEHEHA`". Since this is the second string that is being added to the ArrayList, it will be after the first string: `Hello! Welcome to McDonalds, may I take your order?`. This means that when the string is output it is different from after the first input.

## Part 2

#### Code Snippet
```java
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

#### Failure Inducing Input
```java
@Test
  public void failInput() {
    double[] list = {1.0, 1.0, 1.0, 1.0};
    assertEquals(1.0, ArrayExamples.averageWithoutLowest(list), 0);
  }
```

#### Non-Failure Inducing Input
```java
@Test
  public void nonfailInput() {
    double[] input = {5.0};
    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input), 0);
  }
```

#### Screenshot of Both Inputs JUnit test results

![image](https://user-images.githubusercontent.com/54718041/215363299-4ea3166f-9933-4387-87f7-b2f43356fdf0.png)

The first input ouputs the correct value `0.0`. Since `5.0` is the lowest and only item in the array, if you add up everything except that number, the sum and average should be 0.

The second input should output `1.0` since the lowest is removed. `1.0` is the lowest so the average should be of 3 `1.0`'s. Although, the program may be written to remove all of the lowest on purpose but in this case the purpose will be to remove only one.


#### Fixing the Code
Before: see `Code Snippet` above.

After:
```java
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) { // the code will add up all the numbers
      sum += num;
    }
    sum -= lowest; // then it will subtract the lowest value
    return sum / (arr.length - 1);
  }
```
This code makes sure that only one instance of the lowest in the array is removed instead of all.
