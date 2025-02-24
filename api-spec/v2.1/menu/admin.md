# 전체 문서 조회
전체 DB 데이터 변경서를 조회합니다. 관리자만 조회 가능합니다.
## URL
* /api/sign/admin/doc/dataModify/all
* GET
* application/x-www-form-urlencoded; charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDateFrom|1736920800|int|검색 시작일(기안일 기준)|
|*startDateTo|1737526473|int|검색 종료일(기안일 기준)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|apvLimitFrom|1736920800|int|검색 시작일(결재 기한 기준)|
|apvLimitTo|1737526473|int|검색 종료일(결재 기한 기준)|
|approverName|결재자|String|현재 결재자 이름|
|approverPowerType|1|String|결재자 권한<br>1: 결재<br>2: 실행|
|rejectApproverName|반려자|String|반려자 이름|
|execName|실행자|String|실행자 이름|
|endDateFrom|1736920800|int|검색 시작일(결재 완료일 기준)|
|endDateTo|1737526473|int|검색 종료일(결재 완료일 기준)|
|approvalState|1|int|결재 상태 </br>0: 전체</br>1: 진행 중</br>2: 승인</br>3: 반려|
|execResult|1|int|실행 결과 </br>0: 전체</br>1: 실행 전</br>2: 실행 중</br>3: 실행 완료|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
```text
?startDateFrom=1736920800&startDateTo=1737526473&docId=2025000013&docTitle=요청서1&requestName=홍길동&apvLimitFrom=1736920800&apvLimitTo=1737526473&approverName=결재자&rejectApproverName=반려자&execName=실행자&endDateFrom=1737526473&endDateTo=1737526473&approvalState=1&execResult=1&dataModifyTargetName=PROD01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|list| |Array|SQL 실행 이력 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|apvLimit|2025/05/05 11:30:04|String|결재 기한|
|approverName|결재자1|String|현재 결재자 이름|
|approverPowerType|1|String|결재자 권한<br>1: 결재<br>2: 실행|
|rejectApproverName|반려자|String|반려자 이름|
|execName|실행자|String|실행자 이름|
|endDate|2025/04/28 13:30:04|String|결재 완료일|
|approvalState|1|int|결재 상태 </br>1: 진행 중</br>2: 승인</br>3: 반려|
|execResult|1|int|실행 결과 </br>1: 실행 전2: 실행 중</br>3: 실행 완료|
|dataModifyTargetName|PROD01|String|변경 대상 이름|

[성공]
```json
{
    "code": 200,
    "data": {
        "list": [
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 1",
            "requestName":"홍길동",
            "startDate":"2025/04/28 11:30:04",
            "apvLimit":"2025/05/05 11:30:04",
            "approverName":"결재자1",
            "approverPowerType": 1,
            "rejectApproverName":"반려자",
            "execName":"실행자",
            "endDate":"2025/04/28 13:30:04",
            "approvalState":1,
            "execResult":1,
            "dataModifyTargetName":"PROD01"
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 1",
            "requestName":"홍길동",
            "startDate":"2025/04/28 11:30:04",
            "apvLimit":"2025/05/05 11:30:04",
            "approverName":"결재자1",
            "approverPowerType": 1,
            "rejectApproverName":"반려자",
            "execName":"실행자",
            "endDate":"2025/04/28 13:30:04",
            "approvalState":1,
            "execResult":1,
            "dataModifyTargetName":"PROD01"
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
        "list": []
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "list": []
    },
    "message": "처리에 실패하였습니다."
}
```

# SQL 실행 이력 조회
변경 대상에게 실행된 SQL 이력을 조회합니다.
## URL
* /api/sign/admin/history/execSql
* GET
* application/x-www-form-urlencoded; charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*execDateFrom|1736920800|int|검색 시작일(실행일)|
|*execDateTo|1737526473|int|검색 종료일(실행일)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|execName|김관리|String|실행자 이름|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execResult|1|int|실행 결과 </br>1: 성공</br>2: 실패|
```text
?execDateFrom=1736920800&execDateTo=1737526473&docId=2025000013&docTitle=요청서1&requestName=홍길동&execName=김관리&dataModifyTargetName=PROD01&execResult=1
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|list| |Array|SQL 실행 이력 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|execName|김관리|String|실행자 이름|
|execDate|2025/04/28 13:30:04|String|실행일|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|sql|UPDATE EMP SET EMPNO = 1001 WHERE EMP_ID = 'user01'|String|SQL|
|execResult|1|int|결과 </br>1: 성공</br>2: 실패|
|message|ORA-00904: "EMPNDDO": invalid identifier|String|메시지|

[성공]
```json
{
    "code": 200,
    "data": {
        "list": [
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 1",
            "requestName":"홍길동",
            "startDate":"2025/04/28 11:30:04",
            "execName":"김관리",
            "execDate":"2025/04/28 13:30:04",
            "dataModifyTargetName":"PROD01",
            "sql":"UPDATE EMP SET EMPNO = 1001 WHERE EMP_ID = 'user01'",
            "execResult":1,
            "message":""
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"홍길동",
            "startDate":"2025/04/28 11:30:04",
            "execName":"김관리",
            "execDate":"2025/04/28 13:30:04",
            "dataModifyTargetName":"PROD01",
            "sql":"SELECT * from EMP WHERE EMPNO = 1001",
            "execResult":1,
            "message":""
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
        "list": []
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "list": []
    },
    "message": "처리에 실패하였습니다."
}
```
