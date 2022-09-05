# SQL문 문법 정리

>2022년 8월 31일

## SELECT문
> 원하는 데이터를 가져와 주는 기본적인 구문이자 가장 많이 사용된다.

```sql
SELECT 열 이름 FROM 테이블 이름 WHERE 조건 --가장 많이 쓰이는 형태
```

### SELECT *
> 선택한 DB가 employees라면 다음 두 쿼리는 동일
```sql
SELECT * FROM employees.titles;
SELECT * FROM titles;
```

### SELECT 열 이름

- 테이블에서 필요로 하는 열만 가져오기 기능
  ```SQL
  SELECT first_name FROM employees;
  ```
- 여러 개의 열을 가져오고 싶을 때는 콤마로 구분
  ```SQL
  SELECT first_name,last_name,gender FROM employees;
  ```

## USE문
> SELECT문 학습 위해 사용할 데이터베이스 지정
```SQL
USE 데이터베이스_이름;
```

## 특정 조건의 데이터 조회
> SELECT ... FROM ...WHERE 형식을 사용 

- 기본적인 WHERE절
  - 조회하는 결과에 특정한 조건을 줘서 원하는 데이터만 보고 싶을 때
  - SELECT 필드이름 FROM 테이블이름 WHERE 조건식;
  ```SQL
  SELECT * FROM usertbl WHERE name = '김경호';
  ```
- 관계 연산자의 사용
  - OR 연산자 : 조건들 중 하나만 만족하면 TRUE
  - AND 연산자 : 모든 조건들이 만족해야만 TRUE
  ```SQL
  SELECT userID, Name FROM usertbl WHERE birthYear >=1970 AND height >=182;
  ```
- BETWEEN ... AND와 IN() 그리고 LIKE
  - 데이터가 숫자로 구성되어 있으며 연속적일 때 BETWEEN...AND 사용
  ```SQL
  SELECT name,height FROM usertbl WHERE height BETWEEN 180 AND 183;
  ```
  - 이산적인(Discrete) 값의 조건 : IN() 사용
  ```SQL
  SELECT name, addr FROM usertbl WHERE addr IN('경남','전남','경북');
  ```
  - 문자열의 내용 검색 : LIKE 사용(문자 뒤에 % - 무엇이든 허용, 한 글자와 매치 '_' 사용)
  ```SQL
  SELECT name, height FROM usertbl WHERE name LIKE '김%';
  ``` 


