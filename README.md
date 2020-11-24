
package ca2layhene;
import java.util.*;
/**
 *
 * @author layhenececilio
 */
public class CA2Layhene {
    static void Layhene() {
        /**author:L. Prado
         * 
         */
        System.out.println("This is Layhene's code.");
        System.out.println("This is my mean code.");
    }

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        Layhene();
      
        Scanner grades = new Scanner(System.in);
        
        System.out.println("Insert Github Points: ");
         int github = grades.nextInt();
        System.out.println("Insert Slack Points: ");
         int slack = grades.nextInt();  
        System.out.println("Insert Report Points:");
        int report = grades.nextInt();
        
        int result = (github + slack + report)/4;
        System.out.println("The Group Final Grade is: " + result + "%");
            
        
    }
    
}
