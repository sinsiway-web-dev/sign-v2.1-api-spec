# 기안자 - 진행 중 문서 조회
기안자의 진행 중(결재 중 또는 실행 중)인 결재 문서를 조회합니다.
## URL
* /api/sign/find/request/doc/dataModify/ongoing
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*startDate|1736920800|int|검색 시작일(기안일 기준)|
|*endDate|1737526473|int|검색 종료일(기안일 기준)|
```
{
  "startDate": "1736920800",
  "endDate": "1737526473"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|docList| |Array|SQL 실행 이력 리스트|
|docId|2025000013|String|문서 번호|
|docTitle|데이터 변경 요청서 1 |String|문서 제목|
|requestName|홍길동|String|기안자 이름|
|startDate|2025/04/28 11:30:04|String|기안일|
|approverName|김관리|String|현재 결재자 이름|
|aprvLimit|2025/04/28 13:30:04|String|결재 기한|
|dataModifyTargetName|PROD01|String|변경 대상 이름|
|execStatus|1|int|실행 상태 </br>1: 실행 전</br>2: 실행 중|

[성공]
```json
{
    "code": 200,
    "data": {
        "docList": [
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 1",
            "requestName":"홍길동",
            "startDate":"2025/04/28 11:30:04",
            "approverName":"김관리",
            "aprvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":1,
          },
          {
            "docId":"2025000013",
            "docTitle":"데이터 변경 요청서 2",
            "requestName":"홍길동",
            "startDate":"2025/04/29 11:30:04",
            "approverName":"김관리",
            "aprvLimit":"2025/05/06 13:30:04",
            "dataModifyTargetName":"PROD01",
            "execStatus":2,
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
        "docList": []
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "docList": []
    },
    "message": "처리에 실패하였습니다."
}
```
