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
IMAGE 1------------




IMAGE 2------------