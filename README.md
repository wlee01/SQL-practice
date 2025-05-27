# SQL-practice

used sample data -> worked on basic functions of SQL: select, insert, update, delete. 
practiced utilizing where, and, or like to retrieve custom data. 


<img width="1404" alt="count" src="https://github.com/user-attachments/assets/74c9874c-3346-4920-b74c-2edf998981da" />
<img width="1404" alt="average" src="https://github.com/user-attachments/assets/80fbaf1a-0156-4617-8c77-bc14f31fbf44" />
<img width="1424" alt="city : count" src="https://github.com/user-attachments/assets/e72e968b-c8bf-453a-b5c4-2b51263a249c" />
<img width="1410" alt="city : max" src="https://github.com/user-attachments/assets/e8d3c6b8-419c-45ad-9d99-6e975e66d6af" />


/// 

정규화와 비정규화는 데이터를 다루는 이론적인 설계 개념입니다.



정규화(Normalization)
정규화는 "데이터 중복을 줄이고, 일관성을 높이기 위해 테이블을 쪼개는 것" 입니다.

다음과 같은 특징을 가지고 있습니다.

데이터를 최소한으로만 저장
중복을 제거하고
변경(update)할 때 문제가 생기지 않도록 만든다


정규화가 필요한 이유
이유

설명

데이터 중복 제거

똑같은 데이터를 여러 번 저장하지 않게 함

데이터 무결성 강화

데이터 오류를 줄임 (한 곳만 수정하면 됨)

유지보수 용이

구조가 명확해서 관리하기 쉬움



정규화 단계 (간단 버전)
정규화는 한번에 완벽하게 정리할 수 없기 때문에 다음과 같이 단계를 세분화해서 만들게 됩니다.

단계

의미

예시

1NF (제1정규형)

테이블의 각 컬럼이 원자값(atomic value)만 갖는다

리스트 형태 X, 하나의 값만 저장

2NF (제2정규형)

부분적 종속 제거

기본 키의 일부에만 종속되는 컬럼 제거

3NF (제3정규형)

이행적 종속 제거

기본 키가 아닌 컬럼에 또 다른 컬럼이 종속되지 않게



정규화 예시
나쁜 테이블 (중복 심함)
주문번호

고객명

고객주소

상품명

1

Alice

Seoul

Laptop

2

Alice

Seoul

Mouse

→ 고객 정보가 매번 반복 저장됨



정규화 후 테이블 분리
고객 테이블 (customers)
고객ID

고객명

고객주소

1

Alice

Seoul

주문 테이블 (orders)
주문번호

고객ID

상품명

1

1

Laptop

2

1

Mouse

→ 고객 정보는 한 번만 저장되고, 주문만 따로 관리함!







비정규화(Denormalization)란?
비정규화는 "속도나 편의성을 위해 일부러 정규화를 깨고 중복을 허용하는 것"입니다.



비정규화를 쓰는 이유
이유

설명

성능 최적화

조인(JOIN)이 많으면 느려지기 때문

조회 속도 향상

테이블 합치지 않고 한 번에 읽게 함

단순화

복잡한 테이블 구조를 단순하게



비정규화 예시
고객 테이블과 주소 테이블을 따로 분리하는 대신,
고객 테이블에 주소 컬럼을 그냥 중복 저장하는 경우
고객ID | 고객명 | 고객주소
-------|--------|--------
1      | Alice  | Seoul
2      | Bob    | Busan
→ 조회할 때 JOIN 안 해도 빠르게 가져올 수 있음

