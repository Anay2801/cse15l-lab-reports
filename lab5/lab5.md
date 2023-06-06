# Lab Report 5 - Putting it all together

## Part 1
### Post from the Student
**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**
I'm on a Mac and using Visual Studio Code.

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**
Hey, I have written an algorithm for binary search, however, it does not seem to return the correct index of the value being searched. Here is my code:

![Image]()

I tested it using the following JUnit test case:

![Image]()


**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**
I ran the JUnit test case above using the following the bash script:

![Image]()

### Response from the TA
Hi, I would like to draw ur attention to assigning values to low and high in the `else if` and `else` statements. There is a logical error when you assign these values. The aim is to narrow down the search area. Try fiddling with these 2 values and understand the logic behind the assignment. You should be able to find the error in a while. Let me know if you have any further questions!

### Student's response to the TA
Oh yes! It makes sense now. I searched the wrong part of the array. When the target value is less than the middle element, I subtracted 1 from low and added 1 to high, which leads to an incorrect narrowing down of the search space. Instead, I should have added to low and subtracted from high.

### Final information
**Files Before Bug Fixes:**
**BinarySearch.java -**
```
public class BinarySearch {
  public static int binarySearch(int[] arr, int target) {
      int low = 0;
      int high = arr.length - 1;

      while (low <= high) {
          int mid = (low + high) / 2;

          if (arr[mid] == target) {
              return mid; 
          } else if (arr[mid] < target) {
              low = mid - 1; 
          } else {
              high = mid + 1; 
          }
      }

      return -1; 
  }
}
```
**BinarySearchTest.java - **
```
import static org.junit.Assert.*;
import org.junit.*;

public class BinarySearchTest {
    @Test
    public void testBinarySearch() {
        int[] arr = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
        int target = 56;
        int expectedIndex = 7;

        int actualIndex = BinarySearch.binarySearch(arr, target);
        assertEquals(expectedIndex, actualIndex);
    }
}
```

**test.sh -**
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore BinarySearchTest
```

**Command that induced the bug:**
```bash test.sh```

**ListExamples.java after fix:**

**Terminal after fixes:**


## Part 2 - Reflection
For me, the usage of Vim and the concept of doing all tasks from the command line was the most useful and interesting. Before this class, I had never heard of Vim. The fact that I could view and edit files in another computer (using ssh) was the useful and fascinating component of my lab experience in the second half of the quarter.
