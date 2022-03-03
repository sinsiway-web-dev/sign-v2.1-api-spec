# 결재자 결재 유형 확인
현재 로그인한 결재자의 결재 유형 정보(결재/후결/대결)를 확인합니다.
## URL
* /api/sign/myPage/approval
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|로그인ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|agentApprover||Map|대결자 정보<br/>approvalType = 4 가 아니면 null|
|orgUid|u05|String|사용자 ID|
|name|사용자05|String|이름|
|orgItemName|연구소|String|조직명|
|roleName|테스트|String|역할명|
|approvalType|4|int|결재자 부재 종류<br/>0 : 결재<br/>3 : 후결<br/>4 : 대결|
|startDate|2021/05/04|String|시작일|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "agentApprover": {
            "orgUid": "u05",
            "name": "사용자05",
            "orgItemName": "연구소",
            "roleName": "테스트"
        },
        "approvalType": 4,
        "startDate": "2021/05/04"
    },
    "message": ""
}
```


# 대결 가능 결재자 조회
대결 설정 시 부재 중이지 않은 지정 가능한 결재자 목록을 조회 합니다.
## URL
* /api/sign/myPage/approval/reserveAgentApprover
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|m01|String|결재자 ID|
```
?orgUid=m01
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|approver||Array|대결자 목록|
|orgUid|dba01|String|사용자 ID|
|name|dba01|String|이름|
|orgItemName|연구소|String|조직명|
|roleName|DBA|String|역할명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "approver": [
            {
                "orgUid": "dba01",
                "name": "dba01",
                "orgItemName": "연구소",
                "roleName": "DBA"
            },
            {
                "orgUid": "dba02",
                "name": "dba02",
                "orgItemName": "기술지원",
                "roleName": "DBA"
            }
        ]
    },
    "message": ""
}
```


# 결재 유형 설정 - 결재
결재자의 결재 유형을 결재로 설정합니다.
## URL
* /api/sign/myPage/approval/approvalType/approval
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approverOrgUid|m01|String|결재자 ID|
```json
{
    "approverOrgUid":"m01"
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


# 결재 유형 설정 - 후결
결재자의 결재 유형을 후결로 설정합니다.
## URL
* /api/sign/myPage/approval/approvalType/afterApproval
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approverOrgUid|m01|String|결재자 ID|
|*startDate|2021/05/04|String|후결 설정 시작일|
```json
{
    "approverOrgUid":"au1",
    "startDate":"2021/05/04"
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


# 결재 유형 설정 - 대결
결재자의 결재 유형을 대결로 설정합니다.
## URL
* /api/sign/myPage/approval/approvalType/agentApproval
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*approverOrgUid|m01|String|결재자 ID|
|*agentApproverOrgUid|m02|String|대결자 ID|
|*startDate|2021/05/04|String|대결 설정 시작일|
```json
{
    "approverOrgUid":"m01",
    "agentApproverOrgUid":"m02",
    "startDate":"2021/05/04"
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


# 비밀번호 변경
비밀번호를 변경합니다.
## URL
* /api/sign/myPage/password
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u1|String|사용자 ID|
|*password|password|String|현재 비밀번호|
|*newPassword1|newPassword|String|새 비밀번호|
|*newPassword2|newPassword|String|새 비밀번호 확인 값|
```json
{
    "orgUid":"u1",
    "password":"password",
    "newPassword1":"newPassword",
    "newPassword2":"newPassword"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|changePasswordResultCode|0|int|비밀번호 변경 결과 상세 코드<br/>0 : 비밀번호 변경 성공<br/>1 : 비밀번호 변경 실패<br/>2 : 유효하지 않은 ID 혹은 비밀번호<br/>3 : 현재 비밀번호와 새 비밀번호가 같음<br/>4 : 새 비밀번호화 새 비밀번호 확인 값이 같음<br/>5 : 영문, 숫자, 특수문자 사용 조건 위반<br/>6 : 최소 길이 조건 위반<br/>7 : 최대 길이 조건 위반|
|minLength||int|비밀번호 최소 길이<br/>(*changePasswordResultCode=6일 때만 출력)|
|maxLength||int|비밀번호 최대 길이<br/>(*changePasswordResultCode=7일 때만 출력)|
```json
{
    "code": 500,
    "messageCode": -1030,
    "serverMessage": "Password change failed",
    "clientMessage": "비밀번호 변경에 실패하였습니다.",
    "data": {
        "changePasswordResultCode": 2,
        "minLength": "",
        "maxLength": ""
    }
}
```


# 본인 인증
ID/PW 인증 결과를 알려줍니다.
## URL
* /api/sign/myPage/identityVerification
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|로그인 ID|
|*password|password|String|비밀번호|
```json
{
    "orgUid":"u01",
    "password":"password"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {},
    "messageCode": 200,
    "serverMessage": "success"
}
```