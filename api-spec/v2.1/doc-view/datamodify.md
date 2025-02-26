
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
| *docId            | 2024000002 | String        | 문서 번호                              |
| *orgUid            | user01 | String        | 사용자 ID                              |
| dataEncryptionFlag | 0                     | int           | 암호화 여부<br/>0 : 평문(기본값)<br/>1 : 암호화 |
| *sqlGroupId        | 23, 22                | Array<String> | SQL 그룹 ID 목록                       |
| dbPassword        | petra@one1                | String | 변경 대상 비밀번호<br/>(*문서 상세 조회 시 executeWithPassword 값이 1일 경우 필수 입력입니다.)|

```json
{
    "docId": "2024000002",
    "orgUid": "user01",
    "dataEncryptionFlag": 0,
    "dbPassword": "petra@one1",
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
| isSqlGroupFail          |  false     | boolean    | SQL 그룹 실행 실패 여부  실패: true, 성공: false                                    |
| rolledBackSqlGroup          |       | Array    | 실패 시 자동 롤백된 SQL 그룹 리스트                                      |
| sqlGroupId          |    10023   | String    | 실패 시 자동 롤백된 SQL 그룹 ID                                      |
| sqlGroupName          |    SQL 그룹 1   | String    | 실패 시 자동 롤백된 SQL 그룹 이름                                      |
| succeededSqlGroup          |       | Array    | 실행 성공 SQL 그룹 리스트                                      |
| sqlGroupId          |    10023   | String    | 실행 성공 SQL 그룹 ID                                      |
| sqlGroupName          |    SQL 그룹 1   | String    | 실행 성공 SQL 그룹 이름                                      |

[성공]
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "docExecStatus": 2,
        "succeededSqlGroup": [
            {
                "sqlGroupId": "152",
                "sqlGroupName": "SQL 그룹 3"
            }
        ],
        "isSqlGroupFail": false,
        "rolledBackSqlGroup": []
    }
}
```

[SQL 그룹 실행 실패]
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "docExecStatus": 2,
        "succeededSqlGroup": [],
        "isSqlGroupFail": true,
        "rolledBackSqlGroup": [
            {
                "sqlGroupId": "135",
                "sqlGroupName": "SQL 그룹 1"
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

## 전체 SQL 그룹 실행
모든 SQL 그룹을 한번에 실행 합니다.
### URL
* /api/sign/doc/dataModify/sql-group/exec-all
* POST
* application/json;charset=UTF-8

### Request
| 항목                 | 값(예시)                 | 타입            | 설명                                 |
|--------------------|-----------------------|---------------|------------------------------------|
| *docId            | 2024000002 | String        | 문서 번호                              |
| *orgUid            | user01 | String        | 사용자 ID                              |
| dataEncryptionFlag | 0                     | int           | 암호화 여부<br/>0 : 평문(기본값)<br/>1 : 암호화 |
| dbPassword        | petra@one1                | String | 변경 대상 비밀번호<br/>(*문서 상세 조회 시 executeWithPassword 값이 1일 경우 필수 입력입니다.)|

```json
{
    "docId": "2024000002",
    "orgUid": "user01",
    "dataEncryptionFlag": 0,
    "dbPassword": "petra@one1"
}
```

### Response
| 항목            | 값(예시) | 타입     | 설명                                          |
|---------------|-------|--------|---------------------------------------------|
| code          | 200   | int    | 결과 코드                                       |
| data          |       | Map    | 결과 데이터                                      |
| docExecStatus | 3     | String | 문서 실행 상태<br>1: 실행 전<br>2: 부분 실행<br>3: 모두 실행 |
| isSqlGroupFail          |  false     | boolean    | SQL 그룹 실행 실패 여부  실패: true, 성공: false                                    |
| rolledBackSqlGroup          |       | Array    | 실패 시 자동 롤백된 SQL 그룹 리스트                                      |
| sqlGroupId          |    10023   | String    | 실패 시 자동 롤백된 SQL 그룹 ID                                      |
| sqlGroupName          |    SQL 그룹 1   | String    | 실패 시 자동 롤백된 SQL 그룹 이름                                      |
| succeededSqlGroup          |       | Array    | 실행 성공 SQL 그룹 리스트                                      |
| sqlGroupId          |    10023   | String    | 실행 성공 SQL 그룹 ID                                      |
| sqlGroupName          |    SQL 그룹 1   | String    | 실행 성공 SQL 그룹 이름                                      |

[성공]
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "docExecStatus": 2,
        "succeededSqlGroup": [
            {
                "sqlGroupId": "152",
                "sqlGroupName": "SQL 그룹 3"
            }
        ],
        "isSqlGroupFail": false,
        "rolledBackSqlGroup": []
    }
}
```

[SQL 그룹 실행 실패]
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "docExecStatus": 2,
        "succeededSqlGroup": [],
        "isSqlGroupFail": true,
        "rolledBackSqlGroup": [
            {
                "sqlGroupId": "135",
                "sqlGroupName": "SQL 그룹 1"
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