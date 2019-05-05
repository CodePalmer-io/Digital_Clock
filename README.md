# Digital_Clock
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.SimpleDateFormat;
import java.util.Date;


public class Clock extends JFrame {

    public static void main(String args [])
    {
        JFrame frame = new JFrame("Digital Clock");
        frame.getContentPane().setBackground(Color.BLACK);
        frame.setSize(300,200);
        frame.setLayout(new GridLayout(3,1));
        Label dateLabel = new Label();

        frame.add(dateLabel.getTODAY_DAY());
        frame.add(dateLabel.getTODAY_TIME());
        frame.add(dateLabel.getTODAY_DATE());


        frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }

}

class Label extends JLabel implements ActionListener
{
    private JLabel TODAY_TIME = new JLabel();
    private JLabel TODAY_DATE = new JLabel();
    private JLabel TODAY_DAY = new JLabel();
    SimpleDateFormat sdf;
    Timer timer;

    public Label()
    {
        timer = new Timer(1000, this);
        timer.setRepeats(true);
        timer.start();
    }


    public void actionPerformed(ActionEvent ae)
    {

        Date DATE = new Date();
        sdf = new SimpleDateFormat("MMMM dd, yyyy");
        String date =  sdf.format(DATE);
        TODAY_DATE.setFont(new Font("TimesRoman", Font.PLAIN, 20));
        TODAY_DATE.setText(date);
        TODAY_DATE.setHorizontalAlignment(SwingConstants.RIGHT);
        TODAY_DATE.setForeground(Color.CYAN);

        Date TIME = new Date();
        sdf = new SimpleDateFormat("HH:mm:ss a");
        String time = sdf.format(TIME);
        TODAY_TIME.setFont(new Font("TimesRoman", Font.BOLD, 40));
        TODAY_TIME.setText(time);
        TODAY_TIME.setHorizontalAlignment(SwingConstants.CENTER);
        TODAY_TIME.setForeground(Color.CYAN);

        Date DAY = new Date();
        sdf = new SimpleDateFormat("EEEE   ");
        String Day = sdf.format(DAY);
        TODAY_DAY.setFont(new Font("TimesRoman", Font.PLAIN, 20));
        TODAY_DAY.setText(Day);
        TODAY_DAY.setHorizontalAlignment(SwingConstants.LEFT);
        TODAY_DAY.setForeground(Color.CYAN);

    }

    public JLabel getTODAY_TIME()
    {
        return TODAY_TIME;
    }

    public  JLabel getTODAY_DATE()
    {
        setForeground(Color.cyan);
        return TODAY_DATE;
    }

    public JLabel getTODAY_DAY()
    {
        return TODAY_DAY;
    }

}
