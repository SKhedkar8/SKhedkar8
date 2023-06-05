import java.util.Scanner;

public class ATMSystem {
    private static int userId = 123456; // Example user ID
    private static int userPin = 1234; // Example user PIN
    private static double balance = 1000.0; // Example initial balance
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean loggedIn = false;
        
        while (!loggedIn) {
            System.out.print("Enter user ID: ");
            int enteredId = scanner.nextInt();
            System.out.print("Enter user PIN: ");
            int enteredPin = scanner.nextInt();
            
            if (enteredId == userId && enteredPin == userPin) {
                loggedIn = true;
                System.out.println("Login successful!");
            } else {
                System.out.println("Invalid user ID or PIN. Please try again.");
            }
        }
        
        int choice;
        
        do {
            System.out.println("\nATM Menu");
            System.out.println("1. Transactions History");
            System.out.println("2. Withdraw");
            System.out.println("3. Deposit");
            System.out.println("4. Transfer");
            System.out.println("5. Quit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            
            switch (choice) {
                case 1:
                    showTransactionHistory();
                    break;
                case 2:
                    performWithdraw();
                    break;
                case 3:
                    performDeposit();
                    break;
                case 4:
                    performTransfer();
                    break;
                case 5:
                    System.out.println("Thank you for using our ATM system. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        } while (choice != 5);
        
        scanner.close();
    }
    
    private static void showTransactionHistory() {
        System.out.println("Transaction History:");
        // Add code to retrieve and display transaction history
    }
    
    /**
     * 
     */
    private static void performWithdraw() {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.print("Enter the amount to withdraw: ");
            double amount = scanner.nextDouble();
            
            if (amount > balance) {
                System.out.println("Insufficient funds. Withdrawal canceled.");
            } else {
                balance -= amount;
                System.out.println("Withdrawal successful. Current balance: " + balance);
                // Add code to record the transaction in history
            }
        }
    }
    
    private static void performDeposit() {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.print("Enter the amount to deposit: ");
            double amount = scanner.nextDouble();
            
            balance += amount;
        }
        System.out.println("Deposit successful. Current balance: " + balance);
        // Add code to record the transaction in history
    }
    private static void performTransfer() {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.print("Enter the recipient's user ID: ");
            System.out.print("Enter the amount to transfer: ");
            double amount = scanner.nextDouble();
            
            if (amount > balance) {
                System.out.println("Insufficient funds. Transfer canceled.");
            } else {
                balance -= amount;
                System.out.println("Transfer successful. Current balance: " + balance);
                // Add code to record the transaction in history
   }
        }
}

    public static int getUserId() {
        return userId;
    }

    public static void setUserId(int userId) {
        ATMSystem.userId = userId;
    }

    public static int getUserPin() {
        return userPin;
    }

    public static void setUserPin(int userPin) {
        ATMSystem.userPin = userPin;
    }

    public static double getBalance() {
        return balance;
    }

    /**
     * @param balance
     */
    public static void setBalance(double balance) {
        ATMSystem.balance = balance;
    }
}
