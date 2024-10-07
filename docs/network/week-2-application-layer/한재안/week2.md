# 네트워크 2주차 - Application Layer 1

## 📌 HTTP

---

### 1. HTTP 프로토콜에 대해서 설명해주세요.
    HTTP는 HyperText Transfer Protocol의 약자로, OSI 네트워크 통신 모델의 어플리케이션 계층 프로토콜이다.
    HTTP는 클라이언트-서버 구조 기반의 무상태 프로토콜이고, 
    클라이언트-서버간 메시지중 여러 유형의 요청과 응답을 정의한다.

### 2. HTTP의 요청/응답 모델에 대해 설명해주세요.
    HTTP의 요청/응답 모델은 모두 공통된 HTTP 메시지의 구조를 갖는다.
    HTTP 메시지 구조란, 
        1. 시작 줄(start-line)
            요청 모델에서는, "HTTP 메소드" + "URI" + "HTTP 버전"이 들어간다.
            응답 모델에서는, "프로토콜 버전" + "상태 코드" + "상태 텍스트"가 들어간다.
        2. HTTP 헤더
            요청 모델에서는 아래와 같은 내용이 들어간다.
                1. Request 헤더 : Host, User-Agent, Accept, Origin 등의 요청을 구체화 하는 이름:값 형태의 데이터가 들어간다.
                2. General 헤더 : Date, Connection, Via
                3. Entity 헤더 : Content-Type, Content-Length
            응답 모델에서는 아래와 같은 내용이 들어간다.
                1. Response 헤더 : Server, Access-Control-Allow-Origin, Set-Cookie, HttpOnly
                2. General 헤더 : Date, Connection, Via
                3. Entity 헤더 : Content-Encoding, Content-Type, Date, Last-Modified
        3. 빈 줄
            헤더와 본문의 구분하는 용도이다.
        4. 본문
            요청 모델에서는, POST일 경우 단일-리소스 본문과 다중-리소스 본문으로 나뉜다.
            응답 모델에서는, 길이를 아는 단일-리소스 본문, 길이를 모르는 단일-리소스 본문, 그리고 다중-리소스 본문으로 나뉜다.

### 3. HTTP 메서드 중 GET과 POST의 차이점에 대해 설명해주세요.
    GET과 POST의 차이점은 사용 목적과, 요청의 body 존재 유무에 있다.
    GET은 클라이언트가 서버의 자원을 요청할 때, 사용하고
    POST는 클라이언트가 서버의 자원을 새로 생성할 때 사용한다.
    GET은 데이터를 URL 파라미터에 담아서 보내지만, POST는 body에 담아서 보낸다.

### 4. HTTP 메서드 중 PUT과 PATCH의 차이점에 대해 설명해주세요.
    PUT과 PATCH는 클라이언트가 서버의 자원을 수정할 때 사용한다는 공통점이 있다.
    그러나 PUT은 모든 자원을 수정할 때, PATCH는 일부 자원을 수정할 때 사용한다.
    
    PUT/members/1 라는 요청이 오면, 멤버 1의 정보는 해당 요청의 데이터로 대체된다.
    PUT/members/1 라는 요청이 오면, 멤버 1의 일부 정보가 해당 요청의 데이터로 수정된다.

### 5. HTTP 상태 코드가 무엇인가요? 알고 있는 상태 코드 몇 가지 설명해주세요.
    HTTP 상태 코드는 특정 HTTP 요청이 어떻게 완료됐는지 알려준다.
    상태 코드는 총 5개의 그룹으로 나누어진다.
    1XX : Information (정보 제공)
        임시 응답으로 현재 클라이언트의 요청까지는 처리되었으니 계속 진행하라는 의미이다.

    2XX : Success (성공)
        클라이언트의 요청이 서버에서 성공적으로 처리되었다는 의미이다.        

    3XX : Redirection (리다이렉션)
        완전한 처리를 위해서 추가 동작이 필요하다는 의미이다.
        이때 추가적인 동작의 예시로, 서버의 주소 또는 요청한 URI의 웹 문서가 이동되었으니 그 주소로 다시 시도하라는 응답이 있다.

    4XX : Client Error (클라이언트 에러)
        존재하지 않는 페이지를 요청하는 등 클라이언트의 요청 메시지 내용이 잘못된 경우를 의미한다.        

    5XX : Server Error (서버 에러)
        서버 사정으로 메시지 처리에 문제가 발생했다는 의미이다.
        이때 서버의 사정으로는 서버의 부하, DB 처리 과정 오류, 서버에서 예외가 발생하는 경우이다. 

