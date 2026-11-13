# Tutorial 06 — Answers

### Question 1
Write statements for each of the following

(a) Define a static method that returns the maximum number from 3 integer parameters.
```java
// 1a. Postcondition: returns the largest of a, b and c.
static int max3(int a, int b, int c) {
    int max = a;
    if (b > max) {
        max = b;
    }
    if (c > max) {
        max = c;
    }
    return max;
}

// a call from main:
int largest = max3(4, 9, 7);   // 9
```

(b)Define a static method that determines whether the given integer is a square number.
```java
// 1b. Postcondition: returns true if n is a square number (0, 1, 4, 9, 16, ...).
static boolean isSquare(int n) {
    if (n < 0) {
        return false;                        // no negative number is a square
    }
    long root = Math.round(Math.sqrt(n));    // nearest whole number to the square root
    return root * root == n;                 // long: root * root cannot overflow
}

// a call from main:
if (isSquare(49)) {
    System.out.println("49 is a square number");
}
```

(c)Define a static method used to compute the combination function C(n, k). C(n, k) gives the number of different k-element subsets that can be found in a given set of n elements: C(n, k) = n! / (k! (n − k)!).
```java
// 1c. Precondition: 0 <= k <= n <= 20 (20! is the largest factorial that fits in a long).
//     Postcondition: returns C(n, k) = n! / (k! (n - k)!).
static long combination(int n, int k) {
    return factorial(n) / (factorial(k) * factorial(n - k));
}

// Precondition: 0 <= n <= 20. Postcondition: returns n! (0! is 1).
static long factorial(int n) {
    long result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}

// a call from main:
System.out.println(combination(5, 2));   // 10
```

(d)Define a static method used to determine whether the parameter is a pentagonal number. A pentagonal number is a figurate number that extends the concept of triangular and square numbers to the pentagon: Pn = ½ n(3n − 1).
```java
// 1d. Postcondition: returns true if x is a pentagonal number 1, 5, 12, 22, 35, ...
static boolean isPentagonal(int x) {
    if (x < 1) {
        return false;                        // the sequence starts at P1 = 1
    }
    long p = 0;
    for (long n = 1; p < x; n++) {
        p = n * (3 * n - 1) / 2;             // Pn = n(3n - 1) / 2, always a whole number
    }
    return p == x;                           // stopped exactly on x, or jumped past it
}

// a call from main:
System.out.println(isPentagonal(35));   // true
```

(e)Define a static method that displays the number of letters and the number of digits of a String parameter.
```java
// 1e. Precondition: text is not null.
//     Postcondition: prints how many letters and how many digits text contains.
static void countLettersDigits(String text) {
    int letters = 0, digits = 0;
    for (int i = 0; i < text.length(); i++) {
        char ch = text.charAt(i);
        if (Character.isLetter(ch)) {
            letters++;
        } else if (Character.isDigit(ch)) {
            digits++;
        }                                    // spaces and punctuation are neither
    }
    System.out.println("Letters: " + letters + ", digits: " + digits);
}

// a call from main:
countLettersDigits("WIX1002 Java 27!");   // Letters: 7, digits: 6
```

(f)Define a static void method that generates 10 random numbers within 0 to 100 to the method’s parameter. The random numbers can be accessed by the main method.
```java
// 1f. Precondition: values is not null (main passes an array of 10 elements).
//     Postcondition: every element of the caller's array is a random number from 0 to 100.
static void fillRandom(int[] values) {
    for (int i = 0; i < values.length; i++) {
        values[i] = RANDOM.nextInt(101);     // 0 to 100 inclusive
    }
}

// in main:
int[] numbers = new int[10];
fillRandom(numbers);          // numbers now holds 10 random values
System.out.println(numbers[0]);
```

(g)Define a static void method that returns the area and the circumference of a circle given the argument is radius. Area = πr² and Circumference = 2πr.
```java
// 1g. Precondition: radius >= 0 and result has at least 2 elements.
//     Postcondition: result[0] is the area and result[1] is the circumference.
static void circle(double radius, double[] result) {
    result[0] = Math.PI * radius * radius;   // area = pi r^2
    result[1] = 2 * Math.PI * radius;        // circumference = 2 pi r
}

// in main:
double[] circleResult = new double[2];
circle(2.5, circleResult);
System.out.printf("area %.2f, circumference %.2f%n",
        circleResult[0], circleResult[1]);   // area 19.63, circumference 15.71
```

(h)Define a static method that generates random numbers within 0 – 10. The method will return the first random number that is generated twice.
```java
// 1h. Postcondition: returns the first number from 0 to 10 that is generated twice.
static int firstRepeat() {
    boolean[] seen = new boolean[11];        // seen[v] becomes true once v is drawn
    while (true) {
        int value = RANDOM.nextInt(11);      // 0 to 10
        if (seen[value]) {
            return value;                    // drawn before: the first repeat
        }
        seen[value] = true;
    }
}

// a call from main:
System.out.println("First repeat: " + firstRepeat());
```

### Question 2
```java
import java.util.Scanner;

public class DecreasingOrder {
    // Postcondition: prints a, b and c from largest to smallest, separated by spaces.
    // a, b and c are copies, so swapping them does not change the caller's variables.
    static void printDecreasing(int a, int b, int c) {
        int hold;
        if (a < b) { hold = a; a = b; b = hold; }   // now a >= b
        if (a < c) { hold = a; a = c; c = hold; }   // now a is the largest
        if (b < c) { hold = b; b = c; c = hold; }   // now b >= c
        System.out.println(a + " " + b + " " + c);
    }

    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        System.out.print("Enter three integers: ");
        int x = keyboard.nextInt();
        int y = keyboard.nextInt();
        int z = keyboard.nextInt();

        System.out.print("Decreasing order: ");
        printDecreasing(x, y, z);
    }
}
```
