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
        1. 생성한 Products 확인
    3. Technical Systems(논리적주소)
        1. New Technical System
        2. Third-Party
        3. 내가만든 Product 선택
        4. Business Stystems 탭 선택
    4. Business Systems(물리적주소)
        1. Add New Business System
        2. Logical System Name : EDU02
        3. Name : EDU02
        4. 선택
        5. Related Integration Server : INTEGRATION_ENGINE_JAVA_POD
2. Enterprise Services Builder
    1. Ctrl+N > WOrks Areas > Software Component Version
    2. Import from SLD > 내가만든SLD 선택
    3. English 선택후 저장
    4. Namespace > Open
    5. 저장버튼 옆에 연필버튼(Edit)
    6. Name : URL입력(http포함)
        * #3416 PO Interface List 참고
        * NameFormat : ildong.com/@@@_### -> @@@에서 ### 으로
    7. 왼쪽상단탭 > Change Lists > 2 level 우클릭 > Activate..
    8. Design Objects 탭에서 해당 url 우클릭 > New > Data Types
        * NameFormat : IF@이름@_@@@_S_DT(SOURCE DATA)
        * NameFormat : IF@이름@_###_T_DT(TARGET DATA)
    9. SOURCE Data Type 생성 > @@@ ERP면 SAP 테이블 구조
    10. TARGET Data Type 생성 > ### Legacy DB면 DB 테이블 구조