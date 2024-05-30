Project : 
Banking System: 
Muhammad aamir:  54676 
Syed  Agha Shah Hussain:  53465 
Abdullah Ahmed: 53639 
Report 
Code Report: Banking Application 
 
Overview: 
The provided Java code implements a simple banking application where users can interact with a bank account. The application supports operations such as depositing money, withdrawing money, and checking the account balance. 
 
Components: 
The program consists of the following components: 
 
1.	Bank account Abstract Class 
2.	Savingsaccount Class 
3.	Project Class (Main Class) 
 
Detailed Analysis: 
 
1.	Bankaccount Abstract Class    - Attributes: 
-	accountnumber (String): The account number for the bank account. 
-	balance (double): The balance in the bank account. 
-	Constructor: 
-	Initializes the account number and sets the balance to 0.0. 
-	Methods: 
-	getaccountnumber(): Returns the account number. 
-	getbalance(): Returns the current balance. 
-	setbalance(double balance): Sets the balance (protected method). 
-	deposit(double amount): Abstract method for depositing money. 
-	withdraw(double amount): Abstract method for withdrawing money. 
 
2.	Savingsaccount Class 
-	Extends the Bankaccount class. 
-	Constructor: 
-	Calls the superclass constructor to initialize the account number. 
-	Methods: 
-	deposit(double amount): Adds the specified amount to the balance if the amount is positive; otherwise, prints an error message. 
-	withdraw(double amount): Deducts the specified amount from the balance if the amount is positive and less than or equal to the balance; otherwise, prints an error message. 
 
3.	Project Class (Main Class)    - Main Method: 
-	Uses Scanner to read user input. 
-	Prompts the user to enter the account number. 
-	Creates a Savingsaccount object. 
-	Provides a menu with options to deposit money, withdraw money, check the balance, and exit the program. 
-	Uses a loop to repeatedly display the menu until the user chooses to exit. 
-	Handles user choices with a switch statement: 
-	Deposit: Prompts for an amount and calls the deposit method. 
-	Withdraw: Prompts for an amount and calls the withdraw method.        - Check Balance: Displays the account number and current balance. 
-	Exit: Closes the scanner and exits the program. 
-	Invalid Option: Prints an error message for invalid menu choices. 
 
Code Execution Flow: 
1.	The program starts and prompts the user to enter an account number. 
2.	A Savings account object is created with the entered account number. 
3.	The menu is displayed, and the user selects an option: 
-	Deposit: User enters the amount to deposit, and the balance is updated. 
-	Withdraw: User enters the amount to withdraw, and the balance is updated if the conditions are met. 
-	Check Balance: Displays the account number and current balance. 
-	Exit: Terminates the program. 
4.	The loop continues to display the menu until the user chooses to exit. 
 
Error Handling: 
-	The deposit method checks if the deposit amount is positive. 
-	The withdraw method checks if the withdrawal amount is positive and does not exceed the current balance. 
-	The menu handles invalid options by displaying an error message. 
 
Potential Improvements 
-	Input Validation: Add input validation to handle non-numeric input gracefully. 
-	Enhanced User Feedback: Provide more detailed feedback messages, such as current balance after deposit/withdrawal operations. 
-	Extend Functionality: Implement additional account types and operations, such as transfer between accounts. 
-	Persistence: Add functionality to save account data to a file or database for persistence. 
 
Conclusion: 
The provided code is a basic but functional implementation of a banking application. It demonstrates the use of abstract classes, inheritance, and basic input/output handling in Java. With some enhancements and additional features, it could serve as the foundation for a more robust banking system. 


Code: 
 
package project; import java.util.Scanner; abstract class Bankaccount {     private String accountnumber;     private double balance;     public Bankaccount(String accountnumber) {         this.accountnumber = accountnumber; 
        this.balance = 0.0; 
    } 
    public String getaccountnumber() {         return accountnumber; 
    } 
    public double getbalance() {         return balance; 
    } 
    protected void setbalance(double balance) { 
        this.balance = balance; 
    } 
    public abstract void deposit(double amount);     public abstract void withdraw(double amount); 
} 
class Savingsaccount extends Bankaccount {     public Savingsaccount(String accountnumber) {         super(accountnumber); 
    } 
    @Override 
    public void deposit(double amount) { 
        if (amount > 0) {             setbalance(getbalance() + amount); 
            System.out.println("Deposited: $" + amount); 
        } else { 
            System.out.println("Invalid deposit amount"); 
        } 
    } 
    @Override     public void withdraw(double amount) {         if (amount > 0 && amount <= getbalance()) {             setbalance(getbalance() - amount); 
            System.out.println("Withdrew: $" + amount); 
        } else { 
            System.out.println("Invalid withdrawal amount"); 
        } 
    } 
} 
public class Project  
{ 
    public static void main(String[] args)  
    { 
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter account number: "); 
        String accountnumber = scanner.nextLine(); 
        Bankaccount account = new Savingsaccount(accountnumber); 
        while (true) { 
            System.out.println("\nMenu:"); 
            System.out.println("1. Deposit"); 
            System.out.println("2. Withdraw"); 
            System.out.println("3. Check Balance"); 
            System.out.println("4. Exit"); 
            System.out.print("Choose an option: ");             int choice = scanner.nextInt();             switch (choice) {                 case 1: 
                    System.out.print("Enter amount to deposit: ");                     double depositamount = scanner.nextDouble();                     account.deposit(depositamount); 
                    break;                 case 2: 
                    System.out.print("Enter amount to withdraw: ");                     double withdrawamount = scanner.nextDouble();                     account.withdraw(withdrawamount); 
                    break;                 case 3: 
                    System.out.println("Account Number: " + account.getaccountnumber());                     System.out.println("Balance: $" + account.getbalance()); 
                    break;                 case 4: 
                    System.out.println("Exiting...");                     scanner.close();                     System.exit(0);                 default: 
                    System.out.println("Invalid option. Please try again."); 
            } 
        } 
    }} 

