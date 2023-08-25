# ERD

**Entity Relation Dtagram ?** 개체들 간의 관계를 보기 위해 나타낸 다이어그램

- 전체 업무 및 **데이터 구조 쉽게 파악** 가능
- 업무의 **파악과 이해가 용이**

### **Entity**

---

- 개체
- 테이블

### **Attribute**

---

- entity가 가지고 있는 특징
- 각 테이블의 컬럼
- 구성
  - attribute 특성을 나타내는 이름(→컬럼 이름)
  - 데이터 타입(varchar, int 등)

> **- 숫자**

- 정수 : `tinyint()` ,`smallint()` , `mediumint()`, `int()`, `bigint()`
- 실수 : `decimal()`, `double()`, `float()`

**- 문자 -** `varchar()` : various character의 약자
**-** `char()`

**- 날짜, 시간**

- `date()` : 1000-01-01 ~ 9999-12-31
  **-** `datetime()` : 1000-01-01 00:00:00.000000 ~ 9999-12-31 23:59:59.999999
- `timestamp()` : `datetime()` + `timezone`
  >

### Relationship

---

- **PK(Primary Key)**
  - 주 식별자
  - 테이블을 대표하는 키
  - 한 entity 안에 PK는 2개 이상 존재 불가능
  - PK에는 중복 없음
  - 각 레코드마다 unique 하게 갖는 키
- **FK(Foreign Key)**
  - 외부 식별자
  - 다른 entity의 PK에서 참조됨
- PK와 FK의 관계를 통해 두가지 이상 **entity 사이의 관계 정의** 가능
  - Customers(entity) - Orders(entity)
  - one - many
  - 고객 한명당 여러건의 주문이 있을 수 있음

### ERD 표기법

---

1. **ERD 관계 표기법**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e87604a-a288-4489-9cda-54fe982300d1/Untitled.png)

1. **1:1 식별관계**

ex) 주민 - 주소 관계

1. **1:N 참조필수**

ex) 부서 - 회사원 관계

- 회사원은 한개의 부서에 반드시 소속되어야 함
- 한 개의 부서에 여러 회사원 소속 가능

1. **1:N 참조 NULL허용**

ex) 부서 - 회사원

- 회사원이 꼭 부서에 소속될 필요 없음
- 한 개의 부서에 여러 회사원 소속 가능
- 한개의 부서에 소속된 회사원 없을 수도 있음

1. **비식별 관계 & 식별 관계**

1) 비식별 관계 : 기본키에 외래키가 포함되어 있지 않음 (→ **점선**으로 표현)

2) 식별 관계 : 기본키에 외래키가 포함되어 있음 (→ **실선**으로 표현)
