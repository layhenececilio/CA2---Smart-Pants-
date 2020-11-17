/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package nataliamethods1;

import java.util.Scanner;

/**
 *
 * @author Natalia
 */
public class NataliaMethods {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
     Scanner myKB = new Scanner (System.in);
     
     String input;
     
        System.out.println("Please enter some text");
        
        input = myKB.nextLine();
        
        System.out.println("You entered " + input);
    }
    
}
