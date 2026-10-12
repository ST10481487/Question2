/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.runapplication;

/**
 *
 * @author Mc Donald
 */      
import java.util.Scanner;

public class RunApplication {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        int grandTotal = 0;

        // Enter sales for three cities
        for (int i = 1; i <= 3; i++) {

            System.out.println();
            System.out.println("Select the beverage type");
            System.out.println("1) COFFEE");
            System.out.println("2) TEA");
            System.out.println("3) BOBA");

            System.out.print("Enter your choice: ");
            int choice = input.nextInt();
            input.nextLine();

            String beverageType;

            switch (choice) {
                case 1:
                    beverageType = "COFFEE";
                    break;

                case 2:
                    beverageType = "TEA";
                    break;

                case 3:
                    beverageType = "BOBA";
                    break;

                default:
                    System.out.println("Invalid choice. Please try again.");
                    i--;
                    continue;
            }

            System.out.print("Enter the city: ");
            String city = input.nextLine();

            System.out.print("Enter the total sales of "
                    + beverageType + " beverages in "
                    + city + ": ");

            int totalSales = input.nextInt();
            input.nextLine();

            // Create BeverageSales object
            BeverageSales sales = new BeverageSales(
                    beverageType, city, totalSales);

            // Display report
            sales.printReport();

            // Calculate grand total
            grandTotal += sales.getTotalSales();
        }

        // Display total sales for all cities
        System.out.println();
        System.out.println("TOTAL SALES FOR ALL CITIES");
        System.out.println("**************************");
        System.out.println("GRAND TOTAL: " + grandTotal);

        input.close();
    }
}


/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.runapplication;

/**
 *
 * @author Student
 */
 
public class BeverageSales extends Beverage {

    // Constructor
    public BeverageSales(String beverageType, String city, int totalSales) {
        super(beverageType, city, totalSales);
    }

    // Print report
    public void printReport() {
        System.out.println();
        System.out.println("NUMBER 1 COFFEE HUT REPORT");
        System.out.println("**************************");
        System.out.println("BEVERAGE TYPE: " + getBeverageType());
        System.out.println("CITY: " + getCity());
        System.out.println("TOTAL SALES: " + getTotalSales());
    }
}
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.runapplication;

/**
 *
 * @author Student
 */    
public abstract class Beverage implements IBeverage {

    protected String beverageType;
    protected String city;
    protected int totalSales;

    // Constructor
    public Beverage(String beverageType, String city, int totalSales) {
        this.beverageType = beverageType;
        this.city = city;
        this.totalSales = totalSales;
    }

    // Getter methods
    @Override
    public String getBeverageType() {
        return beverageType;
    }

    @Override
    public String getCity() {
        return city;
    }

    @Override
    public int getTotalSales() {
        return totalSales;
    }
}

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Interface.java to edit this template
 */
package com.mycompany.runapplication;

/**
 *
 * @author Student
 */
 
public interface IBeverage {

    String getBeverageType();

    String getCity();

    int getTotalSales();
}

