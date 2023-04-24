    import java.io.IOException;
    import java.net.URI;
    import java.util.ArrayList;
    class Handler implements URLHandler {
        // The one bit of state on the server: a number that will be manipulated by
        // various requests.
        ArrayList<String> strList = new ArrayList<>();
        String returnString = "";
        public String handleRequest(URI url) {
            if (url.getPath().contains("/add-message")) {
                System.out.println("Path: " + url.getPath());
                String[] parameters = url.getQuery().split("=");
                returnString += parameters[1] + "\n";
                return returnString;
            }
            return "404 Not Found!";
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

![Image](Screenshot 2023-04-23 185808.jpg)

Methods being called:

--The main method to take my port number

--The handleRequest method that takes my specific add-message path and the String with it

Relevant method arguments and fields:

--The add-message argument is relevant as it is the correct command for the path as well as the string coming after the equals sign as that is what is displayed

--The returnString field is relevant as it is what is actually added into by the parameters array index 1, and what is displayed, the example here is that returnString had the String "test" added to it

Class field values changed by request:

-- The values that were changed were the URI as it was modified to accept an "argument" which was whatever String we wanted added to the disply, as well as the returnString field which was previously discussed.  In this case, the addition of the word "test" after the equals in the URI was what was modified

![Image](Screenshot 2023-04-23 185457.jpg)

Methods being called:

--The main method to take my port number

--The handleRequest method that takes my specific add-message path and the String with it

Relevant method arguments and fields:

--The add-message argument is relevant as it is the correct command for the path as well as the string coming after the equals sign as that is what is displayed

--The returnString field is relevant as it is what is actually added into by the parameters array index 1, and what is displayed, the example here is that returnString had the String "again" added to it on top of the previously added "test"

Class field values changed by request:

-- The values that were changed were the URI as it was modified to accept an "argument" which was whatever String we wanted added to the disply, as well as the returnString field which was previously discussed. In this case, the addition of the word "again" after the equals in the URI was what was modified


----END OF PART 1----

    import static org.junit.Assert.*;
    import org.junit.*;

    public class ArrayTests {

      // failure test
      //succesfully reverses the first half of the list however leaves the second half unaltered because when it reaches index 2
      // it will not because it already reversed and updated at the first two indecies.  
      @Test
      public void testReversedInPlace2() {
        int [] input2 = {1, 2, 3, 4};
        ArrayExamples.reverseInPlace(input2);
        assertArrayEquals(new int[]{4, 3, 2, 1}, input2);
      }
        // succesful test
        @Test 
        public void testReverseInPlace() {
        int[] input1 = { 3, 2 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 2, 3 }, input1);
        }
    }
