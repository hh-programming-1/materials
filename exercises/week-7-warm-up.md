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
Player player = new Player("Aleksander Barkov", "Florida Panthers", 30, 50);

System.out.println(player.getName());
System.out.println(player.getTeam());
System.out.println(player.getGoals());
System.out.println(player.getAssists());
System.out.println(player.getPoints());
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
- Print the information of each player in format "Name, Team: Goals + Assists = Points".

Check that the following is printed:

```
Connor McDavid, Edmonton Oilers: 45 + 70 = 115
Nathan MacKinnon, Colorado Avalanche: 40 + 62 = 102
Leon Draisaitl, Edmonton Oilers = 45 + 55 = 100
```