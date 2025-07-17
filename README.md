# TemperatureConverter
#Level-1 Task-1
import javax.swing.*;
import java.awt.event.*;

public class TemperatureConverter extends JFrame {
    private JTextField tempInputField;
    private JComboBox<String> conversionBox;
    private final JButton convertButton;
    private JLabel resultLabel;

    public TemperatureConverter() {
        setTitle("Temperature Converter");
        setSize(400, 250);
        setLayout(null);
        setDefaultCloseOperation(EXIT_ON_CLOSE);

        JLabel enterTempLabel = new JLabel("Enter Temperature:");
        enterTempLabel.setBounds(30, 30, 150, 25);
        add(enterTempLabel);

        tempInputField = new JTextField();
        tempInputField.setBounds(180, 30, 150, 25);
        add(tempInputField);

        JLabel conversionLabel = new JLabel("Convert To:");
        conversionLabel.setBounds(30, 70, 100, 25);
        add(conversionLabel);

        String[] options = {"Celsius to Fahrenheit", "Fahrenheit to Celsius"};
        conversionBox = new JComboBox<>(options);
        conversionBox.setBounds(180, 70, 180, 25);
        add(conversionBox);

        convertButton = new JButton("Convert");
        convertButton.setBounds(140, 110, 100, 30);
        add(convertButton);

        resultLabel = new JLabel("");
        resultLabel.setBounds(30, 160, 300, 30);
        add(resultLabel);

        convertButton.addActionListener((ActionEvent e) -> {
            try {
                double inputTemp = Double.parseDouble(tempInputField.getText());
                String conversionType = (String) conversionBox.getSelectedItem();
                double resultTemp;
                
                if (conversionType.equals("Celsius to Fahrenheit")) {
                    resultTemp = (inputTemp * 9 / 5) + 32;
                    resultLabel.setText(String.format("Result: %.2f °F", resultTemp));
                } else {
                    resultTemp = (inputTemp - 32) * 5 / 9;
                    resultLabel.setText(String.format("Result: %.2f °C", resultTemp));
                }
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(null, "Please enter a valid number!");
            }
        });

        setVisible(true);
    }

    public static void main(String[] args) {
        new TemperatureConverter();
    }
}
