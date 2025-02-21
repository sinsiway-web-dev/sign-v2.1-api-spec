## 문서 상세 조회
작성된 DB 데이터 변경 요청서의 상세 내용을 조회합니다.
### URL
* /api/sign/doc/dataModify/contents
* get
* application/x-www-form-urlencoded;charset=UTF-8

### Request
| 항목      | 값(예시)      | 타입     | 설명     |
|---------|------------|--------|--------|
| *docId  | 2024000005 | String | 문서 ID  |
| *orgUid | user01     | String | 사용자 ID |

```text
?docId=2024000007&orgUid=user01
```

### Response
| 항목                       | 값(예시)                                                       | 타입      | 설명                                                                                                                                                                                                                  |
|--------------------------|-------------------------------------------------------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| code                     | 200| int     | 결과 코드|
| data                     || Map     | 결과 데이터                                                                                                                                                                                                              |
| approver                 || Array   | 결재자 정보                                                                                                                                                                                                              |
| approveOrder             | 1| int     | 결재 순번                                                                                                                                                                                                               |
| approvePowerType         | 0| int     | 결재 권한 종류<br/>0: 결재<br/>1: DB데이터변경실행                                                                                                                                                                                 |
| approveStatus            | 1| int     | 결재 상태<br/>1: 결재 전<br/>2: 승인<br/>3: 반려<br/>4: 후결                                                                                                                                                                     |
| approveDescribe          |승인합니다.| String  | 첨언|
| approveDate              |2024/10/10| String  | 결재일|
| approverName             | 결재자01                                                       | String  | 결재자 이름                                                                                                                                                                                                              |
| approverOrgUid           | m01                                                         | String  | 결재자 ID                                                                                                                                                                                                              |
| approverTitle            |부장| String  | 결재자 직위                                                                                                                                                                                                              |
| approverOrgItemName      | 연구소| String  | 결재자 조직명|
| agentApproverName        |김결재| Sting   | 대리결재자 이름|
| agentApproverOrgUid      |admin1| String  | 대리결재자 ID|
| agentApproverTitle       |팀장| String  | 대리결재자 직위|
| agentApproverOrgItemName |연구소| String  | 대리결재자 조직명|
| dataModifyInfo           || Map     | 변경 실행 정보|
| canExecuteAll            | true| boolean | 전체 실행 가능 여부<br>true: 전체 실행 가능<br>false: 전체 실행 불가능|
| canRejectAll            | true| boolean | 전체 반려 가능 여부<br>true: 전체 반려 가능<br>false: 전체 반려 불가능                                                                                                                                                                   |
| docExecStatus            | 3                                                           | String  | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                                                                                                                                         |
| isDocLogExist     | true                                                         | boolean | 전체 실행 로그 존재 여부<br>true: 존재함<br>false: 존재하지 않음                                                    |
| executableCount     | 2                                                         | int | 실행 가능 SQL 그룹 갯수                                                    |
| execSuccessCount     | 1                                                         | int | 실행 성공 SQL 그룹 갯수                                                    |
| execCompleteCount     | 2                                                         | int | 실행 완료 SQL 그룹 갯수                                                    |
| reExecMaxAllowCount     | 3                                                         | int | 재실행 허용 가능 최대 횟수                                                    |
| isReExecEnabled     | true                                                         | int | 재실행 설정 여부<br>true: 재실행 설정<br>false: 재실행 설정 안함                                                    |
| docExecDate              | 2024/11/14 16:47:25                                         | String  | 문서 실행 완료일                                                                                                                                                                                                           |
| sqlGroup                 |                                                             | Array   | SQL 그룹                                                                                                                                                                                                              |
| sqlGroupId               | 132                                                         | String  | SQL 그룹 ID                                                                                                                                                                                                           |
| sqlGroupName             | SQL 그룹 1                                                    | String  | SQL 그룹 이름                                                                                                                                                                                                           |
| execMsg                  | 변경 SQL 오류 : ORA-01861: literal does not match format string | String  | 실행 실패 메시지                                                                                                                                                                                                           |
| beforeCount              | 10                                                          | int     | 실행 전 검증 데이터 건수                                                                                                                                                                                                      |
| afterCount               | 14                                                          | int     | 실행 후 검증 데이터 건수                                                                                                                                                                                                      |
| beforeSql                | select * from emp_sign where empno=1001                     | String  | 변경 전 검증SQL                                                                                                                                                                                                          |
| afterSql                 | select * from emp_sign where empno=1002                     | String  | 변경 후 검증SQL                                                                                                                                                                                                          |
| modifySql                | update emp_sign set empno=1002 where empno=1001             | String  | 변경 SQL                                                                                                                                                                                                              |
| sqlType                 | 1                                                           | int     | 변경 SQL종류<br/>1 : 기본SQL<br/>2 : PL/SQL                                                                                                                                                                               |
| execResultCode           | 1                                                           | int     | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 중<br>3: 커밋<br>4: 롤백<br>5:실행 에러<br>6: 자동 롤백<br>7: 실행 반려<br>10: 최대 검증 데이터 건수 초과|
| isExecLogExist           | true                                                        | boolean | 실행 로그 존재 여부                                                                                                                                                                                                         |
| execDate                 | 2024/11/12 10:23:22                                         | String  | 실행일                                                                                                                                                                                                                 |
| canExecute               | false| boolean     | 실행 가능 여부<br>true: 실행 가능<br>false: 실행 불가능                                                                                                                                                                            |
| canReject               | false| boolean     | 반려 가능 여부<br>true: 반려 가능<br>false: 반려 불가능                                                                                                                                                                            |
| remainingExecCount               | 3                                                       | int     | 남은 실행 가능 횟수                                                                                                                                                                            |
| doc                      |                                                             | Map     | 결재 문서 정보                                                                                                                                                                                                            |
| currentState             | 6                                                           | int     | 결재 문서 상태<br/>0 : 작성중<br/>1 : 요청<br/>2 : 승인<br/>3 : 반려<br/>4 : 후결<br/>5 : 유효 기간 경과<br/>6 : 무효<br/>7 : 권한 부여 승인<br/>8 : 권한 부여 반려<br/>9 : 권한 회수<br/>10 : 실행 완료<br/>11 : 실행 불가<br/>12 : 권한 부여 유효 기간 경과<br/>13 : 결재 진행 중 |
| currentApproveOrder      | 1                                                           | int     | 결재 중인 결재자 순번                                                                                                                                                                                                        |
| docId                    | 2021000005                                                  | String  | 결재 문서 번호                                                                                                                                                                                                            |
| groundsDocId             | 근거-001                                                      | String  | 근거 문서 번호                                                                                                                                                                                                            |
| createDate               | 2021/04/28 11:30:04                                         | String  | 기안일                                                                                                                                                                                                                 |
| apvLimit                | 2021/05/05                                                  | String  | 결재 기한                                                                                                                                                                                                               |
| requestOrgUid            | u01                                                         | String  | 기안자 ID                                                                                                                                                                                                              |
| requestName              | 사용자01                                                       | String  | 기안자 이름                                                                                                                                                                                                              |
| docTitle                 | \[변경\] DB데이터변경                                              | String  | 문서 제목                                                                                                                                                                                                               |
| requestDescribe          | DB데이터변경사유                                                   | String  | 요청 사유                                                                                                                                                                                                               |
| dataModifyTarget         |                                                             | Map     | 변경 대상 정보                                                                                                                                                                                                            |
| dbAccount                | scott                                                       | String  | DB계정명                                                                                                                                                                                                               |
| dataModifyTargetId       | 34                                                          | String  | 변경 대상 ID                                                                                                                                                                                                            |
| dataModifyTargetName     | PROD                                                        | String  | 변경 대상명                                                                                                                                                                                                              |
| dbTypeText               | ORACLE| String  | DB종류|
|executeWithPassword|1|int|실행 시 비밀번호 입력 여부<br>0: 변경 대상 등록 시 입력<br>1: 문서 실행 시 입력|
|maxVerifyDataCnt|10000|int|검증 데이터 최대 저장 건수|
|maxExecCnt|4000|int|최대 실행 건수|
| message                  |                                                             | String  | 결과 메시지                                                                                                                                                                                                              |

