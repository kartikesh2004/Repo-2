import java.util.Scanner;
import java.util.Random;

public class GuessTheNumberGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int totalRounds = 0;
        int totalWins = 0;
        int totalAttempts = 0;

        // Loop for multiple rounds of the game
        while (true) {
            System.out.println("Welcome to Guess the Number game!");
            System.out.println("I will think of a number between 1 and 100. Try to guess it!");
            int numberToGuess = random.nextInt(100) + 1;
            int attempts = 0;
            boolean hasGuessedCorrectly = false;

            // Give user a limited number of attempts to guess
            int maxAttempts = 10;
            while (attempts < maxAttempts && !hasGuessedCorrectly) {
                System.out.print("Enter your guess (1-100): ");
                int userGuess = scanner.nextInt();
                attempts++;

                // Check the user's guess
                if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else if (userGuess > numberToGuess) {
                    System.out.println("Too high! Try again.");
                } else {
                    hasGuessedCorrectly = true;
                    System.out.println("Congratulations! You guessed the correct number!");
                    totalWins++;
                    totalAttempts += attempts;
                }
            }

            if (!hasGuessedCorrectly) {
                System.out.println("Sorry, you've run out of attempts. The correct number was: " + numberToGuess);
            }

            totalRounds++;

            // Ask if the user wants to play again
            System.out.print("Do you want to play another round? (yes/no): ");
            String playAgain = scanner.next();

            if (playAgain.equalsIgnoreCase("no")) {
                break;
            }
        }

        // Display score after all rounds
        System.out.println("\nGame Over!");
        System.out.println("Total rounds played: " + totalRounds);
        System.out.println("Total rounds won: " + totalWins);
        System.out.println("Total attempts used: " + totalAttempts);
        double averageAttempts = totalRounds > 0 ? (double) totalAttempts / totalRounds : 0;
        System.out.println("Average attempts per round: " + averageAttempts);
        scanner.close();
    }
}
