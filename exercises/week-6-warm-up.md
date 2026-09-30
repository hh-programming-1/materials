# Methods Warm-up Exercises

For this week's exercises, create a new `week6` package (folder) under the `src/main/java` folder. For each exercise, create an exercise-specific `.java` file in the `week6` folder.

```
src/
└── main/
    └── java/
        ├── ...
        └── week6/ 👈
            └── WarmUp1.java 👈
```

> [!IMPORTANT]
> **Warm-up exercises are not submitted or evaluated in Viope**. The purpose of these exercises is to practice the topics with the help of the model solutions.

## Warm-up exercise 1

Create an application that asks the user for a word and determines whether the entered word is a palindrome. Implement the palindrome check in a separate method called `isPalindrome(String word)`.

Examples:

```text
Enter word: java
The word is not a palindrome
```

```text
Enter word: madam
The word is a palindrome
```

## Warm-up exercise 2

In order to ski, the skier needs poles and skis of appropriate length, which are based on the skier's height. Create the following application for this use-case:

- Create a `main` method and ask for the skier's height in centimeters.
- Create the methods `calculatePoleLength(int skierHeight)` and `calculateSkiLength(int poleLength)`.
- Use these methods to print the suitable equipment lengths.

Calculation rules: 

- The pole length is 85% of the skier's height. Poles are sold only in five-centimeter increments, so the calculated length must be rounded to the nearest five centimeters. Implement the rounding in a separate method called `roundToNearestFive(double value)`.
- The ski length is the pole length plus 40cm.

Example:

```
Enter skier's height: 183
Pole length: 155cm
Ski length: 195cm
```

⭐ Optional extension: Create a new class called `Rounding` and move the five-centimeter rounding method into this class. Modify the original code to use the new class.

> [!IMPORTANT]
> Once you have completed these warm-up exercises, check the model solutions in Moodle's "Schedule" page.