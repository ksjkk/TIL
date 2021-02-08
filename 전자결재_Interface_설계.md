# 전자결재 인터페이스 설계
1. 준비
 - apache(그룹웨어 개발)
    - CORS 설정
 - nginx(그룹웨어 운영)
    - CORS 설정

 - eHR(웹HR) -> HR결재문서 신청만 진행. 조회 및 결재는 그룹웨어에서 진행

 - Interface Methods
    - 전사시스템 : form.submit()
    - MISO : 서버단 java class, HttpURLConnection Class
    - eHR : REST API

 - eHR, async에서 상태체크
 - Lineworks Bot API로 미이관 데이터 알림 메세지 발송

 - meta tag : Content-Security-Policy 처리

2. 데이터 전송
 - 결재문서는 크게 결재정보 header(include), 본문 body 데이터로 나뉨
 - header data는 모든 문서의 공통사항으로 common include file에서 처리
 - 본문 body data는 form data를 json으로 변환함

```javascript
function getFormData($form){
    var unindexed_array = $form.serializeArray();
    var indexed_array = {};
    $.map(unindexed_array, function(n, i){
        indexed_array[n['name']] = n['value'];
    });
    return indexed_array;
}
```

 - 본문 body data중 grid 데이터에 대해서는 배열로 받고 json으로 변환
```javascript
// grid 없을때
sendDataToGw(getFormData($("#sendForm")),null);
sendDataToGw(getFormData($("#sendForm")),[]);

// grid 1개 일때
sendDataToGw(getFormData($("#sendForm")),[sheet1]);

// grid 2개일때
sendDataToGw(getFormData($("#sendForm")),[sheet1,sheet2]);
```

 - 데이터는 json 형태로 REST API를 통해서 전송함
 - 그룹웨어에서는 데이터를 json 형태 그대로 CLOB 타입 컬럼에 저장함
 - 본문에서는 JSON body를 가져와서 맵핑