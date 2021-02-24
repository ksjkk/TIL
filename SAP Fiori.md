# SAP Fiori
#### SAP Web 화면
* Tile 테스트
    * CBO 로 개발한것
    * TCODE
    * Fiori Library 찾아서 개발

* Fiori Tcode
    * /UI2/FLPD_CUST
    * /UI2/FLP

* PFCG 권한에서 사용자 등록해야 보임

1. /UI2/FLPD_CUST > 카탈로그 생성
2. +(생성) > '어플리케이션 런처 - 정적'
    * KSB5N,MSC3N
3. 생성후 > 대상매핑 > 대상맵핑생성
4. 그룹생성 > 타일추가
5. Tcode : PFCG
6. 단일역할생성
7. 메뉴 : 생성했던 그룹, 카탈로그 등록
8. 권한 > 권한데이터 조회 > 생성
9. 사용자