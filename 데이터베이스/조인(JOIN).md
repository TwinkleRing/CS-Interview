# 조인(JOIN)
#### JOIN은 데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현해 줍니다.</br>
#### 이러한 JOIN은 보통 SELECT문과 함께 자주 사용됩니다.

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN

### JOIN(INNER JOIN, CROSS JOIN)

#### 예제
* Reservation 테이블의 Name 필드와 Customer 테이블의 Name 필드가 서로 일치하는 레코드만을 INNER JOIN으로 가져오기.</br>

```mysql
SELECT *
FROM RESERVATION
(INNER) JOIN CUSTOMER
ON RESERVATION.NAME = CUSTOMER.NAME;
```

```mysql
SELECT *
FROM RESERVATION, CUSTOMER
WHERE RESERVATION.NAME = CUSTOMER.NAME;
```
#### 실행결과

![JOIN](https://user-images.githubusercontent.com/43642411/109753268-4ea4f600-7c25-11eb-8e0a-d6eba1afaece.PNG)

---

### LEFT JOIN
LEFT JOIN은 첫번째 테이블을 기준으로, 두번째 테이블을 조합하는 JOIN 입니다.
이때 ON 절의 조건을 만족하지 않는 경우에는 첫 번째 테이블의 필드 값을 그대로 가져옵니다.
하지만 해당 레코드의 **두 번째 테이블의 필드 값을 모두 NULL로 표시됩니다.**

#### 예제
* Reservation 테이블의 Name 필드를 기준으로 Customer 테이블의 Name 필드와 일치하는 레코드만을 LEFT JOIN 으로 가져온 후,</br>
* 그 중에서 ReserveDate 필드의 값이 2016년 02월 01일 이후인 레코드만을 선택하는 예제 </br>

```mysql
SELECT *
FROM RESERVATION
LEFT JOIN CUSTOMER
ON RESERVATION.NAME = CUSTOMER.NAME
WHERE RESERVEDATE > '2021-02-01';
```

#### 벤 다이어그램으로 나타낸 LEFT JOIN의 결과

![img_mysql_left_join](https://user-images.githubusercontent.com/43642411/109753200-2d440a00-7c25-11eb-9cf0-fafc80c07956.png)

---

### RIGHT JOIN
RIGHT JOIN은 LEFT 조인과는 반대로 두 번째 테이블을 기준으로, 첫 번째 테이블을 조합하는 JOIN입니다.
이때 ON 절의 조건을 만족하지 않는 경우에는 두 번째 테이블의 필드 값을 그대로 가져옵니다.
하지만 해당 레코드의 **첫 번째 테이블의 필드 값을 모두 NULL로 표시됩니다.**

#### 예제
* Customer 테이블의 Name 필드를 기준으로 Reservation 테이블의 Name 필드와 일치하는 레코드만을 RIGHT JOIN 으로 가져오는 예제</br>

```mysql
SELECT *
FROM RESERVATION
RIGHT JOIN CUSTOMER
ON RESERVATION.NAME = CUSTOMER.NAME;
```

#### 벤 다이어그램으로 나타낸 RIGHT JOIN의 결과

![img_mysql_right_join](https://user-images.githubusercontent.com/43642411/109753608-e9053980-7c25-11eb-9aa1-ff6850e7dbb0.png)
