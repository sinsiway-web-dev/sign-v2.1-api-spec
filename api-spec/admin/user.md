# 사용자 생성
사용자를 생성합니다.

## URL
* /api/sign/admin/user
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u1|String|추가할 사용자 ID|
|*name|사용자1|String|추가할 사용자 이름|
|ptoId|1|String|추가할 사용자의 조직 ID|
|title|사원|String|추가할 사용자의 직위|
|email|u1@sinsiway.com|String|추가할 사용자의 이메일|
|mobile|010-1234-5678|String|추가할 사용자의 휴대전화|
```json
{
    "orgUid":"u1",
    "name":"사용자1",
    "ptoId":"1",
    "title":"사원",
    "email":"u1@sinsiway.com",
    "mobile":"010-1234-5678"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
|orgUid|u1|String|추가한 사용자 ID|
|name|사용자1|String|추가한 사용자 이름|
|ptoId|1|String|추가한 사용자의 조직 ID|
|title|사원|String|추가한 사용자의 직위|
|email|u1@sinsiway.com|String|추가할 사용자의 이메일|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success"
    "data": {
        "orgUid": "u1",
        "name": "사용자1",
        "ptoId": "1",
        "title": "사원",
        "email": "u1@sinsiway.com"
    }
}
```
---

# 사용자 삭제
사용자를 삭제합니다.
## URL
* /api/sign/admin/user
* DELETE
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u1|String|삭제할 사용자 ID|
```json
{
    "orgUid":"u1"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```
---

# 사용자 역할 변경
사용자의 역할 정보를 변경합니다.<br>
역할 추가 시 결재자 권한이 부여됩니다.<br>
역할 삭제 시 결재자 권한이 삭제됩니다.<br>
결재선 내 결재자로 등록되어 있는 경우, 결재 문서 내 결재자로 등록되어 있는 경우 역할 변경 혹은 삭제가 불가능합니다.
## URL
* /api/sign/admin/user/role
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|이메일 변경할 사용자의 로그인 ID|
|*roleId|0|String|역할 ID(0 : 역할 삭제)|
```json
{
    "orgUid": "u01",
    "roleId": "0"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드<br>-10003 : 결재선 내 설정되어 있습니다.<br>-10004 : 결재 문서 내 결재자|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```
---

# 사용자 이메일 변경
사용자의 이메일 정보를 변경합니다.
## URL
* /api/sign/admin/user/email
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|이메일 변경할 사용자의 로그인 ID|
|*email|u01@sinsiway.com|String|이메일 정보를 삭제하고 싶은 경우 공백|
```json
{
    "orgUid": "u01",
    "email": "u01@sinsiway.com"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```
---
# 사용자 휴대전화 변경
사용자의 휴대전화 정보를 변경합니다.
## URL
* /api/sign/admin/user/mobile
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|휴대전화 변경할 사용자의 로그인 ID|
|*mobile|010-1234-5678|String|휴대전화 정보를 삭제하고 싶은 경우 공백|
```json
{
    "orgUid": "u01",
    "mobile": "010-1234-5678"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```
---

# 사용자 비밀번호 초기화
사용자 비밀번호를 초기화 비밀번호로 변경합니다.
## URL
* /api/sign/admin/user/password/init
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|초기화 비밀번호로 변경할 사용자의 로그인 ID|
```json
{
    "orgUid": "u01"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {}
}
```
---
