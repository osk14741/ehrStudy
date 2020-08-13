#### Q1.

```SQL
CREATE TABLE tcons (no      NUMBER
                    CONSTRAINT tcons_no_pk      PRIMARY KEY,
                    name    VARCHAR2(20)
                    CONSTRAINT tcons_name_nn    NOT NULL,
                    jumin   VARCHAR2(13)
                    CONSTRAINT tcons_jumin_nn   NOT NULL
                    CONSTRAINT tcons_jumin_uk   UNIQUE,
                    area    NUMBER(1)
                    CONSTRAINT tcons_area_ck    CHECK(area BETWEEN 1 AND 4),
                    deptno  VARCHAR2(6)
                    CONSTRAINT tcons_deptno_fk  REFERENCES dept2(dcode)
                    );
```

- CHECK() 에 BETWEEN 넣을 수 있다.
- 괄호 잘보자



#### Q2.

tcons 테이블의 name 컬럼이 emp2 테이블의 name 컬럼의 값을 참조하도록 참조키 제약 조건을 추가 설정하는 쿼리를 쓰세요.(tcons 테이블이 자식 테이블입니다.)

```sql
ALTER TABLE tcons
ADD CONSTRAINT tcons_name_fk FOREIGN KEY(name)
REFERENCES emp2(name);
```

- ADD CONSTRAINT 할 때는 얘가 어디에 들어있는지 모름.

- ```
  ADD CONSTRAINT 제약조건이름 옵션
  ```



#### Q3.

tcons 테이블의 jumin 컬럼에 만들어져 있는 unique 제약 조건을 "사용 안 함"으로 변경하되 해당 테이블의 데이터에 DML까지 안 되도록 변경하는 쿼리를 쓰세요.(제약 조건 이름은 tcons_jumin_uk 입니다.)

```sql
ALTER TABLE tcons
DISABLE VALIDATE CONSTRAINT tcons_jumin_uk;
```

- VALIDATE : ENABLE하는 시점까지 입력된 데이터, 이후 입력된 데이터 모두 무결성 검사.
- NOVALIDATE : ENABLE하는 시점까지 해당 테이블에 들어 있는 데이터는 검사하지 않고 ENABLE 하는 시점부터 무결성 검사.



#### Q4.

위 3번 문제에서 "사용 안 함"으로 설정한 제약 조건 tcons_jumin_uk을 사용함으로 변경하되 기존에 있던 내용과 새로 들어올 내용 모두를 체크하는 옵션으로 변경하세요. 그리고 문제가 되는 데이터들은 scott.exceptions 테이블에 저장하도록 설정하세요.

```sql
ALTER TABLE tcons
ENABLE VALIDATE CONSTRAINT tcons_jumin_uk
EXCEPTIONS INTO exceptions;
```

