# 결재선 전체 조회
전체 결재선과 결재 구성원을 모두 조회 합니다.
## URL
* /api/sign/admin/apvLine/all
* GET
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|apvLine||Array|결재선 목록|
|validDocType|0|int|적용 결재 문서<br/>0 : 전체<br/> 1 : SQL 실행 사전 요청서<br/>2 : SQL 실행 소명서<br/> 7 : DB 접속 허가요청서<br/>8 : DB 데이터 변경 요청서<br/>9 : 마스킹 해제 요청서<br/>10 : 사용자 등록 요청서<br/>20 : 기타 보안 규칙 요청서<br/>100 : 사용자 등록 요청서(본인)|
|apvLineId|33|String|결재선 ID|
|apvLineName|테스트결재선|String|결재선명|
|approver||Array|결재 구성원 정보|
|approverType|0|int|결재 구성원 종류<br/>0 : 결재자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|approveLevel|1|int|결재 순서(시작값:1)|
|approvePowerType|1|int|결재 권한 종류<br/>0 : 결재<br/>1 : 실행자|
|apvLineApproverId|14|String|결재 구성원 ID|
|name|테스트|String|결재 구성원 이름<br>type=1,2는 역할명|
|orgUid||String|사용자 ID<br>type=0 only|
|title||String|직위<br>type=0 only|
|orgItemName||String|조직명<br>type=0,2 only|
|roleName||String|역할<br>type=0 only|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "apvLine": [
            {
                "validDocType": 0,
                "apvLineId": "33",
                "apvLineName": "테스트결재선",
                "approver": [
                    {
                        "approverType": 1,
                        "approveLevel": 1,
                        "approvePowerType": 1,
                        "apvLineApproverId": "14",
                        "name": "테스트",
                        "orgUid": "",
                        "title": "",
                        "orgItemName": "",
                        "roleName": ""
                    }
                ]
            },
            {
                "validDocType": 0,
                "apvLineId": "32",
                "apvLineName": "기본결재선",
                "approver": [
                    {
                        "approverType": 1,
                        "approveLevel": 1,
                        "approvePowerType": 0,
                        "apvLineApproverId": "2",
                        "name": "팀장",
                        "orgUid": "",
                        "title": "",
                        "orgItemName": "",
                        "roleName": ""
                    },
                    {
                        "approverType": 1,
                        "approveLevel": 2,
                        "approvePowerType": 1,
                        "apvLineApproverId": "6",
                        "name": "DBA",
                        "orgUid": "",
                        "title": "",
                        "orgItemName": "",
                        "roleName": ""
                    }
                ]
            }
        ]
    },
    "message": ""
}
```


# 결재자 전체 조회
결재 권한을 갖고 있는 사용자(결재자)를 모두 조회 합니다.
## URL
* /api/sign/admin/approver/all
* GET
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|approver||Array|결재자 목록|
|approverType|0|String|결재자 종류<br/>0 : 결재자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|managerId|19|String|결재자 ID|
|name|보안관리자|String|이름|
|orgUid|sa|String|사용자 로그인 ID|
|title||String|직위|
|orgItemName|SINSIWAY|String|조직명|
|roleId|14|String|역할 ID(0:없음)|
|roleName|관리|String|역할명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "approver": [
            {
                "approverType": 0,
                "managerId": "19",
                "name": "보안관리자",
                "orgUid": "sa",
                "title": "",
                "orgItemName": "SINSIWAY",
                "roleId": "14",
                "roleName": "관리"
            },
            {
                "approverType": 0,
                "managerId": "21",
                "name": "결재자01",
                "orgUid": "m01",
                "title": "",
                "orgItemName": "연구소",
                "roleId": "2",
                "roleName": "팀장"
            },
            {
                "approverType": 0,
                "managerId": "25",
                "name": "dba01",
                "orgUid": "dba01",
                "title": "",
                "orgItemName": "연구소",
                "roleId": "6",
                "roleName": "DBA"
            }
        ]
    },
    "message": ""
}
```


# 결재선 추가
결재선을 추가합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)<br/>
결재선명, 적용 문서, 결재선 내 결재자를 설정할 수 있습니다.<br/>
결재선명은 중복 불가합니다.
## URL
* /api/sign/admin/apvLine
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*validDocType|0|int|적용 결재 문서<br/>0 : 전체<br/> 1 : SQL 실행 사전 요청서<br/>2 : SQL 실행 소명서<br/> 7 : DB 접속 허가요청서<br/>8 : DB 데이터 변경 요청서<br/>9 : 마스킹 해제 요청서<br/>10 : 사용자 등록 요청서<br/>20 : 기타 보안 규칙 요청서<br/>100 : 사용자 등록 요청서(본인)|
|*apvLineName|테스트|String|결재선명|
|*approver||Array|결재 구성원 목록|
|*approveLevel|1|int|결재 순서(시작값:1)|
|*approvePowerType|0|int|결재 권한 종류<br/>0 : 결재<br/>1 : 실행자|
|*approverType|0|int|결재 구성원 종류<br/>0 : 결재자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|*apvLineApproverId|21|String|결재 구성원 ID<br/>0 : 결재자 ID<br/>1 : 역할 ID(0:없음)<br/>2 : 조직 역할 ID(0:없음)|
```json
{
    "validDocType": 0,
    "apvLineName": "테스트",
    "approver": [
        {
            "approveLevel": 1,
            "approvePowerType": 0,
            "approverType": 0,
            "apvLineApproverId": "21"
        },
        {
            "approveLevel": 2,
            "approvePowerType": 0,
            "approverType": 1,
            "apvLineApproverId": "2"
        },
        {
            "approveLevel": 3,
            "approvePowerType": 1,
            "approverType": 2,
            "apvLineApproverId": "8"
        }
    ]
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|apvLineId|124|String|결재선 ID|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "apvLineId": "124"
    },
    "message": ""
}
```


