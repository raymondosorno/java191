```
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package JFrames;

/**
 *
 * @author raymondiosorno
 */

``` # heading 1

import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JFormattedTextField;
import javax.swing.JButton;
import java.awt.GridBagLayout;
import java.awt.GridBagConstraints;
import java.awt.Insets;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.text.NumberFormat;

public class Distance extends JFrame implements ActionListener {
    private JLabel milesLabel;
    private JLabel kmLabel;
    private JLabel mLabel;
    private JLabel feetLabel;

    private JFormattedTextField milesField;
    private JFormattedTextField kmField;
    private JFormattedTextField mField;
    private JFormattedTextField feetField;

    private JButton convertButton;

    public Distance() {
        setTitle("Distance Converter");

        // labels
        milesLabel = new JLabel("miles");
        kmLabel = new JLabel("kilometers");
        mLabel = new JLabel("meters");
        feetLabel = new JLabel("feet");

        NumberFormat nf = NumberFormat.getNumberInstance();

        // fields
        milesField = new JFormattedTextField(nf);
        milesField.setColumns(10);
        milesField.setValue(0);

        kmField = new JFormattedTextField(nf);
        kmField.setColumns(10);
        kmField.setEditable(false);   

        mField = new JFormattedTextField(nf);
        mField.setColumns(10);
        mField.setEditable(false);   

        feetField = new JFormattedTextField(nf);
        feetField.setColumns(10);
        feetField.setEditable(false); 

        
        convertButton = new JButton("convert");
        convertButton.addActionListener(this);

        // layout
        setLayout(new GridBagLayout());
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(10, 10, 10, 10);

        gbc.gridx = 0; 
        gbc.gridy = 0; 
        add(milesLabel, gbc);
        gbc.gridx = 1;               
        add(milesField, gbc);

        gbc.gridx = 0; 
        gbc.gridy = 1; 
        add(kmLabel, gbc);
        gbc.gridx = 1;               
        add(kmField, gbc);

        gbc.gridx = 0; 
        gbc.gridy = 2; 
        add(mLabel, gbc);
        gbc.gridx = 1;               
        add(mField, gbc);

        gbc.gridx = 0; 
        gbc.gridy = 3; 
        add(feetLabel, gbc);
        gbc.gridx = 1;               
        add(feetField, gbc);

        gbc.gridx = 0; 
        gbc.gridy = 4; 
        add(convertButton, gbc);
    }
``` ## heading 2
    @Override
    public void actionPerformed(ActionEvent e) {
        try {
        // for JFormattedTextField commit current text to value
            milesField.commitEdit();
        } catch (java.text.ParseException ex) {
            milesField.setValue(0);
        }

        // read as #
        Number n = (Number) milesField.getValue();
        int miles = (n == null) ? 0 : n.intValue(); 

        // conversions
        double km = miles * 1.60934;
        double m = miles * 1609.34;
        double feet = miles * 5280;

        // results
        kmField.setValue(km);
        mField.setValue(m);
        feetField.setValue(feet);
    }

    public static void main(String[] args) {
        Distance frame = new Distance();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setVisible(true);
    }
}
```
