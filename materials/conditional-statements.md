# Conditional statements

## Control statements

- By default the statements on a program are executed one statement at a time from the first line to the last line of the program
- **Control statements** are programming statements that control the order in which statements are executed in a program
- The most common categorization of control statements includes **conditional statements** (make decisions whether to execute certain statements), **loops** (repeating statements) and **jump statements** (changing the execution flow by e.g. returning from a method call)

## If statement

- The most common conditional statement is the `if` statement
- An `if` statement specifies a **condition**. If the condition is true, a code block within the  `{}` brackets is executed
- The condition **must evaluate to either true or false** and is commonly constructed using comparison (e.g. `==` and `<`) and logical operators (e.g. `&&` and `||`)

```java
int grade = 3;

// If grade variable's value equals 5, the if block is executed. Otherwise we skip to the next statement
if (grade == 5) {
  System.out.println("That is the best possible grade!");
}

System.out.println("Goodbye!");
```

```
Goodbye!
```

## Else clause

- An `if` statement can optionally be followed by an `else` clause, which specifies a code block to execute when the `if` statement's condition is false

```java
int grade = 3;

if (grade == 5) {
  System.out.println("That is the best possible grade!");
} else {
  // This else block is executed when the if statement's condition is false
  System.out.print("That is not the best possible grade");
}

System.out.println("Goodbye!");
```

```
That is not the best possible grade
Goodbye!
```

## Else if clause

- If the condition in an `if` statement is false, we can use an `else if` clause to check additional conditions
- The conditions are checked top down. When execution reaches a `else if` clause whose condition is true, its code block is executed and the checking stops

```java
int grade = 3

if (grade == 0) {
  System.out.println("That is a failing grade");
  // If the condition is false, the next else if condition will be checked
} else if (grade < 3) {
  System.out.println("That grade is not so great");
} else if (grade < 5) {
  // When condition is true, the code block is executed and the checking stops
  System.out.println("That is a pretty good grade");
} else {
  System.out.println("That is an awesome grade!");
}

System.out.println("Goodbye!");
```

```
That is a pretty good grade
Goodbye!
```

## Comparison operators

- The **comparison operators** are used to compare two values, e.g. checking if variable's value equals some other value

| Operator | Description              | Example   |
| -------- | ------------------------ | --------- |
| `==`     | Equal to                 | `x == 10` |
| `!=`     | Not equal to             | `x != 10` |
| `>`      | Greater than             | `x > 10`  |
| `<`      | Less than                | `x < 10`  |
| `>=`     | Greater than or equal to | `x >= 10` |
| `<=`     | Less than or equal to    | `x <= 10` |

## Comparing strings

- Even though we can compare integer, double and boolean values using two equals signs (`variable1 == variable2`), **we cannot compare the equality of strings using two equals signs**
- This is because strings are in fact **objects** and with objects, `==` compares whether two variables refer to the same object, not whether they contain the same text
- This is why strings are compared using the `equals` method. The method returns true if the target string equals the parameter and false if it doesn't

```java
String weekday = "Monday";

// We check if the weekday variable's text matches "Monday"
// Instead of "Monday", the equals method could also contain another string variable, e.g. weekday.equals(hatedWeekday)
if (weekday.equals("Monday")) {
    System.out.println("I hate Mondays!");
} else {
    System.out.println("What a nice weekday!");
}
```

```text
I hate Mondays!
```

## 💡 Comparing strings example: password confirmation 

