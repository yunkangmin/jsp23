## 예제 실행을 위한 데이터베이스 생성
- Mysql 5.7.16을 사용한다.
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


```sql
-- engine=InnoDB은 mysql에서 사용되는 구문이다. 테이블을 InnoDB라는 저장엔진을 사용해서 생성한다는 것을 의미한다. 트랜잭션을 올바르게 처리하기 위해 사용한다.
create table member (
	memberid varchar(10) not null primary key,
    password varchar(10) not null,
    name varchar(20) not null,
    email varchar(80)
) engine=InnoDB default character set = utf8;

insert into member(memberid, password, name)
	values('madvirus', '1234', '최범균');
    
insert into member
	values('eral13', '5678', '최범균', 'madvirus@madvirus.net');

commit;
```