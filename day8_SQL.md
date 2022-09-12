# pymysql 실습

## 데이터 삽입(INSERT)
- Cursor Object 가져오기: cursor = db.cursor()
- SQL 실행하기: cursor.execute(SQL)
- 실행 mysql 서버에 확정 반영하기: db.commit()

```python
import pymysql

db = pymysql.connect(host='localhost',port=3306,user='root',passwd='1234',db='ecommerce',charset='utf8')

cursor = db.cursor() # mysql 접속 후 cursor 가져오기
```

```python
for index in range(10):
    product_code = 216573140 + index + 1
    sql = """INSERT INTO product2 VALUES(
    '""" + str(product_code)+  """', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); """
    print(sql)
    cursor.execute(sql)
```


INSERT INTO product2 VALUES(
    '216573141', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573142', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573143', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573144', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573145', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573146', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573147', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573148', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573149', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 

INSERT INTO product2 VALUES(
    '216573150', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'); 




```python
db.commit() # 입력된 데이터를 db서버에 확정시키기

db.close() # 연결 종료
```
---
## 데이터 조회(SELECT)

- Cursor Object 가져오기: cursor = db.cursor()
- SQL 실행하기: cursor.execute(SQL)
- mysql 서버로부터 데이터 가져오기: fetch 메서드 사용
  - fetchall(): Fetch all the rows
  - fetchmany(size=None): Fetch several rows
  - fetchone(): Fetch the next row

```python
import pymysql

db = pymysql.connect(host='localhost',port=3306,user='root',passwd='jimkwon95',db='ecommerce',charset='utf8')
cursor = db.cursor()

sql = "select * from product2"
cursor.execute(sql)
```
10

```python
result = cursor.fetchone() # 현재 커서를 다음 레코드로 이동시키고 해당 레코드를 반환
result
```
('216573141', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F')

```python
result = cursor.fetchall()
result
```
(('216573142', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573143', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573144', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573145', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573146', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573147', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573148', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573149', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'),

 ('216573150', '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'))

 ```python
 db.close()
 ```
 ---
 ## 데이터 수정(UPDATE)
 - Cursor Object 가져오기: cursor = db.cursor()
 - SQL 실행하기: cursor.execute(SQL)
 - 실행 mysql 서버에 확정 반영하기: db.commit()

```python
import pymysql

db = pymysql.connect(host='localhost',port=3306,user='root',passwd='1234',db='ecommerce',charset='utf8')

cursor = db.cursor()

sql = """
UPDATE product2 SET 
    TITLE='하늘하늘 원피스 썸머 스페셜 가디건', 
    ORI_PRICE=33000, 
    DISCOUNT_PRICE=9900, 
    DISCOUNT_PERCENT=70 
    WHERE PRODUCT_CODE='216573141';
"""

cursor.execute(sql)

db.commit()
```

```python
# update 확인

sql = "select * from product2 where product_code='216573141';"

cursor.execute(sql)

result = cursor.fetchone()
result
```
('216573141', '하늘하늘 원피스 썸머 스페셜 가디건', 33000, 9900, 70, 'F')

```python
db.close()
```
---
## 데이터 삭제(DELETE)

- Cursor object 가져오기: db.cursor()
- SQL 실행하기: cursor.execute(SQL)
- 실행 mysql 서버에 확정 반영하기: db.commit()

```python
import pymysql

db = pymysql.connect(host='localhost',port=3306,user='root',passwd='jimkwon95',db='ecommerce',charset='utf8')

cursor = db.cursor()

sql = "DELETE FROM product WHERE PRODUCT_CODE='216573141';"
cursor.execute(sql)
db.commit()
db.close()
```

```python
# 잘 삭제되었나 확인하기

db = pymysql.connect(host='localhost',port=3306,user='root',passwd='jimkwon95',db='ecommerce',charset='utf8')
cursor = db.cursor()
sql = """select * FROM product WHERE PRODUCT_CODE='216573141'"""

cursor.execute(sql)

result = cursor.fetchone()
print(result)

db.commit()

db.close()
```
None