### 6. HTTP 헤더가 뭘까요? 알고 있는 헤더 몇 가지 설명해주세요.
    HTTP 헤더란, HTTP 메시지의 요청/응답을 구체화 하는데 사용된다.
    각 메타데이터는 case-insensitive string followed by a colon and a value in single line로 구성되어 있고
    Request/Response 헤더, General 헤더, Representation 헤더(Entity)로 구분할 수 있다.

### 7. HTTP의 무상태성에 대해서 설명해주세요.
    HTTP는 무상태 프로토콜이다. 
    무상태 프로토콜이란, 어떠한 이전 요청과도 무관한 각각의 요청을
    독립적인 트랜잭션으로 취급하는 통신 프로토콜로, 
    통신이 독립적인 쌍의 요청과 응답을 이룰 수 있게 하는 방식이다.

### 8. HTTP Keep-Alive에 대해서 설명해주세요.
    HTTP Keep-Alive란, HTTP 헤더의 General 헤더의 메타데이터로,
    송신자가 정한 연결에 대한 타임아웃과 
    연결중 전송할 수 있는 요청의 최대 개수를 알려준다.
    해당 메타 데이터는 Connection: keep-alive가 설정되어야만 유효한데,
    HTTP 1.1 부터 Connection: keep-alive는 기본 값으로 설정된다.
    
    추가적으로, keep-alive connection이란, persistent connection을 의미한다.
    connection을 어느정도 열어 넣고, 여러 요청에 재사용함으로써, TCP hand-shake 비용을 아낍니다. 
    이때, connection은 위의 타임아웃과 최대 요청 개수를 통해 관리됩니다.

### 9. HTTP 파이프라이닝에 대해서 설명해주세요.
    HTTP 파이프라이닝이란, persistent connction 사용시, 여러 요청을 보낼 때,
    응답을 기다리지 않고 요청을 연속적으로 보내는 기능이다.
    이때, GET, HEAD, PUT, DELETE와 같은 idempotent 메서드만 파이프라이닝이 가능하다.

### 10. HTTP/1.1, HTTP/2, HTTP/3 각각의 특징에 대해 설명해주세요.
    HTTP/1.1
        HTTP의 첫번째 표준화 버전이다.
        연결 재사용한다.
        파이프라이닝이 추가되었다.
        Server collocation, Host 헤더 덕분에 동일한 IP 주소에 다른 도메인을 호스트팅할 수 있게 되었다.

    HTTP/2
        텍스트 프로토콜이 아닌, binary 프로토콜이다.
        동일한 연결을 통해 병렬 요청을 수행하는 다중화 프로토콜이다.
        요청 집합 간 유사한 경우가 많으므로, 전송된 데이터의 중복과 오버헤드를 제거한다.
        서버 푸시 기능이 추가되었다.

    HTTP/3
        Transport 계층에서 TCP 기반의 통신 대신 QUIC을 사용한다.
        

## 📌 HTTPS

---

### 11. HTTPS에 대해서 설명해주세요.
    HTTPS란, Hypertext Transfer Protocol Secure의 약자로 HTTP의 확장 버전이다.
    HTTPS에서는 브라우저와 서버가 데이터를 전송하기 전에 암호화된 연결을 설정한다.

