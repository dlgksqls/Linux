1. 
- sudo apt-get install python-software-properties <br>
- sudo LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php
- sudo apt-get update <br> 
- sudo apt install php7.4 php7.4-xml php7.4-xml php7.4-mysql php7.4-mbstring php-xml -- php설치
2. sudo apt install apache2 --apache 설치
3. 
- sudo apt install mysql-server --데이터베이스 설정<br>
- sudo mysql_secure_installation
- mysql -u root -p / mysql에 들어가서 데이터베이스 설정
- CREATE USER 'ojs_user'@'localhost' IDENTIFIED BY 'ojs_user_password'; / 데이터베이스 사용자 생성
- CREATE DATABASE `ojs_database`; / 데이터베이스 생성
- GRANT ALL PRIVILEGES ON ojs_database . * TO 'ojs_user'@'localhost'; / 생성된 사용자에게 권한 부여
- FLUSH PRIVILEGES /저장
4. ojs 다운 및 apache 파일에 연동
- apache 파일위치 /var/www/
- ojs홈페이지에서 최신 버전의 ojs.tar.gz 다운받은 후 sudo tar -zxvf로 압축 해제 (압축해제 후 파일 이름 ojs로)
- sudo mv ojs /var/www/ (압축 해제 후 아파치 파일 폴더로 이동)
- sudo chown www-data:www-data -R /var/www/ 쓰기권한 주기
- sudo cp /var/www/ojs/config.TEMPLATE.inc.php /var/www/ojs/config.inc.php // ojs파일에 있는 샘플 템플릿 php 파일을 복사
- sudo nano /var/www/ojs/config.inc.php <br>
<code>
;;;;;;;;;;;;;;;;;;;;;
; Database Settings ;
;;;;;;;;;;;;;;;;;;;;;

[database]

driver = mysql
host = localhost
username = ojs_user
password = ojs_user_password
name = ojs_database

</code>
//ojs파일과 내가 만들었던 데이터베이스 연결

- sudo service apache2 restart 아파치 서버 재시작
- 127.0.0.1/ojs 로 접속!