> Write a program that asks for password and password confirmation. If the password matches the confirmation, the program prints "The password is valid". Otherwise it prints "Error, the password does not match the confirmation!".

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("Enter password: ");
    String password = input.nextLine();

    System.out.print("Confirm password: ");
    String confirmation = input.nextLine();

    if (password.equals(confirmation)) {
        System.out.println("The password is valid");
    } else {
        System.out.println("Error, the password does not match the confirmation!");
    }
}
```

```text
Enter password: secret123
Enter confirmation: secret123
The password is valid
```

## Logical operators

- The **logical operators** are used to combine conditions, e.g. "grade is greater than zero AND grade is less than 3"

| Operator | Description                                    | Example                  |
| -------- | ---------------------------------------------- | ------------------------ |
| `&&`     | And, both conditions must be true              | `age >= 18 && age <= 65` |
| `\|\|`   | Or, one of the conditions must be true         | `day == 6 \|\| day == 7` |
| `!`      | Not, true becomes false and false becomes true | `!isReady`               |

> [!TIP]
> The `||` or operator can be written with the <kbd>alt gr</kbd> + <kbd>< ></kbd> key combination.

```java
// Grade equals 4 OR 5
if (grade == 4 || grade == 5)
// Grade is greater than 2 AND less than 5
if (grade > 2 && grade < 5)
// Weekday equals "Saturday" OR "Sunday"
if (weekday.equals("Saturday") || weekday.equals("Sunday"))
// Weekday does NOT equal "Monday"
if (!weekday.equals("Monday"))
```

## The boolean data type

- The value that goes between the parentheses of the conditional statement should be of type `boolean` after the evaluation. boolean type variables are either true or false
- Comparison operators can also be used outside of conditionals. In those cases, the boolean value resulting from the comparison is stored in a boolean variable for later use

```java
int grade = 5;
// Boolean variables are either true or false
boolean javaIsFun = true;
// Comparisons can be stored to boolean variables
boolean isFailingGrade = grade == 0; // Grade equals 5, so isFailingGrade will be false
boolean isPassingGrade = grade > 0; // Grade equals 5, so isPassingGrade will be true
// Boolean variables can be used in conditions
if (isPassingGrade) {
    System.out.println("Congratulations, you have passed the course!");
}
```

```
Congratulations, you have passed the course!
```

## 💡 Conditional statement example: temperature description

> Write a program that asks for the temperature. If temparature is less than -90°C or greater than 60°C, the program prints "Invalid temperature". If temperature is less than 0°C, the program prints "It is freezing", if it is less than 20°C it prints "It is cool" and otherwise it prints "It is warm".

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter the temperature: ");
    int temperature = Integer.parseInt(input.nextLine());

    if (temperature < -90 || temperature > 60) {
        System.out.println("Invalid temperature");
    } else if (temperature < 0) {
        System.out.println("It is freezing");
    } else if (temperature < 20) {
        System.out.println("It is cool");
    } else {
        System.out.println("It is warm");
    }
}
```

```text
Enter the temperature: 5
It is cool
```

## 💡 Conditional statement example: comission calculation

> Write a program that asks for the selling price of an apartment and calculates the real estate agent's commission for the sale. The commission is 3.44% of the selling price, but at least €2,214."

```java
public static void main(String[] args) {
    double commissionRate = 0.0344; // 3.44%
    double minimumCommission = 2214.00;

    Scanner input = new Scanner(System.in);
    DecimalFormat twoDecimals = new DecimalFormat("0.00");

    System.out.print("Enter selling price: ");
    double sellingPrice = Double.parseDouble(input.nextLine());

    double commission = sellingPrice * commissionRate;

    if (commission < minimumCommission) {
        commission = minimumCommission;
    }

    System.out.println("The sales commission is " + twoDecimals.format(commission));
}
```

```text
Enter selling price: 100000
The sales comission is 3440.00
```

## Switch statement

- A `switch` statement allows a program to choose between multiple blocks of code based on the value of a variable or expression
- The value is compared against several possible cases, and the block of code that matches the value is executed. A default case can optionally be used to handle values that do not match any of the cases

```java
int day = 5;

// Switch specifies the value we want to check, the day variable in this case
switch (day) {
    // Case specifies a value to match against the switch expression
    case 1:
        // This case is selected when the value of the switch expression matches 1
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
    // It is possible to specify multiple values in the same case
    case 6, 7:
        System.out.println("Weekend");
        break;
    // Default case is selected when no other case matches the switch expression
    default:
        System.out.println("Invalid day");
}
```

```text
Friday
```

## 💡 Switch statement example: grade description

> Write a program which asks for a grade (0-5) and prints its description ("Weak" for 0, "Satisfactory" for 2, "Good" for 4 or 3, and "Excellent" for 5). If the grade is not within 0-5 range, the program should print "Invalid grade".

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("Enter a grade (0-5): ");
    int grade = Integer.parseInt(input.nextLine());

    switch (grade) {
        case 5:
            System.out.println("Excellent");
            break;
        case 4, 3:
            System.out.println("Good");
            break;
        case 2:
            System.out.println("Satisfactory");
            break;
        case 1:
            System.out.println("Weak");
            break;
        default:
            System.out.println("Invalid grade");
            break;
    }
}
```

```text
Enter grade (0-5): 4
Good
```

## The ternary operator

$$
\underbrace{\texttt{String description =}}_{\text{variable declaration and assignment}}
\underbrace{\texttt{age >= 18}}_{\text{condition}}
\ \texttt{?}\
\underbrace{\texttt{"Adult"}}_{\text{value if true}}
\ \texttt{:}\
\underbrace{\texttt{"Minor"}}_{\text{value if false}}
\texttt{;}
$$

- The `?` **ternary operator** can be used to assign a value based on a condition
- The condition is written before the `?` symbol. The value before the `:` is returned if the condition is true, while the value after the : is returned if the condition is false
- It is commonly used to replace simple `if` statements

```java
int age = 20;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

```java
int age = 20;
// If age >= 18, description variable's value will be "Adult", otherwise "Minor"
String description = age >= 18 ? "Adult" : "Minor";

System.out.println(description);
```

```text
Adult
```