### 12. SSL/TLS가 무엇인가요?
    SSL이란 Secure Sockets Layer의 약자로 클라이언트와 서버가 서로 데이터를 암호화해 통신할 수 있도록 돕는 보안 계층이다.
    비유를 하자면, HTTP 계층 아래에 SSL 계층이 추가되는 형태이다.
    HTTP외에도 FTP, SMTP와 같은 프로토콜에도 적용할 수 있다.
    
    TLS이란 Transport Layer Security의 약자로 SSL 3.0의 후속작이다.
    많은 변화들이 있어 이전 버전과 구분하기 위해 이름을 통해 구분한다.
    SSL은 더이상 사용되지 않지만, TLS를 설명할 때 SSL이라고 칭하기도 한다.

    SSL/TLS라는 용어는 TLS 프로토콜과 TLS 인증서를 나타낸다.

### 13. 대칭키 암호화 방식에 대해 설명해주세요.
    하나의 키로 암호화와 복호화 모두 수행하는 암호화 기법이다.
    키 공유의 문제가 있다.
    Data Encryption Standard, Electronic Codebook, Cipher Block Chaining, Cipher Feedback, Output Feedback Block, Counter의 방식이 있다.

### 14. 비대칭키 암호화 방식에 대해서 설명해주세요.
    public-secret 한 쌍의 키로 암호화와 복호화를 수행하는 암호화 기법이다.
    public 키를 공유한다.
    하나의 키로 암/복호화를 진행했을 경우, 다른 키로만 복/암호화를 진행할 수 있다.
    RSA, ECC의 방식이 있다.

### 15. 전자 서명에 대해서 설명해주세요.

### 16. HTTPS 암호화 과정에 대해 설명해주세요. (SSL Handshake의 동작 과정을 설명해주세요.)
    웹사이트의 TLS/SSL 인증서에 있는 공개 키를 사용해 데이터를 암호화하는 과정이다.
    SSL Handshake는 TCP 연결이 열린 후 발생한다.

    TLS 1.3 이전의 경우,
    1. 클라이언트 헬로 메시지
        클라이언트가 서버로 "헬로" 메시지를 전송하면서 핸드셰이크를 시작한다.
        해당 메시지에는 클라이언트가 지원하는 TSL 버전, 암호 제품군, 클라이언트 무작위 바이트 문자열이 포함된다.
    2. 서버 헬로 메시지
        클라이언트 헬로의 응답으로, 서버가 서버의 SSL 인증서, 서버에서 선택한 암호 제품군, 서버 무작위 바이트 문자열을 보낸다.
    3. 인증
        클라이언트가 서버의 SSL 인증서를 인증서 발행 기관을 통해 검증한다.
        서버가 인증서에 명시된 서버인지, 실제 해당 도메인의 소유자인지를 확인한다.
    4. 예비 마스터 암호
        클라이언트가 서버에게 예비 마스터 암호라고 하는 무작위 바이트 문자열을 하나 더 전송한다.
        해당 문자열은 서버의 공개 키로 암호화 되어 있다.
    5. 개인 키 사용
        서버가 개인키를 통해 문자열을 해독한다.
    6. 세션 키 생성
        클라이언트와 서버가 클라이언트 무작위, 서버 무작위, 예비 마스터 암호를 사용해 세션 키를 생성한다.
    7. 클라이언트 준비 완료
        클라이언트가 세션 키로 암호화된 완료 메시지를 전송한다.
    8. 서버 준비 완료
        서버 또한 세션 키로 암호화 된 완료 메시지를 전송한다.
    9. 대칭 암호화 성공
        핸드셰이크가 완료되고, 세션 키를 이용해 통신을 진행한다.

## 📌 DNS

---

### 17. DNS가 무엇인가요?
    DNS란, Domain Name System의 약자로, 사람이 읽을 수 있는 도메인 이름을
    기계가 읽을 수 있는 IP 주소로 변환하는 시스템이다.

