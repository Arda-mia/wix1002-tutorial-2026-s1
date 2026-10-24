# Tutorial 03 — Answers

### Question 1
Write statements

  a) 
  ```java
boolean isEqual = 3 * 8 == 27; //To determine the truth value (True or False)
System.out.println("3 x 8 == 27: " + isEqual); // false
```

  b)
  ```java
if (number % 2 == 0) { //have 0 remainder is even number
    System.out.println(number + " is an even number");
} else { //have remainder is an odd number
    System.out.println(number + " is an odd number"); 
}
```

  c)
  ```java
if (ch >= 'A' && ch <= 'Z') { //check capital letter from A to Z
    System.out.println(ch + " is a capital letter");
} else {
    System.out.println(ch + " is not a capital letter");
}
```

  d)
  ```java
if (first.compareToIgnoreCase(second) <= 0) { //by using built-in method compareToIgnoreCase() treating uppercase and lowercase letter as identical
//compare, first comes before second
    System.out.println(first + " " + second);
} else { //means second comes before first
    System.out.println(second + " " + first);
}
```

  e)
  ```java
switch (day) { //day is the control variable (gets input from user and passed to switch block)
    case 0:
        System.out.println("Sunday");
        break; //terminates the switch block once a match is executed
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
        System.out.println("Thursday");
        break;
    case 5:
        System.out.println("Friday");
        break;
    case 6:
        System.out.println("Saturday");
        break;
    default: //if input value doesnot match any of the specific case (acts as a fallback mechanism)
        System.out.println("Invalid day");
}
```

### Question 2
Correct the error

a) 
```java
if (num1 = num2) // = is an assignment operator, not the relational equality comparison operator
    System.out.println("Number 1 is equal to number 2.");
```
Correction:
```java
if (num1 == num2)
    System.out.println("Number 1 is equal to number 2.");
```

b)
```java
if (x > y > z) //java does not support chain comparison, must use logical operators like AND (&&), OR(||)
    System.out.println("x is the largest number");
```
Correction:
```java
if (x > y && x > z)
    System.out.println("x is the largest number");
```

c)
```java
String s1, s2;
if (s1==s2) //== compares references, while equals compares String content
    System.out.println("They are equal strings.");
else (s1!=s2)
    System.out.println("They are not equal strings.");
```
Correction:
```java
String s1 = "Java", s2 = "Java";
if (s1.equals(s2))
    System.out.println("They are equal strings.");
else
    System.out.println("They are not equal strings.");
```

d)
```java
if x>0 or y>0; //1)need () 2)if there is a semicolon at the end of the if statement the next command will always executed 3)instead of or use logical operator OR (||)
    System.out.println("Either x or y is positive");
```
Correction:
```java
if (x > 0 || y > 0)
    System.out.println("Either x or y is positive");
```

### Question 3

Write the outputs when x=9 and y=10

a) 
```java
if (x < 10)
  if (y > 10) //if statements inside if statements (nested if)
    System.out.println("*****");
  else
    System.out.println("#####"); //one line command does not need curly brackets {}
System.out.println("$$$$$");
```
Output:
#####
$$$$$

b)
```java
if (x < 10) {
  if (y < 10) //ignore
    System.out.println("*****");
  else{ //run (x=9)
    System.out.println("#####");
    System.out.println("$$$$$");
  }
}
```
Output:
#####
$$$$$

c)
```java
if (x < 10) {
  if (y < 10)
    System.out.println("*****"); //one line doesnt use curly brackets
  System.out.println("#####"); //else command
}
else {
  System.out.println("$$$$$");
}
```
Output:
#####

d)
```java
if (x > 10) { //does not execute because x=9
  if (y > 10) {
    System.out.println("*****");
    System.out.println("#####");
  }
  else
  System.out.println("$$$$$");
}
```
Output:


### Question 4
Java statements that used if statement to find the bigest number amomg three given integer

```java
import java.util.Scanner;

public class BiggestOfThree {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in); //Get input from user
        System.out.print("Enter three integers: ");
        int a = keyboard.nextInt(); //assign all input in each variable
        int b = keyboard.nextInt();
        int c = keyboard.nextInt();

        int biggest = a; //initialize a as biggest so we can compare
        if (b > biggest) { //if b value bigger than a, reassign the biggest variable
            biggest = b;
        }
        if (c > biggest) { //if c value bigger than a, reassign the biggest variable
            biggest = c;
        }
        System.out.println("The biggest number is " + biggest);
    }
}
```

### Question 5
Java statements that determine whether the Leap year (divisible by 4 but not by 100, and also divisible by 400)
```java
import java.util.Scanner;

public class LeapYear {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in); //get input from user
        System.out.print("Enter a year: ");
        int year = keyboard.nextInt(); //assign input in a variable

        boolean isLeap = (year % 4 == 0 && year % 100 != 0) || year % 400 == 0; //determine true or false
        if (isLeap) { //true
            System.out.println(year + " is a leap year");
        } else { //false
            System.out.println(year + " is not a leap year");
        }
    }
}
```
