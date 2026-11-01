# 레퍼런스 검토와 반영 기록

검토일: 2026-11-01. 처음 공유받은 네 저장소와 후속 선정한 여섯 저장소에서 실제 스킬·템플릿·문서 38개를 읽고, 형식·협업·UX·검증·배포에 관한 공식 문서 9개를 확인했습니다. 핵심 절차와 판단 기준을 검토한 기록이며 전체 저장소의 코드 감사나 해당 도구의 실행 검증은 아닙니다.

## 참고 방식

- 원문 스킬·코드·실행 도구를 저장소에 복사하거나 번역 배포하지 않고, 요구에 맞는 자체 지침을 작성했습니다.
- 출처 링크는 판단의 근거이며 추가 설치 목록이 아닙니다. 프로젝트의 기존 규칙·사용자 지시와 실제 환경을 우선합니다.
- 각 SKILL.md에서 관련 상황에 필요한 로컬 참고 문서만 읽게 했습니다. 모든 작업에서 아래 자료 전체를 내려받거나 열지 않습니다.
- 현재 API·배포 조건·도구 버전이 중요한 실행에서는 해당 버전의 공식 자료를 다시 확인합니다.
- 참고 저장소의 필수 문서 수·고정 질문 수·자동 훅·특정 말투·항상 승인을 요구하는 절차를 그대로 채택하지 않았습니다.

## 공유받은 저장소의 실제 파일

이 링크는 검토 시점 커밋에 고정했습니다. 각 항목의 “반영”은 원문 복제가 아니라 NS Skills에서 새로 작성한 판단 기준을 뜻합니다.

