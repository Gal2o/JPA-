- ## JPA
  - #### Java Persistence API
  - #### 자바 진영의 ORM 기술 표준
  - #### ORM ?
    - #### Object-Relational Mapping (객체 관계 매핑)
    - #### 객체는 객체대로 설계하고,
    - #### RDB는 RDB대로 설계
    - #### ORM 프레임워크가 중간에서 매핑한다.
    - #### 대중적인 언어에는 대부분 ORM 기술이 존재한다.
  - #### JPA는 `Java 애플리케이션`과 `JDBC` 사이에서 동작한다. <br><br> ![image](https://user-images.githubusercontent.com/35948339/143963141-ed770146-9cbd-4af6-adf0-e0ebc981d919.png)
  -------
  - ### JPA 동작 방식
    - #### 저장 <br><br> ![image](https://user-images.githubusercontent.com/35948339/143963194-ee905086-424c-475a-8cac-2acb282e7212.png)
      - #### 1️⃣ MemberDAO에서 객체를 저장하고 싶다.
      - #### 2️⃣ Member 객체를 JPA에게 넘기면, JPA는 `Entity분석을 해서 INSERT 쿼리를 만들어준다.`
      - #### 3️⃣ JDBC API를 사용하여 DB와 통신하여 저장한다.
      - #### 🌟 Java - RDB 간 `패러다임 불일치를 해결`해주는 것이 `JPA 사용목적`
    - #### 조회 <br><br> ![image](https://user-images.githubusercontent.com/35948339/143963998-f7f68f05-e86a-42c1-b151-19e5a377f6aa.png)
      - #### 1️⃣ JPA에게 `id(PK) 값`을 넘기면 JPA는 `Entity분석을 통해 SELECT 쿼리를 만들어낸다.`
      - #### 2️⃣ JDBC API를 사용하여 트랜잭션 후, 결과를 받아서 `ResultSet에 매핑`을 통해 반환을 해준다.
   --------
   - ### JPA 등장 배경
     - #### 과거에는 EJB - 엔티티 빈(자바 표준)인 ORM이 있었다. <br><br> 하지만, 기능이 별로 좋지 못했다. (인터페이스를 엄청 많이 구현, 속도도 느림, 에러도 많이 발생)
     - #### 그래서 등장한 것이 `Hibernate (오픈소스)`
     - #### Hibernate를 거의 유사하게 구현한 것이 JPA
   ------
     - #### JPA는 인터페이스의 모음
     - #### JPA 2.1 표준 명세를 구현한 3가지 구현체 <br><br> ![image](https://user-images.githubusercontent.com/35948339/143964693-926eb557-b710-4f72-ab00-cb1ee3e8adcc.png)
     - #### 8-90% 이상 Hibernate를 사용한다고 생각하면 된다.
   ------
   - ### JPA를 왜 사용해야 하는가?
     - #### SQL 중심적인 개발 ▶ 객체 중심으로 개발
     - #### 생산성 증가
       ``` java
          // 저장
          jpa.persist(member)
          
          // 조회
          Member member = jpa.fine(memberId)
          
          // 수정
          member.setName("변경할 이름")
          
          // 삭제
          jpa.remove(member)
       ```
     - #### 유지보수
       - #### 기존 필드 변경시, 모든 SQL 수정
       ``` java
          public class Member {
              private String memberId;
              private String name;
              
              // 필드를 추가 !!
              private String num -> tel;
          }
          
          INSERT INTO MEMBER(MEMBER_ID, NAME, TEL(자동으로 추가)) VALUES ...
          SELECT MEMBER_ID, NAME, TEL(자동으로 추가) FROM MEMBER M
          UPDATE...
       ```
   -------
   - ### JPA와 패러다임의 불일치 해결
     - #### 


