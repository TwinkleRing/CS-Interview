# 조인(JOIN)
#### JOIN은 데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현해 줍니다.</br>
#### 이러한 JOIN은 보통 SELECT문과 함께 자주 사용됩니다.

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN

### JOIN(INNER JOIN, CROSS JOIN)

> 예제
* Reservation 테이블의 Name 필드와 Customer 테이블의 Name 필드가 서로 일치하는 레코드만을 INNER JOIN으로 가져오기.</br>

```mysql
SELECT *
FROM RESERVATION
(INNER) JOIN CUSTOMER
ON RESERVATION.NAME = CUSTOMER.NAME;
```

#### 실행결과
</br>

![JOIN](https://user-images.githubusercontent.com/43642411/109752440-beb27c80-7c23-11eb-8c80-0aa923fa1b3c.PNG)
