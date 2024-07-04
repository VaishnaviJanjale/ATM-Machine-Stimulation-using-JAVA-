# ATM-Machine-Stimulation-using-JAVA-
import java.util.ArrayList;
import java.util.Scanner;

public class ATMSimulation {

    // Initial balance of the account
    private static double balance = 1000.00;
    // Initial PIN for the account
    private static int pin = 1234;
    // List to store the transaction history
    private static ArrayList<String> transactionHistory = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the ATM Machine Simulation!");

        while (true) {
            // Display menu options
            System.out.println("\nPlease select an option:");
            System.out.println("1. Account Balance Inquiry");
            System.out.println("2. Cash Withdrawal");
            System.out.println("3. Cash Deposit");
            System.out.println("4. PIN Change");
            System.out.println("5. Transaction History");
            System.out.println("6. Exit");

            // Get user choice
            int choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    // Check account balance
                    checkBalance();
                    break;
                case 2:
                    // Withdraw cash from account
                    withdrawCash(scanner);
                    break;
                case 3:
                    // Deposit cash to account
                    depositCash(scanner);
                    break;
                case 4:
                    // Change account PIN
                    changePIN(scanner);
                    break;
                case 5:
                    // View transaction history
                    viewTransactionHistory();
                    break;
                case 6:
                    // Exit the simulation
                    System.out.println("Thank you for using the ATM Machine Simulation. Goodbye!");
                    System.exit(0);
                    break;
                default:
                    // Handle invalid choices
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    // Function to check account balance
    private static void checkBalance() {
        System.out.println("Your current balance is: $" + balance);
        transactionHistory.add("Balance Inquiry: $" + balance);
    }

    // Function to withdraw cash from account
    private static void withdrawCash(Scanner scanner) {
        System.out.print("Enter the amount to withdraw: ");
        double amount = scanner.nextDouble();
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Please take your cash: $" + amount);
            transactionHistory.add("Cash Withdrawal: $" + amount);
        } else {
            System.out.println("Insufficient balance.");
        }
    }

    // Function to deposit cash to account
    private static void depositCash(Scanner scanner) {
        System.out.print("Enter the amount to deposit: ");
        double amount = scanner.nextDouble();
        balance += amount;
        System.out.println("You have deposited: $" + amount);
        transactionHistory.add("Cash Deposit: $" + amount);
    }

    // Function to change account PIN
    private static void changePIN(Scanner scanner) {
        System.out.print("Enter your current PIN: ");
        int currentPIN = scanner.nextInt();
        if (currentPIN == pin) {
            System.out.print("Enter your new PIN: ");
            int newPIN = scanner.nextInt();
            pin = newPIN;
            System.out.println("Your PIN has been successfully changed.");
            transactionHistory.add("PIN Change");
        } else {
            System.out.println("Incorrect PIN. Please try again.");
        }
    }

    // Function to view transaction history
    private static void viewTransactionHistory() {
        if (transactionHistory.isEmpty()) {
            System.out.println("No transactions available.");
        } else {
            System.out.println("Transaction History:");
            for (String transaction : transactionHistory) {
                System.out.println(transaction);
            }
        }
    }
}
