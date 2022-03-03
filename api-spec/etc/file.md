# 파일 업로드
프로그램 매뉴얼 등의 파일을 시스템에 업로드합니다.
## URL
* /api/sign/file/upload
* POST
* multipart/form-data;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*file|img1.jpg|File|파일|
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|fileName|img1.jpg|String|업로드 파일 이름|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "fileName": "img1.jpg"
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 파일 다운로드 
시스템에 업로드되어 있는 매뉴얼 등의 파일을 다운로드합니다.
## URL
* /api/sign/file/download
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*fileName|img1.jpg|String|확장자를 포함한 파일 이름|
```
?fileName="img1.jpg"
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|fileBinary|dGVzdA==|String|Base64 인코딩 파일 바이너리|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "fileBinary": "dGVzdA=="
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```
대상 파일 없음
```json
{
    "clientMessage": "해당 파일이 없습니다.",
    "code": 500,
    "data": {
        "fileBinary": null
    },
    "messageCode": -1026,
    "serverMessage": "File Not Found"
}
```