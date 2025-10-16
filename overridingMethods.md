# heading 1

```
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package OverridingMethods;

/**
 *
 * @author raymondiosorno
 */
public class Book {
   private String title;
   private String author;
   private String publisher;
   private String publicationDate;

   public void setTitle(String bookTitle) {
      title = bookTitle;
   }

   public void setAuthor(String bookAuthor) {
      author = bookAuthor;
   }

   public void setPublisher(String bookPublisher) {
      publisher = bookPublisher;
   }

   public void setPublicationDate(String pubDate) {
      publicationDate = pubDate;
   }

   public void printInfo() {
      System.out.println("Book Information: ");
      System.out.println("   Book Title: " + title);
      System.out.println("   Author: " + author);
      System.out.println("   Publisher: " + publisher);
      System.out.println("   Publication Date: " + publicationDate);
   }
}

//////////////////////end of code////////////////////////////////////////////////////////////


/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package OverridingMethods;

/**
 *
 * @author raymondiosorno
 */
public class Encyclopedia extends Book {
   private String edition;
   private int numPages;

   public void setEdition(String bookEdition) {
      edition = bookEdition;
   }

   public void setNumPages(int pages) {
      numPages = pages;
   }

   public void printInfo() {
      super.printInfo();
      System.out.println("   Edition: " + edition);
      System.out.println("   Number of Pages: " + numPages);
   }
}

//////////////////////end of code////////////////////////////////////////////////////////////


/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package OverridingMethods;

/**
 *
 * @author raymondiosorno
 */
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class BookInformation {
   public static void main(String[] args) throws FileNotFoundException {
      Scanner scnr = new Scanner(new File("src/main/resources/bookInput.txt"));

      Book myBook = new Book();
      Encyclopedia myEncyclopedia = new Encyclopedia();

      myBook.setTitle(scnr.nextLine());
      myBook.setAuthor(scnr.nextLine());
      myBook.setPublisher(scnr.nextLine());
      myBook.setPublicationDate(scnr.nextLine());

      myEncyclopedia.setTitle(scnr.nextLine());
      myEncyclopedia.setAuthor(scnr.nextLine());
      myEncyclopedia.setPublisher(scnr.nextLine());
      myEncyclopedia.setPublicationDate(scnr.nextLine());
      myEncyclopedia.setEdition(scnr.nextLine());
      myEncyclopedia.setNumPages(scnr.nextInt());

      myBook.printInfo();
      myEncyclopedia.printInfo();

      scnr.close();
   }
}
//////////////////////end of code////////////////////////////////////////////////////////////
``` end of code
