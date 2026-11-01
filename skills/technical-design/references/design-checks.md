# 기술 결정·계약·작업 계획

기술 선택이 미정이거나 API·데이터·여러 모듈에 걸친 변경을 계획할 때 관련 부분만 읽는다.

## 결정과 조사

미확정 기술 사항을 실제 결정 질문으로 바꾼다. 선택한 방법·이유·검토한 대안·남는 제약을 필요한 만큼 기록한다. 정해진 답을 꾸미기 위해 대안 표를 늘리지 않는다.

공식 문서·대상 버전의 API·현재 프로젝트 코드·작은 실행 확인 순으로 필요한 근거를 모은다. 예제 프로젝트의 설치 목록을 그대로 가져오지 않는다. 기존 결정과 충돌하면 바뀌어야 하는 이유를 밝힌다.

## API와 데이터 계약

HTTP API가 있다면 관련 요청의 경로·방법·입력 위치·필수 여부·형식, 성공·오류 응답과 권한을 확인한다. 기존 OpenAPI 등 기계 판독 명세가 있으면 이를 갱신하며 별도 문서와 어긋나지 않게 한다. 단순 내부 함수나 로컬 앱에 HTTP API·OpenAPI 문서를 새로 강제하지 않는다.

데이터 변경은 현재 값·제약·관련 읽기·쓰기·호출자와 영향 범위를 확인한다. 구·신 코드가 공존하는지, 기존 데이터를 어떻게 읽고 전환하는지, 실패·재실행·복구가 가능한지 필요한 수준으로 설계한다. 구체적인 DDL·잠금·트랜잭션 성질은 선택한 DB와 버전의 공식 문서에서 확인한다.

## 구현 작업으로 나누기

- 하나의 사용자 흐름을 끝까지 사용할 수 있는 순서로 나눈다. 필요한 기반 작업은 먼저 배치한다.
- 작업마다 관련 요구·변경 영역·선행 작업·완료 확인 방법을 연결한다.
- 해당 변경에 필요한 테스트·문서는 그 작업과 함께 다룬다. 마지막에는 여러 작업을 잇는 통합 확인을 남긴다.
- 같은 파일·공유 상태·미확정 계약에 의존하면 독립 작업으로 표시하지 않는다.
- 요구에 연결되지 않은 작업과 작업이 없는 필수 요구를 확인한다. 사업 성과 지표를 코드 작업으로 억지 변환하지 않는다.

작은 예시: `알림 설정 저장 → 설정 API와 화면 갱신 → 저장·재조회 확인`. 단순 변경에는 이 한 줄이 별도 세 문서를 대신할 수 있다.

## 설계 근거

- [Spec Kit plan](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-plan/SKILL.md): 기술 미확정 사항의 조사와 결정 이유
- [Spec Kit tasks](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-tasks/SKILL.md): 사용자 흐름·의존성과 작업의 연결
- [Spec Kit analyze](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-analyze/SKILL.md): 요구·계획·작업의 누락·불일치 확인
- [OpenSpec 기본 스키마](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/schema.yaml): 작업별 검증과 관련 문서를 같은 묶음에서 처리하는 구성
- [OpenAPI 3.1.1 Operation Object](https://spec.openapis.org/oas/v3.1.1.html#operation-object): HTTP API 계약 검토 예시

OpenAPI 3.1.1은 참고한 판본이며 프로젝트에 사용할 버전을 고정하는 요구가 아니다. 별도 조사 에이전트나 문서 묶음을 필수로 만들지 않는다.
