# 근거 문서 선택 목록 조회
고객사에서 제공한 API 호출을 통해 연동할 근거 문서 정보를 조회합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*customerType|1|String|고객사 종류<br/>1 : 블루월넛|
|*request|홍길동|String|검색 조건|
```json
{
    "customerType" : 1,
    "request" : "홍길동"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|message||String|결과 메시지|
|data||Map|결과 데이터|
|groundsDoc||String|데이터 교환 언어 형식의 정보|
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "groundsDoc": [
            {
                "issue_id": 1,
                "issue_subject": "일감_1",
                "project_id": 71,
                "project_name": "프로젝트_72",
                "tracker_id": 60,
                "tracker_name": "프로젝트 하위 그룹_61",
                "status_id": 1,
                "status_name": "최초 요청",
                "author_id": 1,
                "author_name": "홍길동"
            }
        ],
        "message": ""
    }
}
```


# 근거 문서 조회 DB
고객이 제공한 DB(VIEW)정보를 활용해 DB 데이터 변경 요청서와 연동할 근거 문서 정보를 조회합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc/view
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*companyName|sign|String|회사명<br/>(eugenefn : 유진투자증권)|
|key|1|String|근거 문서 조회 조건<br>회사별 고정 조건에 값만 입력|
```json
{
	"*companyName" : "sign",
	"key" : "1"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|data||Array|근거 문서 데이터|
|columns||Array|근거 문서 컬럼명|
|columnCount|8|int|근거 문서 컬럼 수|
|dataCount|1|int|근거 문서 데이터 로우 수|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "data": [
            {
                "ENAME": "SMITH",
                "COMM": null,
                "HIREDATE": "2080-12-17 00:00:00.0",
                "EMPNO": "7369",
                "MGR": "7902",
                "JOB": "CLERK",
                "DEPTNO": "20",
                "SAL": "900"
            }
        ],
        "columns": [
            "EMPNO",
            "ENAME",
            "JOB",
            "MGR",
            "HIREDATE",
            "SAL",
            "COMM",
            "DEPTNO"
        ],
        "columnCount": 8,
        "dataCount": 1
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 근거 문서 파일 업로드
DB 데이터 변경 요청서 근거 문서 파일을 서버에 업로드 합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc
* POST
* multipart/form-data
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*file|img.jpg|File|근거 문서 파일|
|*orgUid|u1|String|사용자 ID|
```
form-data; orgUid="u1"; file="img.jpg"
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|uploadFileName|u1_20210430093737.jpg|String|업로드 파일명<br>orgUid_yyyyMMddHHmmss.jpg|
```json
{
    "code": 200,
    "data": {
        "uploadFileName": "u1_20210430093737.jpg"
    },
    "message": ""
}
```



# 근거 문서 별 결재 문서 조회
근거 문서와 연결된 DB 데이터 변경 요청서를 조회합니다. 조회된 데이터는 기안일을 기준으로 최신순으로 정렬되어 조회됩니다.
## URL
* /api/sign/doc/dataModify/groundsDoc/doc
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*groundsDocId|근거-001|Array|근거 문서 번호|
```json
{
	"groundsDocId" : [
        "근거-001",
        "근거-002"
    ]
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|doc||Map|키 : groundsDocId<br/>값 : 문서 정보 목록|
|approveState|1|String|결재 상태<br/>1: 결재 중<br/>2 : 승인<br/>3 : 반려<br/>4 : 후결|
|execState|3|String|실행 상태<br/>1 : 실행 성공<br/>2 : 실행 실패<br/>3 : 실행 미완료|
|docId|2021000011|String|결재 문서 번호|
|createDate|2021/04/28 16:33:30|String|기안일|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|

```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "doc": {
            "근거-001": [
                {
                    "approveState": 1,
                    "execState": 3,
                    "docId": "2021000011",
                    "createDate": "2021/04/28 16:33:30"
                },
                {
                    "approveState": 2,
                    "execState": 2,
                    "docId": "2021000010",
                    "createDate": "2021/04/28 15:46:49"
                }
            ]
        }
    },
    "messageCode": 200,
    "serverMessage": "success"
}
```


# 근거 문서 상태 조회 URL
URL 호출을 통해 근거 문서 상태 정보를 조회합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc/status
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*url|http://1.1.1.1/sign/groundsDoc/status|String|근거 문서 상태 조회 URL|
|*key|status|String|근거 문서 상태 키<br>고객사에서 사용하는 값|
```json
{
	"url": "http://1.1.1.1:8080/sign/groundsDoc/status",
	"key": "status"
}
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|status|1|String|근거 문서 상태|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
```json
{
    "clientMessage": "처리되었습니다.",
    "code": 200,
    "data": {
        "status": "1"
    },
    "messageCode": 200,
    "serverMessage": "success"    
}
```


# 근거 문서 변경
기안자가 DB 데이터 변경 요청서에 연결된 근거 문서 정보를 변경할 수 있는 기능을 제공합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc
* PUT
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*orgUid|u01|String|근거 문서 변경 처리자 ID|
|*docId|2021000006|String|결재 문서 번호|
|*groundsDocId|2|String|변경할 근거 문서 번호|
```json
{
    "orgUid": "u01",
    "docId": "2021000006",
    "groundsDocId": "2"
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

# 근거 문서 실행 가능 여부 확인
고객사에서 제공한 API 호출을 통해 연동한 근거 문서의 상태가 실행 가능 상태인지를 확인하는 기능을 제공합니다.
## URL
* /api/sign/doc/dataModify/groundsDoc/isModifiable
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*customerType|1|String|고객사 종류<br/>1 : 블루월넛|
|*request|issue_id=10|String|검색 조건|
```json
{
    "customerType" : 1,
    "request" : "issue_id=10"
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
|isModifiable|true|String|실행 가능 여부<br/>true : 실행 가능<br/>false : 실행 불가능|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {
        "message": "",
        "isModifiable": true
    }
}
```


# 근거 문서 종류 조회
근거 문서 번호로 근거 문서의 종류를 조회합니다. 고객사별로 차이가 있을 수 있습니다.
<br>[고객사 별 근거 문서 종류]
- [현대카드] 1: 일반 협조전, 2: 클라우드 협조전
## URL
* /api/sign/doc/dataModify/groundsDoc/type
* GET
* application/json;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*groundsDocId|CA89-57E456C-144849|String|근거 문서 번호|
```text
groundsDocId=CA89-57E456C-144849
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|messageCode|200|int|결과 메시지 코드|
|serverMessage|success|String|서버용 결과 메시지|
|clientMessage|처리되었습니다.|String|클라이언트용 결과 메시지|
|data||Map|결과 데이터|
|groundsDocType|1|int|근거 문서 종류|
```json
{
    "code": 200,
    "messageCode": 200,
    "clientMessage": "처리되었습니다.",
    "serverMessage": "success",
    "data": {
        "groundsDocType": 2
    }
}
```
