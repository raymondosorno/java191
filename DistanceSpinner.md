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
# heading 1
```
```
import javax.swing.JFrame; //main window
import javax.swing.JLabel; // text
import javax.swing.JSpinner; // user input nemeric spinner
import javax.swing.JTextField; //text
import javax.swing.JButton; //button
import javax.swing.SpinnerNumberModel; // limits and steps for spinner
import java.awt.GridBagLayout; //holder and placer
import java.awt.GridBagConstraints; // placement
import java.awt.Insets; // borders
import java.awt.event.ActionListener; // actions or clicks
import java.awt.event.ActionEvent; // button click

public class DistanceSpinner extends JFrame implements ActionListener {
    private JLabel milesLabel;
    private JLabel kmLabel;

    private JSpinner milesSpinner; 
    private JTextField kmField;  
    
    private JButton convertButton;

    public DistanceSpinner() {
        setTitle("Miles to Kilometers Converter");

        // Labels
        milesLabel = new JLabel("Miles:");
        kmLabel = new JLabel("Kilometers:");

        // start0 min0 max10000 step1
        SpinnerNumberModel spinnerModel = new SpinnerNumberModel(0, 0, 10000, 1);
        milesSpinner = new JSpinner(spinnerModel);

        kmField = new JTextField(10);
        kmField.setEditable(false);

        convertButton = new JButton("Convert");
        convertButton.addActionListener(this);

        // layout
        setLayout(new GridBagLayout());
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(10, 10, 10, 10);

        gbc.gridx = 0;
        gbc.gridy = 0;
        add(milesLabel, gbc);
        gbc.gridx = 1;
        add(milesSpinner, gbc);

        gbc.gridx = 0;
        gbc.gridy = 1;
        add(kmLabel, gbc);
        gbc.gridx = 1;
        add(kmField, gbc);

        gbc.gridx = 0;
        gbc.gridy = 2;
        add(convertButton, gbc);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        
        int miles = (Integer) milesSpinner.getValue();

        double km = miles * 1.60934;

        //ex 1.12
        kmField.setText(String.format("%.2f", km));
    }

    public static void main(String[] args) {
        DistanceSpinner frame = new DistanceSpinner();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setVisible(true);
    }
}
```
