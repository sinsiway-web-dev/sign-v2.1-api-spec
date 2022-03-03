# JDBC - 연결 테스트
보안 대상 DB 상태 확인에 사용하는 JDBC 연결 테스트 입니다.
## URL
* /api/sign/jdbc/connectionTest
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dbType|11|int|Petra db type|
|*jdbcUrl|jdbc:oracle:thin:@192.168.10.110:1522:prod|String|JDBC URL|
|*dbAccount|hr|String|DB 계정|
|*dbPassword|hr|String|DB 비밀번호|
```
?dbType=11&jdbcUrl=jdbc:oracle:thin:@192.168.10.110:1522:prod&dbAccount=hr&dbPassword=hr
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