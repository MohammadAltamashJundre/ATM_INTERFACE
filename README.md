# ATM_INTERFACE
ATM_INTERFACE
import java.util.Scanner;
class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        balance = initialBalance;
    }

    public void deposit(double amount) {
        balance += amount;
    }

    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
        } else {
            System.out.println("Insufficient balance!");
        }
    }

    public void checkBalance() {
        System.out.println("Your current balance is: " + balance);
    }
}

class ATM {
    private BankAccount bankAccount;

    public ATM(double initialBalance) {
        bankAccount = new BankAccount(initialBalance);
    }

    public void displayMenu() {
        System.out.println("Welcome to the ATM!");
        System.out.println("1. Withdraw");
        System.out.println("2. Deposit");
        System.out.println("3. Check Balance");
        System.out.println("4. Quit");
    }

    public void run() {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            displayMenu();
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            if (choice == 1) {
                System.out.print("Enter the amount to withdraw: ");
                double amount = scanner.nextDouble();
                bankAccount.withdraw(amount);
            } else if (choice == 2) {
                System.out.print("Enter the amount to deposit: ");
                double amount = scanner.nextDouble();
                bankAccount.deposit(amount);
            } else if (choice == 3) {
                bankAccount.checkBalance();
            } else if (choice == 4) {
                System.out.println("Thank you for using the ATM!");
                break;
            } else {
                System.out.println("Invalid choice! Please try again.");
            }
        }

        scanner.close();
    }
}

public class Main {
    public static void main(String[] args) {
        ATM atm = new ATM(0.0);
        atm.run();
    }
}
