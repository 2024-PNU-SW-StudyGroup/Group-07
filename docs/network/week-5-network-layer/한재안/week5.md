# 네트워크 5주차 - Network Layer

## 📌 IP

---

### 1. IP주소에 대해서 설명해주세요.
     IP주소는 네트워크상의 장치를 식별하는 고유한 주소이다.
    네트워크 부분과 호스트 부분으로 구성되며,
    논리적 주소체계를 갖고,
    32비트(IPv4) 또는 128비트(IPv6)로 구성된다.

### 2. IPV4와 IPV6는 어떤 차이점이 있을까요?
     IPv4:
    32비트 주소체계 (약 43억개)
    10진수로 표현
    단순한 헤더 구조
    NAT로 주소 부족 문제 해결

     IPv6:
    128비트 주소체계 (거의 무한대)
    16진수로 표현
    확장된 헤더 구조
    자동 구성 기능
    보안 기능 내장
    QoS 지원 강화

### 3. 서브넷과 서브넷 마스크에 대해 설명해주세요.
     서브넷:
    큰 네트워크를 작은 네트워크로 분할
    네트워크 관리 효율성 증가
    브로드캐스트 도메인 분리

     서브넷 마스크:
    네트워크 부분과 호스트 부분 구분
    연속된 1과 0으로 구성
    CIDR 표기법 사용 (예: /24)
    IP 주소와 AND 연산으로 네트워크 주소 계산

### 4. 라우팅이 뭘까요?
     라우팅은 패킷의 최적 경로를 결정하는 과정이다.
    라우팅 테이블을 통해 최적 경로 결정 알고리즘 적용해 최적 경로를 찾는다.
    정적/동적 라우팅 방식 존재하고,
    네트워크 토폴로지 변화 대응할 수 있다.

### 5. Public IP와 Private IP 차이는 뭘까요?
     Public IP:
    인터넷에서 직접 접근 가능
    전 세계적으로 유일한 주소
    ISP에서 할당
    비용 발생
    
     Private IP:
    내부 네트워크에서만 사용
    인터넷 직접 접속 불가
    특정 대역 예약 (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16)
    NAT를 통해 인터넷 접속

### 6. 라우팅 프로토콜에 대해서 설명해주세요.
     내부 라우팅 프로토콜(IGP):
    RIP: 홉 카운트 기반
    OSPF: 최단 경로 우선
    EIGRP: 시스코 전용
    
     외부 라우팅 프로토콜(EGP):
    BGP: 자율 시스템 간 라우팅

### 7. IP는 어떻게 할당될까요?
     정적 할당:
    수동으로 IP 주소 설정
    서버나 네트워크 장비에 주로 사용
    관리자가 직접 설정
    호스트 파일 사용
    
     동적 할당:
    DHCP 서버 사용
    자동으로 IP 주소 할당
    임대 시간 개념 적용
    효율적인 IP 관리 가능
    ARP Spoofing에 취약

### 8. NAT가 뭘까요?
     NAT란, Network Address Translation의 약자로, IP를 변환하는 것으로
    사설 네트워크에 속한 여러 개의 호스트가 하난의 공인 IP 주소를 사용해 인터넷에 접속하기 위해 사용한다.

     NAT의 동작 방식:
    1. Static NAT (1:1 변환)
      - 내부 사설 IP와 외부 공인 IP가 1:1로 매핑
      - 주로 서버에 사용
      - 고정적인 매핑 테이블 유지
    2. Dynamic NAT (N:M 변환)
      - 사설 IP 풀을 공인 IP 풀로 변환
      - 실시간으로 매핑 테이블 생성/삭제
      - 공인 IP가 부족할 수 있음
    3. PAT/NAPT (N:1 변환)
      - 여러 사설 IP를 하나의 공인 IP로 변환
      - 포트 번호로 각 연결 구분
      - 가장 널리 사용되는 방식
    
     NAT의 장점:
    1. IP 주소 절약
      - IPv4 주소 부족 문제 해결
      - 하나의 공인 IP로 여러 기기 연결
    2. 보안 강화
      - 내부 네트워크 구조 은닉
      - 외부에서 직접 접근 차단
      - 방화벽 역할 수행
    3. 유연한 네트워크 설계
      - ISP 변경 시 내부 주소 유지
      - 네트워크 통합/분리 용이
    
     NAT의 단점
    1. 성능 저하
      - 패킷 변환 과정에서 지연 발생
      - NAT 장비에 부하 집중
    2. 일부 응용프로그램 제약
      - P2P 통신 어려움
      - 특정 프로토콜 동작 불가
      - End-to-End 연결성 저하
### 9. ICMP가 뭘까요?
     ICMP란, Internet Control Message Protocol의 약자로, 네트워크 장치에서 네트워크 통신 문제를 진단하는 데
    사용하는 네트워크 계층 프로토콜이다.

     ICMP 메시지 유형:
    오류 보고 메시지
    1. Destination Unreachable (Type 3)
      - Network Unreachable
      - Host Unreachable
      - Protocol Unreachable
      - Port Unreachable
    2. Time Exceeded (Type 11)
      - TTL Exceeded
      - Fragment Reassembly Time Exceeded
    3. Parameter Problem (Type 12)
    4. Source Quench (Type 4)
    5. Redirect (Type 5)
     질의 메시지
    1. Echo Request/Reply (Type 8/0)
    2. Timestamp Request/Reply (Type 13/14)
    3. Information Request/Reply (Type 15/16)
    4. Address Mask Request/Reply (Type 17/18)
    
     ICMP 활용 도구:
    ping
      - Echo Request/Reply 사용
      - 목적지 도달 가능성 확인
      - RTT(Round Trip Time) 측정
      - 패킷 손실률 확인
    traceroute
      - TTL 값을 조절하여 경로 추적
      - Time Exceeded 메시지 활용
      - 각 홉(hop)별 지연 시간 측정
      - 네트워크 병목 구간 파악

     ICMP의 특징:
    신뢰성
      - 비연결형 프로토콜
      - 메시지 전달 보장 없음
      - 에러 보고도 손실될 수 있음
    보안 관련
      - 네트워크 스캐닝에 악용 가능
      - 일부 네트워크에서 ICMP 차단
      - 제한적인 사용 권장
    네트워크 관리
      - 네트워크 문제 진단
      - 성능 모니터링
      - 라우팅 최적화

     ICMP 제한 사항:
    크기 제한
      - 최소 8바이트 헤더
      - IP 패킷 크기 제한 적용
    우선순위
      - 일반 데이터보다 낮은 우선순위
      - 네트워크 혼잡 시 폐기 가능
    처리 제한
      - ICMP 에러에 대한 ICMP 에러 미생성
      - 브로드캐스트/멀티캐스트 제한
      - 단편화된 패킷 제한