```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "approver": [
            {
                "approveOrder": 1,
                "approvePowerType": 0,
                "approveStatus": 1,
                "approveDescribe": "",
                "approveDate": "",
                "approverName": "결재자",
                "approverOrgUid": "user01",
                "approverTitle": "",
                "approverOrgItemName": "sinsiway",
                "agentApproverName": "테스트",
                "agentApproverOrgUid": "test",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": "sinsiway"
            },
            {
                "approveOrder": 2,
                "approvePowerType": 1,
                "approveStatus": 1,
                "approveDescribe": "",
                "approveDate": "",
                "approverName": "실행자",
                "approverOrgUid": "user02",
                "approverTitle": "",
                "approverOrgItemName": "",
                "agentApproverName": "",
                "agentApproverOrgUid": "",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": ""
            }
        ],
        "dataModifyInfo": {
            "docExecStatus": 2,
            "canExecuteAll": false,
            "canRejectAll": false,
            "isDocLogExist": true,
            "docExecDate": "",
            "executableCount": 1,
            "execSuccessCount": 0,
      	    "execCompleteCount": 2,
            "reExecMaxAllowCount": 3,
            "isReExecEnabled": true,
            "sqlGroup": [
                {
                    "sqlGroupId": "4430",
                    "sqlGroupName": "SQL 그룹 1",
                    "execMsg": "",
                    "beforeCount": 0,
                    "afterCount": 0,
                    "beforeSql": "SELECT * FROM DEPT;",
                    "afterSql": "",
                    "modifySql": "insert into dept values(dept_seq.nextval, 'test', 'kor');\ninsert into dept values(dept_seq.nextval, 'test', 'kor');\ninsert into dept values(dept_seq.nextval, 'test', 'kor');",
                    "sqlType": 1,
                    "execResultCode": 7,
                    "isExecLogExist": false,
                    "execDate": "2024/11/30 19:49:21",
                    "canExecute": false,
                    "canReject": false,
                    "remainingExecCount": 3
                },
                {
                    "sqlGroupId": "4433",
                    "sqlGroupName": "SQL 그룹 2",
                    "execMsg": "",
                    "beforeCount": 0,
                    "afterCount": 0,
                    "beforeSql": "SELECT * FROM DEPT;",
                    "afterSql": "",
                    "modifySql": "update dept set loc = 'KOR' where loc = 'kor';",
                    "sqlType": 1,
                    "execResultCode": 1,
                    "isExecLogExist": false,
                    "execDate": "",
                    "canExecute": true,
                    "canRejcet": true,
                    "remainingExecCount": 3
                }
            ]
        },
        "doc": {
            "currentState": 1,
            "currentApproveOrder": 1,
            "docId": "2024000179",
            "groundsDocId": "",
            "createDate": "2024/11/30 19:52:41",
            "apvLimit": "2024/12/01",
            "requestOrgUid": "user100",
            "requestName": "기안자",
            "docTitle": "test",
            "requestDescribe": "DB데이터변경사유"
        },
        "dataModifyTarget": {
            "dbAccount": "scott",
            "dataModifyTargetId": "2",
            "dataModifyTargetName": "testora",
            "dbTypeText": "ORACLE",
            "executeWithPassword": 1,
            "maxVerifyDataCnt": 10000,
            "maxExecCnt": 4000
        }
    }
}
```

