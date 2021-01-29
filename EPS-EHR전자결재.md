## 전자문서 생성 및 확인로직

1. `EHR` eHR에서 문서양식을 생성
2. `EPS` EPS 관리자CMS > 업무시스템관리 > 전자결재 > 양식관리 에서 양식키 생성 WF_EHR_@@LPAD(APPL_CD,3,'0')@@
3. `EPS` 생성했으면 쿼리조회 및 데이터생성

```sql
1. 관리자쪽에서 생성함
    SELECT  *
    FROM    COVI_APPROVAL4J.JWF_FORMS
    WHERE   FORMPREFIX = 'WF_EHR_@@LPAD(APPL_CD,3,'0')@@';
FORMID 체크후

2. DB에 INSERT
    SELECT  *
    FROM    COVI_APPROVAL4J.JWF_FORMSLEGACY
    WHERE   LEGACYFORM = 'WF_EHR_@@LPAD(APPL_CD,3,'0')@@';
INSERT(ID_는 자동생성, TRIGGER 걸려있음)
```

4. `EHR` applCommon통해 Data Send
5. `EPS` 데이터 조회

```sql
1. 로그성이기 때문에 데이터 수정해도 반영X
    SELECT  *
    FROM    COVI_APPROVAL4J.ACT_LEGACY_FOR_EHR_HISTORY
    WHERE   LEGACYKEY = '@@APPL_SEQ@@';
FORMINSTID : Form Instance Id를 확인
2. 데이터확인
    SELECT  *
    FROM    COVI_APPROVAL4J.JWF_FORMINSTANCE
    WHERE   FORMINSTID = '@@FORMINSTID@@';
데이터가 ENCODING 되어 저장됨.
데이터수정은 관리자CMS에서 진행하는것이 좋음.

3. 단순확인 : EPS 관리자CMS > 업무시스템관리 > 전자결재 > 결재문서 관리툴
4. 본문수정 : EPS 관리자CMS > 업무시스템관리 > 전자결재 > 결재문서 관리툴 > 문서속성 > 본문클릭 > 본문수정후 저장
```

6. `EPS` 인터페이스 오류 확인
```sql
    SELECT  *
    FROM    COVI_APPROVAL4J.JWF_LEGACY
    WHERE   MODE_ = 'LEGACY'
    AND     STATE = 'error'
    AND     DELETETIME IS NULL
    AND     FORMPREFIX LIKE 'WF_EHR%';
```

***

## 배포
```bash
cd /devp/app/groupware/UI/approval/WEB-INF/views/forms/templates/   > 개발
cd /prd/app/groupware/UI/approval/WEB-INF/views/forms/templates/    > 운영
```

***

## 결재완료시 프로시저
> Redis에 프로시저명 저장되어있고 java에서 가져옴<br/>
> Redis에 프로시저명과 Cron 설정<br/>
> `EPS` EPS 관리자CMS > 시스템관리 > 기초설정관리 > 설정키 EHR 조회
```java
fileName : FormCmmFunctionSvcImpl.java
method : execApvStatusforEHR

fileName : legacy_formCmmFunction.xml(oracle)
id : selectApvStatusForEHR
mapping되는것 확인해볼것
```