# 작업 성격에 따른 스킬 연결

개발 단계와 작업의 전문 분야를 함께 보고 필요한 지침을 고른다. 이 표의 외부 스킬은 후보이며 설치·호출 완료를 뜻하지 않는다.

## 기본 연결

| 관찰한 필요 | 담당 단계 | 추가로 확인할 전문 분야 |
| --- | --- | --- |
| 사용자가 원하는 결과가 불분명함 | kickoff | 기획 질문·도메인 용어 |
| 화면·조작·상태가 달라짐 | experience-design → implement → verify | 웹 UI·해당 앱 플랫폼 |
| 공개 API·타입·데이터 계약이 달라짐 | technical-design → implement → verify | 인터페이스·호환성·마이그레이션 |
| 버그·테스트·빌드가 실패함 | implement의 원인 조사 → verify | 체계적인 디버깅 |
| 성능 문제가 실제로 관찰됨 | 관련 설계·구현·검증 | 해당 스택·DB의 측정과 병목 확인 |
| 커밋·PR을 수행함 | project-conventions → 해당 Git 작업 | 기존 협업·병합 규칙 |
| CI 설정·배포 절차가 바뀜 | technical-design → implement → verify → 요청된 release | CI/CD·환경별 배포 |

명확한 작은 수정은 변경 위치·유지할 동작·확인 방법을 짧게 정하고 진행한다. 여러 기능이 공유하는 계약·상태·소유권이 불명확하면 관련 설계부터 한다. 단계 수·세션 수·파일 수를 고정 임계값으로 사용하지 않는다.

## 외부 전문 스킬 선택

1. 프로젝트의 실제 언어·프레임워크·DB·버전을 설정·lockfile·관련 코드로 확인한다.
2. 현재 환경에서 사용 가능한 스킬의 설명·실제 식별자·도구 의존성을 확인한다. 저장소 이름과 호출 이름이 같다고 가정하지 않는다.
3. 이번 작업과 겹치는 범위만 선택하고, 하나의 결과물에 책임지는 기본 단계와 전문 지침의 역할을 구분한다.
4. 기존 사용자 결정·프로젝트 규칙·실행 범위와 충돌하는 외부 지침은 그대로 채택하지 않는다. 선택한 적용 범위와 이유를 전달한다.
5. 설치된 스킬이 없으면 실제로 접근 가능한 공식 자료와 로컬 지침으로 수행할 수 있는지 판단한다. 필요한 실행 도구·환경이 없으면 해당 단계의 차단 조건을 기록한다.

React·Next.js, React Native·Expo, PostgreSQL·Supabase 같은 기술 지침은 해당 구성이 확인된 경우에만 연결한다. 참고 자료에 등장한다는 이유로 그 기술을 채택하거나 외부 스킬을 자동 설치하지 않는다.

## 전달할 내용

담당 단계, 선택한 전문 지침·판본, 적용할 부분, 필요한 도구, 완료 확인 방법을 짧게 남긴다. 기존 기획·용어·기술 결정은 관련 경로로 연결하고 관계없는 대화 전체를 반복 전달하지 않는다.

## 설계 근거

- [Addy Osmani: using-agent-skills](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/using-agent-skills/SKILL.md): 단계·전문 분야별 연결 참고
- [BMAD: planning path](https://github.com/bmad-code-org/BMAD-METHOD/blob/bd70c643a7ec85d1ec2e88076b3fbdd8e4517f41/docs/plan/choose-a-planning-path.md): 작업 의도·위험에 맞는 설계 깊이 참고
- [BMAD: UX and architecture](https://github.com/bmad-code-org/BMAD-METHOD/blob/bd70c643a7ec85d1ec2e88076b3fbdd8e4517f41/docs/plan/design-ux-and-architecture.md): 여러 작업이 공유해야 하는 결정의 전달 참고

각 프레임워크의 자동 실행·역할 이름·승인 절차를 설치하거나 강제하는 문서가 아니다.
