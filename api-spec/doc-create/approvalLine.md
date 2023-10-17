# 문서 작성 - 결재선
결재 문서 작성 시 현재 사용 가능한 결재선 조회
## URL
* /api/sign/doc/write/approvalLines/docType/dataModify
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|기안자 ID|
```
?orgUid=u01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|apvLine||Array|결재선 목록|
|apvLineId|32|int|결재선 ID|
|apvLineName|기본 결재선|String|결재선명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "apvLine": [
            {
                "apvLineId": "32",
                "apvLineName": "기본결재선"
            },
            {
                "apvLineId": "33",
                "apvLineName": "테스트결재선"
            }
        ]
    },
    "message": ""
}
```


# 문서 작성 - 결재자
결재 문서 작성 시 사용자가 선택한 결재선의 결재자
## URL
* /api/sign/doc/write/approvalLine/approvers
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|32|int|결재선 ID|
|*orgUid|377|String|기안자 ID|
|*ptoId|377|int|기안자 조직 ID|
```
?apvLineId=32&orgUid=u1&ptoId=377
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|apvLineApprover||Array|결재자 목록|
|approverType|1|int|결재자 종류<br/>0: 결재자<br/>1: 역할<br/>2: 특정 조직의 역할|
|approveLevel|1|int|결재 순번|
|approvePowerType|0|int|결재 권한 종류<br/>0: 결재<br/>1: DB데이터변경실행|
|apvLineApproverId|2|int|결재자ID|
|approver||Map|결재자 정보|
|name|팀장|String|결재자 이름|
|title||String|결재자 직위(*approverType=0)|
|orgItemName||String|결재자 조직명(*approverType in 0 or 2)|
|orgUid||String|결재자ID(*approverType=0)|
|approverTypeApprover||Array|역할로 찾은 실제 결재자(*approverType in 1 or 2)|
|managerId|21|int|실제 결재자ID|
|name|결재자01|String|결재자 이름|
|orgUid|m01|String|결재자 ID|
|title||String|결재자 직위|
|orgItemName|연구소|String|결재자 조직명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "apvLineApprover": [
            {
                "approverType": 1,
                "approveLevel": 1,
                "approvePowerType": 0,
                "apvLineApproverId": "2",
                "approver": {
                    "name": "팀장",
                    "title": null,
                    "orgItemName": null,
                    "orgUid": null
                },
                "approverTypeApprover": [
                    {
                        "managerId": "21",
                        "name": "결재자01",
                        "orgUid": "m01",
                        "title": "",
                        "orgItemName": "연구소"
                    },
                    {
                        "managerId": "23",
                        "name": "결재자02",
                        "orgUid": "m02",
                        "title": "",
                        "orgItemName": "연구소"
                    }
                ]
            },
            {
                "approverType": 1,
                "approveLevel": 2,
                "approvePowerType": 1,
                "apvLineApproverId": "6",
                "approver": {
                    "name": "DBA",
                    "title": null,
                    "orgItemName": null,
                    "orgUid": null
                },
                "approverTypeApprover": [
                    {
                        "managerId": "25",
                        "name": "dba01",
                        "orgUid": "dba01",
                        "title": "",
                        "orgItemName": "연구소"
                    }
                ]
            }
        ]
    },
    "message": ""
}
```
