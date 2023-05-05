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

![Screenshot 2023-04-23 185808](https://user-images.githubusercontent.com/130321865/236385843-b58a9057-35dd-422f-a838-bb20452f8ee2.jpg)


Methods being called:

--The main method to take my port number

--The handleRequest method that takes my specific add-message path and the String with it

Relevant method arguments and fields:

--The add-message argument is relevant as it is the correct command for the path as well as the string coming after the equals sign as that is what is displayed

--The returnString field is relevant as it is what is actually added into by the parameters array index 1, and what is displayed, the example here is that returnString had the String "test" added to it

Class field values changed by request:

-- The values that were changed were the URI.  Specifically, the handler first takes the path of the URI.  If that path only is a `/` then it simply returns the existing set number which starts at 0.  

However, if this is not the case then it checks if the path for the URL contains `/increment` which it will then simply increase num by 1 and display the word number incremented.  

However if this is not the case it will lastly check if the url contains `/add` and if so it will then set a string array variable as the query seperated into two parts using the `.getQuery()` method which will split that query down the equal sign with the part prior being `parameters[0]` and the part following being `parameters[1]` 

If `parameters[0]` is count and `parameters[1]` is a string that can be parsed as a number, it will then do the following, it will parse the string `parameters[1]` as an integer and then increase the num variable by whatever that integer was by doing `num += Integer.parseInt(parameters[1]);` 

This has the effect of checking firstly if the add command is in correct format with count = x, but it will also check if the x is a parseintable string and if so, it will add it to our num to be displayed.  

![Screenshot 2023-04-23 185457](https://user-images.githubusercontent.com/130321865/236385913-ac9297ae-07ff-49f2-87fd-83999aea9f03.jpg)

Methods being called:

--The main method to take my port number

--The handleRequest method that takes my specific add-message path and the String with it

Relevant method arguments and fields:

--The add-message argument is relevant as it is the correct command for the path as well as the string coming after the equals sign as that is what is displayed

--The returnString field is relevant as it is what is actually added into by the parameters array index 1, and what is displayed, the example here is that returnString had the String "again" added to it on top of the previously added "test"

Class field values changed by request:

-- The values that were changed were the URI as it was modified to accept an "argument" which was whatever String we wanted added to the disply, as well as the returnString field which was previously discussed. In this case, the addition of the word "again" after the equals in the URI was what was modified

# ----END OF PART 1----

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
        int[] input1 = {55};
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{55}, input1);
        }
    }
    
![Screenshot 2023-04-23 192157](https://user-images.githubusercontent.com/130321865/236385958-061dabb2-9646-444c-ac5e-35b4b6815315.jpg)
    
    public class ArrayExamples {

      // Changes the input array to be in reversed order
      //BUGGY METHOD
      static void reverseInPlaceBuggy(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = arr[arr.length - i - 1];
        }
      }

        //FIXED METHOD
        static void reverseInPlaceFixed(int[] arr){
          int[] copyArray = new int[arr.length];
          for (int i = 0; i < arr.length; i += 1) {
            copyArray[i] = arr[i];
          }
          for(int i = 0; i < arr.length; i += 1) {
            arr[i] = copyArray[arr.length - i - 1];
          }
        }
    }

--The issue present with the original method can be expressed symptom wise as only copying the first half of the array, then not the second, however the problem was that it would succesfully reverse the first half but then when doing `arr[arr.length - i - 1]` It was indexing the already mofified first half to decide the values for the second half of the array

--The fix for it was to make a shallow copy array with the original items in it and when the actual reversing was taking place, having the reversed values be references of the copy array rather than the already modified original.

# ----END OF PART 2----

--Something I learned from lab 2 that I did not previoulsy know was that you can create your own local host website.  I had no idea that you could do it without a domain and that other people could access it.  Moreover, I did not know that being on the same wifi network would affect whether this is possible or not.
