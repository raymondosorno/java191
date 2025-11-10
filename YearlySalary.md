``` # heading 1
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package JFrames;

/**
 *
 * @author raymondiosorno
 */
```
``` ## heading 2
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;
import javax.swing.JButton;
import java.awt.GridBagLayout;
import java.awt.GridBagConstraints;
import java.awt.Insets;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class YearlySalary extends JFrame implements ActionListener {
    private JLabel wageLabel;
    private JLabel hoursLabel;
    private JLabel salLabel;
    
    private JTextField wageField;
    private JTextField hoursField;
    private JTextField salField;
    
    private JButton calcButton;

    public YearlySalary() {
        setTitle("Salary Calculator");

        // Labels
        wageLabel = new JLabel("hourly wage");
        hoursLabel = new JLabel("hours worked");
        salLabel = new JLabel("yearly salary");

        // Fields
        wageField = new JTextField(10);
        hoursField = new JTextField(10);
        salField = new JTextField(10);
        salField.setEditable(false); // not editable

        // Button
        calcButton = new JButton("calculate");
        calcButton.addActionListener(this);

        // Layout
        setLayout(new GridBagLayout());
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(10, 10, 10, 10);
        
        //wage
        gbc.gridx = 0; 
        gbc.gridy = 0;
        add(wageLabel, gbc);
        gbc.gridx = 1; 
        gbc.gridy = 0;
        add(wageField, gbc);

        //hours
        gbc.gridx = 0; 
        gbc.gridy = 1;
        add(hoursLabel, gbc);
        gbc.gridx = 1; 
        gbc.gridy = 1;
        add(hoursField, gbc);

        //sal
        gbc.gridx = 0; 
        gbc.gridy = 2;
        add(salLabel, gbc);
        gbc.gridx = 1; 
        gbc.gridy = 2;
        add(salField, gbc);

        //button
        gbc.gridx = 0; 
        gbc.gridy = 3;
        add(calcButton, gbc);
    }
```
``` ### heading 3
    @Override
    public void actionPerformed(ActionEvent e) {
        // user input
        String wageText = wageField.getText();
        String hoursText = hoursField.getText();

        // convert to numbers 
        int wage = Integer.parseInt(wageText);
        int hours = Integer.parseInt(hoursText);

        // calculation
        int yearly = wage * hours * 50;

        // show result
        salField.setText(Integer.toString(yearly));
    }

    public static void main(String[] args) {
        YearlySalary frame = new YearlySalary();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setVisible(true);
    }
}
```
