# GuessingGame_INTERNPE_Task1
This game will allow you to guess a number between 1 and 100. The system will take a number randomly and you have to guess the number with limited attempts time. Based on your attempt time, you will see your score.

import java.util.*;

class g {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        do {
            playGame(in);

            System.out.print("          Do you want to try again? (yes/no): ");
            String playAgain = in.next().toLowerCase();

            if (!playAgain.equals("yes")) {
                break;
            }
        } while (true);

        System.out.println("        ....Thanks for playing!....");
        in.close();
    }
    private static void playGame(Scanner scanner) {
        int lb = 1;
        int ub = 100;
        int rand = generateRandomNumber(lb, ub);
        int maxattempt = 6;
        int attempt = 0;
        int score = 0;

        System.out.println("..............Welcome to the Guessing Game!...............");
        System.out.println("      I have selected a number between " + lb + " and " + ub);
        System.out.println("        Now just try to guess the number .." );
        while (true) {
            if (attempt<maxattempt) {
                System.out.print("         Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempt++;
                score = ((rand * 100) - (attempt * 10));

                if (userGuess < rand) {
                    System.out.println("       low! Try again.");
                } else if (userGuess > rand) {
                    System.out.println("       high! Try again.");
                } else {
                    System.out.println("        Congratulations! You guessed the number in " + attempt + " attempts.");
                    System.out.println("        your score:" + score);
                    break;
                }
            }
            else {
                System.out.println("            Sorry!! you missed it, better luck next time...");
                break;
            }
        }
    }
    private static int generateRandomNumber(int lb, int ub) {
        return (int) (Math.random() * (ub - lb + 1)) + lb;
    }
}
