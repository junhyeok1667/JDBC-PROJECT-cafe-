안녕하세요!! 오늘은 저번에 만든 사진버튼을 눌렀을때 결제 폼을 만들어 보도록 하겠습니다.<br>
<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img.png)

여기서 생각해볼 문제가 있습니다. 저희가 만든 사진버튼은 총 4개(한식, 일식, 중식, 양식)입니다.<br>
위의 사진과 같은 결제폼을 4가지 다 만들어야 할까요? 전부 음식종류에 따른 메뉴만 다르고 나머지 부분은 같을 것입니다. 그래서 Day3에 만든 코드에 각 사진 버튼에 ActionListener를 만들어 각 사진을 눌렀을때 매개변수를 넘겨 매개변수를 통해 결제 폼을 만들면 될 것 입니다.<br>
<br>
아래의 사진과 같이 Day3코드에  아래의 코드를 추가해 줍니다.<br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_1.png)

이제 본격적으로 결제 폼을 만들어 보도록 하겠습니다.<br>
<br>
<br>1. 매개변수를 통해 생성자를 만들기
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_2.png)
<br>
<br>2. 상단의 음식종류와 총 결제금액 Label 생성<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_3.png)
<br>
<br>3. 음식 종류에 따른 메뉴 버튼 만들기<br>
매개변수를 통해 지금 어떤 음식종류에 대한 결제 폼인지 확인 후 Mysql과 연동하여 Mysql의 데이터를 통해 메뉴버튼클래스를 통해 메뉴버튼을 만들도록 하겠습니다. <br>
메뉴버튼 클래스를 먼저 만들어보겠습니다.<br>
각 메뉴에는 메뉴 이름, 메뉴 가격, 최대수량, 메뉴번호, 오늘의 메뉴 확인 숫자가 필요합니다. Mysql을 통해 데이터를 읽을때마다 정보를 저장해야 하기에 Vector을 사용하였습니다.<br>
<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_4.png)

<br>Mysql의 데이터를 읽어 메뉴버튼을 만드는 코드를 작성해보겠습니다.<br>
![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_5.png)

결제 폼의 예시 이미지를 보면 5행으로 만들어지기에 5행으로 만들었습니다. <br>

![실행 결과](https://github.com/junhyeok1667/JDBC-PROJECT-cafe-/blob/main/Day4/img_6.png)

<br>
이렇게 코드를 작성 후 실행을 시켜주면 아래의 영상과 같이 작동하게 됩니다.<br>

[![영상 보기](Day4.png)](https://tv.kakao.com/v/448630352)<br>


코드에 부분은 아직 결제 폼이 완성이 아니기에 완성이 되면 한번에 올리겠습니다!!<br>
