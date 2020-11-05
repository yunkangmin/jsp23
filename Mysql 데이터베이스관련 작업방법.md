## Mysql 데이터베이스관련 작업방법
- 워크벤치를 실행하고 root 계정으로 접속한 뒤 아래 명령어들을 실행하자.
```sql
-- 데이터 베이스 생성하기
create database chap14 default character set utf8;

--새로운 계정 추가하기
            --계정      호스트                    암호
create user 'jspexam'@'localhost' identified by 'jsppw';
-- 권한 부여하기
--    권한목록          데이터베이스.대상 계정     호스트
-- all privileges는 모든 권한을 부여한다. 
-- chap14.*로 chap14 데이터베이스의 모든 테이블에 모든 권한을 부여한다.
grant all privileges on chap14.* to 'jspexam'@'localhost';

-- 호스트 값이 %이므로 모든 호스트에서 해당 암호로 접근가능하다.
create user 'jspexam'@'%' identified by 'jsppw';
grant all privileges on chap14.* to 'jspexam'@'%';
```
Mysql은 localhost와 다른 호스트를 구분하므로 사용자 계정을 생성할 때에는 localhost용 계정과 외부에서 접근할 때 사용할 계정을 각각 생성해주어야 한다.

아래와 같이 생성한 계정을 연결해보자.
<img src="/picture/그림1.png" />