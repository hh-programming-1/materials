# Loops

## The purpose of loops

- Previously we familiarized ourselves how the conditional statements control the flow of the program by determining whether to execute some code block or not
- Another way to control the programs flow is to **repeat** the execution of some code block until certain condition is met. Such control structres are called **loops**
- For example, we might want to read user input until they provide certain input
- The most commonly used loop statements in basically every programming language is the `while` and `for` loops

## While loop

- A `while` loop consists of an expression that determines whether or not the code within the loop should be repeated, along with a block containing the source code to be repeated
- We must make sure that **the condition will be true at some point**, otherwise we will end up in an infinite loop, causing the program to crash
- Commonly, this is achieved by altering some variable the condition is tight to within the loop. For example, by increasing a number within the loop after each iteration

```java
int number = 1;

// This code block is executed until number variable's value is greater or equal to 5
while (number < 5) {
    System.out.println(number);
    // In each loop iteration, we increase the number variable's value to avoid an infinite loop
    number = number + 1;
}

// Once the while loop condition is false, the execution of the program continues
System.out.println("Ready!");
```

```
1
2
3
4
Ready!
```

## Breaking out of the loop

- When the `while` loop condition becomes false, the loop ends. It is also possible to end the loop with the `break` statement
- When the `break` statement is executed, e.g. in a `if` statement block, the loop ends

```java
Scanner input = new Scanner(System.in);

while (true) {
    System.out.println("Exit? (y exits): ");
    String answer = input.nextLine();

    if (answer.equals("y")) {
        break;
    }

    System.out.println("Ok! Let's carry on!");
}

System.out.println("Ready!");
```

```
Exit? (y exits): no
Ok! Let's carry on!
Exit? (y exits): still no
Ok! Let's carry on!
Exit? (y exits): y
Ready!
```

## 💡 While loop example: total exercise points

> Write a program which asks for exericse points until a empty string is entered. When the empty string is entered, the program should print the total sum of the exercise points.

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    int total = 0;

    while (true) {
        System.out.print("Enter exercise points: ");
        String points = input.nextLine();

        if (points.equals("")) {
            break;
        }

        total += Integer.parseInt(points);
    }

    System.out.println("Total exercise points: " + total);
}
```

```
Enter exercise points: 3
Enter exercise points: 4
Enter exercise points: 5
Enter exercise points:
Total exercise points: 12
```

## Returning to the start of the loop

- When the execution reaches the end of the loop, the execution starts again from the start of the loop
- We can also return to the beginning from other places besides the end with the `continue` statement
- When the `continue` statement is executed, the execution of the program moves to the beginning of the loop

```java
Scanner scanner = new Scanner(System.in);

while (true) {
    System.out.print("Enter a positive integer: ");
    int number = Integer.parseInt(scanner.nextLine());

    if (number < 0) {
        System.out.println("Unfit number! Try again");
        continue;
    }

    System.out.println("Your input was " + number);
}
```

```
Enter a positive integer: 1
Your input was 1
Enter a positive integer: -2
Unfit number! Try again
Enter a positive integer: 4
Your input was 4
```

## 💡 While loop example: counting positive numbers

> Write a program which asks for a number until a empty string is entered. The program should count every positive number entered. When the empty string is entered, the program should print the number of entered positive numbers.

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    int count = 0;

    while (true) {
        System.out.print("Enter a number: ");
        String value = input.nextLine();

        if (value.equals("")) {
            break;
        }

        int number = Integer.parseInt(value);

        if (number < 0) {
            continue;
        }

        count++;
    }

    System.out.println("Number of positive numbers: " + count);
}
```

```
Enter a number: 5
Enter a number: 2
Enter a number: -1
Enter a number:
Number of positive numbers: 2
```

## For loop

- The `while` loop is useful when **we don't know in advance how many times we need to repeat a code block**.
- For example, in the previous example, we asked for user input until an empty string was provided, without knowing how many inputs the user would enter
- The `for` loop, on the other hand, is more convenient when **we know in advance how many times the code block should be repeated**

## Anatomy of the for loop

$$
\texttt{for (}\
\underbrace{\texttt{int i = 0}}_{\text{initialization}}
\texttt{ }\;
\underbrace{\texttt{i < 5}}_{\text{condition}}
\texttt{ }\;
\underbrace{\texttt{i++}}_{\text{update}}
\texttt{)}
$$

- A `for` loop declaration contains four parts: 
 1. Initialization of the variable for counting the number of executions
 2. The condition of the loop
 3. Increasing (or decreasing or changing) the value of the counter variable
 4. The code block to be executed

```java
//       1.       2.    3.
for (int i = 0; i < 5; i++) {
    // 4.
    System.out.println(i);
}
```

```
0
1
2
3
4
```

## Changing a variable value

- In Java (like in most programming languages), there are shorter versions for increasing, decreasing or multiplying a variable's value by certain amount

```java
int i = 1;

// Two ways to increase i by one
i = i + 1;
i++;
// Two ways to decrease i by one
i = i - 1;
i--;
// Two ways to increase i by 10
i = i + 10;
i += 10;
// Two ways to decrease i by 10
i = i - 10;
i -= 10;
// Two ways to multiply i by 10
i = i * 10;
i *= 10;
```

## 💡 For loop example: printing even numbers

> Write a program which asks a number. Then, the program prints all even numbers until that number.

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("Enter a number: ");
    int number = Integer.parseInt(input.nextLine());

    for (int i = 0; i <= number; i += 2) {
        System.out.println(i);
    }
}
```

## 💡 Nested for loop example: printing a rectangle

> Write a program which asks user for rectangle width and height. Then, the program prints a rectangle of these dimensions filled with a "+" symbol.

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("Enter rectangle width: ");
    int width = Integer.parseInt(input.nextLine());
    System.out.print("Enter rectangle height: ");
    int height = Integer.parseInt(input.nextLine());

    for (int row = 0; row < height; row++) {
        for (int column = 0; column < width; column++) {
            System.out.print("+");
        }
        System.out.println("");
    }
}
```

````
Enter rectangle width: 4
Enter rectangle height: 3
++++
++++
++++