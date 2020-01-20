package machine;
import java.util.Scanner;

public class CoffeeMachine {
        static int waterHas = 400;
        static int milkHas = 540;
        static int coffeeBeansHas = 120;
        static int disposableHas =9;
        static int costs = 550;

        static Scanner scanner = new Scanner(System.in);
        static boolean close = false;

    public static void main(String[] args) {

        do{
        System.out.println("Write action(buy, fill, take, remaining, exit)");
        System.out.println();
        String str1 = scanner.nextLine();
        if(str1.equals("buy")){
            buy();
        } else if(str1.equals("fill")){
            fill();
        } else if(str1.equals("take")) {
           take();
        } else if(str1.equals("remaining")){
           machineHas();
        } else if(str1.equals("exit")){
            exit();
        } 
        }while(close==false);

    }
     static public void machineHas(){
            System.out.println("The coffee machine has:");
            System.out.println(waterHas + " of water");
            System.out.println(milkHas + " of milk");
            System.out.println(coffeeBeansHas + " of coffee beans");
            System.out.println(disposableHas + " of disposable cups");
            System.out.println(costs + " of money");
            
        } 

    public static void buy(){
         System.out.println("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu");
            String var = scanner.next();
            switch(var){
                case "1":
                    if(canMake(250,0,16)){
                    waterHas -=250 ;
                    coffeeBeansHas -= 16;
                    costs += 4;
                    disposableHas -= 1;   
                    break;
                    }
                case "2":
                    if(canMake(350,75,20)){
                    waterHas -= 350;
                    milkHas -= 75;
                    coffeeBeansHas -= 20;
                    costs += 7;
                    disposableHas -= 1;  
                    break;
                    }
                case "3":
                    if(canMake(200,100,12)){
                    waterHas -= 200;
                    milkHas -= 100;
                    coffeeBeansHas -= 12;
                    costs += 6;
                    disposableHas -= 1;
                    break;    
                    }
                case "back":{
                    break;
                    }    
                default:{
                    break;
                }
            }
    }

    public static void fill(){
         System.out.println("Write how many ml of water do you want to add:");
            int waterAdd = scanner.nextInt();
            System.out.println("Write how many ml of milk do you want to add:");
            int milkAdd = scanner.nextInt();
            System.out.println("Write how many grams of coffee beans do you want to add:");
            int coffeeBeansAdd = scanner.nextInt();
            System.out.println("Write how many disposable cups of coffee do you want to add:");
            int disposableAdd = scanner.nextInt();

             waterHas += waterAdd ;
             milkHas += milkAdd;
             coffeeBeansHas += coffeeBeansAdd;       
             disposableHas += disposableAdd;
    }
    public static void take(){
         System.out.println("I gave you $"+ costs);
            costs = 0 ;
    }
    public static void exit(){
        close = true;
    }
    public static boolean canMake(int waterNeed, int milkNeed, int beansNeed){
        if(waterHas>=waterNeed){
            if(milkHas>=milkNeed){
                if(coffeeBeansHas>=beansNeed){
                    System.out.println("I have enough resources, making you a coffee!");
                    return true;
                } else {
                    System.out.println("Sorry, not enough beans!");
                    return false;
                     }
                } else {
                    System.out.println("Sorry, not enough milk!");
                    return false;
                    }
                } else {
                     System.out.println("Sorry, not enough water!");
                     return false;
                }

            }
        
    }

