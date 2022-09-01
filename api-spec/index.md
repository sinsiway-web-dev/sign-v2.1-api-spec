# Sign v2.0 API 명세
# 일반
## Header
로그인을 제외한 모든 API는 로그인 성공 시 전달 받은 accessToken을 헤더 Authorization에 명시합니다.
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*Authorization|eyJ0eXAiOiJKV1Q...|token|로그인 성공 인증 토큰|
## Response code
|code|desc|
|---|---|
|200|성공|
|204|결과 없음|
|500|실패|
## DB 타입
[petra4 database type id](./etc/petra4dbtype.md)
# 로그인
|API|URL|HTTP Method|View|
|---|---|---|---|
|[로그인](./login/login.md/#로그인)|/api/sign/login|POST|로그인|
|[사용자 추가 후 로그인](./login/login.md/#사용자-추가-후-로그인)|/api/sign/login/user|POST|로그인|
|[로그아웃](./login/login.md/#로그아웃)|/api/sign/logout|POST|사용자 - 로그아웃|
# 메뉴
## 전자 결재 - 전체
|API|URL|HTTP Method|View|
|---|---|---|---|
|[전체](./menu/doc-all-list.md/#전체)|/api/sign/doc/dataModify|GET|관리자 용 전체 문서 목록 조회|
|[전체](./menu/doc-all-list.md/#결재-문서-결재자)|/api/sign/doc/dataModify/approver|GET|결재 문서 결재자 정보 조회|
## 전자 결재 - 기안
|API|URL|HTTP Method|View|
|---|---|---|---|
|[기안 - 결재 상태 별 문서 개수](./menu/request.md/#기안---결재-상태-별-문서-개수)|/api/sign/request/approveState/docCount/dataModify|GET|메인 메뉴|
|[기안 - 실행 상태 별 문서 개수](./menu/request.md/#기안---실행-상태-별-문서-개수)|/api/sign/request/execState/docCount/dataModify|GET|메인 메뉴|
|[기안 - 결재 대기](./menu/request.md/#기안---결재-대기)|/api/sign/request/standby/doc/dataModify|GET|기안자 대기 문서 목록|
|[기안 - 결재 승인](./menu/request.md/#기안---결재-승인)|/api/sign/request/approve/doc/dataModify|GET|기안자 승인 문서 목록|
|[기안 - 실행 성공](./menu/request.md/#기안---실행-성공)|/api/sign/request/exec/success/doc/dataModify|GET|기안자 성공 문서 목록|
|[기안 - 실행 실패](./menu/request.md/#기안---실행-실패)|/api/sign/request/exec/fail/doc/dataModify|GET|기안자 실패 문서 목록|
|[기안 - 결재 반려](./menu/request.md/#기안---결재-반려)|/api/sign/request/reject/doc/dataModify|GET|기안자 반려 문서 목록|
|[기안 - 실행 미완료](./menu/request.md/#기안---실행-미완료)|/api/sign/request/exec/unfinished/doc/dataModify|GET|-|
|[기안 - 전체](./menu/request.md/#기안---전체)|/api/sign/request/doc/dataModify|GET|-|
## 전자 결재 - 결재
|API|URL|HTTP Method|View|
|---|---|---|---|
|[결재 - 결재 상태 별 문서 개수](./menu/approver.md/#결재---결재-상태-별-문서-개수)|/api/sign/approver/approveState/docCount/dataModify|GET|메인 메뉴|
|[결재 - 실행 상태 별 문서 개수](./menu/approver.md/#결재---실행-상태-별-문서-개수)|/api/sign/approver/execState/docCount/dataModify|GET|메인 메뉴|
|[결재 - 결재 예정](./menu/approver.md/#결재---결재-예정)|/api/sign/approver/expected/doc/dataModify|GET|결재자 예정 문서 목록|
|[결재 - 결재 대기](./menu/approver.md/#결재---결재-대기)|/api/sign/approver/standby/doc/dataModify|GET|결재자 대기 문서 목록|
|[결재 - 결재 진행](./menu/approver.md/#결재---결재-진행)|/api/sign/approver/progress/doc/dataModify|GET|결재자 진행 문서 목록|
|[결재 - 결재 승인](./menu/approver.md/#결재---결재-승인)|/api/sign/approver/approve/doc/dataModify|GET|결재자 승인 문서 목록|
|[결재 - 결재 반려](./menu/approver.md/#결재---결재-반려)|/api/sign/approver/reject/doc/dataModify|GET|결재자 반려 문서 목록|
|[결재 - 실행 성공](./menu/approver.md/#결재---실행-성공)|/api/sign/approver/exec/success/doc/dataModify|GET|결재자 성공 문서 목록|
|[결재 - 실행 실패](./menu/approver.md/#결재---실행-실패)|/api/sign/approver/exec/fail/doc/dataModify|GET|결재자 실패 문서 목록|
|[결재 - 실행 미완료](./menu/approver.md/#결재---실행-미완료)|/api/sign/approver/exec/unfinished/doc/dataModify|GET|-|
|[결재 - 전체](./menu/approver.md/#결재---전체)|/api/sign/approver/doc/dataModify|GET|-|
# 문서 상세
## 상세 내용
|API|URL|HTTP Method|View|
|---|---|---|---|
|[상세 내용](./doc-view/contents.md/#상세-내용)|/api/sign/doc/dataModify/contents|GET|문서 상세|
|[변경 전 데이터](./doc-view/contents.md/#변경-전-데이터)|/api/sign/doc/dataModify/saveBeforeData|GET|변경 전 데이터 조회 버튼|
|[변경 후 데이터](./doc-view/contents.md/#변경-후-데이터)|/api/sign/doc/dataModify/saveAfterData|GET|변경 후 데이터 조회 버튼|
## 승인/반려/회수
|API|URL|HTTP Method|View|
|---|---|---|---|
|[결재 승인](./doc-view/approval.md/#결재-승인)|/api/sign/approval/approve|POST|결재자 승인 버튼|
|[결재 반려](./doc-view/approval.md/#결재-반려)|/api/sign/approval/reject|POST|결재/실행자 반려 버튼|
|[결재 회수](./doc-view/approval.md/#결재-회수)|/api/sign/doc/withdrawal|PUT|기안자 문서 회수 버튼|
## 데이터 변경
|API|URL|HTTP Method|View|
|---|---|---|---|
|[변경 예상 개수](./doc-view/datamodify.md/#변경-예상-개수)|/api/sign/doc/dataModify/beforeDataCount|GET|실행 전 문서의 변경 건수 버튼|
|[변경 실행](./doc-view/datamodify.md/#변경-실행)|/api/sign/doc/dataModify/modify|POST|실행자 실행 버튼|
|[변경 반려](./doc-view/datamodify.md/#변경-반려)|/api/sign/doc/dataModify/reject|POST|-|
|[변경 검증](./doc-view/datamodify.md/#변경-검증)|/api/sign/doc/dataModify/afterData|GET|실행 완료 데이터 설정 - 검증 버튼|
|[커밋](./doc-view/datamodify.md/#커밋)|/api/sign/doc/dataModify/commit|POST|실행 완료 데이터 설정 - 커밋 버튼|
|[롤백](./doc-view/datamodify.md/#롤백)|/api/sign/doc/dataModify/rollback|POST|실행 완료 데이터 설정 - 롤백 버튼|
## 근거 문서
|API|URL|HTTP Method|View|
|---|---|---|---|
|[근거 문서 변경](./doc-create/groundsDoc.md/#근거-문서-변경)|/api/sign/doc/dataModify/groundsDoc|PUT|기안자 근거 문서 변경 버튼|
# 문서 작성
## 결재선/결재자
|API|URL|HTTP Method|View|
|---|---|---|---|
|[문서 작성 - 결재선](./doc-create/approvalLine.md/#문서-작성---결재선)|/api/sign/doc/write/approvalLines/docType/dataModify|GET|결재선 셀렉트 리스트|
|[문서 작성 - 결재자](./doc-create/approvalLine.md/#문서-작성---결재자)|/api/sign/doc/write/approvalLine/approvers|GET|선택한 결재선의 결재자 목록|
## 근거 문서
|API|URL|HTTP Method|View|
|---|---|---|---|
|[근거 문서 조회 URL](./doc-create/groundsDoc.md/#근거-문서-조회-URL)|/api/sign/doc/dataModify/groundsDoc|GET|근거 문서 선택 목록|
|[근거 문서 조회 DB](./doc-create/groundsDoc.md/#근거-문서-조회-DB)|/api/sign/doc/dataModify/groundsDoc/view|GET|근거 문서 선택 목록|
|[근거 문서 파일 업로드](./doc-create/groundsDoc.md/#근거-문서-파일-업로드)|/api/sign/doc/dataModify/groundsDoc/|POST|이미지(jpg) 파일 업로드|
|[근거 문서 별 결재 문서 조회](./doc-create/groundsDoc.md/#근거-문서-별-결재-문서-조회)|/api/sign/doc/dataModify/groundsDoc/doc|GET|근거 문서 선택 목록|
|[근거 문서 상태 조회 URL](./doc-create/groundsDoc.md/#근거-문서-상태-조회-URL)|/api/sign/doc/dataModify/groundsDoc/status|GET|근거 문서 선택 목록|
## 승인 요청
|API|URL|HTTP Method|View|
|---|---|---|---|
|[SQL 제약 조건](./doc-create/create.md/#SQL-제약-조건)|/api/sign/doc/dataModify/sqlVerify/info/all|GET|문서 생성 시 검증, 변경 쿼리 제약 조건 조회|
|[승인 요청](./doc-create/create.md/#승인-요청)|/api/sign/doc/dataModify/ask|POST|요청 - 승인 요청 버튼|
|[결재 문서 무효화](./doc-create/create.md/#결재-문서-무효화)|/api/sign/doc/invalid|PUT||
# 관리
## 변경 대상
|API|URL|HTTP Method|View|
|---|---|---|---|
|[변경 대상 전체 조회](./admin/target.md/#변경-대상-전체-조회)|/api/sign/doc/dataModify/target/all|GET|관리 - 변경 대상 목록<br>문서 작성 - 변경 대상 선택 목록|
|[변경 대상 추가](./admin/target.md/#변경-대상-추가)|/api/sign/doc/dataModify/target|POST|변경 대상 추가 버튼|
|[변경 대상 삭제](./admin/target.md/#변경-대상-삭제)|/api/sign/doc/dataModify/target|DELETE|변경 대상 삭제 버튼|
|[변경 대상 전체 삭제](./admin/target.md/#변경-대상-전체-삭제)|/api/sign/doc/dataModify/target/all|DELETE|-|
|[변경 대상 비밀번호 변경](./admin/target.md/#변경-대상-비밀번호-변경)|/api/sign/doc/dataModify/target/password|PUT|변경 대상 수정 - 비밀번호 수정|
|[변경 대상 비밀번호 확인](./admin/target.md/#변경-대상-비밀번호-확인)|/api/sign/doc/dataModify/target/password|GET|변경 대상 수정 - 기존 비밀번호 확인|
|[JDBC - 연결 테스트](./etc/jdbc.md/#JDBC---연결-테스트)|/api/sign/jdbc/connectionTest|GET|변경 대상 TEST CONNECTION 버튼|
## 역할
|API|URL|HTTP Method|View|
|---|---|---|---|
|[역할 전체 조회](./admin/org-user-role.md/#역할-전체-조회)|/api/sign/admin/role/all|GET|관리 - 역할 목록<br>관리 - 사용자 역할 - 역할 컬럼<br>관리 - 결재선 - 결재선 추가 - 역할 탭|
|[역할 추가](./admin/org-user-role.md/#역할-추가)|/api/sign/admin/role|POST|역할 추가 버튼|
|[역할 삭제](./admin/org-user-role.md/#역할-삭제)|/api/sign/admin/role|DELETE|역할 삭제 버튼|
## 사용자 역할
|API|URL|HTTP Method|View|
|---|---|---|---|
|[전체 사용자 조회](./admin/org-user-role.md/#전체-사용자-조회)|/api/sign/admin/user/all|GET|사용자 역할 목록|
|[특정 사용자 조회](./admin/org-user-role.md/#특정-사용자-조회)|/api/sign/admin/user|GET|-|
|[조직 사용자 전체 조회](./admin/org-user-role.md/#조직-사용자-전체-조회)|/api/sign/admin/orgUser/all|GET|-|
|[조직 역할 전체 조회](./admin/org-user-role.md/#조직-역할-전체-조회)|/api/sign/admin/orgRole/all|GET|-|
## 사용자
|API|URL|HTTP Method|View|
|---|---|---|---|
|[사용자 생성](./admin/user.md/#사용자-생성)|/api/sign/admin/user|POST||
|[사용자 삭제](./admin/user.md/#사용자-삭제)|/api/sign/admin/user|DELETE||
|[사용자 역할 변경](./admin/user.md/#사용자-역할-변경)|/api/sign/admin/user/role|PUT|역할 컬럼 셀렉트 리스트 선택|
|[사용자 이메일 변경](./admin/user.md/#사용자-이메일-변경)|/api/sign/admin/user/email|PUT||
|[사용자 비밀번호 초기화](./admin/user.md/#사용자-비밀번호-초기화)|/api/sign/admin/user/password/init|PUT||
## 결재선
|API|URL|HTTP Method|View|
|---|---|---|---|
|[결재선 전체 조회](./admin/apvline.md/#결재선-전체-조회)|/api/sign/admin/apvLine/all|GET|현재 결재선 목록|
|[결재자 전체 조회](./admin/apvline.md/#결재자-전체-조회)|/api/sign/admin/approver/all|GET|결재선 추가 - 결재자 탭 |
|[조직 전체 조회](./admin/org-user-role.md/#조직-전체-조회)|/api/sign/admin/org/all|GET|결재선 추가 - 조직/역할 탭 중 조직 목록|
|[조직 역할 조건 조회](./admin/org-user-role.md/#조직-역할-조건-조회)|/api/sign/admin/orgRole|GET|결재선 추가 - 조직/역할 탭 중 역할 목록|
|[결재선 추가](./admin/apvline.md/#결재선-추가)|/api/sign/admin/apvLine|POST|결재선 추가 버튼|
|[결재선 삭제](./admin/apvline.md/#결재선-삭제)|/api/sign/admin/apvLine|DELETE|결재선 삭제 버튼|
|[결재선 변경](./admin/apvline.md/#결재선-변경)|/api/sign/admin/apvLine|PUT|결재선명 수정 - 수정 버튼|
|[참조자 조회](./admin/apvline.md/#참조자-조회)|/api/sign/admin/apvLine/referencer|GET|-|
|[참조자 추가](./admin/apvline.md/#참조자-추가)|/api/sign/admin/apvLine/referencer|POST|-|
|[결재선 적용 대상 조회](./admin/apvline.md/#결재선-적용-대상-조회)|/api/sign/admin/apvLine/validDrafter|GET|-|
|[결재선 적용 대상 추가](./admin/apvline.md/#결재선-적용-대상-추가)|/api/sign/admin/apvLine/validDrafter|POST|-|
|[결재선 조건 조회](./admin/apvline.md/#결재선-조건-조회)|/api/sign/admin/apvLine/approver|GET|-|
## 결재자 부재
|API|URL|HTTP Method|View|
|---|---|---|---|
|[결재자 결재 유형 확인](./admin/mypage.md/#결재자-결재-유형-확인)|/api/sign/myPage/approval|GET|결재자 부재|
|[대결 가능 결재자 조회](./admin/mypage.md/#대결-가능-결재자-조회)|/api/sign/myPage/approval/reserveAgentApprover|GET|결재자 부채 처리 대결 시<br>대리 결재자 선택 목록|
|[결재 유형 설정 - 결재](./admin/mypage.md/#결재-유형-설정---결재)|/api/sign/myPage/approval/approvalType/approval|POST|결재자 부채 처리 - 끔|
|[결재 유형 설정 - 후결](./admin/mypage.md/#결재-유형-설정---후결)|/api/sign/myPage/approval/approvalType/afterApproval|POST|결재자 부채 처리 - 후결|
|[결재 유형 설정 - 대결](./admin/mypage.md/#결재-유형-설정---대결)|/api/sign/myPage/approval/approvalType/agentApproval|POST|결재자 부채 처리 - 대결|
# 비밀번호 변경
|API|URL|HTTP Method|View|
|---|---|---|---|
|[비밀번호 변경](./admin/mypage.md/#비밀번호-변경)|/api/sign/myPage/password|PUT|사용자 soha pw 변경|
|[본인 인증](./admin/mypage.md/#본인-인증)|/api/sign/myPage/identityVerification|GET|-|
# 파일 처리
|API|URL|HTTP Method|View|
|---|---|---|---|
|[파일 업로드](./etc/file.md/#파일-업로드)|/api/sign/file/upload|POST|파일 업로드|
|[파일 다운로드](./etc/file.md/#파일-다운로드)|/api/sign/file/download|GET|파일 다운로드|
# SQL
|API|URL|HTTP Method|View|
|---|---|---|---|
|[SQL 문법 검사](./sql/grammarCheck/grammarCheck.md/#SQL-문법-검사)|/api/sign/sql/grammarCheck|GET||
|[SQL 문법 검사 - DB 데이터 변경 요청서](./sql/grammarCheck/dataModify.md/#SQL-문법-검사---DB-데이터-변경-요청서)|/api/sign/sql/grammarCheck/dataModify|GET||
