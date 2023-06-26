## Spring JPA QueryDSL 정리

---

#### 1. JPAQueryFactory를 필드로 제공하면 동시성 문제?

- JPAQueryFactory를 생성할 때 제공하는 EntityManager(em)에 달려있음.
- 스프링 프레임워크는 여러 쓰레드에서 동시에 같은 EntityManager에 접근해도, 트랜잭션 마다 별도의 영속성 컨텍스트를 제공하기 때문에, 동시성 문제는 고려하지 않아도 괜찮음.

---

#### 2. JPQL이 제공하는 모든 검색 조건 제공

- `member.username.eq("member1")` // username = 'member1'
- `member.username.ne("member1")` //username != 'member1'
- `member.username.eq("member1").not()` // username != 'member1'
- `member.username.isNotNull()` //이름이 is not null
- `member.age.in(10, 20)` // age in (10,20)
- `member.age.notIn(10, 20)` // age not in (10, 20)
- `member.age.between(10,30)` //between 10, 30
- `member.age.goe(30)` // age >= 30
- `member.age.gt(30)` // age > 30
- `member.age.loe(30)` // age <= 30
- `member.age.lt(30)` // age < 30
- `member.username.like("member%")` //like 검색
- `member.username.contains("member")` // like ‘%member%’ 검색
- `member.username.startsWith("member")` //like ‘member%’ 검색

---
