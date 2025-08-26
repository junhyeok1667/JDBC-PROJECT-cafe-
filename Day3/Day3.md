안녕하세요!<br>
오늘은 아래의 그림과 같이 main폼에서 사용자 버튼을 눌렀을때 생성되는 폼을 만들어보도록 하겠습니다.<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img.png)
<br>

문제를 봤을때 우선 상단에는 JLabel을 붙이고 Center에는 GridLayout()으로 2x2의 크기로 나눈 후 사진을 넣으면 될거 같습니다. <br>
그리고 하단에는 Thread()를 사용하여 현재 시각을 붙으면 될거 같은 생각이 드네요.<br>
하지만 여기서 중요한 점은 조건에 나온것 처럼 툴팁을 사용하는 것과 이미지의 좌측 상단의 메뉴라는 tabbedPane이 새롭게 보입니다. <br>
차근차근 한번 풀어가보도록 하겠습니다!<br>


<br>
1. 상단의 식권발매프로그램 Label을 만들어 보도록 하겠습니다.<br>
<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img_1.png)
<br>

2. 중앙에 음식 사진을 넣어보도록 하겠습니다.<br>
<br>
여기서 tooltip을 사용해야 하는데 tooltip이란 이미지위에 커서가 올라가면 이미지에 대한 정보가 나오게 되는 것입니다.<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img_2.png)
<br>

3. 하단에 Thread를 통해 현재 시간을 나타나도록 하겠습니다.<br>
<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img_3.png)
<br>

4. 마지막으로 JFrame에 tabbedPane을 생성해보도록 하겠습니다.<br>
<br>

우선 tabbedPane이란 여러패널을 탭으로 전환할 수 있는 컴포넌트를 말합니다. tabbedPane을 사용하면 공간을 보다 효과적으로 활용할 수 있습니다.<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img_4.png)

이렇게 코드를 작성 후 실행을 해주면 아래의 그림과 같이 결과가 나오게 됩니다.<br>
<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day3/img_5.png)
<br>
이렇게 Day3 사용자 폼 만들기를 해보았습니다.<br>
다음에는 메뉴에 대한 결제 폼을 만들어 보도록 하겠습니다!<br>

```java
package ticket_ui;

import java.awt.BorderLayout;
import javax.swing.*; 
import java.awt.*; 
import java.awt.Color;
import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.util.Calendar;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JToolBar;
import javax.swing.SwingUtilities;

public class User extends JFrame{
	
	JLabel imageLabel[] = new JLabel[4];
	JLabel jl;
	String menu[] = {"한식","중식","일식","양식"};
	
	public User() {
		setTitle("식권 판매 프로그램");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		
		//좌측 상단의 메뉴에 대한 tabbedPane
		JTabbedPane tabPanel = new JTabbedPane(); 
		tabPanel.addTab("메뉴", new Center()); 
		c.add(tabPanel);

     	
		add(new Top(),BorderLayout.NORTH);// 식권 발매 프로그램
		add(tabPanel,BorderLayout.CENTER);//tabpanel
		add(new Bottom(),BorderLayout.SOUTH);//현재시간에 대한 스레드

		
		setSize(500,800);
		setVisible(true);
		
	}
	
	class Top extends JPanel{
		public Top(){
			JLabel la = new JLabel("식권 발매 프로그램");
			la.setFont(new Font("",Font.BOLD,20));
			add(la);
		}
	}
	
	class Center extends JPanel{
		String name[] = {"menu_1","menu_2","menu_3","menu_4"};
		public Center() {
			setLayout(new GridLayout(2,2));
			//메뉴에 대한 사진 넣기
			for(int i = 0; i<imageLabel.length; i++) {
				imageLabel[i] = new JLabel(new ImageIcon("C:\\Users\\User\\Desktop\\ticket1\\ticket\\DataFiles\\"+name[i]+".png"));
				add(imageLabel[i]);
				//각 이미지에 대한 툴팁 생성
				imageLabel[i].setToolTipText(menu[i]);
			}
			
		}
	}
	
	class Bottom extends JPanel{
		String time;
		
		public Bottom() {
			this.setBackground(Color.black);
			jl = new JLabel(time);
			jl.setFont(new Font("", Font.BOLD,25));
			jl.setBackground(Color.BLACK);
			jl.setForeground(Color.GREEN);
			this.add(jl);
		
			TimeLabel t = new TimeLabel();
			t.start();
		}
		
		//현재시간을 나타내는 스레드
		class TimeLabel extends Thread{
			@Override
			public void run() {
				while(true) {
					Calendar calendar = Calendar.getInstance();
					int year = calendar.get(Calendar.YEAR);
					int month = calendar.get(Calendar.MONTH) + 1;
					int day = calendar.get(Calendar.DAY_OF_MONTH);
					int hour = calendar.get(Calendar.HOUR_OF_DAY);
					int minute = calendar.get(Calendar.MINUTE);
					int second = calendar.get(Calendar.SECOND);
					time = "현재시간: ";
					time = time.concat(Integer.toString(year));
					time = time.concat("년");
					int cal[] = {month,day,hour,minute,second};
					String calKor[] = {"월","일","시","분","초"};
					
					for(int i = 0; i<cal.length;i++) {
						time = time.concat(Integer.toString(cal[i]));
						time = time.concat(calKor[i]);
					}
					jl.setText(time);
				}
				
			}
		}
	}
	public static void main(String[] args) {
		new User();

	}

}

 
