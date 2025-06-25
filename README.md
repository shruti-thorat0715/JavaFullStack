package corejava;
 
public class BankingApplication {
 
	public static void main(String[] args) {
	BankAccount_UserOperation myAccount=new BankAccount_UserOperation(1000);
	Thread t1=new DepositThread(myAccount, 500);
	Thread t2=new WithdrawThread(myAccount,700);
	Thread t3=new BalanceThread(myAccount);
	t1.start();
	t2.start();
	t3.start();
 
	}
 
}//BankingApplication
 
class BankAccount_UserOperation{
	private double balance;
 
	public BankAccount_UserOperation(double initbalance) {
		this.balance = initbalance;
	}
	
	public synchronized void deposit(double amount) {
		System.out.println(Thread.currentThread().getName()+" Depositing "+amount);
		this.balance +=amount;
		System.out.println("Updated balance after Deposit : "+this.balance);
	}
	
	public synchronized void withdraw(double amount) {
		if(amount>this.balance) {
			System.out.println(Thread.currentThread().getName()+" Insufficient Balance... transaction failed");
		}
		else {
			System.out.println(Thread.currentThread().getName()+" Withdrawing Amount "+amount);
			this.balance -=amount;
			System.out.println("Updated balance after Withdraw : "+this.balance);
		}
	}
	
	public synchronized void checkBalance() {
		System.out.println(Thread.currentThread().getName()+"Checking balance : "+this.balance);
	}
	
}//BankAccount
 
 
class DepositThread extends Thread{
	private BankAccount_UserOperation account;
	private double amount;
	
	public DepositThread(BankAccount_UserOperation account, double amount) {
		this.account = account;
		this.amount = amount;
	}
	
	@Override
	public void run() {
		account.deposit(amount);
	}
	
}//DepositThread
 
class WithdrawThread extends Thread{
	private BankAccount_UserOperation account;
	private double amount;
	public WithdrawThread(BankAccount_UserOperation account, double amount) {
		this.account = account;
		this.amount = amount;
	}
	
	@Override
	public void run() {
		account.withdraw(amount);
	}
	
	
}//WithdrawThread
 
 
 
class BalanceThread extends Thread{
	private BankAccount_UserOperation account;
 
	public BalanceThread(BankAccount_UserOperation account) {
		this.account = account;
	}
	
	@Override
	public void run() {
		account.checkBalance();
	}
	
}//BalanceThread
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
