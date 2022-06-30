### 관계형 데이터베이스( Relational DataBase )란?

<br/>

관계형 데이터 베이스는 데이터를 **테이블 형태로 저장**한다.  <br/>
쉽게 생각하면 엑셀 표에 데이터를 저장하는 것과 동일하다고 보면된다. <br/>
실제로 각 데이터 항목들은 행(row)에 저장되고, 항목의 속성은 열(column)이라고 표현한다. <br/>
열은 항목의 속성인 만큼 입력되는 데이터의 유형이 정해진다. <br/>

<br/>

### 관계형 데이터베이스에서의 관계

<br/>

관계형 데이터베이스는 왜 관계라는 이름이 붙여졌을까?

결론부터 말하자면 각 테이블의 **행과 행이 연결되는 관계를 맺을 수 있기 때문**이다. <br/> 
테이블 간의 관계는 **일 대 일(1:1)**, **일 대 다(1:N)**, **다 대 다(N:N)** 의 관계가 있다. <br/>
우리는 하나의 테이블에 필요한 모든 필드를 넣고 모든 데이터 항목을 저장할 수 있다. <br/>
하지만 이렇게하면 데이터들이 중복해서 저장되는 상황이 발생할 수 있어 다음 그림 테이블과 같이 비효율적이다. 

<br/>

고객의 상품 주문을 저장하는 테이블이 있다고 가정하면 특정 고객이 여러 상품을 구매하는 경우 고객 이름과 고객 지역 데이터가 계속 해서 중복된다. <br/>
얼핏보기에는 별 문제 없어보이지만 만약에 고객의 지역이 변경된다고 생각해보자. <br/>
그림은 데이터가 3개 뿐이지만 만약 수십, 수백만 그 이상의 데이터라면 쉬운일이 아니다. <br/>
그래서 관계형 데이터베이스 모델에서는 다음 그림과 같이 테이블을 분리하여 행과 행을 연결할 수 있다.


