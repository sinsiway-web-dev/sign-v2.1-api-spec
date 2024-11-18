# Sign new v2.1 API 명세
- 변경서 다중 SQL 그룹 지원을 위해서 작성된 API 명세서 입니다.
- 기존 SIGN v2.1 API의 문서 부분이 수정되었습니다.
- 실행 상태 코드 값이 변경되었습니다.

# 문서 작성
## 승인 요청
작성 완료된 DB 데이터 변경 요청서를 생성 합니다.
### URL
* /api/sign/doc/dataModify/ask
* POST
* application/json;charset=UTF-8
### Request
| 항목                         | 값(예시)                                           | 타입      | 설명                                             |
|----------------------------|-------------------------------------------------|---------|------------------------------------------------|
| *selectBeforeDataCountFlag | false                                           | boolean | 변경 전 데이터 조회 여부<br/>true : 조회<br/>false : 조회 안함 |
| *docTitle                  | \[변경\] DB데이터변경                                  | String  | 문서 제목                                          |
| describe                   | DB데이터변경사유                                       | String  | 사유                                             |
| *aprvLimit                 | 2021/05/05                                      | String  | 결재 기한                                          |
| *dataModifyTargetId        | 34                                              | int     | 변경 대상 ID                                       |
| *orgUid                    | u01                                             | String  | 기안자 ID                                         |
| groundsDocId               | 근거-001                                          | String  | 근거 문서 번호                                       |
| *apvLineApprover           |                                                 | Array   | 결재자 목록                                         |
| *approverOrgUid            | m01                                             | String  | 결재자 ID                                         |
| *approveOrder              | 1                                               | int     | 결재 순서                                          |
| *approvePowerType          | 0                                               | int     | 결재 권한 종류<br/>0 : 결재<br/>1 : DB데이터변경실행          |
| *sqlGroup                  |                                                 | Array   | SQL 그룹 리스트                                     |
| *sqlGroupName              | 사용자 데이터 변경                                      | String  | SQL 그룹 이름(85 자 이하)                             | 
| *modifySqlType             | 1                                               | int     | 변경 SQL종류<br/>1 : 기본SQL<br/>2 : PL/SQL          |
| *modifySql                 | update emp_sign set empno=1002 where empno=1001 | String  | 변경 SQL                                         |
| *beforeSql                 | select * from emp_sign where empno=1001         | String  | 변경 전 검증SQL                                     |
| *afterSql                  | select * from emp_sign where empno=1002         | String  | 변경 후 검증SQL                                     |


```json
{
    "selectBeforeDataCountFlag": false,
    "docTitle": "[변경] DB데이터변경",
    "describe": "DB데이터변경사유",
    "aprvLimit": "2024/11/05",
    "dataModifyTargetId": "2",
    "orgUid": "test",
    "groundsDocId": "",
    "apvLineApprover": [
        {
            "approveOrder": 1,
            "approvePowerType": 0,
            "approverOrgUid": "test"
        },
        {
            "approveOrder": 2,
            "approvePowerType": 1,
            "approverOrgUid": "test"
        }
    ],
    "sqlGroup":[
		    {
				    "sqlGroupName": "SQL 그룹 1",
				    "modifySqlType": 1,
				    "modifySql": "update emp_sign set empno=1002 where empno=1001",
				    "beforeSql": "select * from emp_sign where empno=1001",
				    "afterSql": "select * from emp_sign where empno=1002"
		    },
		    {
				    "sqlGroupName": "SQL 그룹 2",
				    "modifySqlType": 1,
				    "modifySql": "update emp_sign set empno=1003 where empno=1004",
				    "beforeSql": "select * from emp_sign where empno=1003",
				    "afterSql": "select * from emp_sign where empno=1004"
		    }
    ]
}
```
### Response
| 항목      | 값(예시)      | 타입     | 설명       |
|---------|------------|--------|----------|
| code    | 200        | int    | 결과 코드    |
| data    |            | Map    | 결과 데이터   |
| docId   | 2021000005 | String | 결재 문서 번호 |
| message |            | String | 결과 메시지   |

