# 결재 승인
결재 문서 승인
## URL
* /api/sign/approval/approve
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|docType|8|int|결재 문서 종류 <br/> 1 : SQL 실행 사전 요청서<br/>2 : SQL 실행 소명서<br/> 7 : DB 접속 허가요청서<br/>8 : DB 데이터 변경 요청서<br/>9 : 마스킹 해제 요청서<br/>10 : 사용자 등록 요청서<br/>20 : 기타 보안 규칙 요청서|
|approveOrder|1|int|결재 순서|
|orgUid|m01|String|결재자 ID|
|docId|2021000004|String|결재 문서 번호|
|describe|승인합니다.|String|첨언|
```json
{
    "docType": 8,
    "approveOrder": 1,
    "orgUid": "m01",
    "docId": "2021000004",
    "describe": "승인합니다"
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


# 결재 반려
결재 문서 반려
## URL
* /api/sign/approval/reject
* POST
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|docType|8|int|결재 문서 종류 <br/> 1 : SQL 실행 사전 요청서<br/>2 : SQL 실행 소명서<br/> 7 : DB 접속 허가요청서<br/>8 : DB 데이터 변경 요청서<br/>9 : 마스킹 해제 요청서<br/>10 : 사용자 등록 요청서<br/>20 : 기타 보안 규칙 요청서|
|approveOrder|2|int|결재 순서|
|orgUid|dba01|String|결재자 ID|
|docId|2021000004|String|결재 문서 번호|
|describe|반려합니다.|String|첨언|
```json
{
    "docType": 8,
    "approveOrder": 2,
    "orgUid": "dba01",
    "docId": "2021000004",
    "describe": "반려합니다"
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


# 결재 회수
결재 처리 전 상태 문서를 기안자가 회수
## URL
* /api/sign/doc/withdrawal
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*docId|2020000001|String|결재 문서 번호|
|*orgUid|u1|String|회수 처리자 ID|
```json
{
    "docId":"2020000001",
	"orgUid":"u1"
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