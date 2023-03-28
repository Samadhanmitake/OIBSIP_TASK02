# OIBSIP_TASK02
ATMinterface.java
import java.util.Scanner;

import org.w3c.dom.NameList;

class atm{
    int balance=50000;
    int amount;
    String tranHist="Transaction History = \n";
    int tran=0;
    String uname,psd;
    public void register()
    {
        Scanner sc=new Scanner(System.in);
        System.out.println("Chose \n 1.Register \n 2.Exit");
        int t=sc.nextInt();
        if(t==1){
            System.out.println("Enter your name = ");
            String name=sc.next();
            System.out.println("Enter User name = ");
            uname=sc.next();
            System.out.println("Enter password = ");
            psd=sc.next();
            System.out.println("Enter account number = ");
            int accNo=sc.nextInt();
            System.out.println("Successfully Register ");
        }
        else{
            System.out.println("Thank you successfuly exit");
        }
    }
    public int login()
    {
        int result=0;
        Scanner sc=new Scanner(System.in);
        System.out.println("Choce \n 1.Login \n 2.Exit");
        int t=sc.nextInt();
        if(t==1){
            System.out.println("Enter User name = ");
            String Uname=sc.next();
            if(Uname.equals(uname))
            {
                System.out.println("Enter password = ");
                String password=sc.next();
                if(password.equals(psd)){
                    System.out.println("Login Succesfully");
                    result=1;
                }
            }
            else{
                System.out.println("Enter correct User name ");
            }
        }
        return result;
    }
    void Withdraw(){
        Scanner sc=new Scanner(System.in);
        System.out.println("Enter withdraw amount = ");
        amount=sc.nextInt();
        if(balance > amount){
            balance=balance-amount;
            String str=amount+" Rs Withdraw \n";
            System.out.println("Successfully "+str);
            tranHist=tranHist.concat(str);
            tran++;
        }
        else{
            System.out.println("Insufficient balance ");
        }
    }
    void Transaction(){
        if(tran==0){
            System.out.println("Empty \n");
        }
        else{
            System.out.println(tranHist);
        }
    }
    void Deposit()
    {
        Scanner sc=new Scanner(System.in);
        System.out.println("Enter Deposit Amount = ");
        int amount=sc.nextInt();
        balance=balance+amount;
        String str=amount+" Rs Deposit \n";
        System.out.println("Successfully "+str);
        tranHist=tranHist.concat(str);
        tran++;
    }
    void Transfer()
    {
        Scanner sc=new Scanner(System.in);
        System.out.println("Enter Transfer person name = ");
        String Tname=sc.next();
        System.out.println("Enter Transfer Amount = ");
        int amount=sc.nextInt();
        if(balance > amount){
            balance=balance - amount;
            String str=amount + " Rs Tranfer to "+Tname +"\n";
            System.out.println("Successfully "+str);
            tranHist=tranHist.concat(str);
            tran++;
        }
    }
    void balance(){
        System.out.println("Account balance = "+balance+"\n");
    }

}
public class ATMinterface2 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int loop=1;
        atm a=new atm();
        a.register();
        int r=a.login();
        if(r==1){
        while(loop!=0){
            System.out.println("Enter choice - \n1.Transactin Histry \n2.Withdraw \n3.deposit \n4.Transfer \n5.Balance \n6.Exit");
            int input=sc.nextInt();
            switch(input){
                case 1:
                a.Transaction();
                break;
                case 2:
                a.Withdraw();
                break;
                case 3:
                a.Deposit();
                break;
                case 4:
                a.Transfer();
                break;
                case 5:
                a.balance();
                break;
                case 6:
                System.out.println("Succesfully Exit ");
                loop=0;
                break;
                default :
                System.out.println("Please Enter Number in between 1 to 6 ");
            }
        }
    }
    else{
        System.out.println("Out");
    }
        System.out.println();
        
    }
}
