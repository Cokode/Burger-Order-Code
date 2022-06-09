# Burger-Order-Code
Built a program to help a Burger company take orders from customers 

public class BurgerTypes {

    private BasicBurger basicBurger;
    private HealthyBurger healthyBurger;
    //private DeluxeHamburger deluxeHamburger;

    public BurgerTypes(BasicBurger basicBurger, HealthyBurger healthyBurger, DeluxeHamburger deluxeHamburger) {
        this.basicBurger = basicBurger;
        this.healthyBurger = healthyBurger;
        //this.deluxeHamburger = deluxeHamburger;
    }

    public BasicBurger getBasicBurger() {
        return basicBurger;
    }

    public HealthyBurger getHealthyBurger() {
        return healthyBurger;
    }

//    private DeluxeHamburger getDeluxeHamburger() {
//        return deluxeHamburger;
//    }
}


import java.util.Scanner;

public class BasicBurger{
    private String breadType;
    private String meat;
    private double price;
    private String name;

    public BasicBurger(String breadType, String meat, double price, String name) {
        this.breadType = breadType;
        this.meat = meat;
        this.price = price;
        this.name = name;
    }

    final double lettuce = 4.3;
    final double tomato = 3.8;
    final double carrot = 2.6;
    final double corn = 1.7;

    public void additions(){
        System.out.println(this.breadType + " " + this.meat  + " " + this.name + " $" + this.price );


        System.out.println();
        double sumAll = getPrice() + lettuce + tomato + carrot + corn;
        System.out.println("Additional items: " + "\n" +
                "lettuce: $" + lettuce + "\n" +
                "tomato: $" + tomato + "\n" +
                "carrot: $" + carrot + "\n" +
                "corn: $" + corn + "\n" +
                "SubTotal: $" + sumAll);
    }

    public void takeOrder() {
        System.out.println("Order for " + getClass().getSimpleName()+ "$" + this.price + "\n");
        double sum = this.price + 0;
        double total = 0;
        System.out.println("To add lettuce press 1" + "\n" +
                "To add Tomato press 2" + "\n" +
                "To add carrot press 3" + "\n" +
                "To add corn press 4" + "\n" +
                "press 0 for base with no addition" + "\n" +
                "To complete the order press OK");

        Scanner scanner = new Scanner(System.in);
        while(true){
            boolean hasInt = scanner.hasNextInt();
            if(hasInt){
                int input = scanner.nextInt();
                switch(input){
                    case 1 -> System.out.println(sum += lettuce);
                    case 2 -> System.out.println(sum += tomato);
                    case 3 -> System.out.println(sum += carrot);
                    case 4 -> System.out.println(sum +=  corn);
                    case 0 -> sum = this.price;
                    default -> System.out.println("invalid orderCode");
                }
                scanner.nextLine();

            } else {
                System.out.println("Total order: $" + (sum));
                break;
            }
        }
        scanner.close();
    }


    public double baseFee(){
        return price;
    }
    private String Type() {
        return breadType;
    }

    private double getPrice() {
        return price;
    }

    private String getName() {
        return name;
    }
}


import java.util.Scanner;

public class HealthyBurger extends BasicBurger{




    public HealthyBurger() {
        super("Brown rye bread roll", "Pork", 12.6, "HealthyBurger");
    }

    final double cheeseSlice = 5.8;
    final double chickenChops = 10.7;



    private double details(){
        return cheeseSlice + chickenChops + super.baseFee();
    }

    @Override
    public void takeOrder() {
        System.out.println("Order for " + getClass().getSimpleName()+ " $" + baseFee() + "\n");
        double sum = 0;
        double total = 0;
        System.out.println("To add lettuce press 1" + "\n" +
                "To add Tomato press 2" + "\n" +
                "To add carrot press 3" + "\n" +
                "To add corn press 4" + "\n" +
                "To add cheeseSlice press 5" + "\n" +
                "To add chickenChops press 6" + "\n" +
                "press 0 for base with no addition" + "\n" +
                "To complete the order press OK");

        Scanner scanner = new Scanner(System.in);
        while(true){
            boolean hasInt = scanner.hasNextInt();
            if(hasInt){
                int input = scanner.nextInt();
                switch(input){
                    case 1 -> System.out.println(sum += lettuce);
                    case 2 -> System.out.println(sum += tomato);
                    case 3 -> System.out.println(sum += carrot);
                    case 4 -> System.out.println(sum +=  corn);
                    case 5 -> System.out.println(sum += cheeseSlice);
                    case 6 -> System.out.println(sum += chickenChops);
                    case 0 -> System.out.println(sum = super.baseFee());
                    default -> System.out.println("invalid orderCode");
                }
                scanner.nextLine();

            } else {
                System.out.println("Total order: $" + (sum + baseFee()));
                break;
            }
        }
        scanner.close();
    }


    @Override
    public void additions(){
        super.additions();

        System.out.println("\n" + "Add more picks for HealthyBurger addition:" );
        double sumAll = cheeseSlice + chickenChops + details();
        System.out.println("lettuce: $" + cheeseSlice + "\n" +
                "tomato: $" + chickenChops + "\n" +
                "SubTotal: $" + details());
    }
}


import java.util.Scanner;

public class Main {


    private final double coke = 3.9;
    private final double chips = 5.8;
    private double price = 10.5;

    private void deluxeBurgerAdditions() {
        System.out.println("Order for Deluxe Burger: $" + price + "\n" + "Add Deluxe Burger addition:" );
        double sumAll = coke + chips + price;
        System.out.println("coke: $" + coke + "\n" +
                "chips: $" + chips + "\n" +
                "SubTotal: $" + sumAll + "\n");
    }

    public void takeOrder2() {
        System.out.println("Order for Deluxe Burger" + price + "\n");
        double sum = price + 0;
        double total = 0;
        System.out.println("To add chips press 1" + "\n" +
                "To add coke press 2" + "\n" +
                "press 0 for base with no addition" + "\n" +
                "To complete the order press OK");

        Scanner scanner = new Scanner(System.in);
        while(true){
            boolean hasInt = scanner.hasNextInt();
            if(hasInt){
                int input = scanner.nextInt();
                switch(input){
                    case 1 -> System.out.println(sum += chips);
                    case 2 -> System.out.println(sum += coke);
                    case 0 -> sum = price;
                    default -> System.out.println("invalid orderCode");
                }
                scanner.nextLine();

            } else {
                System.out.println("Total order: $" + (sum));
                break;
            }
        }
        scanner.close();
    }

    public static void main(String[] args){
        DeluxeHamburger newDeluxeHamburger = new DeluxeHamburger();
        HealthyBurger healthyBurger = new HealthyBurger();
        BasicBurger newBasicBurger = new BasicBurger("Curly bread", "Beef", 10.5, "Basic Burger");
        BurgerTypes burgerTypes = new BurgerTypes(newBasicBurger, healthyBurger, newDeluxeHamburger);

        //burgerTypes.getHealthyBurger().takeOrder();
        //burgerTypes.getDeluxeHamburger().additions();
        Main deluxeHamBurger = new Main();
        deluxeHamBurger.deluxeBurgerAdditions();
        deluxeHamBurger.takeOrder2();

        //System.out.println(basicBurger.getName());
    }
}
