# Tutorial 05 — Answers
### Question 1
(a) declare an array used to store 12 floating-point numbers
```java
double[] numbers = new double[12]
```
(b)initialise an array used to store the values A to E
```java
char[] letters = {'A', 'B', 'C', 'D', 'E'};
```
(c)declare an array used to store 100 students’ names
```java
String[] names = new String[100]; 
```
(d)declare an array for a table with 6 rows and 2 columns used to store integer values
```java
int[][] table = new int[6][2]; 
```
(e)initialise an array with the values shown below
```java
int[][] array = { {6, 9}, {2, 5}, {4, 6} };
```
(f)after initialising the array, modify its values to the second table
```java
array[1][1] = 4;   //     row 1, column 1: 5 becomes 4
array[2][0] = 3;   //     row 2, column 0: 4 becomes 3
array[2][1] = 7;   //     row 2, column 1: 6 becomes 7
```
(g)display all the values of an array named contact in separate lines.
```java
for (int k = 0; k < contact.length; k++) {
    System.out.println(contact[k]);   // println: one value per line
}
```

### Question 2
Correct the error in each of the following statements.
(a)
```java
String[] code = {'AAA', 'AAB', 'AAC', 'AAD'};
```
correction:
```java
String[] code = {"AAA", "AAB", "AAC", "AAD"};
```
(b)
```java
int[] num = new num[10];
for(int k=0; k<=num.length(); k++)
    sum+=num;
```
correction:
```java
int[] num = new int[10];                //must name the element type
int sum = 0;                            //initialize sum value
for (int k = 0; k < num.length; k++)    //the indexes are 0 to 9
    sum += num[k];                      //specify the index
```
(c)
```java
int [][]t = new int[3][];
t[1][2] = 5;
```
correction:
```java
int[][] t = new int[3][];   // 3 rows that do not exist yet: each t[r] is null
t[1] = new int[3];          // create row 1 with 3 columns
t[1][2] = 5;

// or create every row at once:
int[][] t = new int[3][3];
```
(d)
```java
int i=4;
int []score = new int[5];
score [1] = 78;
score[++i] = 100;
```
correction:
```java
int i = 4;
int[] score = new int[5];   // valid indexes 0 to 4
score[1] = 78;
score[i] = 100;             // index 4, the last element
```

### Question 3
Determine the values of each element of array marks. Assume the array was declared as:
```java
int[] marks = new int[5];
int i = 0, j = 1;
marks[i] = 12;
marks[j] = marks[i] + 19;
marks[j-1] = marks[j] * marks [j];
marks[j*3] = marks[i+1];
marks[++j] = marks[i]%5;
marks[2*j] = marks[j-1];
```
marks[0]=961
marks[1]=31
marks[2]=1
marks[3]=31
marks[4]=31

### Question 4
Write the statements that display the number of occurrences of the word "the" (case sensitive) in a string array named sentence.

```java
String[] sentence = {"the", "cat", "and", "The", "dog", "saw", "the", "bird"};
int count = 0;
for (int k = 0; k < sentence.length; k++) {
    if (sentence[k].equals("the")) {   // case sensitive: "The" does not match
        count++;
    }
}
System.out.println("\"the\" occurs " + count + " time(s)");   // 2
```

### Question 5
Write the statements that display the string array named sentence in reverse order. Each string element must be displayed in reverse order as well.
```java
for (int k = sentence.length - 1; k >= 0; k--) {           // last element first
    for (int c = sentence[k].length() - 1; c >= 0; c--) {   // last character first
        System.out.print(sentence[k].charAt(c));
    }
    if (k > 0) {
        System.out.print(" ");                               // space between words
    }
}
System.out.println();                                        // nuf si avaJ
```

### Question 6
Write the statements that generate 1 random integer within 0–255. Convert the number to binary and store the bits in an 8-bit array. Then, display the binary number.
```java
import java.util.Random;

public class RandomBinary {
    public static void main(String[] args) {
        Random random = new Random();
        int number = random.nextInt(256);   // 0 to 255

        int[] bits = new int[8];            // 8 bits: bits[0] is 128, bits[7] is 1
        int value = number;
        for (int k = 7; k >= 0; k--) {
            bits[k] = value % 2;            // remainder is the next bit from the right
            value /= 2;
        }

        System.out.println("Random number: " + number);
        System.out.print("Binary: ");
        for (int k = 0; k < bits.length; k++) {
            System.out.print(bits[k]);
        }
        System.out.println();
    }
}
```
