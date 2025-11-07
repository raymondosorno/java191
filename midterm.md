```
#heading 1 version one
V1
#main
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package MidTerm;

/**
 *
 * @author raymondiosorno
 */
// Inventory Control System - Version 1.0
```
```
## heading 2 star of code main
public class InventorySystem {
    public static void main(String[] args) {
        // one of each type of constructors
        PainKiller pain1 = new PainKiller("Tylenol", "greatvalue", "2026-03-01", "Adult");
        Bandage band1 = new Bandage("Band-Aid", "greatvalue", "2037-09-12", "All Ages", "Y");
        Equipment equip1 = new Equipment("Thermometer", "greatvalue", 1.2);
        
        pain1.display();
        band1.display();
        equip1.display();

        pain1.update("2027-07-18");
        pain1.display();
    }
}

====================================


public class PainKiller {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;

    public PainKiller(String name, String company, String expiryDate, String ageGroup) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
    }

    public void display() {
        System.out.println("Painkiller Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
    }

    public void update(String newExpiry) {
        this.expiryDate = newExpiry;
        System.out.println("Expiry date updated to: " + newExpiry);
    }

}

==================================================



public class Bandage {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;
    private String waterproof; // "Y" or "N"

    public Bandage(String name, String company, String expiryDate, String ageGroup, String waterproof) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
        this.waterproof = waterproof;
    }

    public void display() {
        System.out.println("Bandage Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
        System.out.println("Waterproof: " + waterproof);
    }
}
===========================================


public class Equipment {
    private String name;
    private String company;
    private double weight; // lbs

    public Equipment(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void display() {
        System.out.println("Equipment Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight (lbs): " + weight);
    }
}

```
==========================================================

```
### V2 only changed main to this everything else is the same 

public class InventorySystem {

    public static void main(String[] args) {
        try {
            String name = "Tylenol";
            String company = "Johnson & Johnson";
            String expiry = "2026-05-10";
            String ageGroup = " "; 

            if (name.isEmpty()) {
                throw new IllegalArgumentException("Painkiller name cannot be empty.");
            }

            if (!(ageGroup.equalsIgnoreCase("Adult") || ageGroup.equalsIgnoreCase("Child"))) {
                throw new IllegalArgumentException("Age group must be 'Adult' or 'Child'.");
            }

            Painkiller pain1 = new Painkiller(name, company, expiry, ageGroup);

            pain1.display();

        } catch (IllegalArgumentException e) {
            // handles known bad inputs
            System.out.println("Input Error: " + e.getMessage());
        } catch (Exception e) {
            // handles other unexpected errors
            System.out.println("An unexpected error occurred: " + e.getMessage());
        }
    }
}
 
===========================================================


public class PainKiller {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;

    public PainKiller(String name, String company, String expiryDate, String ageGroup) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
    }

    public void display() {
        System.out.println("Painkiller Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
    }

    public void update(String newExpiry) {
        this.expiryDate = newExpiry;
        System.out.println("Expiry date updated to: " + newExpiry);
    }

}

==================================================



public class Bandage {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;
    private String waterproof; // "Y" or "N"

    public Bandage(String name, String company, String expiryDate, String ageGroup, String waterproof) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
        this.waterproof = waterproof;
    }

    public void display() {
        System.out.println("Bandage Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
        System.out.println("Waterproof: " + waterproof);
    }
}
===========================================

public class Equipment {
    private String name;
    private String company;
    private double weight; // lbs

    public Equipment(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void display() {
        System.out.println("Equipment Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight (lbs): " + weight);
    }
}



========================================================
```
```
### V3 only changed main to this and created new class “InvalidInputException”

public class InventorySystem {
    public static void main(String[] args) {
        Painkiller pain1 = new Painkiller("Tylenol", "Johnson & Johnson", "2026-05-10", "Adult");
        Bandage band1 = new Bandage("Band-Aid", "3M", "2027-01-15", "All Ages", "Y");

        try {
            // set to 0 to test the exception, or leave as a valid positive number
            Equipment equip1 = new Equipment("Thermometer", "c4", 1.2);

            // original displays
            pain1.display();
            band1.display();
            equip1.display();

        } catch (InvalidInputException e) {   // catch the custom exception
            System.out.println("Input Error: " + e.getMessage());
        }
    }
}

===========================================================


public class PainKiller {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;

    public PainKiller(String name, String company, String expiryDate, String ageGroup) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
    }

    public void display() {
        System.out.println("Painkiller Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
    }

    public void update(String newExpiry) {
        this.expiryDate = newExpiry;
        System.out.println("Expiry date updated to: " + newExpiry);
    }

}

==================================================



public class Bandage {
    private String name;
    private String company;
    private String expiryDate;
    private String ageGroup;
    private String waterproof; // "Y" or "N"

    public Bandage(String name, String company, String expiryDate, String ageGroup, String waterproof) {
        this.name = name;
        this.company = company;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
        this.waterproof = waterproof;
    }

    public void display() {
        System.out.println("Bandage Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
        System.out.println("Waterproof: " + waterproof);
    }
}
===========================================


public class Equipment {
    private String name;
    private String company;
    private double weight; // lbs

    public Equipment(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void display() {
        System.out.println("Equipment Information:");
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight (lbs): " + weight);
    }
}
===========================================================

public class InvalidInputException extends Exception {
    public InvalidInputException(String message) {
        super(message);
    }
}


```
