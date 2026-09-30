# Solutions: Classes & Objects Warm-up Exercises

## Player class

Create this class in `Player.java` in the `week7` package. It is used by all three exercises.

```java
package week7;

public class Player {
    private final String name;
    private final String team;
    private int goals;
    private int assists;

    public Player(String name, String team, int goals, int assists) {
        this.name = name;
        this.team = team;
        this.goals = goals;
        this.assists = assists;
    }

    public String getName() {
        return name;
    }

    public String getTeam() {
        return team;
    }

    public int getGoals() {
        return goals;
    }

    public int getAssists() {
        return assists;
    }

    public int getPoints() {
        return goals + assists;
    }

    public void addGoals(int goals) {
        this.goals += goals;
    }

    public void addAssists(int assists) {
        this.assists += assists;
    }
}
```

## Warm-up exercise 1

```java
package week7;

public class WarmUp1 {
    public static void main(String[] args) {
        Player barkov = new Player("Aleksander Barkov", "Florida Panthers", 30, 50);

        System.out.println(barkov.getName());
        System.out.println(barkov.getTeam());
        System.out.println(barkov.getGoals());
        System.out.println(barkov.getAssists());
        System.out.println(barkov.getPoints());
    }
}
```

## Warm-up exercise 2

```java
package week7;

public class WarmUp2 {
    public static void main(String[] args) {
        Player mcdavid = new Player("Connor McDavid", "Edmonton Oilers", 35, 70);
        Player mackinnon = new Player("Nathan MacKinnon", "Colorado Avalanche", 40, 60);
        Player draisaitl = new Player("Leon Draisaitl", "Edmonton Oilers", 45, 55);

        mcdavid.addGoals(10);
        mackinnon.addAssists(2);
        draisaitl.addGoals(5);

        printPlayer(mcdavid);
        printPlayer(mackinnon);
        printPlayer(draisaitl);
    }

    private static void printPlayer(Player player) {
        System.out.println(player.getName() + ", " + player.getTeam() + ": "
                + player.getGoals() + " + " + player.getAssists() + " = " + player.getPoints());
    }
}
```

## Warm-up exercise 3

```java
package week7;

import java.util.ArrayList;
import java.util.Scanner;

public class WarmUp3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        ArrayList<Player> players = new ArrayList<>();

        while (true) {
            System.out.print("Enter name: ");
            String name = input.nextLine();
            if (name.isEmpty()) {
                break;
            }

            System.out.print("Enter team: ");
            String team = input.nextLine();
            System.out.print("Enter goals: ");
            int goals = Integer.parseInt(input.nextLine());
            System.out.print("Enter assists: ");
            int assists = Integer.parseInt(input.nextLine());
            players.add(new Player(name, team, goals, assists));
        }

        for (Player player : players) {
            System.out.println(player.getName() + ", " + player.getTeam() + ": "
                    + player.getGoals() + " + " + player.getAssists() + " = " + player.getPoints());
        }
    }
}
```