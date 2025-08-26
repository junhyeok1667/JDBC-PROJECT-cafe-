안녕하세요. 오늘은 Day1에 이어 이제 ui를 만들어 보도록 하겠습니다.<br>
오늘 만들 부분은 아래의 사진과 같은 메인 부분입니다.<br>
<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day2/img.png)

GridLayout()을 이용하여 영역을 나누고 영역마다 JButton()을 생성해주도록 하겠습니다.<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day2/img_1.png)

<br>
각 Button에 대한 Actionlistener은 다음에 추가해보겠습니다!<br>
이렇게 간단하게 코드를 작성하면 아래의 사진처럼 결과물이 나오게 됩니다.<br>
오늘은 간단한 메인부분을 작성해보았습니다.<br>

```java
package ticket_ui;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JPasswordField;



public class main extends JFrame{
	
	public main() {
		setTitle("메인");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container  c = getContentPane();
		//Gridlayout으로 영역나누기
		c.setLayout(new GridLayout(4, 1));
		String menuString[] = {"사용자","관리자","사원등록","종료"};
		JButton btn[] = new JButton[menuString.length];
		
		for(int i = 0; i<btn.length; i++) {
			btn[i] = new JButton(menuString[i]);
			add(btn[i]);
			btn[i].addActionListener(new Action());
		}
		
		
		setSize(300,300);
		setVisible(true);
	}
	class Action implements ActionListener{
		@Override
		public void actionPerformed(ActionEvent e) {
			JButton jbtn = (JButton)e.getSource();
			
			if(jbtn.getText().equals("사용자")) {
				
			}else if(jbtn.getText().equals("관리자")) {
				
			}else if(jbtn.getText().equals("사원등록")) {
				
			}else {
				dispose();
			}
			
		}
	}

	public static void main(String[] args) {
		main m = new main();
	}

}


