# 로그인
기본 soha password 인증을 사용하는 로그인
다중 인증을 사용하는 경우 해당 API 호출 후 다중 인증 종류에 맞는 다중 인증 로그인 API 호출을 해야 로그인 완료

## URL
* /api/sign/login
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*id|u01|String|로그인 ID|
|*password|비밀번호|String|비밀번호|
```json
{
    "id":"u01",
    "password":"비밀번호"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|signManagerFlag|0|int|SIGN 관리자 플래그<br> 0 : 일반 사용자<br/>1 : SIGN 관리자|
|mfa|0|int|다중 인증 종류<br> 0 : SOHA 인증<br/>1 : SOHA 인증 + 구글 OTP 인증|
|ptoId|377|String|조직 ID|
|roleId|0|String|역할 ID(0:없음)|
|name|사용자01|String|이름|
|roleName||String|역할명|
|loginResultCode|0|int|로그인 결과 상세 코드<br>1 ~ 10 : 비밀번호 만료 남은 기한<br>11 : 초기화 비밀번호 사용<br>200 : 성공<br>-170 : 비밀번호가 만료<br>-171 : 계정 잠김<br>500 : 실패<br>-10000 : 구글 OTP 인증 실패|
|userType|0|int|사용자 권한 종류<br/>0 : 기안자<br/>2 : 결재자|
|orgUid|u01|String|로그인 ID|
|title||String|직위|
|orgItemName|연구소|String|조직명|
|token|eyJ0eX...|String|인증 토큰|
```json
{
    "signManagerFlag": 0,
    "mfa": 1,
    "ptoId": "377",
    "roleId": "0",
    "name": "사용자01",
    "roleName": "",
    "loginResultCode": 200,
    "userType": 0,
    "orgUid": "u01",
    "title": "",
    "orgItemName": "연구소",
    "token": "eyJ0eX..."
}
```

# 다중 인증 - 구글 OTP 인증 로그인
기본 soha password 인증과 구글 OTP 인증을 사용하는 로그인
## URL
* /api/sign/mfaGoogleOtpLogin
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*id|u01|String|로그인 ID|
|*password|비밀번호|String|비밀번호|
|*code|인증 코드|String|6자리 인증 코드|
```json
{
    "id":"u01",
    "password":"비밀번호",
    "code" : "357197"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|signManagerFlag|0|int|SIGN 관리자 플래그<br> 0 : 일반 사용자<br/>1 : SIGN 관리자|
|mfa|0|int|다중 인증 종류<br> 0 : SOHA 인증<br/>1 : SOHA 인증 + 구글 OTP 인증|
|ptoId|377|String|조직 ID|
|roleId|0|String|역할 ID(0:없음)|
|name|사용자01|String|이름|
|roleName||String|역할명|
|loginResultCode|0|int|로그인 결과 상세 코드<br>1 ~ 10 : 비밀번호 만료 남은 기한<br>11 : 초기화 비밀번호 사용<br>200 : 성공<br>-170 : 비밀번호가 만료<br>-171 : 계정 잠김<br>500 : 실패<br>-10000 : 구글 OTP 인증 실패|
|userType|0|int|사용자 권한 종류<br/>0 : 기안자<br/>2 : 결재자|
|orgUid|u01|String|로그인 ID|
|title||String|직위|
|orgItemName|연구소|String|조직명|
|token|eyJ0eX...|String|인증 토큰|
```json
{
    "signManagerFlag": 0,
    "mfa": 1,
    "ptoId": "377",
    "roleId": "0",
    "name": "사용자01",
    "roleName": "",
    "loginResultCode": 200,
    "userType": 0,
    "orgUid": "u01",
    "title": "",
    "orgItemName": "연구소",
    "token": "eyJ0eX..."
}
```


# 사용자 추가 후 로그인
로그인 시 사용자 정보가 없는 경우 사용자를 추가하고 로그인
## URL
* /api/sign/login/user
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u05|String|로그인 ID|
|*name|사용자05|String|이름|
|*ptoId|377|int|조직 ID|
|*email|u05@sinsiway.com|String|이메일|
```json
{
    "orgUid":"u05",
    "name":"사용자05",
    "ptoId":377,
    "email":"u05@sinsiway.com"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|signManagerFlag|0|int|SIGN 관리자 플래그<br> 0 : 일반 사용자<br/>1 : SIGN 관리자|
|ptoId|377|String|조직 ID|
|roleId|0|String|역할 ID(0:없음)|
|name|사용자05|String|이름|
|roleName||String|역할명|
|loginResultCode|0|int|로그인 결과 상세 코드<br>1 ~ 10 : 비밀번호 만료 남은 기한<br>11 : 초기화 비밀번호 사용<br>200 : 성공<br>500 : 실패|
|userType|0|int|사용자 권한 종류<br/>0 : 기안자<br/>2 : 결재자|
|orgUid|u05|String|로그인 ID|
|title||String|직위|
|orgItemName|연구소|String|조직명|
|token|eyJ0eX...|String|인증 토큰|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "signManagerFlag": 0,
        "ptoId": "377",
        "roleId": "0",
        "name": "사용자05",
        "roleName": "",
        "loginResultCode": 0,
        "userType": 0,
        "orgUid": "u05",
        "title": "",
        "orgItemName": "연구소",
        "token": "eyJ0eX..."
    },
    "message": ""
}
```


# 로그아웃
브라우저 세션 로그아웃
## URL
* /api/sign/logout
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|로그인 ID|
```json
{
   "orgUid" : "u01"
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

