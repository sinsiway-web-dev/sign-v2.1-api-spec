# 역할 전체 조회
전체 역할을 조회 합니다.
## URL
* /api/sign/admin/role/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|role||Array|역할 목록|
|roleId|2|String|역할 ID(0:없음)|
|roleName|팀장|String|역할명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "role": [
            {
                "roleId": "2",
                "roleName": "팀장"
            },
            {
                "roleId": "6",
                "roleName": "DBA"
            }
        ]
    },
    "message": ""
}
```
---

# 역할 추가
역할을 추가합니다.(단, 관리자 권한을 가진 사용자로만 추가 가능)
## URL
* /api/sign/admin/role
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*roleName|DBA|String|역할명|
```json
{
    "roleName":"DBA"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|roleId|6|String|추가된 역할 ID(0:없음)|
|roleName|DBA|String|추가된 역할명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "roleId": "6",
        "roleName": "DBA"
    },
    "message": ""
}
```
---

# 역할 삭제
역할을 삭제합니다.(단, 관리자 권한을 가진 사용자로만 삭제 가능)
## URL
* /api/sign/admin/role
* DELETE
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*roleId|10|int|역할 ID(0:없음)|
```json
{
    "roleId":10
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|apvLine||Array|역할을 사용중인 결재선 정보<br>정상 동작 시 null|
|apvLineId||String|결재선 ID|
|apvLineName||String|결재선명|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {
        "apvLine": null
    },
    "message": ""
}
```
결재선에 사용 중인 역할을 삭제 시도 시
```json
{
    "code": 500,
    "data": {
        "apvLine": [
            {
                "apvLineId": "137",
                "apvLineName": "결재선"
            }
        ]
    },
    "message": ""
}
```
---

# 전체 사용자 조회
전체 사용자 정보를 조회합니다.
## URL
* /api/sign/admin/user/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
|user||Array|사용자 목록|
|ptuId|379|String|사용자 ID|
|name|사용자01|String|이름|
|orgUid|u01|String|로그인 ID|
|title||String|직위|
|ptoId|377|String|조직 ID|
|orgItemName|연구소|String|조직명|
|roleId|0|String|역할 ID(0:없음)|
|roleName||String|역할명|
|email||String|이메일|
|mobile||String|휴대전화|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {
        "user": [
            {
                "ptuId": "100",
                "name": "기안자1",
                "orgUid": "u1",
                "title": "사원",
                "ptoId": "500",
                "orgItemName": "개발1",
                "roleId": "0",
                "roleName": "",
                "email": "u1@sinsiway.com",
                "mobile": "010-1234-5678"
            },
            {
                "ptuId": "101",
                "name": "결재자1",
                "orgUid": "au1",
                "title": "부장",
                "ptoId": "500",
                "orgItemName": "개발1",
                "roleId": "1",
                "roleName": "팀장",
                "email": "au1@sinsiway.com",
                "mobile": "010-1234-5678"
            }
        ]
    }
}
```
---

# 특정 사용자 조회
조건 검색으로 특정 사용자 정보를 조회합니다.
## URL
* /api/sign/admin/user
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|orgUid|100|int|사용자 ID|
|ptuId|100|int|사용자 PTU_ID|
|ptoId|500|int|조직 ID|
```
?orgUid=u1&ptuId=100&ptoId=500
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|serverMessage|success|String|서버용 결과 메시지|
|data||Map|결과 데이터|
|user||Array|사용자 목록|
|ptuId|100|String|사용자 ID|
|name|사용자01|String|이름|
|orgUid|u01|String|로그인 ID|
|title|사원|String|직위|
|ptoId|500|String|조직 ID|
|orgItemName|연구소|String|조직명|
|roleId|0|String|역할 ID(0:없음)|
|roleName||String|역할명|
|email|u01@sinsiway.com|String|이메일|
|mobile||String|휴대전화|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {
        "user": [
            {
                "ptuId": "100",
                "name": "사용자01",
                "orgUid": "u01",
                "title": "사원",
                "ptoId": "500",
                "orgItemName": "연구소",
                "roleId": "0",
                "roleName": "",
                "email": "u1@sinsiway.com",
                "mobile": "010-1234-5678"
            }
        ]
    }
}
```
---

