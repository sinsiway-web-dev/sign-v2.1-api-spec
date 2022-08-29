# 전체
전체 DB 데이터 변경 요청서 목록을 조회 합니다.
## URL
* /api/sign/doc/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|<font color='red'>*</font>startDateFrom|2021/01/01|String|결재 시작일(= 기안일) 기준 검색 시작일|
|<font color='red'>*</font>startDateTo|2021/12/31|String|결재 시작일(= 기안일) 기준 검색 종료일|
|approvalState|1, 2, 3|Map|결재 상태<br/>1: 결재 중<br/>2 : 승인<br/>3 : 반려|
|execState|1, 2, 3|Map|실행 상태<br/>1 : 실행 전<br/>2 : 성공<br/>3 : 실패|
|docId|2021000001|String|결재 문서 번호|
|docTitle|DB 데이터 변경 데스트|String|결재 문서 제목|
|requestName|사용자01|String|기안자 이름|
|execName|실행자01|String|실행자 이름|
|approverName|결재자01|String|현재 결재자 이름|
|approveApproverName|결재자01|String|마지막 승인자 이름|
|rejectApproverName|결재자01|String|결재 반려자 이름|
```
{
    "startDateFrom":"2021/01/01",
    "startDateTo":"2021/12/31",
    "approvalState":[1, 2, 3],
    "execState":[1, 2, 3],
    "docId":"2021000001",
    "docTile":"DB 데이터 변경 테스트",
    "requestName":"사용자01",
    "execName":"실행자01",
    "approverName":"결재자01",
    "approveApproverName":"결재자01",
    "rejectApproverName":"결재자01"
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
|docId|2021000018|String|문서 번호|
|approvalState|1|int|결재 상태<br/>1: 결재 중<br/>2 : 승인<br/>3 : 반려|
|execState|2|int|실행 상태<br/>1 : 실행 전<br/>2 : 성공<br/>3 : 실패|	
|docTitle|테스트|String|문서 제목|
|requestName|기안자1|String|기안자 이름|
|startDate|2021/05/06 08:00:24|String|결재 시작일(= 기안일)|
|endDate|-|String|결재 완료일<br/>결재가 완료된 경우 : 날짜<br/>결재가 완료되지 않은 경우 : -|
|approvalLimitDate|2021/12/31 23:59:59|String|결재 기한|
|execName|결재자2|String|실행자 이름<br/>실행자가 없는 경우 : -|
|execDate|-|String|실행일<br/>실행 전인 경우 : -|	
|approverName|결재자2|String|현재 결재자<br/>approvalState(결재 상태)가 1(결재 중)인 경우 : 현재 결재자 이름<br/>approvalState(결재 상태)가 1(결재 중)이 아닌 경우 : -|
|agentApproverName|-|String|현재 결재자의 대결자|
|approveApproverName|-|String|마지막 승인자<br/>approvalState(결재 상태)가 2(승인)인 경우 : 마지막 승인자 이름<br/>approvalState(결재 상태)가 2(승인)이 아닌 경우 : -|
|approveAgentApproverName|-|String|마지막 승인자의 대결자|
|approveApprovalDate|-|String|마지막 승인자 결재일|
|approveApprovalState|1|String|마지막 승인자 결재 상태<br/>1 : 승인<br/>2 : 후결|	
|rejectApproverName|1|String|반려자<br/>approvalState(결재 상태)가 3(반려)인 경우 : 반려자 이름<br/>approvalState(결재 상태)가 3(반려)이 아닌 경우 : -|
|rejectAgentApproverName|1|String|반려자의 대결자|
|rejectApprovalDate|1|String|반려자 반려일|
|groundsDocId|1|String|근거 문서 번호<br/>근거 문서 번호가 없는 경우 : -|
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
                "docId": "2021000018",
                "approvalState": 1,
                "execState": 2,
                "docTitle": "테스트",
                "requestName": "기안자1",
                "startDate": "2021/05/06 08:00:24",
                "endDate": "-",
                "approvalLimitDate": "2021/12/31 23:59:59",
                "execName": "결재자2",
                "execDate": "-",
                "approverName": "결재자2",
                "agentApproverName": "-",
                "approveApproverName": "-",
                "approveAgentApproverName": "-",
                "approveApprovalDate": "-",
                "approveApprovalState": 0,
                "rejectApproverName": "-",
                "rejectAgentApproverName": "-",
                "rejectApprovalDate": "-",
                "groundsDocId": "1"
            }
        ]
    }
}
```
