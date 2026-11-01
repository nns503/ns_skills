# NS Skills

직접 만들고 사용하는 AI 에이전트 스킬 모음입니다. **설명, 사용 예시와 작업 지침은 한국어를 기본으로 작성합니다.**

신규 앱 개발, 기능 추가, 버그 수정과 리팩토링에서 필요한 단계를 선택하고 기획부터 구현·검증·요청된 배포까지 연결합니다. 개별 단계만 따로 사용할 수도 있습니다.

> **v0.1.0 초안:** 8개 스킬과 마켓플레이스 설정을 작성했습니다. 스킬 형식과 로컬 파일 연결을 확인했으며, 실제 클라이언트 설치·앱 개발·배포를 통한 동작 검증은 아직 수행하지 않았습니다.

## 스킬 목록

| 스킬 | 하는 일 | 요청 예시 |
| --- | --- | --- |
| [app-orchestrator](skills/app-orchestrator/SKILL.md) | 단계 선택·연결, 진행과 재개 관리 | 이 아이디어로 앱을 만들고 실행 검증까지 진행해줘. |
| [project-conventions](skills/project-conventions/SKILL.md) | 기존 규칙과 작업에 적용할 기준 확인 | 이 프로젝트의 코드·커밋·PR 규칙을 정리해줘. |
| [kickoff](skills/kickoff/SKILL.md) | 목표·범위·완료 조건 구체화 | 이 아이디어를 MVP 요구사항으로 구체화해줘. |
| [experience-design](skills/experience-design/SKILL.md) | 사용자 흐름·화면·상태 설계 | 이 기능의 사용자 시나리오와 화면 상태를 설계해줘. |
| [technical-design](skills/technical-design/SKILL.md) | 스택·API·DB·코드 구조와 작업 계획 | 기존 구조에 맞는 API와 데이터 설계를 해줘. |
| [implement](skills/implement/SKILL.md) | 계획에 따른 변경과 작업 단위 검증 | 이번 기능을 구현하고 관련 테스트를 확인해줘. |
| [verify](skills/verify/SKILL.md) | 요구사항·회귀 검증과 코드 리뷰 | 이번 변경이 완료 조건을 만족하는지 리뷰해줘. |
| [release](skills/release/SKILL.md) | 대상 환경과 플랫폼에 맞는 릴리스 | 개발 환경에 배포하고 핵심 흐름을 확인해줘. |

## 사용하는 방식

전체 개발을 맡길 때는 `app-orchestrator`, 특정 작업만 할 때는 해당 단계 스킬을 선택합니다. 설치 환경에서 표시되는 실제 식별자를 사용하세요. 아래 `$...` 표기는 스킬을 지정하는 요청 예시이며 셸 명령이 아닙니다.

```text
$app-orchestrator로 개인 지출 관리 앱의 최소 버전을 만들고 로컬 실행 검증까지 진행해줘.
$app-orchestrator로 기존 앱에 다크모드를 추가해줘. 서버·DB 변경과 배포는 범위 밖이야.
$verify로 이번 변경을 리뷰하고 실행하지 못한 검증도 알려줘.
$release로 모바일 앱의 내부 테스트용 빌드를 준비해줘. 스토어 제출은 하지 마.
```

오케스트레이터는 기존 프로젝트와 규칙을 확인한 다음 필요한 단계만 선택합니다. 스킬 호출 기능이 없는 환경에서는 해당 `SKILL.md`를 읽고 수행하도록 설계했습니다. 플러그인을 설치했다고 별도 실행 엔진이나 외부 서비스 연결이 생기는 것은 아닙니다.

```text
프로젝트·규칙 확인
    → 기획 → UX → 기술 설계 → 구현 → 검증 → 요청된 릴리스
                    ↑                 │
                    └──── 수정 ───────┘
```