## 문서 전체 실행 로그 조회
문서 전체의 실행 로그를 조회합니다.
### URL
* /api/sign/doc/dataModify/execLog
* GET
* application/x-www-form-urlencoded;charset=UTF-8

### Request
| 항목          | 값(예시)      | 타입         | 설명             |
|-------------|------------|------------|----------------|
| *docId      | 2024000002 | String     | 문서 번호          |

```text
?docId=2024000176
```

### Response
| 항목         | 값(예시)      | 타입     | 설명     |
|------------|------------|--------|--------|
| code       | 200        | int    | 결과 코드  |
| message    |            | String | 결과 메시지 |
| data       |            | Map    | 결과 데이터 |
| execLog    |            | list | 실행 로그  |
| date    |2025/02/03 11:12:45.902| String | 날짜  |
| execType    | 1 | int | 실행 종류<br>1: 변경 전 SQL 실행<br>2: 변경 SQL 실행<br>3: 변경 후 SQL 실행<br>4: 커밋<br>5: 롤백|
| sqlGroupName    |SQL 그룹 1| String | SQL 그룹 이름(커밋, 롤백 시 빈 값 응답) |
| sqlLog    |  | list | SQL 실행 로그(커밋, 롤백 시 빈 값 응답) |
| date    |2025/02/11 11:21:12.122| String | 날짜|
| stmt       |SELECT| String    | SQL 문장 |
| result       |1| int    | 결과<br>0 이상의 수 : 수행(조회) 건수<br>0 미만의 수 : 수행(조회) 실패 |
| msg       | SIGN ERROR : 변경 후 데이터 저장에 실패하였습니다. |String| 실패 메시지(성공 시 빈 값 응답) |
| execResult    | 1 | int | 실행 결과<br>1: 성공<br>2: 실패|
| msg    | SIGN ERROR : 변경 후 데이터 저장에 실패하였습니다.  | String | 실패 메시지(성공 시/SQL 실행 로그일 시 빈 값 응답) |

[성공]
```json
{
  "code": 200,
  "message": "처리되었습니다.",
  "data": {
    "execLog": [
      {
        "date": "",
        "execType": 1,
        "sqlGroupName": "SQL 그룹 1",
        "sqlLog": [
          {
            "date": "2025/02/11 11:21:12.122",
            "stmt": "SELECT",
            "result":1,
            "msg":""
          }
        ],
        "execResult": 1,
        "msg": ""
      },
      {
        "date": "",
        "execType": 2,
        "sqlGroupName": "SQL 그룹 1",
        "sqlLog": [
          {
            "date": "2025/02/11 11:21:12.122",
            "stmt": "INSERT",
            "result":1,
            "msg":""
          },
          {
            "date": "2025/02/11 11:21:12.322",
            "stmt": "UPDATE",
            "result":-1,
            "msg":"ORA-00904: \"LOC3\": invalid identifier"
          }
        ],
        "execResult": 2,
        "msg": ""
      },
      {
        "date": "2025/02/11 11:21:12.122",
        "execType": 5,
        "sqlGroupName": "",
        "sqlLog": [],
        "execResult": 1,
        "msg": ""
      }
    ]
  }
}
```

[실패]
```json
{
    "code": 500,
    "data": {},
    "message": "처리에 실패하였습니다."
}
```
