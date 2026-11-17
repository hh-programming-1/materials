# Example exam

For each exercise, create an exercise-specific `.java` file in the `exam` folder.

```
src/
└── main/
    └── java/
        └── exam/ 👈
            └──  Exercise1.java 👈
```

## 1. Numbers (Exercise1.java)

Write a class `Exercise1` with a `main` method that asks the user for two positive integers. After reading the numbers, check that the given numbers were positive. Then your program calculates their sum and average.

Your program must then print the sum (addition) and the average of the numbers as shown in the sample run:

```
Enter the first number:
-7
Enter a positive number:
7
Enter the second number:
13
The sum of the numbers is 20
The average of the numbers is 10
```

Hint: To ask for input, you need the Java Scanner class. Transform the input to numbers appropriately.

## 2. Divisible numbers (Exercise2.java)

### Part 1

Write a class `Exercise2` with a main method that prints the numbers from 50 down to 1. You may use any loop structure to go through the numbers.

### Part 2

Change your program so that not all numbers in the range are printed. The program should print only the even numbers. All other numbers must be left unprinted.

Excerpt from the sample program run:

```
50
48
46
44
(part of the output removed)
6
4
2
```

Hint: You can check whether a number is divisible using the remainder, which should be zero.

## 3. Celsius to Fahrenheit (Exercise3.java)

### Part 1

Write a class `Exercise3` and add to it a static private method `celsiusToFahrenheit`. The `celsiusToFahrenheit` method takes one floating-point number as a parameter: celsius. The method converts the temperature given in Celsius to Fahrenheit and returns the result as a floating-point number. The conversion formula is °F = (°C) · 1.8 + 32.

### Part 2

Add a `main` method to your class. The `main` method must call the `celsiusToFahrenheit` method. In the call, give celsius the value 23.5. Print the value returned by the method on the screen as shown in the sample run:

```
23.5 degrees Celsius is 74.3 degrees Fahrenheit.
```

Hint: Note that in this task you do not need to ask the user for anything. It is enough that your `main` method is "hard-coded" and always works the same way. What matters is that the method you write could be reused to convert any temperature, in case it were part of a larger program.

## 4. Word list (Exercise4.java)

### Part 1

Write a class `Exercise4` and add a `main` method to it. In the `main` method, your program asks the user for strings until the user enters only the - character. The strings entered by the user must be stored in a String-type list or array.

### Part 2

After the strings have been asked for, print the total number of characters in the entered strings.

### Part 3

Finally, ask the user how many of the strings they entered should be printed. After the user's choice, your program prints the requested number of strings, starting from the beginning.

### Part 4

Your program must not crash even if the user enters a number at the end that is larger than the number of strings in the list. If the number the user enters is greater than the length of the list, all strings are printed.

```
Enter the next line (- to stop): Boat
Enter the next line (- to stop): Oars
Enter the next line (- to stop): Life vest
Enter the next line (- to stop): -
The strings you entered contain 22 characters in total
How many lines should be printed: 2
Boat
Oars
```

Hints: Store the strings on a list. In this task you need at least the list's `add`, `get`, and `size` methods. You do not need to handle the case where the user enters an empty line as the very first input.

## 5. Companies (Exercise5.java)

### Part 1

Write a class `Company` that has private instance variables, i.e. fields, for business ID, name, address, and revenue. Implement the variables and the constructor so that your class works according to the example code. In addition, write get and set methods for all fields, following Java conventions.

### Part 2

Write a `toString` method for the `Company` class that builds a string matching the sample run. To test the `Company` class, create a `Exercise5` class with a `main` method.

Example code:

```java
Company company1 = new Company("12345-W","Kesko Oy", "Sipoo", 34000000.0);
Company company2 = new Company("98765-A", "Nokia Oy", "Espoo", 720000000.0);
Company company3 = new Company("55555-F", "Nordea Oy", "Helsinki", 12000000.0);
```

Output of the example code:

```
Business ID: 12345-W, Kesko Oy, Sipoo, revenue: 34000000,0 euros.
Business ID: 98765-A, Nokia Oy, Espoo, revenue: 720000000,0 euros.
Business ID: 55555-F, Nordea Oy, Helsinki, revenue: 12000000,0 euros.
```