[성공]
```json
{
    "code": 200,
    "data": {
        "docId": "2021000005"
    },
    "message": ""
}
```

[실패]
```json
{
    "code": 500,
    "message": "",
    "data": {}
}
```

# 문서 실행
## 부분 SQL 그룹 실행
여러 개의 SQL 그룹을 한번에 실행 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/exec
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |
| dataEncryptionFlag | 0                     | int           | 암호화 여부<br/>0 : 평문(기본값)<br/>1 : 암호화 |
| *sqlGroupId        | 23, 22                | Array<String> | SQL 그룹 ID 목록                       |

```json
{
    "execId": "109923-sdf89sd6-ASD21",
    "dataEncryptionFlag": 0,
    "sqlGroupId": [
        "23", 
        "44"
    ]
}
```

### Response
| 항목            | 값(예시) | 타입     | 설명                                          |
|---------------|-------|--------|---------------------------------------------|
| code          | 200   | int    | 결과 코드                                       |
| data          |       | Map    | 결과 데이터                                      |
| docExecStatus | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행 |

[성공]
```json
{
    "code": 200,
    "data": {
      "docExecStatus": 2
    },
    "message": "처리되었습니다."
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

## 전체 SQL 그룹 실행
모든 SQL 그룹을 한번에 실행 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/exec-all
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |
| dataEncryptionFlag | 0                     | int           | 암호화 여부<br/>0 : 평문(기본값)<br/>1 : 암호화 |

```json
{
    "execId": "109923-sdf89sd6-ASD21",
    "dataEncryptionFlag": 0
}
```

### Response
| 항목            | 값(예시) | 타입     | 설명                                          |
|---------------|-------|--------|---------------------------------------------|
| code          | 200   | int    | 결과 코드                                       |
| data          |       | Map    | 결과 데이터                                      |
| docExecStatus | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행 |

[성공]
```json
{
    "code": 200,
    "data": {
      "docExecStatus": 2
    },
    "message": "처리되었습니다."
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

## 부분 커밋
실행 성공한 SQL 그룹의 변경 사항을 커밋합니다.
- 실행 상태(execResultCode = 2)인 SQL 그룹이 1개 이상 있어야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/commit
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |

```json
{
    "execId": "109923-sdf89sd6-ASD21"
}
```

### Response
| 항목                | 값(예시) | 타입     | 설명                                                                                          |
|-------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus     | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| committedSqlGroup |       | Array  | 커밋된 SQL 그룹 리스트                                                                              |
| sqlGroupId        | 129   | String | SQL 그룹 ID                                                                                   |
| execResultCode    | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "committedSqlGroup" :[
            {
                "sqlGroupId" : "23",
                "execResultCode" : 3
            },
            {
                "sqlGroupId" : "44",
                "execResultCode" : 3
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## 전체 커밋
전체 SQL 그룹의 변경 사항을 커밋합니다.
- 모든 SQL 그룹이 실행 상태(execResultCode = 2)여야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/commit-all
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |

```json
{
    "execId": "109923-sdf89sd6-ASD21"
}
```

### Response
| 항목                | 값(예시) | 타입     | 설명                                                                                          |
|-------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus     | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| committedSqlGroup |       | Array  | 커밋된 SQL 그룹 리스트                                                                              |
| sqlGroupId        | 129   | String | SQL 그룹 ID                                                                                   |
| execResultCode    | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "committedSqlGroup" :[
            {
                "sqlGroupId" : "23",
                "execResultCode" : 3
            },
            {
                "sqlGroupId" : "44",
                "execResultCode" : 3
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## 부분 롤백
실행 성공한 SQL 그룹의 변경 사항을 롤백합니다.
- 실행 상태(execResultCode = 2)인 SQL 그룹이 1개 이상 있어야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/rollback
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |

```json
{
    "execId": "109923-sdf89sd6-ASD21"
}
```

### Response
| 항목                 | 값(예시) | 타입     | 설명                                                                                          |
|--------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus      | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| rolledBackSqlGroup |       | Array  | 커밋된 SQL 그룹 리스트                                                                              |
| sqlGroupId         | 129   | String | SQL 그룹 ID                                                                                   |
| execResultCode     | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "rolledBackSqlGroup" :[
            {
                "sqlGroupId" : "23",
                "execResultCode" : 4
            },
            {
                "sqlGroupId" : "44",
                "execResultCode" : 4
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## 전체 롤백
전체 SQL 그룹의 변경 사항을 롤백합니다.
- 모든 SQL 그룹이 실행 상태(execResultCode = 2)여야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/rollback-all
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |

```json
{
    "execId": "e594ad39-a2b8-492d-af9e-83a001358df8"
}
```

### Response
| 항목                 | 값(예시) | 타입     | 설명                                                                                          |
|--------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus      | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| rolledBackSqlGroup |       | Array  | 커밋된 SQL 그룹 리스트                                                                              |
| sqlGroupId         | 129   | String | SQL 그룹 ID                                                                                   |
| execResultCode     | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "rolledBackSqlGroup" :[
            {
                "sqlGroupId" : "23",
                "execResultCode" : 4
            },
            {
                "sqlGroupId" : "44",
                "execResultCode" : 4
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## 실행 반려
SQL 그룹의 실행을 반려합니다.
- SQL 그룹의 상태가 실행 전(1)이여야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/reject
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |
| *sqlGroupId        | 23, 22                | Array<String> | SQL 그룹 ID 목록                       |

```json
{
    "execId": "e594ad39-a2b8-492d-af9e-83a001358df8",
    "sqlGroupId": [
      "123", 
      "876"
    ]
}
```

### Response
| 항목               | 값(예시) | 타입     | 설명                                                                                          |
|------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus    | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| rejectedSqlGroup |       | Array  | 반려된 SQL 그룹 리스트                                                                              |
| sqlGroupId       | 23    | String | SQL 그룹 ID                                                                                   |
| execResultCode   | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "rejectedSqlGroup" :[
            {
                "sqlGroupId" : "123",
                "execResultCode" : 7
            },
            {
                "sqlGroupId" : "876",
                "execResultCode" : 7
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## 전체 실행 반려
모든 SQL 그룹의 실행을 반려합니다.
- 모든 SQL 그룹의 상태가 실행 전(1)이여야 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/reject-all
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *execId            | 109923-sdf89sd6-ASD21 | String        | 실행 ID                              |

```json
{
    "execId": "e594ad39-a2b8-492d-af9e-83a001358df8"
}
```

### Response
| 항목               | 값(예시) | 타입     | 설명                                                                                          |
|------------------|-------|--------|---------------------------------------------------------------------------------------------|
| docExecStatus    | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| rejectedSqlGroup |       | Array  | 반려된 SQL 그룹 리스트                                                                              |
| sqlGroupId       | 23    | String | SQL 그룹 ID                                                                                   |
| execResultCode   | 1     | int    | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |

[성공]
```json
{
    "code": 200,
    "data": {
        "docExecStatus": 2,
        "rejectedSqlGroup" :[
            {
                "sqlGroupId" : "123",
                "execResultCode" : 7
            },
            {
                "sqlGroupId" : "876",
                "execResultCode" : 7
            }
        ]
    },
    "message": "처리되었습니다."
}
```

[실패]
- 실행 ID가 만료되고 변경 대상과의 커넥션이 해제됩니다.
```json
{
  "code": 500,
  "message": "처리에 실패하였습니다.",
  "data": {
    "docExecStatus": 0
  }
}
```

## SQL 그룹 실행 정보 조회
실행 ID로 현재 실행 상태와 SQL 그룹의 상세 내용을 조회합니다.
### URL
* /api/sign/doc/dataModify/sql-group/exec-info
* get
* application/x-www-form-urlencoded;charset=UTF-8

### Request
| 항목      | 값(예시)                 | 타입     | 설명    |
|---------|-----------------------|--------|-------|
| *execId | 109923-sdf89sd6-ASD21 | String | 실행 ID |

```text
?execId=109923-sdf89sd6-ASD21
```

### Response
| 항목             | 값(예시)                                                       | 타입      | 설명                                                                                          |
|----------------|-------------------------------------------------------------|---------|---------------------------------------------------------------------------------------------|
| code           | 200                                                         | int     | 결과 코드                                                                                       |
| data           |                                                             | Map     | 결과 데이터                                                                                      |
| docExecStatus  | 3                                                           | String  | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                 |
| sqlGroup       |                                                             | Array   | SQL 그룹 리스트                                                                                  |
| sqlGroupId     | 110                                                         | String  | SQL 그룹 ID                                                                                   |
| sqlGroupName   | SQL 그룹 1                                                    | String  | SQL 그룹 이름                                                                                   |
| execResultCode | 1                                                           | int     | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려 |
| modifySql      | update emp_sign set empno=1002 where empno=1001             | String  | 변경 SQL                                                                                      |
| beforeSql      | select * from emp_sign where empno=1001                     | String  | 변경 전 검증SQL                                                                                  |
| afterSql       | select * from emp_sign where empno=1002                     | String  | 변경 후 검증SQL                                                                                  |
| isLogExist     | true                                                        | boolean | 실행 로그 존재 여부                                                                                 |
| beforeCount    | 10                                                          | int     | 실행 전 검증 데이터 건수                                                                              |
| afterCount     | 14                                                          | int     | 실행 후 검증 데이터 건수                                                                              |
| failMessage    | 변경 SQL 오류 : ORA-01861: literal does not match format string | String  | 실행 실페 메시지                                                                                   |
| execDate       | 2024/11/12 10:23:22                                         | String  | 실행일                                                                                         |

[성공]
```json
{
    "code": 200,
    "data": {
      "docExecStatus": 2,
      "sqlGroup": [
        {
          "sqlGroupId": "192",
          "sqlGroupName": "SQL 그룹 1",
          "execResultCode": 2,
          "modifySql": "update emp_sign set empno=1002 where empno=1001",
          "beforeSql": "select * from emp_sign where empno=1001",
          "afterSql": "select * from emp_sign where empno=1002",
          "isLogExist": true,
          "beforeCount": 1,
          "afterCount": 2,
          "failMessage": "",
          "execDate": ""
        },
        {
          "sqlGroupId": "192",
          "sqlGroupName": "SQL 그룹 1",
          "execResultCode": 3,
          "modifySql": "update emp_sign set empno=1002 where empno=1001",
          "beforeSql": "select * from emp_sign where empno=1001",
          "afterSql": "select * from emp_sign where empno=1002",
          "isLogExist": true,
          "beforeCount": 1,
          "afterCount": 2,
          "failMessage": "",
          "execDate": "2024/11/12 10:23:22"
        },
        {
          "sqlGroupId": "192",
          "sqlGroupName": "SQL 그룹 1",
          "execResultCode": 1,
          "modifySql": "update emp_sign set empno=1002 where empno=1001",
          "beforeSql": "select * from emp_sign where empno=1001",
          "afterSql": "select * from emp_sign where empno=1002",
          "isLogExist": true,
          "beforeCount": 1,
          "afterCount": 2,
          "failMessage": "",
          "execDate": ""
        }
      ]
    },
    "message": "처리되었습니다."
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

## 실행 중 이탈

### URL
* /api/sign/doc/dataModify/exit
* post
* application/x-www-form-urlencoded;charset=UTF-8
*
### Request
| 항목      | 값(예시)                 | 타입     | 설명    |
|---------|-----------------------|--------|-------|
| *execId | 109923-sdf89sd6-ASD21 | String | 실행 ID |

```json
{
    "execId": "109923-sdf89sd6-ASD21"
}
```

### Response
| 항목            | 값(예시) | 타입     | 설명                                          |
|---------------|-------|--------|---------------------------------------------|
| code          | 200   | int    | 결과 코드                                       |
| data          |       | Map    | 결과 데이터                                      |

[성공]
```json
{
    "code": 200,
    "data": {},
    "message": "처리되었습니다."
}
```

# 문서 내용 조회
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

## Response
| 항목                       | 값(예시)                                                       | 타입      | 설명                                                                                                                                                                                                                  |
|--------------------------|-------------------------------------------------------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| code                     | 200                                                         | int     | 결과 코드                                                                                                                                                                                                               |
| data                     |                                                             | Map     | 결과 데이터                                                                                                                                                                                                              |
| approver                 |                                                             | Array   | 결재자 정보                                                                                                                                                                                                              |
| approveOrder             | 1                                                           | int     | 결재 순번                                                                                                                                                                                                               |
| approvePowerType         | 0                                                           | int     | 결재 권한 종류<br/>0: 결재<br/>1: DB데이터변경실행                                                                                                                                                                                 |
| approveStatus            | 1                                                           | int     | 결재 상태<br/>1: 결재 전<br/>2: 승인<br/>3: 반려<br/>4: 후결                                                                                                                                                                     |
| approveDescribe          |                                                             | String  | 첨언                                                                                                                                                                                                                  |
| approveDate              |                                                             | String  | 결재일                                                                                                                                                                                                                 |
| approverName             | 결재자01                                                       | String  | 결재자 이름                                                                                                                                                                                                              |
| approverOrgUid           | m01                                                         | String  | 결재자 ID                                                                                                                                                                                                              |
| approverTitle            |                                                             | String  | 결재자 직위                                                                                                                                                                                                              |
| approverOrgItemName      | 연구소                                                         | String  | 결재자 조직명                                                                                                                                                                                                             |
| agentApproverName        |                                                             | Sting   | 대리결재자 이름                                                                                                                                                                                                            |
| agentApproverOrgUid      |                                                             | String  | 대리결재자 ID                                                                                                                                                                                                            |
| agentApproverTitle       |                                                             | String  | 대리결재자 직위                                                                                                                                                                                                            |
| agentApproverOrgItemName |                                                             | String  | 대리결재자 조직명                                                                                                                                                                                                           |
| dataModifyInfo           |                                                             | Map     | 변경 실행 정보                                                                                                                                                                                                            |
| docExecStatus            | 3                                                           | int     | 문서 실행 상태                                                                                                                                                                                                            |
| docExecStatus            | 3                                                           | String  | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행                                                                                                                                                                         |
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
| *sqlType                 | 1                                                           | int     | 변경 SQL종류<br/>1 : 기본SQL<br/>2 : PL/SQL                                                                                                                                                                               |
| execResultCode           | 1                                                           | int     | SQL 그룹 실행 결과 코드<br>1: 실행 전<br>2: 실행 성공<br>3: 커밋<br>4: 롤백<br>5:실행 실패<br>6: 자동 롤백<br>7: 실행 반려                                                                                                                         |
| isExecLogExist           | true                                                        | boolean | 실행 로그 존재 여부                                                                                                                                                                                                         |
| execDate                 | 2024/11/12 10:23:22                                         | String  | 실행일                                                                                                                                                                                                                 |
| doc                      |                                                             | Map     | 결재 문서 정보                                                                                                                                                                                                            |
| currentState             | 6                                                           | int     | 결재 문서 상태<br/>0 : 작성중<br/>1 : 요청<br/>2 : 승인<br/>3 : 반려<br/>4 : 후결<br/>5 : 유효 기간 경과<br/>6 : 무효<br/>7 : 권한 부여 승인<br/>8 : 권한 부여 반려<br/>9 : 권한 회수<br/>10 : 실행 완료<br/>11 : 실행 불가<br/>12 : 권한 부여 유효 기간 경과<br/>13 : 결재 진행 중 |
| currentApproveOrder      | 1                                                           | int     | 결재 중인 결재자 순번                                                                                                                                                                                                        |
| docId                    | 2021000005                                                  | String  | 결재 문서 번호                                                                                                                                                                                                            |
| groundsDocId             | 근거-001                                                      | String  | 근거 문서 번호                                                                                                                                                                                                            |
| createDate               | 2021/04/28 11:30:04                                         | String  | 기안일                                                                                                                                                                                                                 |
| aprvLimit                | 2021/05/05                                                  | String  | 결재 기한                                                                                                                                                                                                               |
| requestOrgUid            | u01                                                         | String  | 기안자 ID                                                                                                                                                                                                              |
| requestName              | 사용자01                                                       | String  | 기안자 이름                                                                                                                                                                                                              |
| docTitle                 | \[변경\] DB데이터변경                                              | String  | 문서 제목                                                                                                                                                                                                               |
| requestDescribe          | DB데이터변경사유                                                   | String  | 요청 사유                                                                                                                                                                                                               |
| dataModifyTarget         |                                                             | Map     | 변경 대상 정보                                                                                                                                                                                                            |
| dbAccount                | scott                                                       | String  | DB계정명                                                                                                                                                                                                               |
| dataModifyTargetId       | 34                                                          | String  | 변경 대상 ID                                                                                                                                                                                                            |
| dataModifyTargetName     | PROD                                                        | String  | 변경 대상명                                                                                                                                                                                                              |
| dbTypeText               | ORACLE                                                      | String  | DB종류                                                                                                                                                                                                                |
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
                "approverName": "테스트1",
                "approverOrgUid": "test1",
                "approverTitle": "",
                "approverOrgItemName": "sinsiway",
                "agentApproverName": "",
                "agentApproverOrgUid": "",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": ""
            },
            {
                "approveOrder": 2,
                "approvePowerType": 1,
                "approveStatus": 1,
                "approveDescribe": "",
                "approveDate": "",
                "approverName": "테스트2",
                "approverOrgUid": "test2",
                "approverTitle": "",
                "approverOrgItemName": "sinsiway",
                "agentApproverName": "",
                "agentApproverOrgUid": "",
                "agentApproverTitle": "",
                "agentApproverOrgItemName": ""
            }
        ],
        "dataModifyInfo": {
            "docExecStatus": 3,
            "docExecDate": "2024/11/14 16:47:25",
            "sqlGroup": [
                {
                    "sqlGroupId": "89",
                    "sqlGroupName": "testSQL 그룹 1",
                    "execMsg": "",
                    "beforeCount": 11,
                    "afterCount": 11,
                    "beforeSql": "select * from emp;",
                    "afterSql": "select * from emp;",
                    "modifySql": "insert into dept values(1001, 'test', 'test');",
                    "sqlType": 1,
                    "execResultCode": 3,
                    "isExecLogExist": true,
                    "execDate": "2024/11/14 16:43:35"
                },
                {
                    "sqlGroupId": "123",
                    "sqlGroupName": "testSQL 그룹 2",
                    "execMsg": "",
                    "beforeCount": 11,
                    "afterCount": 11,
                    "beforeSql": "select * from emp;",
                    "afterSql": "select * from emp;",
                    "modifySql": "insert into dept values(1002, 'test', 'test');",
                    "sqlType": 1,
                    "execResultCode": 3,
                    "isExecLogExist": true,
                    "execDate": "2024/11/14 16:55:35"
                }
            ]
        },
        "doc": {
            "currentState": 1,
            "currentApproveOrder": 1,
            "docId": "2024000007",
            "groundsDocId": "",
            "createDate": "2024/11/14 16:46:48",
            "aprvLimit": "2024/12/05",
            "requestOrgUid": "test",
            "requestName": "테스트",
            "docTitle": "[변경] DB데이터변경",
            "requestDescribe": "DB데이터변경사유"
        },
        "dataModifyTarget": {
            "dbAccount": "scott",
            "dataModifyTargetId": "2",
            "dataModifyTargetName": "testora",
            "dbTypeText": "ORACLE"
        }
    }
}
```

## 변경 전 데이터 조회
- SQL 그룹 실행 상태가 2: 실행 성공, 3: 커밋 상태일 시 호출 가능합니다.
### URL
* /api/sign/doc/dataModify/sql-group/before-data
* get
* application/x-www-form-urlencoded;charset=UTF-8

### Request
| 항목          | 값(예시)      | 타입     | 설명        |
|-------------|------------|--------|-----------|
| *docId      | 2024000005 | String | 문서 ID     |
| *sqlGroupId | 23         | String | SQL 그룹 ID |

```text
?docId=2024000005&sqlGroupId=23
```

### Response
| 항목         | 값(예시)      | 타입            | 설명       |
|------------|------------|---------------|----------|
| code       | 200        | int           | 결과 코드    |
| data       |            | Map           | 결과 데이터   |
| column     |            | Array<String> | 컬럼       |
| data       |            | Array<Map>    | 데이터      |
| message    |            | String        | 결과 메시지   |

[성공]
```json
{
    "code": 200,
    "data": {
        "column": [
            "EMPNO",
            "ENAME",
            "SAL"
        ],
        "data": [
          {
            "EMPNO":" 1001",
            "ENAME": "TEST01",
            "SAL": "999"
          },
          {
            "EMPNO":" 1002",
            "ENAME": "TEST02",
            "SAL": "99"
          }
        ]
    },
    "message": "처리되었습니다."
}
```

[내용 없음]
```json
{
    "code": 204,
    "data": {
        "beforeData": {
            "column": [],
            "data": []
        }
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "beforeData": {
            "column": [],
            "data": []
        }
    },
    "message": "처리에 실패하였습니다."
}
```

## 변경 후 데이터 조회
- SQL 그룹 실행 상태가 2: 실행 성공, 3: 커밋 상태일 시 호출 가능합니다.
### URL
* /api/sign/doc/dataModify/sql-group/after-data
* get
* application/x-www-form-urlencoded;charset=UTF-8

### Request
| 항목          | 값(예시)      | 타입     | 설명        |
|-------------|------------|--------|-----------|
| *docId      | 2024000005 | String | 문서 ID     |
| *sqlGroupId | 23         | String | SQL 그룹 ID |

```text
?docId=2024000005&sqlGroupId=23
```

### Response
| 항목         | 값(예시)      | 타입            | 설명       |
|------------|------------|---------------|----------|
| code       | 200        | int           | 결과 코드    |
| data       |            | Map           | 결과 데이터   |
| column     |            | Array<String> | 컬럼       |
| data       |            | Array<Map>    | 데이터      |
| message    |            | String        | 결과 메시지   |

[성공]
```json
{
    "code": 200,
    "data": {
        "column": [
            "EMPNO",
            "ENAME",
            "SAL"
        ],
        "data": [
          {
            "EMPNO":" 1001",
            "ENAME": "TEST01",
            "SAL": "999"
          },
          {
            "EMPNO":" 1002",
            "ENAME": "TEST02",
            "SAL": "99"
          }
        ]
    },
    "message": "처리되었습니다."
}
```

[내용 없음]
```json
{
    "code": 204,
    "data": {
        "beforeData": {
            "column": [],
            "data": []
        }
    },
    "message": "데이터가 없습니다."
}
```

[실패]
```json
{
    "code": 500,
    "data": {
        "beforeData": {
            "column": [],
            "data": []
        }
    },
    "message": "처리에 실패하였습니다."
}
```


