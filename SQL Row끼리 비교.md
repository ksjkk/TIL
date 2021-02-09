# LAG / LEAD
## WHERE은 컬럼값을 비교하지만  한 ROW를 기준으로 다른 ROW의 값을 비교하고 싶을때 LAG/LEAD를 사용
## LAG는 다음, LEAD는 이전 ROW를 가져와 비교할수있음. 함수내 ORDER BY / DESC를 통해 동일하게 사용할 수 있음
```sql
LAG(APP_DATE) OVER (PARTITION BY ENTER_CD,SEQ,SABUN ORDER BY VER DESC) NEXT_APP_DATE
 = LEAD(APP_DATE) OVER (PARTITION BY ENTER_CD,SEQ,SABUN ORDER BY VER) NEXT_APP_DATE

-- SELECT 했을때 조회되는 다음 ROW의 값을 컬럼값으로 가져올 수 있음.
-- CONNECT 를 사용하지 않아도 되서 편리
```