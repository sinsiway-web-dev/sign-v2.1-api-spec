# SQL 문법 검사 - DB 데이터 변경 요청서
DB 데이터 변경 대상 ID로 DB 연결 정보를 조회한 후 SQL 문법 검사를 수행합니다.

## URL
* /api/sign/sql/grammarCheck/dataModify
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|dataModifyTargetId|1|int|DB 데이터 변경 대상 ID|
|grammarCheckSql|select * from|String|문법 검사할 SQL|
```
{
    "dataModifyTargetId" : 1,
    "grammarCheckSql" : "update emp; select * from emp;"
}
```
## Response
### 성공
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|failSql||SQL|문법 검사 실패 SQL|

```json
{
    "code": 200,
    "messageCode": 200,
    "serverMessage": "success",
    "clientMessage": "처리되었습니다.",
    "data": {
        "failSql": ""
    }
}
```
### 실패
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|500|int|결과 코드|
|messageCode|-500|int|결과 메시지 코드|
|serverMessage|sql.SQLSyntaxError : ORA-00971: missing SET keyword\n|String|서버용 결과 메시지
|clientMessage|처리에 실패하였습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|failSql|update emp|SQL|문법 검사 실패 SQL|

```json
{
    "code": 200,
    "messageCode": 200,
    "serverMessage": "success",
    "clientMessage": "처리되었습니다.",
    "data": {
        "failSql": "update emp"
    }
}
```
