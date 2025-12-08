``` # heading 1 sql
CREATE DATABASE IF NOT EXISTS Miramar;
USE Miramar;
CREATE TABLE IF NOT EXISTS Student (
    SSN VARCHAR(9) PRIMARY KEY,
    FirstName VARCHAR(50),
    MiddleName VARCHAR(100),
    LastName VARCHAR(50),
    DOB DATE,
    Street VARCHAR(100),
    Phone VARCHAR(20),
    Zipcode VARCHAR(10),
    deptID INT
);
SHOW TABLES;
DESC Student;
DELETE FROM Student WHERE SSN = '111222333';


```

``` #heading 2 java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package Databases;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;

public class MiramarDatabase {

    public static void main(String[] args) {

        // connect to the database
        String url = "jdbc:mysql://localhost:3306/Miramar";
        String user = "root";
        String password = "babylayla";

        try {
            Connection con = DriverManager.getConnection(url, user, password);
            System.out.println("Connected!");

            Statement stmt = con.createStatement();

            // insert the record
            String insert = "INSERT INTO Student " +
                    "(SSN, FirstName, MiddleName, LastName, DOB, Street, Phone, Zipcode, deptID) " +
                    "VALUES ('111222333', 'Philip', 'David Charles', 'Collins', " +
                    "'1951-01-30', 'NA', 'NA', 'NA', 1234)";

            int rowsInserted = stmt.executeUpdate(insert);
            System.out.println("Rows inserted: " + rowsInserted);

            // update zip
            String update = "UPDATE Student SET Zipcode = '92126' " +
                            "WHERE SSN = '111222333'";
            int rowsUpdated = stmt.executeUpdate(update);
            System.out.println("Rows updated: " + rowsUpdated);

            // select and print the new record
            String query = "SELECT SSN, FirstName, MiddleName, LastName, DOB, " +
                           "Street, Phone, Zipcode, deptID " +
                           "FROM Student WHERE SSN = '111222333'";

            ResultSet rs = stmt.executeQuery(query);

            System.out.println("\nStudent record:");
            while (rs.next()) {
                String ssn = rs.getString("SSN");
                String first = rs.getString("FirstName");
                String middle = rs.getString("MiddleName");
                String last = rs.getString("LastName");
                String dob = rs.getString("DOB");
                String street = rs.getString("Street");
                String phone = rs.getString("Phone");
                String zip = rs.getString("Zipcode");
                int dept = rs.getInt("deptID");

                System.out.println(ssn + " | " + first + " | " + middle + " | " +
                                   last + " | " + dob + " | " + street + " | " +
                                   phone + " | " + zip + " | " + dept);
            }

            con.close();

        } catch (Exception e) {
            System.out.println("Error:");
            e.printStackTrace();
        }
    }
}

``` end of code
