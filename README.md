## Ctrl 누르고  => <a href='http://ec2-3-36-55-158.ap-northeast-2.compute.amazonaws.com' target="_blank" rel="noopener">Flask-library</a>

### 👉 주요 사용 기술은 아래와 같습니다.  

Flask  
Flask-SQLAlchemy   
javascript  
MySQL  
HTML + Flask Jinja2  

### 👉 핵심 기능

* 로그인 / 로그아웃  
* 회원가입  
* 책 대여/반납  
* 책 평점/댓글 남기기

### Tree 구조
```
lib/  
┣ static/  
┃ ┣ css/  
┃ ┣ img/  
┃ ┗ js/  
┣ templates/  
┃ ┣ base.html           
┃ ┣ book_info.html  
┃ ┣ checkin.html  
┃ ┣ login.html  
┃ ┣ main.html  
┃ ┣ register.html  
┃ ┗ rental_log.html  
┣ app.py  
┣ form.py  
┣ models.py  
┣ pyvenv.cfg  
┗ requirements.txt 
```

### 2021-09-09 업데이트 내용  
⏰ 웹페이지를 만들면서 느낀점
1. Python 3에서는 암묵적인 상대경로 import가 안된다는 것  
해결 방법 : 절대경로를 사용한다.   
😭 해결 방법과 원인을 파악하고 이해하는데 너무 오래걸렸다. 그래도 이제는 더 천천히 자료를 찾아보고, 찾은 자료들을 참고하여 하나씩 실행하면서 이해하고 경험을 습득하고 있다.  

2. MySQL Workbench에서 테이블에 직접 엑셀 데이터를 copy and paste 하려는데, columns가 1개 없다?  
해결 방법 : 엑셀 시트에서 Ctrl + F -> 찾을 내용에 Ctrl + j -> 모두 바꾸기 누르기  
🤬 개행 문자가 있을 거라고는 생각을 못했다. 웹페이지에 사용되는 엑셀 데이터가 작아서 수기로 입력 해도 되지만, 만약 1억개가 넘는 데이터라면...이라는 상상으로 원인을 찾고 해결을 했다...기가 빨린다...  

3. flask를 실행한 상태에서 ORM을 사용하여 print를 하면 id 값만 보여준다.   
해결 방법 : __repr__ 로 어떤 모습으로 출력할지 정해줄 수 있다.  
출력 값을 보고, 왜 이렇게 나오지? 다 보이면 좋지 않나? 라는 물음에 자료를 찾았다.

4. SQLAlchemy 와 Flask-SQLAlchemy는 다르다.  
해결 방법 : 내가 무엇을 쓰고 있는지 정확하게 알고 문서를 보자  
멍청하게도 위 2개가 같은 것으로 인지하고 사용법을 찾았다. 이 코드는 되고, 저 코드는 안되고, 너무 화가났다. 맞는데!?!! 왜 ... 아... 다르다. 2개는 다르다... 내가 2개를 섞어서 썼구나...  

5. flask db migrate 명령 후, "Table '~~~' already exists" 라는 에러 메세지가 보인다.  
해결 방법 : __tablename__ = '소문자' MySQL은 대소문자를 가린다.  
몰랐다. 처음에 flask db init부터 migrate -> upgrade까지 잘 되서 몰랐다. 테이블 혹은 컬럼을 고치고 다시 하려니 에러가 보인다. 아... 몇번이나 테이블을 지웠다가 다시 만들었는데...ㅂㄷㅂㄷ  

6. azure vm에서 mysql을 설치 했다. 로컬에서 사용하던 mysql을 서버로 그대로 옮길 수 있지 않을까?  
해결 방법 : 로컬 db를 .sql파일로 만들어서 vm으로 옮긴 후 mysql에 import 했다.  
다행이다. 수기로 작성했으면, 개발자를 그만 둬야 할 느낌이었다...  
