# CA2/Smart-Pants
Java codeteam work

/**
 *
 * @author Awa
 */
 
 try {
            
            BufferedReader myKB2 = new BufferedReader(new InputStreamReader(System.in));
            
            System.out.println("Please enter a number");
            int num1 = Integer.parseInt(myKB2.readLine());
            
            System.out.println("Please enter another number");
            int num2 = Integer.parseInt(myKB2.readLine());
            
            
            if (num2 == 0){
                System.out.println("Erro! \n");
            }
            
            else{
                System.out.println("The first number Divided by the second number is " + (num1/num2) + "\n");
            }
            
        }
        
        catch (Exception e){
            System.out.println("Erro! \n");
        }
