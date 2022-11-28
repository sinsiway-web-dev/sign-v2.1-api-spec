# SQL 제약 조건
DB 데이터 변경 요청서 작성 시 DB 데이터 변경 SQL 제약 조건을 조회
## URL
* /api/sign/doc/dataModify/sqlVerify/info/all
* GET
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|sqlVerifyInfo||Array|SQL 검증 정보|
|dataModifySqlType|1|int|적용 SQL 종류<br>1 : 변경 SQL<br>2 : 변경 전 데이터 조회 SQL<br>3 : 변경 후 데이터 조회 SQL|
|sqlVerifyTextInfo||Array|SQL 검증 문장 정보|
|textType|1|int|SQL 검증 문장 종류<br>1 : 일반 문장<br>2 : 정규식|
|textMean|5|int|SQL 검증 문장 의미<br>1 : 그외<br>2 : SQL 종류<br>3 : 테이블<br>4 : 컬럼<br>5 : 조건|
|textCheckType|1|int|SQL 검증 문장 확인 종류<br>1 : 필수<br>2 : 사용 불가능|
|text|WHERE|String|SQL 검증 문장|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "code": 200,
    "messageCode": 200,
    "serverMessage": "success",
    "clientMessage": "처리되었습니다.",
    "data": {
        "sqlVerifyInfo": [
            {
                "dataModifySqlType": 1,
                "sqlVerifyTextInfo": [
                    {
                        "textType": 1,
                        "textMean": 5,
                        "textCheckType": 1,
                        "text": "WHERE"
                    }
                ]
            }
        ]
    }
}
```

---

# 승인 요청
작성 완료된 DB 데이터 변경 요청서를 생성 합니다.
## URL
* /api/sign/doc/dataModify/ask
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|selectBeforeDataCountFlag|false|boolean|변경 전 데이터 조회 여부<br/>true : 조회<br/>false : 조회 안함|
|orgUid|u01|String|기안자 ID|
|apvLineApprover||Array|결재자 목록|
|approveOrder|1|int|결재 순서|
|approvePowerType|0|int|결재 권한 종류<br/>0 : 결재<br/>1 : DB데이터변경실행|
|approverOrgUid|m01|String|결재자 ID|
|executant|dba01|String|실행자 ID|
|aprvLimit|2021/05/05|String|결재 기한|
|docTitle|\[변경\] DB데이터변경|String|문서 제목|
|describe|DB데이터변경사유|String|사유|
|groundsDocId|근거-001|String|근거 문서 번호|
|groundsDocType|0|int|근거 문서 종류<br/>현대 캐피탈(0 : 공통 / 1 : 캐피탈 / 2 : Auto 지점용)|
|dataModifyTargetId|34|int|변경 대상 ID|
|beforeSql|select * from emp_sign where empno=1001|String|변경 전 검증SQL|
|afterSql|select * from emp_sign where empno=1002|String|변경 후 검증SQL|
|dataModiSqlType|1|int|변경 SQL종류<br/>1 : 기본SQL<br/>2 : PL/SQL|
|dataModiSql|update emp_sign set empno=1002 where empno=1001|String|변경 SQL|
```json
{
    "selectBeforeDataCountFlag": false,
    "orgUid": "u01",
    "apvLineApprover": [
        {
            "approveOrder": 1,
            "approvePowerType": 0,
            "approverOrgUid": "m01"
        },
        {
            "approveOrder": 2,
            "approvePowerType": 1,
            "approverOrgUid": "dba01"
        }
    ],
    "executant": "dba01",
    "aprvLimit": "2021/05/05",
    "docTitle": "[변경] DB데이터변경",
    "describe": "DB데이터변경사유",
    "groundsDocId": "근거-001",
    "dataModifyTargetId": "34",
    "beforeSql": "select * from emp_sign where empno=1001",
    "afterSql": "select * from emp_sign where empno=1002",
    "dataModiSqlType": 1,
    "dataModiSql": "update emp_sign set empno=1002 where empno=1001"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docId|2021000005|String|결재 문서 번호|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "docId": "2021000005"
    },
    "message": ""
}
```

---

# 결재 문서 무효화
결재 문서를 무효화 처리합니다.<br>
무효화 처리된 결재 문서는 조회 API를 통해 조회 불가능합니다.

## URL
* /api/sign/doc/invalid
* PUT
* application/json;charset=UTF-8

## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|docId|2021000001|String|결재 문서 번호|

```json
{
    "docId": "2021000001"
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
