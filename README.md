# ATM-SIMULATION-MACHINE
//ATM Machine Simulation code by DEV GOSWAMI.

import java.util.*;

public class Atmmachine { <br>
    public static void main(String []args) { <br>
        // plugin the card into atm.<br>
    ATM cardscanned = new ATM();

    // when card succesfully scanned by atm then it asks for pin.

    cardscanned.checkpin();
    
}
}   
    class ATM{

        //Initializing the balance and pin.
    
    double balance = 0.00;
    int pin = 0000;
    int withdraw;
    int deposit;
    int balanceinquiry;
    int transaction = 0;
    String tranhist= "";
    
       //verifying the pin entered by card holder.

    public void checkpin(){
        System.out.println("Enter your pin");
        Scanner sc = new Scanner(System.in);
        int enteredpin = sc.nextInt();
        if(enteredpin == pin){

            //if pin successfully matched go for further transactions.

            menu();
        }
        else{
            System.out.println("Please Enter correct pin!");

            //if ur pin do not match try again...

            checkpin();
        }
    }
   
   //Calling the menu of ATM.

  public void menu(){ <br>
        System.out.println("1.Account balance inquiry"); <br>
        System.out.println("2.DEPOSIT MONEY"); <br>
        System.out.println("3.WITHDRAW MONEY"); <br>
        System.out.println("4.CHANGE PIN"); <br>
        System.out.println("5.TRANSACTION HISTORY"); <br>
        System.out.println("6.EXIT"); <br>
        System.out.println("Please Enter your choice:"); <br>

        Scanner sc = new Scanner(System.in);
        int choice = sc.nextInt(); 
        switch (choice) {
            case 1: balanceinquiry();
                    System.out.println("");  
                    break;
            case 2: Deposit();
                    System.out.println("");  
                    break;
            case 3: Withdraw();
                    System.out.println("");  
                    break;
            case 4: ChangePin();
                    System.out.println("");  
                    break;
            case 5: TranHist();
                    System.out.println("");  
                    break;
            case 6:  System.out.println("THANK YOU FOR USING THE ATM. GoodBye!");    
                     System.exit(0);
            default :  System.out.println("Please enter a valid choice:");  
                       System.out.println();
                       menu();
            
        }
    }
 
    //To check the balance in your account.

    void balanceinquiry(){
        System.out.println("Your Balance is:" + balance);
        System.out.println();
        menu();
    }

//To deposit the balance in your account.

     public void Deposit() {
        System.out.println("Enter the amount you want to deposit:");
        Scanner sc = new Scanner(System.in);
        deposit = sc.nextInt();
        balance = balance + deposit;

        transaction++;  //whenever any transaction done increament the transaction.

        System.out.println("Amount deposited successfully.");

        String str = transaction + "." + deposit + "RS deposited\n";  //record the transaction details sequentially.
        tranhist = tranhist.concat(str);    //Add the transaction details to transaction history.
        balanceinquiry();
        System.out.println();
        menu();
    }

//Withdraw balance from your account.

   public void Withdraw(){

        System.out.println("Enter the amount to withdraw");
        Scanner sc = new Scanner(System.in);
         withdraw = sc.nextInt();

        //If your entered withdrawl amount is greater than available balance in your account.

         if(withdraw > balance){
            System.out.println("Insufficient funds in your account!");  
         }

         //Otherwise withdraw successful.
         else{
         balance = balance - withdraw; 

         transaction++;    //whenever any transaction done increament the transaction.
         System.out.println("Please collect your Cash.");

         String str = transaction + "." + withdraw + "RS withdrawed\n";  //record the transaction details sequentially.
         tranhist = tranhist.concat(str);   //Add the transaction details to transaction history.
         }

         //After successfully withdrawn,your available balance will be shown.

         balanceinquiry();
         System.out.println();
         menu();

    }

//if u want to change your atm pin.

     public void ChangePin() {
        System.out.println("Enter the new pin");
        Scanner sc = new Scanner(System.in);    //Enter the New Pin.
         int p = sc.nextInt();
         System.out.println("Confirm Pin");  //User needs to enter the pin two times for conforming the pin.
        int q = sc.nextInt();
        if(p == q){
         pin = p;

        System.out.println("Pin Changed successfully.");  //After the Pin change, enter the new pin to access your account.
        checkpin();}
        else{
            System.out.println("PIN DOES NOT MATCH!\n ENTER SAME NEW PIN BOTH TIMES ");
            ChangePin();
        }
     }
     
    public void TranHist() {
        //check if any transaction is done or not?
        if(transaction == 0){
             System.out.println("No transaction history recorded.");  //if not done show no transaction performed
        }
        else{
            System.out.print(tranhist);  //if transactions are done show them.
        }
        
    }
}
