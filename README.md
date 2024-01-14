# codesoft-task3
//ATM INTERFACE//

import java.util.Scanner;

class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful.New balance: " + balance);
        } else {
            System.out.println("Invalid amount for deposit.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal successful.New balance: " + balance);
        } else {
            System.out.println("Insufficient funds or invalid amount for withdrawal.");
        }
    }
}

class atm1 {
    private BankAccount account;
    private Scanner scanner;

    public atm1(BankAccount account) {
        this.account = account;
        this.scanner = new Scanner(System.in);
    }

    public void showMenu() {
        System.out.println("1. Check Balance");
        System.out.println("2. Deposit");
        System.out.println("3. Withdraw");
        System.out.println("4.Exit");
    }

    public void run() {
        int choice;
        do {
            showMenu();
            System.out.print("Enter your choice:");
            choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    CheckBalance();
                    break;
                case 2:
                    deposit();
                    break;
                case 3:
                    withdraw();
                    break;
                case 4:
                    System.out.println("Thank You For Using the ATM");
                    break;
                default:
                    System.out.println("Invalid choice. please select a valid option");

            }
        } while (choice != 4);
    }

    private void CheckBalance() {
        System.out.println("Your current blance is: " + account.getBalance());

    }

    private void deposit() {
        System.out.print("enter the amount to deposit: ");
        double amount = scanner.nextDouble();
        account.deposit(amount);
    }

    private void withdraw() {
        System.out.print("enter the amount to withdraw: ");
        double amount = scanner.nextDouble();
        account.withdraw(amount);
    }
}

public class atm {
    public static void main(String[] args) {
        System.out.println("welcome to the ATM!");
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter your four Digit PIN: ");
        int enteredPin = sc.nextInt();

        BankAccount userAccount = new BankAccount(1000.0); // initial balance
        atm1 atm = new atm1(userAccount);
        atm.run();
    }
}
