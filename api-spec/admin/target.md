# 변경 대상 전체 조회
DB 데이터 변경 요청서 변경 대상(DB)을 모두 조회 합니다.
## URL
* /api/sign/doc/dataModify/target/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|dataModifyTargetList||Array|변경 대상 목록|
|dbType|11|int|petra db type|
|dbTypeText|ORACLE|String|DB 종류명|
|dataModifyTargetId|34|String|변경대상ID|
|dbPassword|암호화된비밀번호|String|DB 계정 비밀번호|
|dataModifyTargetName|PROD|String|변경대상명|
|dbAccount|scott|String|DB 계정명|
|dbCharacterSet||String|DB 캐릭터 셋<br>강제 인코딩 용|
|changeCharacterSet||String|변경 캐릭터 셋<br>강제 인코딩 용|
|jdbcUrl|jdbc:oracle:thin:@192.168.10.110:1522:PROD|String|JDBC URL|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "dataModifyTargetList": [
            {
                "dbType": 11,
                "dbTypeText": "ORACLE",
                "dataModifyTargetId": "34",
                "dbPassword": "5AUhf4...",
                "dataModifyTargetName": "PROD",
                "dbAccount": "scott",
                "dbCharacterSet": "",
                "signCharacterSet": "",
                "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:PROD"
            }
        ]
    },
    "message": ""
}
```


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
```json
{
    "dbType": 11,
    "dataModifyName": "테스트",
    "dbAccount": "hr",
    "dbPassword": "hr",
    "dbCharacterSet": "",
    "signCharacterSet": "",
    "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:prod"
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


# 변경 대상 삭제
DB 데이터 변경 요청서 변경 대상을 삭제합니다.
## URL
* /api/sign/doc/dataModify/target
* DELETE
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dataModifyTargetId|121|int|변경 대상 ID|
```json
{
    "dataModifyTargetId": 121
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


# 변경 대상 전체 삭제
DB 데이터 변경 요청서 전체 변경 대상을 삭제합니다.
## URL
* /api/sign/doc/dataModify/target/all
* DELETE
## Request
없음
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


# 변경 대상 비밀번호 확인
입력한 비밀번호가 DB 데이터 변경 대상의 접속 비밀번호가 맞는지 확인합니다. 변경 대상이 없거나 비밀번호가 올바르지 않은 경우 code 500으로 DB에서 전달 받은 에러 메시지를 message로 응답합니다.
## URL
* /api/sign/doc/dataModify/target/password
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dataModifyTargetId|119|String|변경 대상 ID|
|*dbPassword|hr|String|DB 비밀번호|
```
?dataModifyTargetId=119&dbPassword=hr
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


# 변경 대상 비밀번호 변경
관리자 권한을 갖고 있는 사용자가 DB 데이터 변경 요청서 변경 대상 비밀번호를 변경합니다.
## URL
* /api/sign/doc/dataModify/target/password
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|sa|String|관리자 ID|
|*dataModifyTargetId|119|String|변경 대상 ID|
|*dbPassword|hr|String|DB 비밀번호|
|*newDbPassword|hr|String|새 DB 비밀번호|
```json
{
    "orgUid": "sa",
    "dataModifyTargetId": "119",
    "dbPassword": "hr",
    "newDbPassword": "hr"
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
