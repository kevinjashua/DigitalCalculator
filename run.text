import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;

public class DigitalCalculator extends JFrame {
    private JTextField display;
    private double num1, num2, result;
    private char operator;

    public DigitalCalculator() {
        setTitle("Digital Calculator");
        setSize(400, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        display = new JTextField();
        display.setFont(new Font("Arial", Font.PLAIN, 24));
        display.setHorizontalAlignment(JTextField.RIGHT);
        display.setEditable(false);
        display.setPreferredSize(new Dimension(400, 50));
        add(display, BorderLayout.NORTH);

        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(5, 4, 10, 10));
        String[] buttons = {
            "7", "8", "9", "/",
            "4", "5", "6", "*",
            "1", "2", "3", "-",
            "0", ".", "=", "+",
            "C", "√", "%", "1/x"
        };

        for (String text : buttons) {
            JButton button = new JButton(text);
            button.setFont(new Font("Arial", Font.PLAIN, 20));
            button.addActionListener(new ButtonClickListener());
            panel.add(button);
        }

        add(panel, BorderLayout.CENTER);
    }

    private class ButtonClickListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            String command = e.getActionCommand();

            if (command.charAt(0) >= '0' && command.charAt(0) <= '9' || command.equals(".")) {
                display.setText(display.getText() + command);
            } else if (command.equals("C")) {
                display.setText("");
                num1 = num2 = result = 0;
            } else if (command.equals("=")) {
                num2 = Double.parseDouble(display.getText());
                switch (operator) {
                    case '+': result = num1 + num2; break;
                    case '-': result = num1 - num2; break;
                    case '*': result = num1 * num2; break;
                    case '/': result = num1 / num2; break;
                }
                display.setText(String.valueOf(result));
            } else if (command.equals("√")) {
                num1 = Double.parseDouble(display.getText());
                display.setText(String.valueOf(Math.sqrt(num1)));
            } else if (command.equals("%")) {
                num1 = Double.parseDouble(display.getText());
                display.setText(String.valueOf(num1 / 100));
            } else if (command.equals("1/x")) {
                num1 = Double.parseDouble(display.getText());
                display.setText(String.valueOf(1 / num1));
            } else {
                num1 = Double.parseDouble(display.getText());
                operator = command.charAt(0);
                display.setText("");
            }
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> new DigitalCalculator().setVisible(true));
    }
}