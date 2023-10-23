#Part 1
#My code of StringServer:

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {

    int num = 0;

    public static String s = "";

    public String handleRequest(URI url) {

        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                num += 1;
                s += num + ". "  + parameters[1] + "\n";
                return s;
            }
            else{
                return "404 Not Found!";
            }
        }
        return "Please use the '/add-message' to add a single string.";
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
#Add first single string "Hello".
![Image](6.jpg)
Which methods in your code are called?
The handleRequest method is called.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The relevant arguments are the URL and UCI. The UCI includes the path and query. Relevant fields are ```String s``` and ```int num```. ```String s``` is used to add and hold strings from add-messages. ```int num``` is used to show how many single strings we put.


How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
When we add "/add-message?s=Hello". The " /add-message" is the path, the "?s=Hello" is the query. Meanwhile, I use ```String[] parameters = url.getQuery()``` to take the query= parameters[] that I entered and use ```url.getQuery().split("=")``` to separate ? and Hello separately. Thus, ```parameters[0] = s```and ```parameters[1] = Hello```. I set up an if loop so that when ```parameters[0] = "s"``` we make num +1 with ``num+=1``. and ```s += num + ". " + parameters[1] + "\n"``` to add num and parameters[1] to the ```String s``` with a newline. So the output is "1. Hello".


#Add second single string "How are you".
![Image](7.jpg)
Which methods in your code are called?
The handleRequest method is called.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The relevant arguments are the URL and UCI. The UCI includes the path and query. Relevant fields are ```String s``` and ```int num```. ```String s``` is used to add and hold strings from add-messages. ```int num``` is used to show how many single strings we put.

How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
When we add "/add-message?s=How are you". The " /add-message" is the path, the "?s=Hello" is the query. Meanwhile, I use ```String[] parameters = url.getQuery()``` to take the query= parameters[] that I entered and use ```url.getQuery().split("=")``` to separate ? and Hello separately. Thus, ```parameters[0] = s```and ```parameters[1] = Hello```. I set up an if loop so that when ```parameters[0] = "s"``` we make num +1 with ``num+=1``. and ```s += num + ". " + parameters[1] + "\n"``` to add num and parameters[1] to the ```String s``` with a newline. Also, because my computer can't output ```%20``` as a space. Therefore, the output is "2. How+are+you".

The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer)
![Image](4.jpg)
The absolute path to the private key is in ```C:\Users\syunn\.ssh\id_rsa.pub```

The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6)
![Image](8.jpg)
The absolute path to the public key is in ```/home/linux/ieng6/cs15lfa23/cs15lfa23gw/.ssh```

