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
|dbPassword|hr|String|DB 비밀번호<br>저장 시 암호화<br>`passwordFlag=1` 일 시 필수 입력<br>`passwordFlag=0` 일 시 빈값|
|*passwordFlag|1|int|비밀번호 입력 여부<br>1: 변경 대상 등록 시 입력<br>0: 문서 실행 시 입력|
|*jdbcUrl|jdbc:oracle:thin:@1.1.1.1:1521:ora10r2|String|JDBC URL|
|*maxVerifyDataCnt|1000|int|검증 데이터 최대 저장 건수|
|maxExecCnt|1000|int|최대 실행 건수(기본값 : 무제한)|
|dbCharacterSet||String|DB 캐릭터 셋<br>강제 인코딩 용|
|signCharacterSet||String|SIGN 캐릭터 셋<br>강제 인코딩 용|
```json
{
    "dbType": 11,
    "dataModifyName": "테스트",
    "dbAccount": "hr",
    "dbPassword": "hr",
    "passwordFlag": 1,
    "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:prod",
    "maxVerifyDataCnt": 10,
    "maxExecCnt": 10,
    "dbCharacterSet": "UTF-8",
    "signCharacterSet": "UTF-8"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|message||String|결과 메시지|
### 결과 코드
- 200 : 성공
- 201 : 변경 대상 이름 중복
- 그 외 : 실패
### 응답 예시
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {}
}
```

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
|dataModifyTargetName|PROD|String|변경대상명|
|dbAccount|scott|String|DB 계정명|
|dbPassword|암호화된비밀번호|String|DB 계정 비밀번호|
|passwordFlag|1|int|실행 시 비밀번호 입력 여부<br>1: 변경 대상 등록 시 입력<br>0: 문서 실행 시 입력|
|dbCharacterSet||String|DB 캐릭터 셋<br>강제 인코딩 용|
|signCharacterSet||String|변경 캐릭터 셋<br>강제 인코딩 용|
|jdbcUrl|jdbc:oracle:thin:@192.168.10.110:1522:PROD|String|JDBC URL|
|maxVerifyDataCnt|1000|int|검증 데이터 최대 저장 건수|
|maxExecCnt|1000|int|최대 실행 건수<br>1보다 작은 수: 무제한<br>1이상의 수: 해당 값으로 설정 됨|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "dataModifyTargetList": [
            {
                "dbType": 11,
                "dbTypeText": "ORACLE",
                "dataModifyTargetId": "4",
                "dataModifyTargetName": "테스트",
                "dbAccount": "hr",
                "dbPassword": "Kv2l0tDT7oiU/g0L+QGghkllm1wowKcGQl9IAe9a7piebwLakIG6bpqP46o0tbXJ",
                "dbCharacterSet": "",
                "signCharacterSet": "",
                "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:prod",
                "maxVerifyDataCnt": 10,
                "maxExecCnt": 10,
                "passwordFlag": 1,
            },
            {
                "dbType": 11,
                "dbTypeText": "ORACLE",
                "dataModifyTargetId": "13",
                "dataModifyTargetName": "테스트2",
                "dbAccount": "test",
                "dbPassword": "",
                "dbCharacterSet": "UTF-8",
                "signCharacterSet": "UTF-8",
                "jdbcUrl": "jdbc:oracle:thin:@192.168.10.110:1522:prod",
                "maxVerifyDataCnt": 10,
                "maxExecCnt": 0,
                "passwordFlag": 0
            }
        ]
    }
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
<br>

# 변경 대상 수정
DB 데이터 변경 요청서 변경 대상을 수정합니다.
## URL
* /api/sign/doc/dataModify/target
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dataModifyTargetId|34|String|변경대상ID|
|dbPassword|tiger|String|DB 비밀번호<br>`passwordFlag=1` 일 시 필수 입력<br>`passwordFlag=0` 일 시 빈값|
|*passwordFlag|1|int|실행 시 비밀번호 입력 여부<br>1: 변경 대상 등록 시 입력<br>0: 문서 실행 시 입력|
|*jdbcUrl|jdbc:oracle:thin:@1.1.1.1:1521:ora10r2|String|JDBC URL|
|*maxVerifyDataCnt|1000|int|검증 데이터 최대 저장 건수|
|maxExecCnt|1000|int|최대 실행 건수(0 : 무제한)|
|dbCharacterSet|UTF-8|String|DB 캐릭터 셋<br>강제 인코딩 용|
|signCharacterSet|UTF-8|String|SIGN 캐릭터 셋<br>강제 인코딩 용|
```json
{
    "dataModifyTargetId": 121,
    "dbPassword": "tiger",
    "passwordFlag": 0,
    "jdbcUrl": "jdbc:oracle:thin:@1.1.1.1:1521:ora10r2",
    "maxVerifyDataCnt": 10000,
    "maxExecCnt": 0,
    "dbCharacterSet": "",
    "signCharacterSet": ""
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