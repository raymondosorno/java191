''' start of code 

# heading 1
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package LinkedList;

/**
 *
 * @author raymondiosorno
 */
import java.util.Scanner;
import java.util.Deque;
import java.util.ArrayDeque;

public class Racecar {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ## heading 2
        System.out.println("Enter your text:");
        String line = sc.nextLine();
        
        line = line.toLowerCase();
        line = line.replaceAll("\\s+", "");
        
        Deque<Character> deque = new ArrayDeque<>();
        for(int i = 0; i < line.length(); i++) {
           deque.addLast(line.charAt(i));
        
        }
        
        boolean isPalindrome = true;
        while(deque.size() > 1) {
            char front = deque.removeFirst();
            char back = deque.removeLast();
            
            if (front != back){
                isPalindrome = false;
                break;
            
            }
        
        }
        
        System.out.println(isPalindrome);


        sc.close();
    }
}
``` end of code 
