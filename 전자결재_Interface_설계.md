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