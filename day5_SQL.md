# SQL문 문법 정리

>2022년 9월 7일

## 그 외의 응용 문법

### 서브쿼리
> 서브쿼리문은 쿼리문 안에 또 쿼리문이 들어있는 것을 말한다.

  ex) 김경호보다 키가 크거나 같은 사람의 이름과 키 출력

  ```sql
  SELECT name, height FROM usertbl WHERE height > (SELECT height FROM usertbl WHERE Name = '김경호');
  ```
- ANY
  - 서브쿼리의 여러 개의 결과 중 한가지만 만족해도 ok
  - SOME은 ANY와 동일한 의미로 사용
  - ANY(서브쿼리)는 IN(서브쿼리)와 동일한 의미
- ALL
  - 서브쿼리의 결과 중 여러 개의 결과를 모두 만족해야 한다.
- ORDER BY
  - 출력되는 순서를 조절하는 구문
  - 오름차순은 ASC, 내림차순은 DESC를 사용
  - ORDER BY 뒤에 아무것도 쓰지 않으면 기본 오름차순 정렬이 원칙이다.
  ```sql
  SELECT name, height FROM usertbl ORDER BY height DESC, name ASC;
  -- 키가 큰 순서대로 정렬하되, 키가 같은 경우에는 이름 순으로 정렬
  ```
- DISTINCT
  - 중복된 것을 골라서 세기 어려울 때 사용
  - 중복된 것은 하나만 골라서 출력
- LIMIT
  - 일부를 보기 위해 사용
  - 상위 N개만 출력하는 'LIMIT N' 구문 사용
- CREATE TABLE ... SELECT
  - 테이블을 복사해서 사용할 경우 사용한다.
  - 지정한 일부 열만 복사하는 것도 가능
  ```SQL
  CREATE TABLE new_tbl(SELECT 복사할 열 FROM 기존테이블)
  ```
  ---
### GROUP BY 및 HAVING 그리고 집계 함수

- GROUP BY
  - 보통 집계 함수(Aggregate Function)와 함께 사용
  - 효율적인 데이터 그룹화를 위하여 사용
  ```sql
  SELECT userID, SUM(amount) FROM buytbl GROUP BY userID;
  --각 사용자 별로 구매한 개수를 합쳐서 출력
  ```
- AS
  - 가독성을 높히기 위해 사용
  ```SQL
  SELECT userID AS '사용자 아이디', SUM(amount) AS '총 구매 개수' FROM buytbl GROUP BY userID;
  --userID를 '사용자 아이디'라는 별칭으로 지정하였음
  ```
- GROUP BY와 함께 사용되는 집계 함수

    | 함수명| 설명  |
    |---|---|
    | AVG()  | 평균을 구한다  |
    | MIN()  | 최소값을 구한다 |
    | MAX()  | 최대값을 구한다 |
    | COUNT() | 행의 개수를 센다 |
    | COUNT(DISTINCT) | 행의 개수를 센다(중복은 1개만 인정) |
    | STDEV()  | 표준편차를 구한다 |
    | VAR_SAMP()  | 분산을 구한다 |

  ```SQL
  SELECT AVG(amount) AS '평균 구매 개수' FROM buytbl;
  --전체 구매자가 구매한 물품의 개수 평균
  ```
- HAVING절
  - WHERE와 비슷하게 조건 제한하는 것, but 집계 함수에 대해서 조건을 제한하는 것이다.
  - HAVING절은 꼭 GROUP BY절 다음에 나와야 한다(순서 바뀌면 안됨)
  
- ROLLUP
  - 총합 또는 중간 합계가 필요한 경우 사용
  - GROUP BY절과 함께 WITH ROLLUP문 사용
  ```SQL
  SELECT num, groupName, SUM(price * amount) AS '비용'
    FROM buytbl
    GROUP BY groupName,num
    WITH ROLLUP; -- 분류(groupName)별로 합계 및 합계들의 총합 구하기
  ```
### 데이터의 변경을 위한 SQL문

- INSERT
  - 데이터의 삽입 시 사용
    ```SQL
    INSERT [INTO] 테이블[(열1, 열2, ...)] VALUES(값1, 값2);
    ```
  - 테이블 이름 다음에 나오는 열 생략 가능
  - INSERT INTO ... SELECT 구문 사용하여 다른 테이블의 데이터를 가져와 대량으로 입력하는 효과를 가질 수 있다
- UPDATE
  - 기존에 입력되어 있는 값 변경하는 구문
  ```SQL
  UPDATE 테이블이름
    SET 열1=값1, 열2=값2 ...
    WHERE 조건;
  ```
  - WHERE절 생략 가능하나, 생략하면 테이블의 전체 행의 내용을 변경한다. 그러므로 웬만하면 빼먹지 말기
- DELETE FROM
  - 행 단위로 데이터 삭제하는 구문
  - 마찬가지로 WHERE절 없으면 데이터 전체를 삭제함




