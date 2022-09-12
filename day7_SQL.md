# Python에서 SQL 데이터 다루기

## pymysql
> mysql을 python에서 사용할 수 있는 라이브러리이다. 다양한 라이브러리가 존재하지만 제일 설치하기 쉬움

```python
!pip install pymysql
```

### 순서

1. 라이브러리 가져오기

```python
import pymysql
```

2. 접속하기

```python
db = pymysql.connect(host='localhost',port=3306,user='root',passwd='1234',db='ecommerce',charset='utf8')
# DB를 새로 만드는 경우에는 db는 생략해도 된다
```

3. cursor 가져오기
> 쿼리문에 의해서 반환된 결과값들을 저장하는 메모리 공간

```python
cursor = db.cursor()
```

4. SQL 구문 만들기

```python
sql = '''
    CREATE TABLE product2(
        PRODUCT_CODE VARCHAR(20) NOT NULL,
        TITLE VARCHAR(200) NOT NULL,
        ORI_PRICE INT,
        DISCOUNT_PRICE INT,
        DISCOUNT_PERCENT INT,
        DELIVERY VARCHAR(2),
        PRIMARY KEY(PRODUCT_CODE)
    );
'''
```

5. SQL 구문 실행하기

```PYTHON
cursor.execute(sql)
```

6. DB에 Commit하기

```python
db.commit()
```

7. DB 연결 닫기

```python
db.close() # 빼먹지 않도록 주의할 것
```