# 조직 전체 조회
전체 조직 목록을 조회 합니다.
## URL
* /api/sign/admin/org/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|org||Array|조직 목록|
|orgItemDepth|0|int|조직 순위|
|leafNodeFlag|0|int|말단 여부|
|ptoId|372|String|조직 ID|
|orgItemName|SINSIWAY|String|조직명|
|org0PtoId|372|String|0 번째 노드의 조직 ID|
|org1PtoId|0|String|1 번째 노드의 조직 ID|
|org2PtoId|0|String|2 번째 노드의 조직 ID|
|org3PtoId|0|String|3 번째 노드의 조직 ID|
|org4PtoId|0|String|4 번째 노드의 조직 ID|
|org5PtoId|0|String|5 번째 노드의 조직 ID|
|org6PtoId|0|String|6 번째 노드의 조직 ID|
|org7PtoId|0|String|7 번째 노드의 조직 ID|
|org8PtoId|0|String|8 번째 노드의 조직 ID|
|org9PtoId|0|String|9 번째 노드의 조직 ID|
|org0Name|SINSIWAY|String|0 번째 노드의 조직명|
|org1Name||String|1 번째 노드의 조직명|
|org2Name||String|2 번째 노드의 조직명|
|org3Name||String|3 번째 노드의 조직명|
|org4Name||String|4 번째 노드의 조직명|
|org5Name||String|5 번째 노드의 조직명|
|org6Name||String|6 번째 노드의 조직명|
|org7Name||String|7 번째 노드의 조직명|
|org8Name||String|8 번째 노드의 조직명|
|org9Name||String|9 번째 노드의 조직명|
```json
{
    "code": 200,
    "data": {
        "org": [
            {
                "orgItemDepth": 0,
                "leafNodeFlag": 0,
                "ptoId": "372",
                "orgItemName": "SINSIWAY",
                "org0PtoId": "372",
                "org1PtoId": "0",
                "org2PtoId": "0",
                "org3PtoId": "0",
                "org4PtoId": "0",
                "org5PtoId": "0",
                "org6PtoId": "0",
                "org7PtoId": "0",
                "org8PtoId": "0",
                "org9PtoId": "0",
                "org0Name": "SINSIWAY",
                "org1Name": "",
                "org2Name": "",
                "org3Name": "",
                "org4Name": "",
                "org5Name": "",
                "org6Name": "",
                "org7Name": "",
                "org8Name": "",
                "org9Name": ""
            }
        ]
    },
    "message": ""
}
```
---

# 조직 역할 조건 조회
조건 검색을 통한 특정 조직의 역할을 조회 합니다.<br>
역할 생성 시, 모든 조직에 동일 역할을 자동 생성하고 있어<br>
사실상 전체 역할을 출력함
## URL
* /api/sign/admin/orgRole
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|ptoId|372|int|조직 ID|
```
?ptoId=372
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|orgRole||Array|조직 역할 목록|
|orgRoleId|5|String|조직 역할 ID(0:없음)|
|roleId|2|String|역할 ID(0:없음)|
|roleName|팀장|String|역할명|
```json
{
    "code": 200,
    "data": {
        "orgRole": [
            {
                "orgRoleId": "5",
                "roleId": "2",
                "roleName": "팀장"
            },
            {
                "orgRoleId": "9",
                "roleId": "6",
                "roleName": "DBA"
            }
        ]
    },
    "message": ""
}
```
---

# 조직 사용자 전체 조회
조직이 있는 모든 사용자를 조회 합니다.<br>
역할 결재선 사용을 위해 조직이 필수 값이므로, 사실상 해당 api는 "사용자 전체 조회"와 결과가 같아야 함
## URL
* /api/sign/admin/orgUser/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|orgUser||Array|사용자 목록|
|ptuId|379|String|사용자 ID|
|name|사용자01|String|이름|
|orgUid|u01|String|로그인 ID|
|title||String|직위|
|ptoId|377|String|조직 ID|
|orgItemName|연구소|String|조직명|
|roleId|0|String|역할 ID(0:없음)|
|roleName||String|역할명|
```json
{
    "code": 200,
    "data": {
        "orgUser": [
            {
                "ptuId": "379",
                "name": "사용자01",
                "orgUid": "u01",
                "title": "",
                "ptoId": "377",
                "orgItemName": "연구소",
                "roleId": "0",
                "roleName": ""
            },
            {
                "ptuId": "380",
                "name": "사용자02",
                "orgUid": "u02",
                "title": "",
                "ptoId": "377",
                "orgItemName": "연구소",
                "roleId": "0",
                "roleName": ""
            }
        ]
    },
    "message": ""
}
```
---

# 조직 역할 전체 조회
조직의 역할을 모두 조회 합니다.<br>
역할 생성 시, 모든 조직에 동일 역할을 자동 생성하고 있어<br>
조직x역할 수 만큼 항상 출력됨
## URL
* /api/sign/admin/orgRole/all
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
없음
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|orgRole||Array|조직 역할 목록|
|orgRoleId|3|String|조직 역할 ID(0:없음)|
|roleId|2|String|역할 ID(0:없음)|
|roleName|팀장|String|역할명|
```json
{
    "code": 200,
    "data": {
        "orgRole": [
            {
                "orgRoleId": "3",
                "roleId": "2",
                "roleName": "팀장"
            },
            {
                "orgRoleId": "4",
                "roleId": "2",
                "roleName": "팀장"
            },
            {
                "orgRoleId": "5",
                "roleId": "2",
                "roleName": "팀장"
            }
        ]
    },
    "message": ""
}
```
---
