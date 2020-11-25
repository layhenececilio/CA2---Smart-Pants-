
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

package leilamethod;

import java.util.Scanner;

/**
 *Program that asks and checks the user for their age and output a message 
 * @author leila
 */
public class LeilaMethod {
    
    static void leilaMethod (){
        
         int userAge;
        Scanner ageScanner = new Scanner (System.in);   //Opening the Scanner to scan the input from the user
        
        System.out.println("Please enter your age");    //Asks user to type their age 
         
        try{
            userAge = ageScanner.nextInt(); // Gets the age entered
                
            String personAge = Integer.toString(userAge); //Converting int into a String
            
            if (!personAge.matches("[0-9 ]+")) {  //It returns false if the number is a negative one 
           
               System.out.println("The 'Age' is not a positive number " + personAge.matches("[0-9 ]+"));
                
             
                //Checking if the user is under the age of 18 years old
            }else if (userAge < 18) {
                System.out.println("You are still very strong");
            
                //Checking if the user is over 18 and under 66 years old
            }else if((userAge >= 18) && (userAge < 66)){
                System.out.println("You hold the world on your hands!");
            
                //Checking if the user is over 66 and under 100 years old
                //100 is the maximum age set because the user might type something like 453 as their age
            }else if ((userAge >= 66) && (userAge <= 100)){
                System.out.println("You deserve to have fun!");
            
            }else{
                System.out.println("You are a Legend");
            }   //Out put the age of the user
            
        }catch(Exception e){
            System.out.println("That was not a number! Please enter a number!");
        }
    }

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        leilaMethod();   
    }
}

# CA2/Smart-Pants
Java codeteam work


package CA2TimeTaskWhoAreYou;

import java.util.Scanner;


public class MethodsExercise {
    static void AwaMethod(){
    /**
     * author: Awa
     */
        System.out.println("This is Awa code.");
    }


public class CA2TimeTaskWhoAreYou {

   /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        
        Scanner myKB = new Scanner(System.in);
        
        String input;
        
            System.out.println("Who are you?");
            
                input = myKB.nextLine();
            
            
            System.out.println("Oh, that is a very nice name, " + input + "!!!");
        
    }
    
}



package programblabla;

import java.io.*;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class MainClass {

static void brunoMethod() {

/*
*Author: Bruno
*/

    private static final String EMPTY = " ";
    //Constant for gender
    private static final String MALE = "M";
    private static final String FEMALE = "F";
    private static final String TRANS = "T";

    public static void main(String args[]) {
        try {
            //Reading file information
            List<PersonObject> fileData = readFileInformation();
            //Creating output object
            List<StatusObject> listStatusObject = new ArrayList<>();
            //Loot through the list of PersonObject
            for (PersonObject personObject : fileData) {
                String currentName = "";
                //Processing the gender
                String title = getGender(personObject.getGender());
                //Processing the status
                String status = getStatus(personObject.getAge());
                String name = personObject.getName();
                //Splitting the full name per empty spaces
                String[] fullNameAsList = name.split(EMPTY);
                //Get the first position of the array as the first name
                String firstName = fullNameAsList[0];
                //Loop through the other names and separate by empty space
                for (int i = 1; i < fullNameAsList.length; i++) {
                    currentName = currentName + fullNameAsList[i] + EMPTY;
                }
                //Concatenate salutation + empty space + the last name + , + first name letter
                currentName = title + EMPTY + currentName.trim() + ", " + firstName.charAt(0);
                //Create StatusObject with name and status
                StatusObject statusObject = new StatusObject(currentName, status);
                //Add the object on the output list
                listStatusObject.add(statusObject);
            }
            //save output file
            saveInToFile(listStatusObject);
            //print error in the console in case of exception    
        } catch (Exception e) {
            System.out.println(e.getMessage());
            e.printStackTrace();
        }
    }

    private static void saveInToFile(List<StatusObject> listStatusObject) throws Exception {
        //Creating the file to be filled
        FileWriter fileWriter = new FileWriter("C:\\Users\\user\\Desktop\\CCT\\Mandatory Labs\\programblabla\\src\\programblabla\\status.txt");
        //loop through the list of status objects and write the file line by line
        for (StatusObject statusObject : listStatusObject) {
            fileWriter.write(statusObject.getName());
            fileWriter.write(System.lineSeparator());
            fileWriter.write(statusObject.getStatus());
            fileWriter.write(System.lineSeparator());
        }
        //close the writen file
        fileWriter.close();
    }

    private static List<PersonObject> readFileInformation() throws Exception {
        int counter = 1;
        //Creating basic objects
        PersonObject personObject = new PersonObject();
        List<PersonObject> listPerson = new ArrayList<>();
        List<String> fileInformation = new ArrayList<>();
        //Reading file
        FileReader fileReader
                = new FileReader(
                        "C:\\Users\\user\\Desktop\\CCT\\Mandatory Labs\\programblabla\\src\\programblabla\\people.txt");

        Scanner scanner = new Scanner(fileReader);
        while (scanner.hasNextLine()) {
            //Adding each file line into a string list
            fileInformation.add(scanner.nextLine());
        }

        //Validating file information
        //if the file is empty or if theres not enough information the content of the file is wrong
        if (fileInformation.isEmpty() || fileInformation.size() % 3 != 0) {
            throw new ExercicioException("An information is missing, please verify it.");
        } else {
            //For each iten of the fileInformation list fill the objects and add into a list of PersonObject
            for (String info : fileInformation) {
                if (counter == 1) {
                    personObject.setName(info);
                    counter++;
                } else if (counter == 2) {
                    personObject.setAge(info);
                    counter++;
                } else if (counter == 3) {
                    personObject.setGender(info);
                    listPerson.add(personObject);
                    personObject = new PersonObject();
                    counter = 1;
                }
            }
        }
        //Close the file
        scanner.close();
        return listPerson;
    }

    private static String getGender(String gender) {
        String title = "";
        //Validate gender value
        if (!(gender.equals(MALE) || gender.equals(FEMALE) || gender.equals(TRANS))) {
            throw new ExercicioException("No valid gender was found.");
        } else {
            //Atributes the salutation based on the gender
            switch (gender) {
                case MALE:
                    title = "Mr.";
                    break;
                case FEMALE:
                    title = "Ms.";
                    break;
                case TRANS:
                    title = "Mx.";
                    break;
            }
        }
        return title;
    }

    private static String getStatus(String age) {
        int ageAsInt = Integer.parseInt(age);
        //Validating the age and returning the status based on the age
        if (ageAsInt < 0 || ageAsInt > 100) {
            throw new ExercicioException("No valid age was found.");
        } else if (ageAsInt < 19) {
            return "School";
        } else if (ageAsInt > 66) {
            return "Retired";
        } else if (ageAsInt > 18 && ageAsInt < 26) {
            return "College";
        } else {
            return "Worker";
        }
    }


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
        // TODO code application logic here
     Scanner myKB = new Scanner (System.in);
     
     String input;
     
        System.out.println("Please enter some text");
        
        input = myKB.nextLine();
        
        System.out.println("You entered " + input);
    }
    

     
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
