# 네트워크 3주차 - Application Layer 2

## 📌 쿠키/세션

---

### 1. 쿠키와 세션에 대해서 설명해주세요.
     쿠키란, 브라우저에 저장되는 작은 텍스트 파일로, 
    HTTP의 stateless 특성을 보완하기 위한 클라이언트 측 데이터 저장 방식이다.
    주요 속성으로 다음과 같다.
    Name, Value, Max-age, Domain, Path, Secure, HttpOnly, SameSite

     세션이란, 서버측에서 사용자 상태를 유지하는 방식이다.
    실제 데이터는 서버에 저장되며, 특정 세션 저장소의 세션 ID를 클라이언트에게 쿠키로 전달한다.

### 2. JWT 토큰에 대해서 설명해주세요.
     JWT란, 당사자 간 정보를 JSON 객체로 안전하게 전송하는 방식이다.
    Header, Payload, Signature의 구조로 이루어져 있다.
    Signature를 통해 Header와 Payload가 전송 과정중 변조되지 않았음을 확인 할 수 있다.
    정보 보호를 위해선 JWT 자체를 암호화해야한다.
    추가적으로, JWT는 세션과 달리 stateless하여 서버의 부하를 감소 시킨다.

## 📌 REST

---

### 3. REST에 대해서 설명해주세요.  Restful API는 뭘까요?
     REST란, Representational State Transfer의 약자로, Scalability, Generality, Independece등 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.
    자원(Resource), 행위(Verb), 표현(Representation)으로 구성된다.
    
     RESTful API란, REST 아키텍처를 따르는 API를 칭한다.
    RESTful API로 HTTP가 있다.

### 4. REST 제약 조건에 대해 설명해주세요.
     REST를 만족시키려면 다음과 같은 조건들에 부합해야 한다.
    1. Client-Server : 클라이언트와 서버의 관심사는 분리되어야함
    2. Stateless : 각 요청은 독립적이며 이전 요청에 대한 정보가 불필요해야함
    3. Cache : 응답은 캐시 가능 여부를 명시해야함
    4. Uniform Interface
        - Resource Identification in Requests
        - Resource manipulation through Representations
        - Self-descriptive Messages
        - Hypermedia as the Engine of Application State
    5. Layered System : 계층화된 시스템 아키텍처
    6. Code on Demand : 서버가 클라이언트에게 실행 가능한 코드를 다운로드하여 실행할 수 있는 기능을 제공하는 것

### 5. URL, URI, URN 차이가 뭘까요?
     URI란, Uniform Resource identifier의 약자로, 리소스를 식별하는 방식이다.
    URL과 URN을 포함하는 상위 개념이다.

     URL이란, Uniform Resource Locator의 약자로 리소스의 위치를 지정한다.
    인터넷상에서 자원을 식별하는데 사용된다.    

     URN이란, Uniform Recourse Name의 약자로 리소스의 이름을 지정한다.
    위치와 관계없이 자원을 식별하는데 사용된다.

## 📌 보안/캐시

---

### 6. SOP와 CORS에 대해서 설명해주세요.
     SOP란, Same-Origin Policy의 약자로, 동일 출처에서만 리소스 접근을 허용하는 것이다.
    이때, 출처란 프로토콜, 호스트, 포트의 조합이다.

     CORS란, Cross-Origin Resource Sharing의 약자로 다른 출처의 리소스 요청을 허용하는 메커니즘이다.
    HTTP 헤더를 기반으로 동작하며 주요 헤더는 다음과 같다.
    1. Access-Control-Allow-Origin
    2. Access-Control-Allow-Methods
    3. Access-Control-Allow-Headers

### 7. XSS 공격이 무엇이고, 방어하는 방법을 설명해주세요.
     XSS란, Cross-Site Scripting의 약자로, 웹사이트에 악성 스크립트를 삽입하는 공격 방식이다.
    종류로는 Stored XSS, Reflected XSS, DOM-based XSS가 있다.

    방어 방법은 다음과 같다.
    1. 입력 값 검증 및 필터링
    2. HTML 이스케이프 처리
    3. CSP(Content Security Policy) 적용
    4. HttpOnly 쿠키 사용
    5. 최신 보안 업데이트 유지

