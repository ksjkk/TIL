# SAP - CO 인수인계

## 1. 인터페이스
## 2. 예산

```
se80
package : ZCO01
```

### 예산
+ 전사시스템에서 요청 (PO쪽)
+ 예산체크
    + FUNCTION : ZCO_FG02 > ZCO_BUDGET_CHECK_DOC
    + 예산은 CBO 실적은 SD
+ 예산/실적 조회(ZCOR0050)
    + 예산등록은 계속해도됨(덮어씀)
    + 추가예산은 가감
    + 실적합계 / 가용예산 => 제일 중요
    + 실적(승인 + 미승인) => 결산전표는 빠짐( F로 시작 )
    + 결산기준실적( 실적(승인 + 미승인) + 결산전표 ) => 크게 의미없음(단순조회용)
    + 견본비 : 회계전표 안읽고 SD쪽 파일읽음(견본비 계정이 아닌 그룹으로 통제걺)
+ 내부오더생성
    + PMS 과제생성시 Send(PO Interface)
    + 등록된 내부오더별 예산등록
+ 견적원가
    + 통 CBO
    + 실적과 견적원가는 CO가 주체가 되어 데이터 던져줌(SO) / 요청받아서 처리는 SI
    + BATCH 아님, 버튼클릭으로 전송

### 전표실적(ZCOR0640)
+ 너무 많아서 BATCH로(당월은 30분단위)(전월은 새벽에 하루에 1번)