![image](https://user-images.githubusercontent.com/78454649/176692469-73090f20-42d6-4e2c-8699-3f80c9eef340.png)


그림과 같이 테이블 간의 관계는 기본 키(primary key) 와 외래 키(foreign key) 라는 개념을 사용하여 맺어질 수 있다. <br/> 
기본 키는 고유한 ID 필드로 그림에서는 고객 번호 필드이다. 이 필드는 각 행이 중복된 값을 가질 수 없다. <br/>
외래 키는 기본 키를 참조하는 필드로 그림에서는 주문 테이블의 고객 번호 필드이고 각 테이블의 행을 연결시켜주는 역할을 한다. <br/>
이렇게 테이블을 분리하고 관계를 형성해 데이터를 효율적으로 관리할 수 있다.<br/>
( 테이블을 분리하고 중복 데이터를 제거하는 과정을 정규화 라고 한다.)<br/>


<br/>

### SQL(Structured Query Language) 이란 

<br/>

관계형 데이터베이스에서 주요한 특징 중 하나는 SQL이라는 구조화 질의어를 사용한다는 것이다. <br/>
SQL은 RDBMS에서 사용하는 프로그래밍 언어라고 보면 된다.  <br/>
SQL을 통해 RDBMS에서 데이터를 검색하고, 추가하고, 업데이트하고, 삭제하는 작업 등 데이터를 관리한다.

<br/>

### RDBMS

<br/>

관계형 DBMS는 열이 속성을 나타내고 테이블의 각 행이 레코드를 나타내는 테이블 형식으로 데이터를 저장한다. <br/>
RDBMS는 CRUD(Create, Read, Update, Delete) 조작을 허용한다. <br/>
SQL(Structured Query Language)은 관계형 데이터베이스 관리 시스템(RDMS)에서 데이터를 쿼리, 업데이트 및 삭제하는 데 사용되는 언어이다. <br/>
SQL은 표준 쿼리 언어이다. SQL언어의 쿼리는 SQL명령 또는 SQL문이라고도 한다. <br/>

<br/>

### ORM (Object Relational Mapping)

<br/>

객체지향적 구조? 모든 데이터는 객체이며, 각 객체는 독립된 데이터와 독립된 함수를 지님<br/>
SQL 구조? 데이터는 테이블 단위로 관리되며 객체들을 조회하기 위한 명령어를 사용<br/>
ORM은 각 테이블 또는 구분하고자 하는 데이터 단위로 객체를 구현하고, 데이터 간의 관계를 형성<br/>

![image](https://user-images.githubusercontent.com/78454649/176698971-0974a3d1-9ee5-47d4-851a-6779b05d88d8.png)

객체와 관계형 데이터베이스의 데이터를 **자동으로 매핑(연결)** 해주는 Framework <br/>
즉, 객체가 테이블이 되도록 매핑 시켜주는 것을 말합니다.

객체지향 프로그래밍은 클래스를 사용하고, 관계형 데이터베이스는 테이블을 사용하기 때문에 객체 모델과 관계형 모델간에 불일치가 존재 <br/>
→ ORM을 통해 객체 간의 관계를 바탕으로 **SQL을 자동으로 생성하여 불일치를 해결**

즉, 객체를 통해 간접적으로 데이터베이스 데이터를 다룸 <br/>
이러한 중간 계층을 Persistence Layer라 하며,  <br/>
ORM Framework들은 기존의 Entity Bean이 수행하던 Persistence Bridge의 역할을 ORM 패러다임의 Entity 방식으로 가능하게 함

<br/>

---

<br/>

### 사용예제

* Java

```java

public class Person{
    private String name;
    private String height;
    private String weight;
    private String ssn;
    //implement getter & setter methods
}

```

<br/>

* ibatis

```sql

<select id="getPerson" resultClass="net.agilejava.person.domain.Person">
    SELECT name, height, weight, ssn FROM USER WHERE name = #name#;
</select>

```

해당 쿼리의 결과를 받을 객체를 지정해줄 수 있다. 
즉, getPerson이라고 정의된 쿼리 결과는 net.agilejava.person.domain의 Person 객체에 자동으로 매핑되는 것이다. <br/>

<br/>

* Hibernate

```sql

<hibernate-mapping>
    <class name="net.agilejava.person.domain.Person" table="person">
        <id name="name" column="name"/>
        <property name="height" column="height"/>
        <property name="weight" column="weight"/>
        <property name="ssn" column="ssn"/>
    <class>
</hibernate-mapping>

```

위 두개의 Framework의 예시를 보면 알 수 있듯이,  <br/>
setter 메소드가 있으면 객체에 결과를 set하는 작업을 따로 해주지 않아도 자동으로 해당 값이 할당된다. 

물론 여기에 1:m 이나 m:1등의 관계들이 형성되면 추가적인 작업이 필요하긴 하지만,  <br/>
일단 눈에 보이는 간단한 부분은 처리가 되는 것을 볼 수 있다. 물론 반대의 경우에도 객체를 던져주면 <br/>
ORM Framework에서 알아서 get을 수행해 해당하는 column에 넣어주게 된다.


<br/>

### JPA

<br/>

* ORM

그렇다면 ORM은 무엇일까요? <br/>
ORM이란 객체와 DB의 테이블이 매핑을 이루는 것을 말합니다. (Java 진영에 국한된 기술은 아닙니다.)<br/>
즉, 객체가 테이블이 되도록 매핑 시켜주는 것을 말합니다.<br/>
ORM을 이용하면 SQL Query가 아닌 직관적인 코드(메서드)로서 데이터를 조작할 수 있습니다.


예를들어, User 테이블의 데이터를 출력하기 위해서 MySQL에서는 SELECT * FROM user; 라는 query를 실행해야 하지만, <br/>
ORM을 사용하면 User 테이블과 매핑된 객체를 user라 할 때, **user.findAll() 라는 메서드 호출로 데이터 조회가 가능**합니다.


query를 직접 작성하지 않고 메서드 호출만으로 query가 수행되다 보니, ORM을 사용하면 생산성이 매우 높아집니다.<br/>
그러나 query가 복잡해지면 ORM으로 표현하는데 한계가 있고, 성능이 raw query에 비해 느리다는 단점이 있는데요,<br/>
그래서 나중에 다루게 될 JPQL, QueryDSL 등을 사용하거나 한 프로젝트 내에서 Mybatis와 JPA를 같이 사용하기도 합니다.

<br/>

* JPA 탄생 배경

JDBC API를 사용했을 때의 문제는 다음과 같습니다.

유사한 CURD SQL 반복 작업 <br/>
객체를 단순히 데이터 전달 목적으로 사용할 뿐, 객체 지향적이지 못함 ( 페러다임 불일치 ) <br/>

그래서 객체와 테이블을 매핑 시켜주는 ORM이 주목 받기 시작했고, 자바 진영에서는 JPA라는 표준 스펙이 정의 되었습니다.


<br/>

* Hibernate의 특징

생산성 : 

Hibernate는 SQL를 직접 사용하지 않고, 메서드 호출만으로 쿼리가 수행됩니다. <br/>
즉, SQL 반복 작업을 하지 않으므로 생산성이 매우 높아집니다. <br/>
그런데 SQL을 직접 사용하지 않는다고 해서 SQL을 몰라도 된다는 것은 아닙니다.


유지보수 : 

테이블 컬럼이 하나 변경되었을 경우, <br/>
Mybatis에서는 관련 DAO의 파라미터, 결과, SQL 등을 모두 확인하여 수정해야 함 <br/>
JPA를 사용하면 JPA가 이런 일들을 대신해주기 때문에 유지보수 측면에서 좋습니다. 

<br/><br/>

* 정리

JPA가 SQL을 직접 작성하지 않는다고 해서 JDBC API를 사용하지 않는다는 것은 아닙니다. <br/>
Hibernate가 지원하는 메서드 내부에서는 JDBC API가 동작하고 있으며, 단지 개발자가 직접 SQL을 직접 작성하지 않을 뿐입니다. <br/>
그래서 JPA에서 수행하는 쿼리가 내 의도대로 실행이 된건지 모니터링을 할 줄 알아야 합니다.

JPA는 통계 쿼리처럼 복잡한 SQL을 수행하기 힘들기 때문에, <br/>
비즈니스에 따라 Mybatis를 사용할 지 Hibernate를 사용할 지 상황에 맞는 선택이 중요할 것입니다.

참고 : https://victorydntmd.tistory.com/195