작은 수정은 짧은 계획으로 처리하고, 화면이나 데이터 변경이 없으면 해당 설계를 생략합니다. 생략 이유와 완료 근거를 남겨 중단한 작업을 이어갈 수 있게 합니다.

## 설치와 구성

`ns-skills` 플러그인 하나에 8개 스킬을 묶었습니다. Claude Code·Codex의 마켓플레이스 설정을 제공하며, 실제 설치 지원과 호출 이름은 사용하는 클라이언트에서 확인해야 합니다. **로컬 초안이 GitHub에 반영되기 전에는 원격 저장소 설치에 이번 변경이 포함되지 않습니다.**

- [마켓플레이스 설치·구성 안내](docs/marketplace.md)
- [전체 설계와 초기 검증 시나리오](docs/workflow.md)
- [레퍼런스 28개 검토와 반영 기록](docs/references.md)
- [스킬 작성 안내](docs/creating-skills.md)

## 저장소 구조

```text
ns_skills/
├── README.md
├── AGENTS.md
├── plugin.json                      # 루트 skills/를 패키징
├── skills/                          # 8개 스킬의 원본과 UI 메타데이터
│   ├── app-orchestrator/            # 진행 규약·변경 기록 양식 포함
│   ├── project-conventions/         # 규칙이 없을 때 사용할 기본 제안 포함
│   ├── kickoff/
│   ├── experience-design/
│   ├── technical-design/
│   ├── implement/
│   ├── verify/
│   └── release/                     # 웹·서버, 모바일, 데스크톱 참고 절차
├── template/SKILL.md                 # 새 스킬 작성용, 배포 목록에서 제외
├── docs/
│   ├── workflow.md
│   ├── references.md                 # 참고 파일·공식 자료와 반영 내역
│   ├── creating-skills.md
│   └── marketplace.md
├── .claude-plugin/marketplace.json
└── .agents/plugins/marketplace.json
```

프로젝트별 결정과 진행 기록은 **대상 앱 저장소**에 남깁니다. 이 저장소와 설치된 스킬 폴더에는 재사용할 지침과 양식만 둡니다. 기존 Spec Kit·OpenSpec 문서가 있으면 그 구조를 재사용합니다.

## 언어와 의존성

- 폴더명·식별자는 영문 소문자·숫자·하이픈, 설명·지침·사용 예시는 한국어로 작성합니다.
- 결과물의 언어는 사용자의 명시적 요청을 따릅니다.
- 특정 스택이나 외부 플러그인을 필수로 지정하지 않습니다. 실제 작업에 필요한 파일·실행·검증 도구는 대상 환경에서 제공되어야 합니다.
- 기획·설계는 문서 접근만으로 진행할 수 있지만 구현과 배포는 해당 환경·서비스의 도구와 권한이 필요합니다. 확인하지 않은 호환성을 보장하지 않습니다.

## 출처와 라이선스

저장소 구성은 [anthropics/skills](https://github.com/anthropics/skills), 워크플로 아이디어는 [speckit-agent-skills](https://github.com/dceoy/speckit-agent-skills), [OpenSpec](https://github.com/Fission-AI/OpenSpec), [Ponytail](https://github.com/DietrichGebert/ponytail)을 참고했습니다. 이번 초안의 지침은 이 저장소의 요구에 맞춰 새로 작성했으며, 참고 프로젝트의 코드·스킬 본문을 복사하지 않았습니다.

외부 자료를 추후 포함하면 원본 URL·라이선스·변경 내용을 기록합니다. 저장소 전체의 배포 라이선스는 아직 정하지 않았습니다.

공유받은 네 저장소의 실제 스킬·템플릿 19개와 공식 문서 9개를 추가 검토해 단계별 판단 기준을 보강했습니다. [레퍼런스 기록](docs/references.md)에서 고정된 원본 파일과 반영 위치를 확인할 수 있습니다. 각 스킬은 관련 상황에 필요한 참고 문서만 읽도록 구성했습니다.