# 결재선 삭제
결재선을 삭제합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)
## URL
* /api/sign/admin/apvLine
* DELETE
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|123|int|결재선 ID|
```json
{
    "apvLineId": 33
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


# 결재선 변경
결재선명을 변경합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)<br/>
결재선명은 중복 불가합니다.
## URL
* /api/sign/admin/apvLine
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|124|String|결재선 ID|
|*apvLineName|연구소 결재선|String|변경할 결재선 명|
```json
{
	"apvLineId":"124",
	"apvLineName":"연구소 결재선"
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


# 참조자 조회
특정 결재선 내 참조자 들을 조회합니다.
## URL
* /api/sign/admin/apvLine/referencer
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|32|String|결재선 ID|
```
?apvLineId=32
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|referencer||Array|참조자 목록|
|referencerType|0|int|참조자 종류<br/>0 : 사용자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|apvLineReferencerId|375|String|참조자 ID|
|name|사용자02|String|이름|
|orgUid|u02|String|사용자 ID|
|title||String|직위|
|orgItemName|SINSIWAY|String|조직명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "referencer": [
            {
                "referencerType": 0,
                "apvLineReferencerId": "375",
                "name": "사용자02",
                "orgUid": "u02",
                "title": "",
                "orgItemName": "SINSIWAY"
            }
        ]
    },
    "message": ""
}
```


# 참조자 추가
결재선 내 참조자를 추가합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)
## URL
* /api/sign/admin/apvLine/referencer
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|32|String|결재선 ID|
|*referencer||Array|참조자 목록|
|*referencerType|0|int|참조자 종류<br/>0 : 사용자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|*apvLineReferencerId|375|String|참조자 ID<br/>참조자 종류 0 - 사용자 ID<br/>참조자 종류 1 - 역할 ID(0:없음)<br/>참조자 종류 2 - 조직 역할 ID(0:없음)|
```json
{
	"apvLineId":32,
	"referencer": [
            {
                "referencerType": 0,
                "apvLineReferencerId": 375
            }
        ]
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


# 결재선 적용 대상 조회
결재선 적용 대상(사용자 또는 조직)을 조회 합니다.
## URL
* /api/sign/admin/apvLine/validDrafter
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|32|String|결재선 ID|
```
?apvLineId=32
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|validDrafter||Array|적용 대상 목록|
|validDrafterType|0|int|적용 대상 종류<br/>0 : 사용자<br/>1 : 조직|
|apvLinevalidDrafterId|373|String|적용 대상 ID|
|name|사용자01|String|이름|
|orgUid|u01|String|사용자 ID|
|title||String|직위|
|orgItemName|SINSIWAY|String|조직명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "validDrafter": [
            {
                "validDrafterType": 0,
                "apvLinevalidDrafterId": "373",
                "name": "사용자01",
                "orgUid": "u01",
                "title": "",
                "orgItemName": "SINSIWAY"
            }
        ]
    },
    "message": ""
}
```


# 결재선 적용 대상 추가
결재선을 사용할 적용 대상(사용자 또는 조직)을 추가합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)
## URL
* /api/sign/admin/apvLine/validDrafter
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|32|String|결재선 ID|
|*validDrafter||Array|적용 대상 목록|
|*validDrafterType|0|int|적용 대상 종류<br/>0 : 사용자<br/>1 : 조직|
|*apvLineIdValidDrafterId|373|String|적용 대상 ID<br/>적용 대상 종류 0 - 사용자 ID<br/>적용 대상 종류 1 - 조직 ID|
```json
{
	"apvLineId":32,
	"validDrafter": [
            {
                "validDrafterType": 0,
                "apvLineIdValidDrafterId": 373
            }
        ]
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


# 결재선 조건 조회
특정 결재선 내 결재자들을 조회합니다.
## URL
* /api/sign/admin/apvLine/approver
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*apvLineId|124|String|결재선 ID|
```
?apvLineId=124
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|approver||Array|결재 구성원 목록|
|approveLevel|1|int|결재 순서(시작값:1)|
|approvePowerType|0|int|결재 권한 종류<br/>0 : 결재<br/>1 : 실행자|
|approverType|0|int|결재자 종류<br/>0 : 결재자<br/>1 : 역할<br/>2 : 특정 조직의 역할|
|apvLineApproverId|21|String|결재 구성원 ID|
|name|결재자01|String|이름|
|orgUid|m01|String|사용자 ID|
|title||String|직위|
|orgItemName|연구소|String|조직명|
|roleName|팀장|String|역할|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "approver": [
            {
                "approveLevel": 1,
                "approvePowerType": 0,
                "approverType": 0,
                "apvLineApproverId": "21",
                "name": "결재자01",
                "orgUid": "m01",
                "title": "",
                "orgItemName": "연구소",
                "roleName": "팀장"
            },
            {
                "approveLevel": 2,
                "approvePowerType": 0,
                "approverType": 1,
                "apvLineApproverId": "2",
                "name": "팀장",
                "orgUid": "",
                "title": "",
                "orgItemName": "",
                "roleName": ""
            },
            {
                "approveLevel": 3,
                "approvePowerType": 1,
                "approverType": 2,
                "apvLineApproverId": "8",
                "name": "DBA",
                "orgUid": "",
                "title": "",
                "orgItemName": "연구소",
                "roleName": ""
            }
        ]
    },
    "message": ""
}
```