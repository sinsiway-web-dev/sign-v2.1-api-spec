# 결재 - 결재 상태 별 문서 개수
현재 사용자가 결재자로 있는 문서의 결재 상태 별 개수 조회
## URL
* /api/sign/approver/approveState/docCount/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approveState|1, 2, 3, 4, 5|int|결재 상태<br/>1 : 결재 예정<br/>2 : 결재 대기<br/>3 : 결재 진행<br/>4 : 승인<br/>5 : 반려|
|*apvOrgUid|m01|String|사용자 ID|
|createDateFrom|2021/01/01|String|기안일 기준 검색 시작일|
|createDateTo|2021/12/31|String|기안일 기준 검색 종료일|
```json
{
    "approveState" : [1, 2, 3, 4, 5],
    "apvOrgUid" : "m01",
    "createDateFrom" : "2021/01/01",
    "createDateTo" : "2021/12/31"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docCount||List|결재 상태 별 문서 개수 목록|
|approveState|2|String|결재 상태<br/>1 : 결재 예정<br/>2 : 결재 대기<br/>3 : 결재 진행<br/>4 : 승인<br/>5 : 반려|
|count|1|int|조회한 결재 문서 개수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docCount": [
            {
                "approveState": 1,
                "count": 0
            },
            {
                "approveState": 2,
                "count": 1
            },
            {
                "approveState": 3,
                "count": 0
            },
            {
                "approveState": 4,
                "count": 0
            },
            {
                "approveState": 5,
                "count": 0
            }
        ]
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 실행 상태 별 문서 개수
현재 사용자가 결재자로 있는 문서의 실행 상태 별 개수 조회
## URL
* /api/sign/approver/execState/docCount/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*execState|1, 2, 3|Map|실행 상태<br/>1 : 실행 전<br/>2 : 실행 성공<br/>3 : 실행 실패|
|*apvOrgUid|m01|String|사용자 ID|
|createDateFrom|2021/01/01|String|기안일 기준 검색 시작일|
|createDateTo|2021/12/31|String|기안일 기준 검색 종료일|

```json
{
    "execState" : [1, 2, 3],
    "apvOrgUid" : "m01",
    "createDateFrom" : "2020/01/01",
    "createDateTo" : "2020/12/31"
 }
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docCount||List|실행 상태 별 문서 개수 목록|
|execState|1|String|실행 상태<br/>1 : 실행 성공<br/>2 : 실행 실패<br/>3 : 실행 미완료|
|count|1|int|조회한 결재 문서 개수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docCount": [
            {
                "execState": 1,
                "count": 0
            },
            {
                "execState": 2,
                "count": 0
            },
            {
                "execState": 3,
                "count": 1
            }
        ]
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 결재 예정
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 결재 순서가 오지 않은 문서 목록 조회
## URL
* /api/sign/approver/expected/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request

|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|dba01|String|사용자 ID|
```
?orgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|aprvLimit|2021/05/04|String|결재 기한|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "aprvLimit": "2021/05/04",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 결재 대기
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 결재 순서가 도래한 문서 목록 조회
## URL
* /api/sign/approver/standby/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|사용자 ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|aprvLimit|2021/05/04|String|결재 기한|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "aprvLimit": "2021/05/04",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 결재 진행
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 자신이 승인 후 다음 결재가 진행 중인 문서 목록 조회
## URL
* /api/sign/approver/progress/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|사용자 ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|aprvLimit|2021/05/04|String|결재 기한|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "aprvLimit": "2021/05/04",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 결재 승인
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 최종 승인 완료 된 결재 문서 목록 조회
## URL
* /api/sign/approver/approve/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|dba01|String|사용자 ID|
```
?orgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|endDate|2021/04/27 17:16:05|String|결재 완료일|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "endDate": "2021/04/27 17:16:05",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 결재 반려
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 반려 된 결재 문서 목록 조회
## URL
* /api/sign/approver/reject/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request

|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|사용자 ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000002|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 17:19:56|String|기안일|
|endDate|2021/04/27 17:20:10|String|결재 완료일|
|rejectApproverName|결재자01|String|반려 결재자 이름|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000002",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 17:19:56",
                "endDate": "2021/04/27 17:20:10",
                "rejectApproverName": "결재자01",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 실행 성공
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 실행 성공한 문서 목록 조회
## URL
* /api/sign/approver/exec/success/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|사용자 ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Map|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|execName|dba01|String|실행자|
|execDate|2021/04/27 17:16:05|String|실행일|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "execName": "dba01",
                "execDate": "2021/04/27 17:16:05",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 실행 실패
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 실행 실패한 문서 목록 조회
## URL
* /api/sign/approver/exec/fail/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|dba01|String|사용자 ID|
```
?orgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Map|조회한 결재 문서 목록|
|docId|2021000003|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 17:30:48|String|기안일|
|execName|dba01|String|실행자|
|execDate|2021/04/27 17:31:16|String|실행일|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000003",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 17:30:48",
                "execName": "dba01",
                "execDate": "2021/04/27 17:31:16",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 결재 - 실행 미완료
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 중 실행이 안된 문서 목록(반려 포함)
## URL
* /api/sign/approver/exec/unfinished/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|dba01|String|사용자 ID|
```
?orgUid=dba01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Map|조회한 결재 문서 목록|
|docId|2021000002|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|결재 문서 제목|
|createDate|2021/04/27 17:19:56|String|기안일|
|aprvLimit|2021/05/04|String|결재 기한|
|requestName|사용자01|String|기안자|
|groundsDocId|근거-001|String|근거 문서 번호|
|docCount|1|int|조회한 결재 문서 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000002",
                "docTitle": "[변경] DB데이터변경",
                "createDate": "2021/04/27 17:19:56",
                "aprvLimit": "2021/05/04",
                "requestName": "사용자01",
                "groundsDocId": "근거-001"
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```

# 결재 - 전체
현재 사용자가 결재자로 있는 DB 데이터 변경 요청서 목록 조회
## URL
* /api/sign/approver/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|사용자 ID|
```
?orgUid=user01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|docList||Array|조회한 결재 문서 목록|
|docId|2021000001|String|결재 문서 번호|
|docTitle|\[변경\] DB데이터변경|String|제목|
|requestName|사용자01|String|기안자|
|createDate|2021/04/27 15:35:15|String|기안일|
|endDate||String|결재 완료일|
|aprvLimit|2021/05/04|String|결재 기한|
|rejectApproverName||String|반려한 결재자 이름|
|execName||String|실행자|
|execDate||String|실행일|
|groundsDocId|근거-001|String|근거 문서 번호|
|approveState|3|String|결재 상태<br/>1: 결재 중<br/>2 : 승인<br/>3 : 반려<br/>4 : 후결|
|execState|3|String|실행 상태<br/>1 : 실행 성공<br/>2 : 실행 실패<br/>3 : 실행 미완료|
|docCount|1|int|조회한 결재 문서 개수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|

```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "docList": [
            {
                "docId": "2021000001",
                "docTitle": "[변경] DB데이터변경",
                "requestName": "사용자01",
                "createDate": "2021/04/27 15:35:15",
                "endDate": "",
                "aprvLimit": "2021/05/04",
                "rejectApproverName": "",
                "execName": "",
                "execDate": "",
                "groundsDocId": "근거-001",
                "approveState": 3,
                "execstate": 3
            }
        ],
        "docCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```
