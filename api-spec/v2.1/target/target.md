# 변경 대상 추가
DB 데이터 변경 요청서 변경 대상을 추가합니다.
## URL
* /api/sign/doc/dataModify/target
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dbType|11|int|Petra db type|
|*dataModifyName|테스트|String|변경 대상명|
|*dbAccount|hr|String|DB 계정|
|*dbPassword|hr|String|DB 비밀번호<br>저장 시 암호화|
|dbCharacterSet||String|DB 캐릭터 셋<br>강제 인코딩 용|
|signCharacterSet||String|SIGN 캐릭터 셋<br>강제 인코딩 용|
|*jdbcUrl|jdbc:oracle:thin:@1.1.1.1:1521:ora10r2|String|JDBC URL|
|*maxVerifyDataCnt|1000|int|검증 데이터 최대 저장 건수|
|maxExecCnt|1000|int|최대 실행 건수(기본값 : 무제한)|
```json
{
    "dbType": 11,
    "dataModifyName": "테스트",
    "dbAccount": "hr",
    "dbPassword": "hr",
    "dbCharacterSet": "",
    "signCharacterSet": "",
    "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:prod",
    "maxVerifyDataCnt": 1000,
    "maxExecCnt": 1000
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