### 8. CSRF 공격이 무엇이고, 방어하는 방법을 설명해주세요.
    CSRF란, Cross-Site Request Forgery의 약자로, 사용자의 권한을 이용한 악의적인 요청 공격을 뜻한다.
    사용자가 로그인된 상태에서 사용자의 권한을 악용한 요청들을 발생시킨다.

    방어 방법은 다음과 같다.
    1. CSRF 토큰 사용
    2. SameSite 쿠키 속성
    3. Referer 검증
    4. Double Submit Cookie
    5. Custom Request Headers

### 9. SQL Injection 공격이 무엇이고, 방어하는 방법을 설명해주세요.
    SQL Injection이란, SQL 쿼리에 악의적인 코드를 삽입하는 공격이다.
    데이터베이스의 데이터를 조작 및 탈취가 가능하다.

    방어 방법은 다음과 같다.
    1. Prepared Statement 사용
    2. 입력 값 검증
    3. 이스케이프 처리
    4. ORM 사용
    5. 최소 권한 원칙 적용
    6. 에러 메시지 제한

### 10. 웹 캐시에 대해 설명해주세요.
     웹 캐시란, 사용자(client)가 웹 사이트(server)에 접속할 때, 
    정적 컨텐츠(이미지, JS, CSS 등)를 특정 위치(client, network 등)에 저장하여, 
    웹 사이트 서버에 해당 컨텐츠를 매번 요청하여 받는것이 아니라, 
    특정 위치에서 불러오는 것이다.
    종류로는 브라우저 캐시, 프록시 캐시, CDN가 있다.
    이를 통해 사이트 응답시간을 줄이고, 서버 트래픽 감소 효과를 볼 수 있다.

## 📌 프록시

---

### 11. 프록시 서버에 대해서 설명해주세요.
     프록시 서버란, 클라이언트와 서버 사이의 중개 서버를 칭한다.
    대신 통신을 수행해 다양한 부가 기능을 제공하는 것이 목적이다.
    양쪽 모두에게 반대편 시스템처럼 동작한다.
    
    주요 기능은 다음과 같다.
    1. 캐싱 : 자주 요청되는 콘텐츠를 저장
    2. 로드 밸런싱 : 서버 부하 관리를 위한 트래픽 분산
    3. 보안 : 서버의 IP 주소를 숨기고 악성 트래픽 필터링, DDoS 공격 방어
    4. 익명성 : 클라이언트 IP 주소를 은폐, 지리적 제한 우회
    5. 접근 제어 : URL 필터링, 콘텐츠 제한, 사용자 인증

### 12. 포워드 프록시에 대해서 설명해주세요.
    동작방식 : 클라이언트 -> 포워드 프록시 -> 인터넷 -> 서버
    주요기능 : 캐싱, 접근 제어, 익명성 보장, 콘텐츠 필터

### 13. 리버스 프록시에 대해서 설명해주세요.
    동작방식 : 클라이언트 -> 인터넷 -> 리버스 프록시 -> 서버
    주요기능 : 로드 밸런싱, SSL 종료, 캐싱, 보안, 압축

### 14. L7 로드 밸런서에 대해서 설명해주세요.
    URL 기반 라우팅
    /images/* -> 이미지 서버
    /api/* -> API 서버
    /static/* -> 정적 파일 서버

    콘텐츠 기반 라우팅
    plaintextCopyContent-Type: image/* -> 이미지 서버
    User-Agent: Mobile -> 모바일 서버

    SSL 종료
      - 클라이언트와의 암호화 통신 처리
      - 백엔드 서버는 일반 HTTP 통신

    세션 유지
      - 동일 사용자 요청을 같은 서버로 전송
      - 세션 데이터 일관성 유지

    로브밸런싱 알고리즘 : Round Robin, Least Connection, IP Hash, URL Hash, Weighted Round Robin 

### 15. 커넥션 타임아웃과 리드 타임아웃에 대해 설명해주세요.
    TCP 커넥션 타임 아웃
      - TCP 연결 수립시 최대 대기 시간
      - 3 way handshake 과정에서 발생 (네트워크 문제나 서버 과부하 시 발생)

    리드 타임아웃
      - 데이터 수신 대기 최대 시간
      - 이미 연결된 상태에서 발생
        1. 연결 수립 완료
        2. 요청 전송
        3. 응답 대기 <- 이 단계에서 측정
            - 서버 처리 시간 고려 필요
            - 대용량 데이터 전송 시 더 길게 설정해야함