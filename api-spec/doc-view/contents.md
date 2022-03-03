# 상세 내용
작성된 DB 데이터 변경 요청서의 상세 내용을 조회합니다.
## URL
* /api/sign/doc/dataModify/contents
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2021000005|String|결재 문서 번호|
|*orgUid|u01|String|사용자 ID|
```
?docId=2021000005&orgUid=u01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|approver||Array|결재자 정보|
|approveOrder|1|int|결재 순번|
|approvePowerType|0|int|결재 권한 종류<br/>0: 결재<br/>1: DB데이터변경실행|
|approveStatus|1|int|결재 상태<br/>1: 결재 전<br/>2: 승인<br/>3: 반려<br/>4: 후결|
|approveDescribe||String|첨언|
|approveDate||String|결재일|
|approverName|결재자01|String|결재자 이름|
|approverOrgUid|m01|String|결재자 ID|
|approverTitle||String|결재자 직위|
|approverOrgItemName|연구소|String|결재자 조직명|
|agentApproverName||Sting|대리결재자 이름|
|agentApproverOrgUid||String|대리결재자 ID|
|agentApproverTitle||String|대리결재자 직위|
|agentApproverOrgItemName||String|대리결재자 조직명|
|dataModifyInfo||Map|변경 실행 정보|
|execResult|0|int|실행 결과<br/>0: 실행 전<br/>1: 실행완료(성공)<br/>2: 실행완료(실패)<br/>8: 결재 반려|
|execResultMessage||String|실행 결과 메시지|
|beforeCount|0|int|변경 전 데이터 건수|
|afterCount|0|int|변경 후 데이터 건수|
|beforeSql|select * from emp_sign where empno=1001|String|변경 전 검증SQL|
|afterSql|select * from emp_sign where empno=1002|String|변경 후 검증SQL|
|dataModifySql||Array|변경 SQL 목록|
|sqlType|1|int|변경 SQL 종류<br/>1: 기본SQL<br/>2: PL/SQL|
|sqlText|update emp_sign set empno=1002 where empno=1001|String|변경 SQL|
|doc||Map|결재 문서 정보|
|currentState|6|int|결재 문서 상태<br/>0 : 작성중<br/>1 : 요청<br/>2 : 승인<br/>3 : 반려<br/>4 : 후결<br/>5 : 유효 기간 경과<br/>6 : 무효<br/>7 : 권한 부여 승인<br/>8 : 권한 부여 반려<br/>9 : 권한 회수<br/>10 : 실행 완료<br/>11 : 실행 불가<br/>12 : 권한 부여 유효 기간 경과<br/>13 : 결재 진행 중|
|currentApproveOrder|1|int|결재 중인 결재자 순번|
|docId|2021000005|String|결재 문서 번호|
|groundsDocId|근거-001|String|근거 문서 번호|
|createDate|2021/04/28 11:30:04|String|기안일|
|aprvLimit|2021/05/05|String|결재 기한|
|requestOrgUid|u01|String|기안자 ID|
|requestName|사용자01|String|기안자 이름|
|docTitle|\[변경\] DB데이터변경|String|문서 제목|
|requestDescribe|DB데이터변경사유|String|요청 사유|
|dataModifyTarget||Map|변경 대상 정보|
|dbAccount|scott|String|DB계정명|
|dataModifyTargetId|34|String|변경 대상 ID|
|dataModifyTargetName|PROD|String|변경 대상명|
|dbTypeText|ORACLE|String|DB종류|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "approver": [
            {
                "approveOrder": 1,
                "approvePowerType": 0,
                "approveStatus": 1,
                "approveDescribe": "",
                "approveDate": "",
                "approverName": "결재자01",
                "approverOrgUid": "m01",
                "approverTitle": "",
                "approverOrgItemName": "연구소",
                "agentApproverName": "",
                "agentApproverOrgUid": "",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": ""
            },
            {
                "approveOrder": 2,
                "approvePowerType": 1,
                "approveStatus": 1,
                "approveDescribe": "",
                "approveDate": "",
                "approverName": "dba01",
                "approverOrgUid": "dba01",
                "approverTitle": "",
                "approverOrgItemName": "연구소",
                "agentApproverName": "",
                "agentApproverOrgUid": "",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": ""
            }
        ],
        "dataModifyInfo": {
            "execResult": 0,
            "execResultMessage": "",
            "beforeCount": "0",
            "afterCount": "0",
            "beforeSql": "select * from emp_sign where empno=1001",
            "afterSql": "select * from emp_sign where empno=1002",
            "dataModifySql": [
                {
                    "sqlType": 1,
                    "sqlText": "update emp_sign set empno=1002 where empno=1001"
                }
            ]
        },
        "doc": {
            "currentState": 6,
            "currentApproveOrder": 1,
            "docId": "2021000005",
            "groundsDocId": "근거-001",
            "createDate": "2021/04/28 11:30:04",
            "aprvLimit": "2021/05/05",
            "requestOrgUid": "u01",
            "requestName": "사용자01",
            "docTitle": "[변경] DB데이터변경",
            "requestDescribe": "DB데이터변경사유"
        },
        "dataModifyTarget": {
            "dbAccount": "scott",
            "dataModifyTargetId": "34",
            "dataModifyTargetName": "PROD",
            "dbTypeText": "ORACLE"
        }
    },
    "message": ""
}
```


# 변경 전 데이터
DB 데이터 변경 실행 완료 후 로그로 기록된 변경 전 데이터를 조회합니다.
## URL
* /api/sign/doc/dataModify/saveBeforeData
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2021000001|String|결재 문서 번호|
|*dataDecryptionFlag|1|int|복호화 여부<br/>0 : 복호화 안함<br/>1 : 복호화<br>(기본값 - 암호문은 복호화, 평문은 평문 출력)|
```
?docId=2021000001&dataDecryptionFlag=1
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docId|2021000001|String|결재 문서 번호|
|beforeData||Map|변경 전 데이터|
|column||Array|컬럼|
|data||Array|데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "docId": "2021000001",
        "beforeData": {
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


# 변경 후 데이터
DB 데이터 변경 실행 완료 후 로그로 기록된 변경 후 데이터를 조회합니다.
## URL
* /api/sign/doc/dataModify/saveAfterData
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2021000001|String|결재 문서 번호|
|*dataDecryptionFlag|1|int|복호화 여부<br/>0 : 복호화 안함<br/>1 : 복호화<br>(기본값 - 암호문은 복호화, 평문은 평문 출력)|
```
?docId=2021000001&dataDecryptionFlag=1
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docId|2021000001|String|결재 문서 번호|
|afterData||Map|변경 후 데이터|
|column||Array|컬럼|
|data||Array|데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "docId": "2021000001",
        "afterData": {
            "column": [
                " EMPNO",
                " ENAME",
                " SAL"
            ],
            "data": [
                [
                    " 1002",
                    " TEST01",
                    " 999"
                ]
            ]
        }
    },
    "message": ""
}
```