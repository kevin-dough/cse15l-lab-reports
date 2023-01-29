## Week 3 Lab Report
> By Kevin Do


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
![image](https://user-images.githubusercontent.com/54718041/215361255-36897b84-aa2c-4098-9134-8d2eeb772f9e.png)

![image](https://user-images.githubusercontent.com/54718041/215361266-528baa70-5725-463d-8a19-c5ce8a4e4d0b.png)

![image](https://user-images.githubusercontent.com/54718041/215361308-53085aa7-7254-4d2b-861a-4e7b81c67f04.png)

![image](https://user-images.githubusercontent.com/54718041/215361311-baa2eafe-06d1-4d1a-9709-b70e15a8867e.png)





IMAGE 2------------
