# SELECT 문
* MySQL에서는 SELECT문을 사용하여 테이블의 레코드를 선택할 수 있습니다.


## 문법

```mysql
SELECT 필드이름
FROM 테이블이름
[WHERE 조건]
```

FROM 절은 레코드를 선택할 테이블의 이름을 명시합니다.
해당 테이블에서 선택하고 싶은 필드의 이름을 SELECT 키워드 바로 뒤에 명시하면 됩니다.
이때 WHERE 절을 사용하면, 선택할 레코드의 조건을 좀 더 상세히 설정할 수 있습니다.


### 테이블의 모든 필드 선택
```mysql
SELECT *
FROM 테이블이름
```

### 특정 조건의 레코드 선택
```mysql
SELECT *
FROM STUDENT
WHERE NAME = '홍길동';
```

### 여러 조건의 레코드 선택
```mysql
SELECT *
FROM STUDENT
WHERE STUDENTID <= 3 AND AdmissionDate > '2021-02-01';
```

### 특정 필드만을 선택

```mysql
SELECT NAME, RoomNum
FROM RESERVATION;
```

### 중복되는 값 제거
```mysql
SELECT DISTINCT NAME
FROM RESERVATION;
```

### 선택한 결과 정렬하기
```mysql
SELECT *
FROM RESERVATION
ORDER BY ReserveDate;
```

### 선택한 결과 정렬하기2
```mysql
SELECT *
FROM RESERVATION
ORDER BY ReserveDate DESC, RoomNum ASC;
```
### 별칭(Alias) 이용하기
```mysql
SELECT 필드이름 AS 별칭
FROM 테이블이름;
```

```mysql
SELECT 필드이름 
FROM 테이블이름 AS 별칭;
```

```






