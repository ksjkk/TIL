KPI Renewal
==============================
KPI 재설계 및 eHR 모듈화 이관
------------------------------
### 일반/영업/계열사/연구소

1. 그룹코드관리
    * 항목구분
        + 재무성과 / S&OP / 혁신과제 / GWP / 직무과제
    * 평가구분
        + 정량
        + 정성
            + 기대효과
            + Milestone
            + BARS
            + 표준화
            + Checklist
            + Survey
    * 연평가기준
        + 정량
            + 연평균
            + 연말(12월)
            + 본인입력
            + 자동화
        + 정성
    * 자동화항목 당성률/평점 입력방식(사용자)
        + 입력불가
        + 평점만 입력
        + 달성률만 입력
        + 달성률, 평점 모두 입력
    * 조직구분
        + 회사
        + 부문(본부/부문/실)
        + 부서(팀/파트↑/그룹↓)
    * 영업유통구분
        + 의원
        + 병원
        + 약국

2. DB Item 관리
    * 자동화항목 달성률, 평점 계산식

3. KPI조직관리
    * 연간,월간 생성 관리
    * 회사 > 연/월구분 > 연 > 월 > 부문/부서구분 > 부문코드 > 부서코드 > 부서명 > 조직장사번 > 조직평가자사번
    * 부서 > 상위부서장(그룹장 or 부문장)평가
    * 부문 > 부사장(COO)평가

4. 평가대상자관리
    * 생성기준 관리(성과연봉직 기준 등) ※ 휴직자는 어떻게 할것인지 체크
    * 연간,월간 생성 관리
    * 회사 > 연/월구분 > 연 > 월 > 부문/부서코드 > 사번 > 이름 > 평가자사번
    * 파트원 > 파트장평가
    * 파트장 > 팀장평가
    * 팀원 > 팀장평가

5. 항목관리
    * 조직의 항목은 일괄 업로드
    * 개인의 항목은 조직의 항목을 끌어오거나, 개인이 직접 등록
    * 전체항목관리
    * 자동화항목관리
    
6. 조직 항목, 실적 등록자(조직장 제외)
    * default 조직장 등록
    * 회사 > 연/월구분 > 부서코드 > 사번 > 이름 > 시작(년/년월) > 종료(년/년월) > 사유