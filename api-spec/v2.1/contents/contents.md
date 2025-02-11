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
