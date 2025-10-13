/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package exceptions;

/**
 *
 * @author raymondiosorno
 */
import java.util.Scanner;

public class StepConverter {
#1 exception
    public static double stepsToMiles(int steps) throws Exception {
        if (steps < 0) {
            throw new Exception("Exception: Negative step count entered.");
        }

        // 2000 steps = 1 mile
        // divide steps by 2000.0 to get miles
        double miles = steps / 2000.0;
        return miles;
    }
##2 main
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in); // to read user input

        // Read number of steps from user
        int userSteps = scnr.nextInt();

        try {
            // Call the stepsToMiles() method and store the returned miles
            double milesWalked = stepsToMiles(userSteps);

            // Print the miles with 2 decimal places
            System.out.printf("%.2f", milesWalked);
        } 
        catch (Exception excpt) {
            // If an exception happens, print the message
            System.out.println(excpt.getMessage());
        }
    }
}
###end
