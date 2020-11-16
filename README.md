# CA2/Smart-Pants
Java codeteam work

//just a scanner sample and today`s homework.

import java.util.Scanner;

public static void main(String[] args) {

static void brunoMethod() {

/**
*Author: Bruno
*/

{

Scanner myKB = new Scanner(System.in);

int myNum;
    
   System.out.println("Please enter your age!");

try {
    
    myNum = myKB.nextInt();
   
   if ( myNum<0 || myNum>99 ) {
   
   System.out.println("That`s not a valid number, please verify it! ");
   
   }
   
   else if ( myNum<18 ) {
  
  System.out.println("To young to vote!");
  
  }
  
  else if ( myNum>17 && myNum<66 ) {
  
  System.out.println("Working hard?");
  
  }
  
  else {
  
  System.out.println("Enjoy your retirement!");
  
  }
  
  }
  
  catch(Exception e) {
  
  System.out.println("That`s not a number, please verify it!");
  
  }
  
    }

}

}
