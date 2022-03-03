# 변경 예상 개수
DB 데이터 변경 실행 전 상태에서 변경 예상 데이터 개수를 조회합니다.
## URL
* /api/sign/doc/dataModify/beforeDataCount
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2021000006|String|결재 문서 번호|
|*execOrgUid|dba01|String|실행자 ID|
```
?docId=2021000006&execOrgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|dataCount|1|int|변경 예상 데이터 개수|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "dataCount": 1
    },
    "message": ""
}
```


# 변경 실행
DB 데이터 변경 요청서의 DB 데이터 변경을 수행합니다.
## URL
* /api/sign/doc/dataModify/modify
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dataEncryptionFlag|0|int|암호화 여부<br/>0 : 평문(기본값)<br/>1 : 암호화|
|*docId|2021000006|String|결재 문서 번호|
|*execOrgUid|dba01|String|실행자 ID|
```json
{
    "dataEncryptionFlag": 0,
    "docId": "2021000006",
    "execOrgUid": "dba01"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
| executionResult|4|int|실행 결과<br/>0 : 실행 전<br/>2 : 실행 완료(실패)<br/>4 : 실행 미완료(성공)|
|executionFailSqlType|null|String|실패 SQL 종류<br/>1 : 변경 SQL<br/>2 : 변경 전 데이터 조회 SQL<br/>3 : 변경 후 데이터 조회 SQL|
|executionFailMessage|null|String|SQL 실패 메시지|
|executionLog|UPDATE 1\n|String|쿼리 실행 후 DB 응답 값|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "executionResult": 4,
        "executionFailSqlType": null,
        "executionFailMessage": null,
        "executionLog": "UPDATE 1\n"
    },
    "message": ""
}
```


# 변경 반려
DB 데이터 변경 요청서의 DB 데이터 변경 반려 처리를 수행합니다.
## URL
* /api/sign/doc/dataModify/reject
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approveOrder|1|int|결재 순서|
|*orgUid|user01|String|결재자 로그인 ID|
|*docId|2019000001|String|결재 문서 번호|
|*describe|반려합니다.|String|첨언|
```json
{
    "approveOrder":1,
    "orgUid":"user01",
    "docId":"2019000001",
    "describe":"반려합니다."
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```


# 변경 검증
DB 데이터 변경 커밋 전 상태에서 변경 후 데이터를 조회합니다. 실행 과정 내 검증 기능을 담당합니다.
## URL
* /api/sign/doc/dataModify/afterData
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2021000006|String|결재 문서 번호|
|*dataDecryptionFlag|1|int|복호화 여부<br/>0 : 복호화 안함<br/>1 : 복호화|
|execOrgUid|dba01|String|실행자 ID|
```
?docId=2021000006&dataDecryptionFlag=1&execOrgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|dataCount|1|int|변경 데이터 개수|
|afterData||Map|변경 후 데이터|
|column||Array|컬럼|
|data||Array|데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "dataCount": 1,
        "afterData": {
            "column": [
                " EMPNO",
                " ENAME",
                " SAL"
            ],
            "data": [
                [
                    " 1001",
                    " TEST01",
                    " 999"
                ]
            ]
        }
    },
    "message": ""
}
```


# 커밋
DB 데이터 변경 요청서의 DB 데이터 변경 내용을 커밋하고 변경 후 데이터 저장 및 DB 데이터 변경을 완료합니다.
## URL
* /api/sign/doc/dataModify/commit
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approveOrder|2|int|결재 순서|
|*describe|승인합니다|String|첨언|
|*docId|2021000006|String|결재 문서 번호|
|*execOrgUid|dba01|String|실행자 ID|
```json
{
    "approveOrder": 2,
    "describe": "승인합니다",
    "docId": "2021000006",
    "execOrgUid": "dba01"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리 되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|commitFailSqlType|null|int|커밋 실패 SQL 종류<br/>1 : 커밋<br/>2 : 변경 후 데이터 조회 SQL|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "commitFailSqlType": null
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 롤백
DB 데이터 변경 요청서의 DB 데이터 변경 내용을 롤백하고 DB 데이터 변경을 완료합니다.
## URL
* /api/sign/doc/dataModify/rollback
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approveOrder|2|int|결재 순서|
|*describe|승인합니다|String|첨언|
|*docId|2021000010|String|결재 문서 번호|
|*execOrgUid|dba01|String|실행자 ID|
```json
{
    "approveOrder": 2,
    "describe": "승인합니다",
    "docId": "2021000010",
    "execOrgUid": "dba01"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {},
    "message": ""
}
```