#Arrays#
An array is an ordered list of items of a given data type. 
Each item in an array is called an element.
example of declaring Array reference variable and array allocation.
```
dataType[] arrayName = new dataType[numElements];
```
An array reference variable can refer to arrays of various sizes. The new keyword creates space in memory to store the array with the specific number of elements. The array reference variable is assigned to refer to that newly allocated array. Ex: int[] gameScores = new int[4]; declares an array reference variable gameScores, allocates an array of four integers, and assigns gameScores to refer to the allocated array.

Terminology note: [ ] are brackets. { } are braces. In an array access, the number in brackets is called the index of the corresponding element.
The first array element is at index 0.

an array is useful to easily lookup the Nth item in a list.
An array's index must be an integer type. The array index cannot be a floating-point type, even if the value is 0.0, 1.0, etc

Example Problem:
Assign tempVal with the myVals array element at the index one after the value held in variable i.
```
tempVal = myVals[i+1];
```
Note: can put in variables or expressions inside the brackets of an array.

**Loops and arrays**
A key advantage of arrays becomes evident when used in conjunction with loops. The program below uses a loop to allow a user to enter 8 integer values, storing those values in an array, and then printing those 8 values.
An array's length property, accessed by appending .length after the array's name, indicates the number of array elements. Ex: In the program below, userVals.length is 8 because the array was allocated with 8 elements.

```
import java.util.Scanner;

public class ArrayPrinter {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      final int NUM_ELEMENTS = 8;             // Number of elements in array
      int[] userVals = new int[NUM_ELEMENTS]; // User numbers
      int i;                                  // Loop index

      System.out.println("Enter " + NUM_ELEMENTS + " integer values...");
      for (i = 0; i < userVals.length; ++i) {
         userVals[i] = scnr.nextInt();
         System.out.println("Value: " + userVals[i]);
      }
      
      System.out.print("You entered: ");
      for (i = 0; i < userVals.length; ++i) {
         System.out.print(userVals[i] + " ");
      }
      System.out.println();
   }
}
```
The Result: 
Enter 8 integer values...
Value: 5
Value: 99
Value: -1
Value: -44
Value: 8
Value: 555555
Value: 0
Value: 2
You entered: 5 99 -1 -44 8 555555 0 2

**Array initialization**
An array's elements are automatically initialized to default values when using the new keyword to initialize the array reference. The default value for elements of integer and floating-point data types is zero, and the default value for boolean elements is false. For information on default values of other data types, see The Java Language Specification.

A programmer may initialize an array's elements with non-default values by specifying the initial values in braces {} separated by commas. Ex: int[] myArray = {5, 7, 11}; creates an array of three integer elements with values 5, 7, and 11. Such array initialization does not require the use of the new keyword, because the array's size is automatically set to the number of elements within the braces. For larger arrays, initialization may be done by first defining the array, and then using a loop to assign array elements.

**Challenge Activity 8.2.3 Printing array elements with a for loop**

Write a for loop to print all elements in courseGrades, following each element with a space (including the last). Print forwards, then backwards. End each loop with a newline. Ex: If courseGrades = {7, 9, 11, 10}, print:
7 9 11 10 
10 11 9 7 

Hint: Use two for loops. Second loop starts with i = courseGrades.length - 1.

```
import java.util.Scanner;

public class CourseGradePrinter {
   public static void main (String [] args) {
      Scanner scnr = new Scanner(System.in);
      final int NUM_VALS = 4;
      int [] courseGrades = new int[NUM_VALS];
      int i;

      for (i = 0; i < courseGrades.length; ++i) {
         courseGrades[i] = scnr.nextInt();
      }

      for(i=0; i < courseGrades.length; ++i){
         System.out.print(courseGrades[i] + " ");
      }
      System.out.println("");
      
      for(i = (courseGrades.length - 1); i >= 0; --i){
         System.out.print(courseGrades[i] + " ");
      }
      System.out.println("");

   }
}
```
**8.4 Iterating through arrays**
```
// Iterating through myArray
for (i = 0; i < myArray.length; ++i) {
   // Loop body accessing myArray[i]
}
```
Iterating through an array example: Program that computes the sum of an array's elements.

```
import java.util.Scanner;

public class ArraySum {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      final int NUM_ELEMENTS = 8;             // Number of elements
      int[] userVals = new int[NUM_ELEMENTS]; // User numbers
      int i;                                  // Loop index
      int sumVal;                             // For computing sum

      // Prompt user to populate array
      System.out.println("Enter " + NUM_ELEMENTS + " integer values...");
      
      for (i = 0; i < userVals.length; ++i) {
         userVals[i] = scnr.nextInt();
         System.out.println("Value: " + userVals[i]);
      }

      // Determine sum
      sumVal = 0;
      for (i = 0; i < userVals.length; ++i) {
         sumVal = sumVal + userVals[i];
      }
      System.out.println("Sum: " + sumVal);
   }
}
```
Result:
Enter 8 integer values...
Value: 3
Value: 5
Value: 234
Value: 346
Value: 234
Value: 73
Value: 26
Value: -1
Sum: 920

...

Enter 8 integer values...
Value: 3
Value: 5
Value: 234
Value: 346
Value: 234
Value: 73
Value: 26
Value: 1
Sum: 922

Iterating through an array example: Program that finds the max item.
```
import java.util.Scanner;

public class ArrayMax {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      final int NUM_ELEMENTS = 8;             // Number of elements
      int[] userVals = new int[NUM_ELEMENTS]; // Array of user numbers
      int i;                                  // Loop index
      int maxVal;                             // Computed max

      // Prompt user to populate array
      System.out.println("Enter " + NUM_ELEMENTS + " integer values...");
      
      for (i = 0; i < userVals.length; ++i) {
         userVals[i] = scnr.nextInt();
         System.out.println("Value: " + userVals[i]);
      }

      // Determine largest (max) number
      maxVal = userVals[0];                   // Largest so far
      
      for (i = 0; i < userVals.length; ++i) {
         if (userVals[i] > maxVal) {
            maxVal = userVals[i];
         }
      }
      System.out.println("Max: " + maxVal);
   }
}
```
Result:
Enter 8 integer values...
Value: 3
Value: 5
Value: 23
Value: -1
Value: 456
Value: 1
Value: 6
Value: 83
Max: 456

...

Enter 8 integer values...
Value: -5
Value: -10
Value: -44
Value: -2
Value: -27
Value: -9
Value: -27
Value: -9
Max: -2

A common error is to try to access an array with an index that is out of the array's index range.



*******************************************************************************************************************************************************************
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/float437/Programming1Notes/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/float437/Programming1Notes/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
