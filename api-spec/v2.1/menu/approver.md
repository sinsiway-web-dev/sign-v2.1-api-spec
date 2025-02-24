# 결재자 - 대기 문서 조회
결재자가 결재해야할 대기 문서 리스트를 조회합니다.
## URL
* /api/sign/approver/doc/dataModify/standby
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDateFrom|1736920800|int|검색 시작일(기안일 기준)|
|*startDateTo|1737526473|int|검색 종료일(기안일 기준)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|apvLimitFrom|1736920800|int|검색 시작일(결재 기한)|
|apvLimitTo|1737526473|int|검색 종료일(결재 기한)|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execState|1, 3|List<int>|실행 상태 </br>null: 전체</br>1: 실행 전</br>2: 실행 중</br>3: 실행 완료|
```
?startDateFrom=1736920800&startDateTo=1737526473&docId=2025000013&docTitle=데이터 변경 요청서 1&requestName=홍길동&apvLimitFrom=1737526473&apvLimitTo=1737526473&dataModifyTargetName=PROD01&execStatus=0
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|list| |Array|문서 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|apvLimit|2025/04/28 13:30:04|String|결재 기한|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execStatus|1|int|실행 상태 </br>1: 실행 전</br>2: 실행 중</br>3: 실행 완료|

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
            "apvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":1
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"홍길동",
            "startDate":"2025/04/29 11:30:04",
            "apvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":2
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

# 결재자 - 진행 중 문서 조회
결재자의 처리 순서가 되지 않았거나 이미 처리한 문서 중, 다른 사람이 처리 중인 문서를 조회합니다.
## URL
* /api/sign/approver/doc/dataModify/ongoing
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDateFrom|1736920800|int|검색 시작일(기안일 기준)|
|*startDateTo|1737526473|int|검색 종료일(기안일 기준)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|apvLimitFrom|1736920800|int|검색 시작일(결재 기한)|
|apvLimitTo|1737526473|int|검색 종료일(결재 기한)|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execState|1, 3|List<int>|실행 상태 </br>null: 전체</br>1: 실행 전</br>2: 실행 중</br>3: 실행 완료|
```
?startDateFrom=1736920800&startDateTo=1737526473&docId=2025000013&docTitle=데이터 변경 요청서 1&requestName=홍길동&apvLimitFrom=1737526473&apvLimitTo=1737526473&dataModifyTargetName=PROD01&execStatus=0
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|list| |Array|문서 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|apvLimit|2025/04/28 13:30:04|String|결재 기한|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execStatus|1|int|실행 상태 </br>1: 실행 전</br>2: 실행 중</br>3: 실행 완료|

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
            "apvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":1
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"홍길동",
            "startDate":"2025/04/29 11:30:04",
            "apvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":2
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

# 결재자 - 완료 문서 조회
결재자의 처리해야 할 문서 중 결재를 모두 완료한 문서를 조회합니다.
## URL
* /api/sign/approver/doc/dataModify/complete
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDateFrom|1736920800|int|검색 시작일(기안일 기준)|
|*startDateTo|1737526473|int|검색 종료일(기안일 기준)|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|endDateFrom|1736920800|int|검색 시작일(결재 완료일 기준)|
|endDateTo|1737526473|int|검색 종료일(결재 완료일 기준)|
|rejectApproverName|결재자1|String|반려자 이름|
|approvalState|2|List<int>|결재 상태 </br>null: 전체</br>2: 승인</br>3: 반려|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
```
?startDateFrom=1736920800&startDateTo=1737526473&docId=2025000013&docTitle=데이터 변경 요청서 1&requestName=홍길동&endDateFrom=1737526473&endDateTo=1737526473&rejectApproverName=결재자1&approvalState=0&dataModifyTargetName=PROD01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|list| |Array|문서 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|endDate|2025/04/28 13:30:04|String|결재 완료일|
|rejectApproverName|결재자1|String|반려자 이름|
|approvalState|2|int|결재 상태 </br>2: 승인</br>3: 반려|
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
            "endDate":"2025/05/06 13:30:04",
            "rejectApproverName":"결재자1",
            "approvalState":2,
            "dataModifyTargetName":"PROD01"
          },
          {
            "docId":"2025000014",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"기안자1",
            "startDate":"2025/04/28 11:30:04",
            "endDate":"2025/05/06 13:30:04",
            "rejectApproverName":"결재자2",
            "approvalState":3,
            "dataModifyTargetName":"PROD02"
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

