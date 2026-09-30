# Classes & Objects Warm-up Exercises

For this week's exercises, create a new `week7` package (folder) under the `src/main/java` folder. For each exercise, create an exercise-specific `.java` file in the `week7` folder.

```
src/
└── main/
    └── java/
        ├── ...
        └── week7/ 👈
            └── WarmUp1.java 👈
```

## Warm-up 1

Create a `Player.java` file in the `week7` folder. In that file, implement a `Player` class with the attributes `name`, `team`, `goals` and `assists`. The `goals` and `assists` attributes are integers other attributes are strings. The class should have a constructor and methods `getName`, `getTeam`, `getGoals`, `getAssists` and `getPoints`. The `getPoints` should return the sum of player's goals and assists. The ohter methods should simply return the corresponding attribute's value.

Finally, create a `WarmUp1.java` file in the `week7` folder. Implement a `main` method with the following content:

```java
// name, team, goals, assists
Player barkov = new Player("Aleksander Barkov", "Florida Panthers", 30, 50);

System.out.println(barkov.getName());
System.out.println(barkov.getTeam());
System.out.println(barkov.getGoals());
System.out.println(barkov.getAssists());
System.out.println(barkov.getPoints());
```

Check that the following is printed:

```text
Aleksander Barkov
Florida Panthers
30
50
80
```

## Warm-up 2

Implement the `addGoals(int goals)` and `addAssists(int assists)` methods to the `Player` class for increasing goals and assists by the given amount.

Then, create an application, which initializes the following three `Player` objects:

| Name             | Team               | Goals | Assists |
| ---------------- | ------------------ | ----- | ------- |
| Connor McDavid   | Edmonton Oilers    | 35    | 70      |
| Nathan MacKinnon | Colorado Avalanche | 40    | 60      |
| Leon Draisaitl   | Edmonton Oilers    | 45    | 55      |

After initializing the objects do the following:

- Increase the number of goals for McDavid by 10.
- Increase the number of assists by MacKinnon by 2.
- Increase the number of goals by Draisaitl by 5.
- Print the information of each player in format "Name, Team: Goals + Assists = Points".

Check that the following is printed:

```
Connor McDavid, Edmonton Oilers: 45 + 70 = 115
Nathan MacKinnon, Colorado Avalanche: 40 + 62 = 102
Leon Draisaitl, Edmonton Oilers = 50 + 55 = 105
```

## Warm-up exercise 3

Create an application, which asks the user to enter player's information (name, team, goals, assists) until the user enters an empty name. The players should be added to an `ArrayList`. After the user enters an empty name, the application should print all the players on the list in format "Name, Team: Goals + Assists = Points".

Example:

```
Enter name: Connor McDavid
Enter team: Edmonton Oilers
Enter goals: 35
Enter assists: 70
Enter name: Nathan MacKinnon
Enter team: Colorado Avalanche
Enter goals: 40
Enter assists: 60
Enter name:
Connor McDavid, Edmonton Oilers: 35 + 70 = 105
Nathan MacKinnon, Colorado Avalanche: 40 + 60 = 100
```

> [!TIP]
> Read the user input in a `while` loop until the input is an empty string:
> 
> ```java
> while (true) {
>   System.out.print("Enter value: ");
>   String value = input.nextLine();
>   if (/* Condition to stop reading the input */) {
>     // End the while loop 
>     break;
>   }
>
>   // Do something with the input
> }
>
> System.out.println("Done!");
> ```

> [!IMPORTANT]
> Once you have completed these warm-up exercises, check the model solutions in Moodle's "Schedule" page.
