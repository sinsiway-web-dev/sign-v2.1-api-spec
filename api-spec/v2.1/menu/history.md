# SQL 실행 이력 조회
변경 대상에게 실행된 SQL 이력을 조회합니다.
## URL
* /api/sign/history/execSql
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDate|1736920800|int|검색 시작일(실행일)|
|*endDate|1737526473|int|검색 종료일(실행일)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|execName|김관리|String|실행자 이름|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|result|1|int|결과 </br>1: 성공</br>2: 실패|
```
{
  "startDate": "1736920800",
  "endDate": "1737526473",
  "docId": "2025000013",
  "docTitle": "데이터 변경 요청서 1",
  "requestName": "홍길동",
  "execName": "김관리",
  "dataModifyTargetName": "PROD01",
  "result": 1
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|execSqlHist| |Array|SQL 실행 이력 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|createDate|2025/04/28 11:30:04|String|기안일|
|execName|김관리|String|실행자 이름|
|execDate|2025/04/28 13:30:04|String|실행일|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|sql|UPDATE EMP SET EMPNO = 1001 WHERE EMP_ID = 'user01'|String|SQL|
|result|1|int|결과 </br>1: 성공</br>2: 실패|

[성공]
```json
{
    "code": 200,
    "data": {
        "execSqlHist": [
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 1",
            "requestName":"홍길동",
            "createDate":"2025/04/28 11:30:04",
            "execName":"김관리",
            "execDate":"2025/04/28 13:30:04",
            "dataModifyTargetName":"PROD01",
            "sql":"UPDATE EMP SET EMPNO = 1001 WHERE EMP_ID = 'user01'",
            "result":1
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"홍길동",
            "createDate":"2025/04/28 11:30:04",
            "execName":"김관리",
            "execDate":"2025/04/28 13:30:04",
            "dataModifyTargetName":"PROD01",
            "sql":"SELECT * from EMP WHERE EMPNO = 1001",
            "result":1
          }
        ]
    },
    "message": "처리되었습니다."
}
```

[데이터 없음]
```json
{
    "code": 204,
    "data": {
        "execSqlHist": []
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "execSqlHist": []
    },
    "message": "처리에 실패하였습니다."
}
```
