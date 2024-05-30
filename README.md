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