### 18. DNS 작동 방식에 대해 설명해주세요.
    사용자가 주소창에 'example.com'을 입력했고 어떠한 곳에도 DNS 조회 정보가 없을 때,
    1. 사용자가 보낸 쿼리를 DNS resolver가 수신한다.
    2. DNS resolver는 우선 Local DNS 서버에게 질의한다.
    3. Local DNS 서버에서 찾지 못했다면, DNS Root Name 서버에게 질의한다.
    4. Root Name 서버는 요청된 도메인 확장자에 해당하는 DNS TLD 서버의 주소를 반환한다.
    5. 이후, DNS resolver는 DNS TLD 서버에게 질의한다. 
    6. DNS TLD 서버는 도메인 이름 서버의 IP 주소를 반환한다.
    7. DNS resolver는 받은 도메인 이름 서버의 IP 주소로 질의한다.
    8. DNS resolver는 처음 요청한 도메인의 IP 주소를 웹 브라우저에게 보낸다.
    

### 19. DNS 질의 종류에 대해 설명해주세요.
    Recursive Query (재귀적 질의)
        레코드 (사용자가 요청한 IP 주소)를 반환하는 것이다.
        클라이언트가 요청한 레코드를 응답하거나 
        레코드가 없을 때는 오류메시지를 사용하여 응답하도록 요구한다.

    Iterative Query (반복적 질의)
        반복적으로 다른 DNS 서버에게 쿼리를 보내게 해서 응답을 하도록 요청한다.
        자세히는 쿼리 한 DNS 서버가 일치하는 데이터가 없을 경우 
        하위 수준의 도메인네임 스페이스에 해당하는 DNS서버 참조를 반환한다.
        클라이언트는 반환받은 참조주소로 쿼리 한다.

### 20. DNS 서버에게 IP 주소를 요청할 때, 왜 UDP를 사용하나요?
    DNS가 UDP를 사용하는 이유는 빠른 속도와 연결 상태를 유지하지 않고 정보 기록을 최소화하기 위함이다.

### 21. DNS 레코드가 무엇인가요?
    DNS 레코드란, 권한 있는 DNS 서버에 있는 명령으로서, 도메인에 연계된 IP 주소 및 해당 도메인에 대한
    요청의 처리 방법에 대한 정보를 제공한다. 해당 레코드는 DNS 구문으로 구성된다.
    모든 DNS 레코드는 TTL이 존재하며 계속 새로고침 된다.

# Reference
[HTTP 메세지](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages) <br/>
[HTTP 메서드](https://velog.io/@cv_/GET-vs-POST-PUT-vs-PATCH-%EA%B0%81%EA%B0%81%EC%9D%98-%EC%B0%A8%EC%9D%B4) <br/>
[HTTP 상태 코드](https://hongong.hanbit.co.kr/http-%EC%83%81%ED%83%9C-%EC%BD%94%EB%93%9C-%ED%91%9C-1xx-5xx-%EC%A0%84%EC%B2%B4-%EC%9A%94%EC%95%BD-%EC%A0%95%EB%A6%AC/) <br/>
[TCP keep-alive vs. HTTP keep-alive](https://sabarada.tistory.com/262) <br/>
[HTTP 커넥션](https://developer.mozilla.org/en-US/docs/Web/HTTP/Connection_management_in_HTTP_1.x) <br/>
[HTTP 발전](https://developer.mozilla.org/en-US/docs/Web/HTTP/Evolution_of_HTTP) <br/>
[SSL/TLS](https://aws.amazon.com/ko/compare/the-difference-between-ssl-and-tls/) <br/>
[TSL 핸드셰이크](https://www.cloudflare.com/ko-kr/learning/ssl/what-happens-in-a-tls-handshake/) <br/>
[DNS](https://kghworks.tistory.com/126) <br/>
[DNS 레코드](https://www.cloudflare.com/ko-kr/learning/dns/dns-records/) <br/>


