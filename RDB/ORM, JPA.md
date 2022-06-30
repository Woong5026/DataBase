### ORM 이란?

<br/>

ORM 이란 Object-Relational Mapping 의 약자로, <br/>
이름 그대로 객체(Object)와 관계형 데이터(Relational data) 를 매핑하기 위한 기술이다. <br/>
이러한 매핑이 필요한 이유는 객체 지향 언어과 관계형 데이터베이스사이의 **패러다임 불일치**가 있기때문이다.  <br/>
이 둘 간의 패러다임 불일치 때문에 개발자는 더 많은 코드를 작성해야 하며, 이는 반복적이고 실수하기 쉬운 작업이 된다. <br/>
그렇기 때문에 개발자는 객체지향적인 설계에 집중할 수 없게 된다. ORM이 바로 이러한 문제를 해결해 준다. 

<br/>

### 패러다임 불일치

<br/>

객체 지향 프로그래밍과 관계형 데이터베이스 사이의 데이터 표현 방식이 달라서 생기는 문제를 패러다임 불일치라고 한다. <br/>
패러다임 불일치가 일어나는 이유는 애초에 이들의 목표와 동작 방식이 다르기 때문이다.

* 객체 지향

필드와 메서드 등을 묶어서 객체로 잘 만들어 사용하는 것이 목표 <br/>
객체 지향 프로그래밍은 추상화, 캡슐화, 정보은닉, 상속, 다형성 등 시스템의 복잡성을 제어할 수 있는 다양한 장치들을 제공한다.

* 관계형 데이터베이스

데이터를 잘 정규화해서 보관하는 것이 목표

<br/>

### JPA

<br/>

JPA는 Java Persistence API의 약자로, 자바 ORM 기술에 대한 API 표준 명세이다.  <br/>
즉, 인터페이스의 모음이다. 이러한 JPA 인터페이스를 구현한 대표적인 프레임워크가 하이버네이트(Hibernate)이다. <br/>
JPA는 애플리케이션과 JDBC 사이에서 동작한다. 개발자가 JPA를 사용하면, JPA 내부에서 JDBC API를 사용하여 SQL을 호출하여 DB와 통신한다. <br/>
즉, 개발자가 직접 JDBC API를 쓸 필요가 없다.

![image](https://user-images.githubusercontent.com/78454649/176725179-adb2285d-603d-46c9-8fe7-a16673eb1862.png)


<br/>

### Hibernate

<br/>

JPA를 구현한 프레임워크 중 사실상 표준이다. 오픈소스 소프트웨어이다. <br/>
여기서 주목해야할 점은 JPA는 기술 스펙이고 하이버네이트는 이 기능을 구현하여 공급해주는 역할이다.

<br/>

### Spring Data JPA

<br/>

Spring framework에서 **JPA를 편리하게 사용할 수 있도록 지원하는 프로젝트(모듈)** 이다. <br/>
Spring Data JPA의 목적은 JPA를 사용할 때 필수적으로 생성해야하나, <br/>
**예상가능하고 반복적인 코드들을 대신 작성**해줘서 코드를 줄여주는 것이다. <br/>
이는 JPA를 한 단계 추상화시킨 **Repository라는 인터페이스를 제공**함으로써 이루어진다.

 Spring Data JPA는 JPA Provider이 아니다. <br/>
 단지 데이터 계층에 접근하기 위해 필요한 뻔한 코드들의 사용을 줄여주도록 하는 인터페이스이다. <br/>
 여기서 반드시 기억해야할 점은 Spring Data JPA는 항상 하이버네이트와 같은 JPA provider가 필요하다는 것이다.

![image](https://user-images.githubusercontent.com/78454649/176725604-2b47a9d3-0b28-4641-81e9-622a9db7cc4b.png)

<br/>

### Spring Data JPA 예제 코드

<br/>

* Entity 생성

```java

@Entity
public class Product extends Timestamped {
    @GeneratedValue(strategy = GenerationType.AUTO)
    @Id
    private Long id;
    private Long userId;
    private String title;
    private String image;
    private String link;
    private int lprice;
    private int myprice;
}

```

* Spring Data JPA) Repository 생성

```java

public interface ProductRepository extends JpaRepository<Product, Long> {
}

```

* Spring Data JPA) Repository 기본 제공 기능

```java

// 1. 상품 생성
Product product = new Product(...);
productRepository.save(product);

// 2. 상품 전체 조회
List<Product> products = productRepository.findAll();

// 3. 상품 전체 개수 조회
long count = productRepository.count();

// 4. 상품 삭제
productRepository.delete(product);

```

* Spring Data JPA) 추가기능

interface 만 선언해 주면, 구현은 Spring Data JPA 가 대신한다.

```java

public interface ProductRepository extends JpaRepository<Product, Long> {
  // (1) 회원 ID 로 등록된 상품들 조회
  List<Product> findAllByUserId(Long userId);

  // (2) 상품명이 title 인 관심상품 1개 조회
  Product findByTitle(String title);

  // (3) 상품명에 word 가 포함된 모든 상품들 조회
  List<Product> findAllByTitleContaining(String word);

  // (4) 최저가가 fromPrice ~ toPrice 인 모든 상품들을 조회
  List<Product> findAllByLpriceBetween(int fromPrice, int toPrice);
}

```




