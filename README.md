import javax.swing.*;
‎import java.awt.*;
‎import java.awt.event.*;
‎
‎public class Calculator extends JFrame implements ActionListener {
‎   
‎    private JTextField textField;
‎    private double num1, num2, result;
‎    private char operator;
‎
‎    public Calculator() {
‎        
‎        setTitle("Simple Calculator");
‎        setSize(300, 400);
‎        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
‎        setLayout(new BorderLayout());
‎
‎        
‎        textField = new JTextField();
‎        textField.setEditable(false);
‎        textField.setFont(new Font("Arial", Font.BOLD, 20));
‎        add(textField, BorderLayout.NORTH);panel.setLayout(new GridLayout(4, 4, 10, 10));
‎
‎        String[] buttons = {
‎            "7", "8", "9", "/",
‎            "4", "5", "6", "*",
‎            "1", "2", "3", "-",
‎            "0", "C", "=", "+"
‎        };
‎
‎        for (String text : buttons) {
‎            JButton button = new JButton(text);
‎            button.setFont(new Font("Arial", Font.BOLD, 18));
‎            button.addActionListener(this);
‎            panel.add(button);
‎        }
‎
‎        add(panel, BorderLayout.CENTER);
‎        setVisible(true);
‎    }
‎
‎    public void actionPerformed(ActionEvent e) {
‎        String command = e.getActionCommand();command.charAt(0) <= '9')) {
‎            textField.setText(textField.getText() + command);
‎        } else if (command.charAt(0) == 'C') {
‎            textField.setText("");
‎            num1 = num2 = result = 0;
‎        } else if (command.charAt(0) == '=') {
‎            num2 = Double.parseDouble(textField.getText());
‎
‎            switch (operator) {
‎                case '+': result = num1 + num2; break;
‎                case '-': result = num1 - num2; break;
‎                case '*': result = num1 * num2; break;
‎                case '/': 
‎                    if (num2 != 0) result = num1 / num2; 
‎                    else {
‎                        textField.setText("Error");
‎                        return;
‎                    }
‎                    break;
‎            }
‎            textField.setText(String.valueOf(result));Double.parseDouble(textField.getText());
‎            operator = command.charAt(0);
‎            textField.setText("");
‎        }
‎    }
‎
‎    public static void main(String[] args) {
‎        new Calculator();
‎    }
‎}
