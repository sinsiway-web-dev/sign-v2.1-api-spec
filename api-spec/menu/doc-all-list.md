# 전체
전체 DB 데이터 변경 요청서 목록을 조회 합니다.
## URL
* /api/sign/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|docId|2021000001|String|결재 문서 번호|
|requestName|사용자01|String|기안자 이름|
|docTitle|DB 데이터 변경 테스트|String|결재 문서 제목|
|<font color='red'>*</font>startDateFrom|2021/01/01|String|기안일 기준 검색 시작일|
|<font color='red'>*</font>startDateTo|2021/12/31|String|기안일 기준 검색 종료일|
|approverName|결재자01|String|결재자 이름|
|execName|실행자01|String|실행자 이름|
|rejectApproverName|결재자01|String|반려자 이름|
|approvalState|1, 2, 3|Map|결재 상태<br/>1: 결재 중<br/>2 : 승인<br/>3 : 반려|
|execState|1, 2, 3|Map|실행 상태<br/>1 : 실행 전<br/>2 : 성공<br/>3 : 실패|
```
{
    "docId":"2021000001",
    "requestName":"사용자01",
    "docTile":"DB 데이터 변경 테스트",
    "startDateFrom":"2021/01/01",
    "startDateTo":"2021/12/31",
    "approverName":"결재자01",
    "execName":"실행자01",
    "rejectApproverName":"결재자01"
    "approvalState":[1, 2, 3],
    "execState":[1, 2, 3]
}
```
## Response
### 데이터 없음
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|204|int|결과 코드|
|messageCode|204|int|결과 메시지 코드|
|serverMessage|no content|String|서버용 결과 메시지
|clientMessage|데이터가 없습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|docCount|0|int|조회한 결재 문서 수|
|docList||Map|조회한 결재 문서 목록|

```json
{
    "code": 204,
    "messageCode": 204,
    "serverMessage": "no content",
    "clientMessage": "데이터가 없습니다.",
    "data": {
        "docList": [],
        "docCount": 0
    }    
}
```
### 데이터 있음
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|docCount|1|int|조회한 결재 문서 수|
|docList||Map|조회한 결재 문서 목록|
|docId|2021000018|String|결재 문서 번호|
|requestName|기안자1|String|기안자 이름|
|docTitle|테스트|String|결재 문서 제목|
|approvalState|1|int|결재 상태<br/>0 : 상태 없음<br/>1 : 예정<br/>2 : 진행<br/>3 : 승인<br/>4 : 반려|
|execState|2|int|실행 상태<br/>0 : 상태 없음<br/>1 : 예정<br/>2 : 진행<br/>3 : 성공<br/>4 : 실패|
|groundsDocId|1|String|근거 문서 번호|
|approvalLimitDate|2021/12/31 23:59:59|String|결재 기한|
|startDate|2021/05/06 08:00:24|String|기안일|
|endDate|-|String|결재 완료일|
|rejectApproverName|1|String|반려자|
|rejectAgentApproverName|1|String|반려자의 대결자|
|rejectApprovalDate|1|String|반려자 반려일|
|execName|결재자2|String|실행자 이름|
|execDate|-|String|실행일|	
```json
{
    "code": 200,
    "messageCode": 200,
    "serverMessage": "success",
    "clientMessage": "처리되었습니다.",
    "data": {
        "docCount": 1,
        "docList": [
            {
                "docId": "2021000003",
                "requestName": "기안자1",
                "docTitle": "테스트",
		        "approvalState": 4,
                "execState": 0,
                "groundsDocId": "53",
                "approvalLimitDate": "2021/11/30 23:59:59",
                "startDate": "2021/03/24 14:07:02",
                "endDate": "2021/03/24 14:08:40",
                "rejectApproverName": "결재자2",
                "rejectAgentApproverName": "",
                "rejectApprovalDate": "1616562520",
                "execName": "보안관리자1",
                "execDate": "2021/03/24 14:07:37"
            }
        ]
    }
}
```

# 결재 문서 결재자
작성된 DB 데이터 변경 요청서의 결재자 정보를 조회합니다.

## URL
* /api/sign/doc/dataModify/approver
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2022000001|String|결재 문서 번호|
```
?docId=2022000001
```
## Response
### 데이터 없음
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|204|int|결과 코드|
|messageCode|204|int|결과 메시지 코드|
|serverMessage|no content|String|서버용 결과 메시지
|clientMessage|데이터가 없습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|docCount|0|int|조회한 결재 문서 수|
|docList||Map|조회한 결재 문서 목록|

```json
{
    "code": 204,
    "messageCode": 204,
    "serverMessage": "no content",
    "clientMessage": "데이터가 없습니다.",
    "data": {
        "docList": [],
        "docCount": 0
    }    
}
```
### 데이터 있음
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
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
```json
{
    "code": 200,
    "messageCode": 200,
    "serverMessage": "success",
    "clientMessage": "처리되었습니다.",
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
        ]
    }
}
```