| 출처·파일 | 반영한 내용 | 적용 위치 |
| --- | --- | --- |
| [dceoy/speckit-agent-skills · skills/speckit-baseline/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-baseline/SKILL.md) | 현재 동작·가정·사용자 의도 분리 | app-orchestrator |
| [dceoy/speckit-agent-skills · skills/speckit-specify/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-specify/SKILL.md) | 사용자 문제와 검증 가능한 완료 조건 | kickoff |
| [dceoy/speckit-agent-skills · skills/speckit-clarify/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-clarify/SKILL.md) | 실제 결정에 영향을 주는 모호성 우선 확인 | kickoff |
| [dceoy/speckit-agent-skills · skills/speckit-plan/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-plan/SKILL.md) | 미확정 기술 조사·선택 이유·대안 | technical-design |
| [dceoy/speckit-agent-skills · skills/speckit-tasks/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-tasks/SKILL.md) | 사용자 흐름·작업 의존성·완료 확인 | technical-design |
| [dceoy/speckit-agent-skills · skills/speckit-analyze/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-analyze/SKILL.md) | 요구·설계·작업의 누락과 충돌 | technical-design, verify |
| [dceoy/speckit-agent-skills · skills/speckit-converge/SKILL.md](https://github.com/dceoy/speckit-agent-skills/blob/4bddf979ec6c9c682ddceee56d41646045297072/skills/speckit-converge/SKILL.md) | 의도와 실제 코드의 차이·남은 작업 | app-orchestrator |
| [Fission-AI/OpenSpec · schemas/spec-driven/schema.yaml](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/schema.yaml) | 변경 종류·산출물 의존성·작업별 검증 | kickoff, technical-design, verify |
| [Fission-AI/OpenSpec · schemas/spec-driven/templates/proposal.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/templates/proposal.md) | 변경 이유·범위·영향을 간결하게 기록 | kickoff, 변경 기록 양식 |
| [Fission-AI/OpenSpec · schemas/spec-driven/templates/spec.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/templates/spec.md) | 조건·행동·기대 결과를 연결 | kickoff, verify |
| [Fission-AI/OpenSpec · schemas/spec-driven/templates/design.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/templates/design.md) | 목표·제외 범위·결정·제약 | technical-design |
| [Fission-AI/OpenSpec · schemas/spec-driven/templates/tasks.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/schemas/spec-driven/templates/tasks.md) | 작은 단위의 추적 가능한 작업 | technical-design, implement |
| [Fission-AI/OpenSpec · skills/openspec-apply-change/SKILL.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/skills/openspec-apply-change/SKILL.md) | 현재 컨텍스트·작업과 실제 수행 결과 연결 | implement |
| [Fission-AI/OpenSpec · skills/openspec-verify-change/SKILL.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/skills/openspec-verify-change/SKILL.md) | 완결성·동작·일관성과 삭제·이름 변경 검증 | verify |
| [Fission-AI/OpenSpec · skills/openspec-update-change/SKILL.md](https://github.com/Fission-AI/OpenSpec/blob/27c0515724decc633818c735ee596481eec78a8b/skills/openspec-update-change/SKILL.md) | 변경된 결정의 양방향 영향 재확인 | app-orchestrator |
| [DietrichGebert/ponytail · skills/ponytail/SKILL.md](https://github.com/DietrichGebert/ponytail/blob/96608e078b2d5ea607c5c3b8b5a54d1c1fba6846/skills/ponytail/SKILL.md) | 기존 기능 재사용·최소한의 완결된 변경 | project-conventions, implement |
| [DietrichGebert/ponytail · skills/ponytail-review/SKILL.md](https://github.com/DietrichGebert/ponytail/blob/96608e078b2d5ea607c5c3b8b5a54d1c1fba6846/skills/ponytail-review/SKILL.md) | 연결된 코드·실제 실패 조건·사용 규모 검토 | verify |
| [anthropics/skills · skills/webapp-testing/SKILL.md](https://github.com/anthropics/skills/blob/ca45fc496a3436251f191354091d557da31c15b5/skills/webapp-testing/SKILL.md) | 실제 렌더링 상태 확인 후 조작 | experience-design, verify |
| [anthropics/skills · skills/frontend-design/SKILL.md](https://github.com/anthropics/skills/blob/ca45fc496a3436251f191354091d557da31c15b5/skills/frontend-design/SKILL.md) | 사용자·실제 콘텐츠에 맞는 시각 방향 | experience-design |

### 검토한 저장소 버전

- `dceoy/speckit-agent-skills`: `4bddf979ec6c9c682ddceee56d41646045297072`
- `Fission-AI/OpenSpec`: `27c0515724decc633818c735ee596481eec78a8b`
- `DietrichGebert/ponytail`: `96608e078b2d5ea607c5c3b8b5a54d1c1fba6846`
- `anthropics/skills`: `ca45fc496a3436251f191354091d557da31c15b5`

원본 라이선스 표기는 speckit-agent-skills의 AGPL-3.0, OpenSpec·Ponytail의 MIT 및 Anthropic 개별 스킬의 LICENSE.txt를 참고합니다. 원문 파일을 포함하는 변경을 한다면 해당 판본의 실제 조건을 별도로 확인하고 출처·변경 내역과 함께 기록합니다. 이 목록은 NS Skills의 배포 라이선스를 결정하지 않습니다.

## 추가 선정한 여섯 저장소

후속 검토에서는 아래 실제 스킬·문서 19개를 추가로 읽었습니다. 반영은 작업에 맞게 재구성한 자체 지침이며, 외부 스킬을 설치하거나 실행했다는 의미가 아닙니다.

| 출처·파일 | 반영한 내용 | 적용 위치 |
| --- | --- | --- |
| [addyosmani/agent-skills · skills/using-agent-skills/SKILL.md](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/using-agent-skills/SKILL.md) | 단계와 전문 분야를 함께 보는 선택 기준 | app-orchestrator |
| [addyosmani/agent-skills · skills/api-and-interface-design/SKILL.md](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/api-and-interface-design/SKILL.md) | 외부 계약·오류·신뢰 경계·재시도 결과 미확정 | technical-design |
| [addyosmani/agent-skills · skills/deprecation-and-migration/SKILL.md](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/deprecation-and-migration/SKILL.md) | 실제 호출자·기존 데이터의 공존·단계 전환 | technical-design, release |
| [addyosmani/agent-skills · skills/ci-cd-and-automation/SKILL.md](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/ci-cd-and-automation/SKILL.md) | 현재 버전과 실제 CI 검사 결과 연결 | release |
| [addyosmani/agent-skills · skills/shipping-and-launch/SKILL.md](https://github.com/addyosmani/agent-skills/blob/8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e/skills/shipping-and-launch/SKILL.md) | 실제 동작·관찰 근거·복구 판단 | release |
| [obra/superpowers · skills/systematic-debugging/SKILL.md](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/systematic-debugging/SKILL.md) | 재현·원인·정상 사례 비교·가설·수정·회귀 확인 | implement |
| [obra/superpowers · skills/verification-before-completion/SKILL.md](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/verification-before-completion/SKILL.md) | 완료 주장에 맞는 검사 범위와 실제 결과 | verify |
| [mattpocock/skills · skills/productivity/grilling/SKILL.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/productivity/grilling/SKILL.md) | 질문의 선행 결정과 사실 조사·사용자 선택의 구분 | kickoff |
| [mattpocock/skills · skills/engineering/domain-modeling/SKILL.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/domain-modeling/SKILL.md) | 사용자·기획·코드 간 개념 경계 대조 | project-conventions, kickoff |
| [mattpocock/skills · skills/engineering/domain-modeling/GLOSSARY-FORMAT.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/domain-modeling/GLOSSARY-FORMAT.md) | 도메인 용어·의미·혼동할 표현·현재 코드 매핑 | project-conventions |
| [mattpocock/skills · skills/engineering/domain-modeling/ADR-FORMAT.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/domain-modeling/ADR-FORMAT.md) | 중요한 결정만 짧게 기록 | project-conventions |
| [bmad-code-org/BMAD-METHOD · docs/plan/choose-a-planning-path.md](https://github.com/bmad-code-org/BMAD-METHOD/blob/bd70c643a7ec85d1ec2e88076b3fbdd8e4517f41/docs/plan/choose-a-planning-path.md) | 의도·위험·공유 범위에 맞춘 실행 깊이 | app-orchestrator |
| [bmad-code-org/BMAD-METHOD · docs/plan/design-ux-and-architecture.md](https://github.com/bmad-code-org/BMAD-METHOD/blob/bd70c643a7ec85d1ec2e88076b3fbdd8e4517f41/docs/plan/design-ux-and-architecture.md) | 분리된 작업에 공유할 계약·UX·기술 결정 | app-orchestrator, experience-design, technical-design |
| [vercel-labs/agent-skills · skills/react-best-practices/SKILL.md](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/react-best-practices/SKILL.md) | React·Next.js일 때 관련 데이터 흐름·경계·성능 지침 선택 | technical-design |
| [vercel-labs/agent-skills · skills/web-design-guidelines/SKILL.md](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/web-design-guidelines/SKILL.md) | 웹 UI에 관련된 전문 검토 지침 선택 | experience-design, technical-design |
| [vercel-labs/agent-skills · skills/react-native-skills/SKILL.md](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/react-native-skills/SKILL.md) | React Native·Expo일 때 관련 목록·상태·플랫폼 지침 선택 | technical-design |
| [supabase/agent-skills · skills/supabase-postgres-best-practices/SKILL.md](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/SKILL.md) | PostgreSQL일 때 데이터·조회·연결·잠금 지침 선택 | technical-design |
| [supabase/agent-skills · skills/supabase-postgres-best-practices/references/security-rls-basics.md](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/references/security-rls-basics.md) | RLS를 쓰는 프로젝트의 실제 실행 역할과 격리 검증 | technical-design |
| [supabase/agent-skills · skills/supabase-postgres-best-practices/references/schema-constraints.md](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/references/schema-constraints.md) | 실제 DB 판본·제약·데이터·재실행 조건 확인 | technical-design |

### 추가 검토 판본

- `addyosmani/agent-skills`: `8bfcc1f9916f2eea55494d8c1fa7f4bde867dd9e`
- `obra/superpowers`: `2ce8aa15d05bd57213e6f746f953aafb7ded7a8b`
- `mattpocock/skills`: `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`
- `bmad-code-org/BMAD-METHOD`: `bd70c643a7ec85d1ec2e88076b3fbdd8e4517f41`
- `vercel-labs/agent-skills`: `1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62`
- `supabase/agent-skills`: `c9be0e931b7930f7d02126d04774d904c381e7d7`

Addy Osmani·Superpowers·Matt Pocock·Supabase는 저장소의 MIT 표기를 확인했습니다. BMAD의 실제 LICENSE는 MIT와 별도 상표 고지를 포함합니다. Vercel의 React·React Native 스킬에는 MIT가 표기되어 있으며, 다른 파일의 조건까지 동일하다고 일반화하지 않습니다. 이번에는 원문 본문·코드·실행 도구를 포함하지 않고 판본 링크와 자체 판단 기준을 기록했습니다.

### 선별 적용

- 스킬 선택은 개발 단계와 실제 전문 분야를 함께 봅니다. 외부 스킬의 가용성·식별자·적용 범위를 확인하고 없는 설치·실행을 보고하지 않습니다.
- 디버깅은 재현·실패 위치·가설·최소 실험·수정·회귀 확인을 연결합니다. 고정 시도 횟수나 모든 변경의 TDD 의무는 추가하지 않습니다.
- 용어는 사용자·기획·API·DB·코드의 의미를 맞추되 공개 이름을 자동 변경하지 않습니다. 중요한 공유 결정만 필요한 위치에 기록합니다.
- Vercel·Supabase 지침은 실제 웹·React·Next.js·React Native·Expo·PostgreSQL·Supabase 구성과 이번 변경이 확인될 때만 선택합니다. 다른 기술에도 적용할 특정 의존성·SQL·최적화 방식을 정하지 않습니다.
- CI·배포는 실제 검사 대상·결과와 서비스 동작을 확인합니다. 원문의 고정 임계값·자동 통보·자동 병합·모든 배포의 기능 플래그 의무는 채택하지 않습니다.
- 판본에 따라 바뀌는 세부 SQL·SDK·보안·배포 조건은 실제 작업 시 해당 버전의 공식 자료와 동작으로 확인합니다.

## 추가 공식 문서

| 문서 | 반영한 내용 | 적용 위치 |
| --- | --- | --- |
| [Agent Skills 형식](https://agentskills.io/specification) | 필수 메타데이터·필요한 시점의 참고 자료 로딩 | 스킬 구조·작성 안내 |
| [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) | scope·파괴적 변경 표시·형식 채택과 자동화 구분 | project-conventions |
| [Google 코드 리뷰 기준](https://google.github.io/eng-practices/review/reviewer/looking-for.html) | 설계·기능·복잡성·유효한 테스트·명명·일관성 | project-conventions, verify |
| [W3C 상태 메시지 해설](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html) | 포커스 이동 없이 표시되는 상태의 접근성 | experience-design |
| [OpenAPI 3.1.1](https://spec.openapis.org/oas/v3.1.1.html) | HTTP API 입력·응답·권한·폐기 정보 확인 기준 | technical-design |
| [Playwright 자동 대기](https://playwright.dev/docs/actionability) | 관찰한 요소의 동작 가능 조건·재시도 단언 | experience-design, verify |
| [GitHub Actions 배포 제어](https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/control-deployments) | 환경·보호 규칙·동시 실행과 실제 배포 결과 구분 | release: 웹·서버 |
| [Android 릴리스 준비](https://developer.android.com/studio/publish/preparing) | 릴리스 구성·서명된 빌드·실제 대상 시험 | release: 모바일 |
| [Apple TestFlight 개요](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/) | 업로드·베타 테스트·필요한 검토·정식 출시 구분 | release: 모바일·해당 macOS 배포 |

판본이 있는 표준은 참고한 판본을 표시했으며 프로젝트의 채택 버전을 강제하지 않습니다. W3C Understanding 문서는 해설이며 전체 접근성 적합성 확인을 대신하지 않습니다. 플랫폼 자료의 조건·지원 범위는 배포 시점에 재확인합니다.

## 초기 초안에서 보강한 점

1. 기존 코드의 관찰 사실과 의도한 요구사항을 구분하고, 변경 규모에 맞는 경로를 선택합니다.
2. 요구 → 작업·코드 → 검증 근거를 연결하고, 구현과 관련 테스트·문서를 같은 작업에서 다룹니다.
3. 추가·수정·삭제·이름 변경의 검증 방향을 구분합니다.
4. 호출자·export·fixture·설정·직렬화까지 필요한 영향 범위를 확인합니다.
5. 사용자·콘텐츠와 기존 디자인을 근거로 UI를 설계하고 실제 상태에서 조작·검증합니다.
6. 리뷰는 구체적인 실패 조건과 영향으로 설명하고 취향·추측과 결함을 구분합니다.
7. CI 시작·성공·배포 완료·실제 동작과 앱 업로드·검토·출시 상태를 구분합니다.

## 이번 추가 보강

- 단계·작업 분야·실제 기술 구성을 함께 보는 스킬 선택 기준
- 원인 조사·가설·최소 실험·수정·회귀 확인의 디버깅 흐름
- 도메인 용어·공유 결정과 기존 코드의 매핑
- 외부 API의 재시도·결과 미확정, 기존 사용자·데이터의 전환 기준
- 해당 스택에서만 적용할 Vercel·Supabase 전문 지침
- 완료 주장에 필요한 실제 검사 범위와 배포 후 동작 근거

## 남은 검증

형식·파일 연결과 지침 정합성은 확인하지만, 실제 스킬 선택·클라이언트 설치·앱 구현·배포 동작은 별도 실행 검증이 필요합니다. [검증 시나리오](workflow.md)의 미실행 상태를 그대로 유지합니다.
