``` # heading 1
CREATE DATABASE IF NOT EXISTS auto;
USE auto;

CREATE TABLE IF NOT EXISTS cars (
    car_name VARCHAR(255) PRIMARY KEY,
    mpg DOUBLE,
    horsepower DOUBLE
);

TRUNCATE TABLE cars;

INSERT INTO cars (car_name, mpg, horsepower) VALUES
('Ford Focus', 28, 160),
('Toyota Camry', 24, 178),
('Honda Accord', 26, 192),
('Chevrolet Impala', 22, 305),
('Nissan Sentra', 30, 149),
('Jeep Wrangler', 20, 285),
('Mazda 3', 29, 186),
('Subaru Outback', 26, 182),
('Kia Soul', 31, 147),
('Ford Mustang', 21, 450),
('Old Concept Car', 25, NULL);

SELECT * FROM cars;

```

``` # heading 2

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package AutosDatabases;

import javax.swing.*;
import java.awt.*;
import java.sql.*;

public class CarFrame extends JFrame {

    private JSlider mpgSlider;
    private JSlider hpSlider;
    private JTextArea output;

    public CarFrame() {

        setTitle("Car Search");
        setSize(500, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        JPanel topPanel = new JPanel();
        topPanel.setLayout(new GridLayout(3, 2));

        topPanel.add(new JLabel("Minimum MPG:"));
        mpgSlider = new JSlider(0, 60, 0);

        mpgSlider.setMajorTickSpacing(10);
        mpgSlider.setMinorTickSpacing(2);
        mpgSlider.setPaintTicks(true);
        mpgSlider.setPaintLabels(true);

        topPanel.add(mpgSlider);

        topPanel.add(new JLabel("Minimum Horsepower:"));
        hpSlider = new JSlider(0, 500, 0);

        hpSlider.setMajorTickSpacing(100);
        hpSlider.setMinorTickSpacing(25);
        hpSlider.setPaintTicks(true);
        hpSlider.setPaintLabels(true);

        topPanel.add(hpSlider);

        JButton searchButton = new JButton("Search");
        topPanel.add(searchButton);

        topPanel.add(new JLabel(""));

        add(topPanel, BorderLayout.NORTH);

        output = new JTextArea();
        output.setEditable(false);
        add(new JScrollPane(output), BorderLayout.CENTER);

        searchButton.addActionListener(e -> searchCars());

        setVisible(true);
    }

    private void searchCars() {

        output.setText("");

        int minMPG = mpgSlider.getValue();
        int minHP = hpSlider.getValue();

        String url = "jdbc:mysql://localhost:3306/auto";
        String user = "root";
        String password = "babylayla";

        Connection con = null;
        Statement stmt = null;

        try {
            con = DriverManager.getConnection(url, user, password);
            stmt = con.createStatement();

            String sql =
                "SELECT * FROM cars " +
                "WHERE mpg >= " + minMPG +
                " AND (horsepower >= " + minHP + " OR horsepower IS NULL)";

            ResultSet rs = stmt.executeQuery(sql);

            boolean found = false;

            while (rs.next()) {
                found = true;

                String name = rs.getString("car_name");
                double mpg = rs.getDouble("mpg");
                Double hp = rs.getObject("horsepower", Double.class);

                output.append(name + " | MPG: " + mpg +
                        " | HP: " + (hp == null ? "Unknown" : hp) + "\n");
            }

            if (!found) {
                output.setText("No cars matched your search.");
            }

        } catch (Exception ex) {
            output.setText("Database error:\n" + ex.getMessage());
        } finally {
            try { if (stmt != null) stmt.close(); } catch (Exception e) {}
            try { if (con != null) con.close(); } catch (Exception e) {}
        }
    }

    public static void main(String[] args) {
        new CarFrame();
    }
}
``` end of code
