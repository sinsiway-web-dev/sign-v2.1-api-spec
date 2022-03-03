# SQL 문법 검사
실행 계획(Query Plan)을 활용해 SQL 문법 검사를 수행합니다.
단, ORACLE(EXPLAIN PLAN FOR)과 MySQL(EXPLAIN)만 가능

## URL
* /api/sign/sql/grammarCheck
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|dbType|11|int|DB 종류|
|jdbcUrl|jdbc:oracle:thin:@1.1.1.1:1521:ora10r2|String|JDBC URL|
|dbAccount|scott|String|DB 계정명|
|encryptedDbPassword|5AUhf47BeGBlJZGMfo4TGwAA==AAUA|String|암호화된 DB 계정 비밀번호|
|grammarCheckSql|select * from|String|문법 검사할 SQL|
```
{
    "dbType" : 11,
    "jdbcUrl" : "jdbc:oracle:thin:@1.1.1.1:1521:ora10r2",
    "dbAccount" : "scott",
    "encryptedDbPassword" : "5AUhf47BeGBlJZGMfo4TGwAA==AAUA",
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
