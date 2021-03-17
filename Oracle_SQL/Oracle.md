# Oracle

## 구조

![화면 캡처 2021-03-17 220818](https://user-images.githubusercontent.com/60080744/111472505-5d36f580-876d-11eb-9972-3e6b415ba39f.jpg)

# SQL

## 정의

데이터베이스를 관리하기 위해 설계된 프로그래밍 언어



## 종류

### DDL(데이터 정의어)

데이터 베이스를 정의하는 언어, 생성, 수정 , 삭제 등 전체적인 골격을 결정

- CREATE : 생성
- ALTER : 수정
- DROP : DB, 테이블 삭제
- TRUNCATE : 테이블 초기화



### DML(데이터 조작어)

정의된 데이터베이스에 입력된 레코드를 조회하거나 수정하거나 삭제하는 역할

테이블에 있는 행과 열을 조작하는 언어

- SELECT : 데이터 조회
- INSERT :  데이터 삽입
- UPDATE :  데이터 수정
- DELETE : 데이터 삭제



### DCL(데이터 제어어)

데이터베이스에 접근하거나 객체에 권한을 주는 등의 역할

- GRANT :  특정 데이터베이스 사용자에게 특정 작업에 대한 수행권한 부여
- REVOKE :  특정 데이터베이스 사용자에게 특정 작업에 대한 권한 박탈, 회수
- COMMIT : 트랜잭션의 작업이 정상적으로 완료되었음을 알려준다
- ROLLBACK : 트랜잭션이 작업이 비정상적으로 종료 되었을 때 원래의 상태로 복구
  - 단, COMMIT를 ROLLBACK전에 실행하면 ㄷ안된다.



## 문자셋

### ISO-8859-1

아스키코드(특수문자, 숫자, 알파벳), 1byte



### EUC-KR

MS949와 같음, iso-8859-1 + 한글(2byte로 표현)



### UTF-8

iso-8859-1 + 한글(3byte로 표현) + 기타언어



### UTF-16

iso-8859-1(2byte) + 모든언어(2byte)

8, 16은 비트수를 나타낸다



## 속성(열) 타입

### 문자

- VARCHAR 2: 가변, 4000byte 
- CHAR : 고정
- CLOB :  가변, 4Gbyte



### 숫자

- NUBMER



### 이미지

- BLOB



## primary key

PK를 설정하는 방법

```mysql
-- 첫번째
userid varchar(20) not null primary key

-- 2번째
userid varchar(20) not null
constraints pk_userid primary key (userid)

-- 3번째
userid varchar(20) not null

alter table users
    add constraint pk_userid primary key (userid);
```

