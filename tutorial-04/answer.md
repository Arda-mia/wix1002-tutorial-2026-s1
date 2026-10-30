# Tutorial 01 — Answers

### Question 1
Write statements for each of the following:

a) find the largest integer n so that n³ is less than 2000

```java
int n = 0;
while ((n + 1) * (n + 1) * (n + 1) < 2000) {
    n++;
}
System.out.println("n = " + n);   // n = 12, because 12^3 = 1728 and 13^3 = 2197
```
b) display the square numbers of the first twelve integers starting from 1

```java
for (int i = 1; i <= 12; i++) {
    System.out.println(i + " squared is " + i * i);
}
```

c) display a 4-by-5 matrix using random numbers within 0 to 100

```java
Random random = new Random();             // import java.util.Random;
for (int row = 1; row <= 4; row++) {      // 4 rows
    for (int col = 1; col <= 5; col++) {  // 5 columns in each row
        System.out.printf("%5d", random.nextInt(101));   // 0 to 100 
    } // %5d:Specifies that the output should occupy at least 5 character spaces, Specifies that the value to be inserted is a whole integer.
    System.out.println();                 // end the row
}
```

d) compute the sum of numbers from 1 to a given number

```java
import java.util.Scanner;

public class SumToN {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in); // creates a scanner object that allows your program to read input from the user via the keyboard
        System.out.print("Enter a number: ");
        int number = keyboard.nextInt(); //read input

        int sum = 0; //initialize sum as 0
        for (int i = 1; i <= number; i++) {
            sum += i;
        }
        System.out.println("Sum of 1 to " + number + " = " + sum);
    }
}
```

e) compute the sum of the series 1/25 + 2/24 + 3/23 + … + 25/1 in two decimal places.

```java
double sum = 0;
for (int i = 1; i <= 25; i++) {
    sum += (double) i / (26 - i);   // numerator i, denominator 26 - i
}
System.out.printf("Sum = %.2f%n", sum);   // Sum = 74.21
```

### Question 2
Correct the error in each of the following statements.

a)
```java
for (x = 10; x > 0; x++) //1. initialize iteration 2.infinite loop
    sum += x;
```
Correction:
```java
int sum = 0;
for (int x = 10; x > 0; x--)
    sum += x;          // 10 + 9 + ... + 1 = 55
```

b)
```java
do //command more than one line need {}
    x += 2;
    y += x;
    System.out.println(x + " and " + y);
while (x < 100) //semicolumn
```
Correction:
```java
int x = 0, y = 0;
do {
    x += 2;
    y += x;
    System.out.println(x + " and " + y);
} while (x < 100);
```

c)
```java
for ( x==1, y==20; x < y, x++, y-=2); //1. need to initialize x and y 2. == is compares instead initializing values 3. semicolumn after header makes an empty body
    System.out.println(x & " " & y); // & is not string concatenation (join two or more strings together creating a single line string)
```
Correction:
```java
int x, y;
for (x = 1, y = 20; x < y; x++, y -= 2)
    System.out.println(x + " " + y);
```

d)
```java
i =1; //initialize i
while(i<10) { // i < 10 can never have iteration of tenth creating error (logic error)
    if (i==10) 
        System.out.println("Program End");
} // i is never updated creating infinite loop error
```
Correction:
```java
int i = 1;
while (i <= 10) {
    if (i == 10)
        System.out.println("Program End");
    i++;
}
```

### Question 3

Write the statements that display the first ten values of the Fibonacci sequence, given the formula f1 = 1, f2 = 1, fn = fn−1 + fn−2.

```java
int previous = 1, current = 1;       // f1 and f2 (assigning the two first value as 1)
System.out.print(previous + " " + current);
for (int n = 3; n <= 10; n++) { // for the next 7 fibonacci number so n=3
    int next = previous + current;   // fn = fn-1 + fn-2 (to get the next fibonacci number)
    System.out.print(" " + next);    // print next fibonacci number
    previous = current;              // slide the window forward (reassigning the variable)
    current = next;
}
System.out.println();                // 1 1 2 3 5 8 13 21 34 55 (print a new empty line for the next in case for the future statements)
```

### Question 4
Write the statements that display a string in reverse order. Use String.length() to get the length of the string.

```java
import java.util.Scanner;

public class ReverseString {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);             // creates a scanner object that allows your program to read input from the user via the keyboard
        System.out.print("Enter a string: ");
        String text = keyboard.nextLine();                     // Reads an entire line of text (including spaces) and store in variable named text

        String reversed = "";                                  // initializing empty string variable named reversed
        for (int i = text.length() - 1; i >= 0; i--) {         // text.length(): Gives the total number of characters in the string
                                                               // - 1: Because Java counts string positions (indices) starting at 0
            reversed += text.charAt(i);                        // text.charAt(i): A built-in method that looks at the string and grabs the single character sitting at index i.
        }
        System.out.println("Reverse: " + reversed);
    }
}
```
