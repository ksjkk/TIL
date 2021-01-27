# SAP PO
## SAP PI만 사용중, CE:포탈개념.. -> 공식 PO

* 인터페이스 방식
    * DBCO : DB Connect
    * RFC
    * PO

- ENTERPRISE SERVICES REPOSITORY(ESR) : 개발
- INTEGRATION DIRECTORY :  어디로 보낼거냐
- ADAPTER ENGINE : 보낸다

+ SAP
+ SAP-PO
+ LEGACY
    + REST ADAPTER
    + FILE/FTP ADAPTER
    + SOAP ADAPTER
    + REST ADAPTER

```
1. 시스템 정보 확인
2. 인터페이스 방식 설정
    2-1. Synchronous : 동기식 -> 보내고 확인까지 하는 부분
    2-2. Asynchronous : 비동기식 -> 보내고 끝
    2-3. Application 방식 : ex) Rest
    2-4. Data Get 방식 : ex) Api DB
```

## 개발
0. 정의서 : SAP -> APS TABLE DATA INSERT
1. System Landscape Directory
    0. 개발 순서를 꼭 지켜줘야함.
    1. Products
        1. 설치되어있는 Products가 왼쪽에 표시됨
        2. By Product > New.. 버튼 클릭
        3. Create a new product and version
        4.  Name : ILDONG_EDU02  VENDOR : ildong.com  VERSION : 1.0
        5. INSTANCE NAME : EDU02
        6. NAME FORMAT : ERP_`<MODULE>`
        7. FINISH
    2. Software Components
    3. Technical Systems(논리적주소)
    4. Business Systems(물리적주소)