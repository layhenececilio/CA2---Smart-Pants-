


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
