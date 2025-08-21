# **2-03 JPA로 데이터베이스 사용하기**

- DB와 SQL: DB는 데이터를 모으고 관리하는 저장소. DB를 관리하려면 SQL(Structured Query Language)이라는 언어를 사용해야 함
- ORM: 스프링 부트와 달리 DB는 java를 이해하지 못한다. 하지만, ORM(Object Relational Mapping)이라는 도구를 사용하여 java 문법으로도 DB를 다룰 수 있다. 즉, 개발자는 ORM을 이용하여 SQL을 직접 작상하지 않아도 DB의 데이터를 처리할 수 있다.

## ORM

: SQL을 사용하지 않고, DB를 관리할 수 있는 도구. 데이터베이스의 테이블을 자바 클래스로 만들어 관리할 수 있다.

아래의 쿼리문으로 question 테이블에 데이터를 추가할 수 있다.

```sql
insert into question (id, subject, content) values (1, '안녕하세요', '가입 인사드립니다 ^^');
insert into question (id, subject, content) values (2, '질문 있습니다', 'ORM이 궁금합니다');
```

ORM을 이용하면 아래의 java문을 통해서 question 테이블에 데이터를 추가할 수 있다.

```java
Question q1 = new Question();
q1.setId(1);
q1.setSubject("안녕하세요");
q1.setContent("가입 인사드립니다 ^^");
this.questionRepository.save(q1);

Question q2 = new Question();
q2.setId(2); 
q2.setSubject("질문 있습니다"); 
q2.setContent("ORM이 궁금합니다"); 
this.questionRepository.save(q2);
```

beour 프로젝트 코드를 통해서 확인할 수 있는 ORM

```java
        Space space = Space.builder()
                .name(spaceRequestDto.getName())
                .address(spaceRequestDto.getAddress())
                .description(spaceRequestDto.getDescription())
                .build();

        Space saved = spaceRepository.save(space);
```

이처럼 데이터를 관리하는 데 사용하는 ORM의 자바 클래스(Space, Question)를 엔티티라고 한다.

- ORM 장점: MySQL, Oracle, MS SQL 같은 DBMS의 종류에 관계 없이 일관된 자바 코드를 사용할 수 있어서 프로그램 유지/보수 용이.
- DB vs DBMS: 구분하지 않고 쓰기도 함.
    - DB: 데이터를 담는 통
    - DBMS: DB+Management System, DB를 관리하는 소프트웨어

## JPA(Java Persistence API)

: 스프링 부트는 ORM 기술의 표준으로서 JPA를 사용하여 DB를 관리한다. 

- JPA는 인터페이스 모음이다. 이 인터페이스를 구현한 실제 클래스가 필요하다.
- JPA를 구현한 실제 클래스에는 대표적으로 Hibernate가 있다.
- 즉, 하이버네이트는 JPA의 인터페이스를 구현한 실제 클래스이자 자바의 ORM 프레임워크이다.

Q. JPA와 Hibernate, JDBC?

- 참고: build.gradle **implementation**
    
    `build.gradle` 파일에서 작성한 `implementation`은 필요한 라이브러리 설치를 위해 가장 일반적으로 사용하는 설정이다.  `implementation`은 해당 라이브러리가 변경되더라도 이 라이브러리와 연관된 모든 모듈을 컴파일하지 않고 변경된 내용과 관련이 있는 모듈만 컴파일하므로 프로젝트를 리빌드(rebuild)하는 속도가 빠르다.

