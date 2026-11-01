# 마켓플레이스 구성 안내

## 현재 상태

실제 스킬이 아직 없으므로 두 마켓플레이스의 `plugins` 목록은 비워 두었습니다. 현재 파일은 목록을 작성하기 위한 초기 구성입니다. 클라이언트에서 등록·설치하는 동작은 아직 확인하지 않았습니다.

첫 스킬을 추가한 뒤 플러그인 항목을 등록하고, 해당 클라이언트에서 설치와 실행을 확인합니다. `template/`는 배포하지 않습니다.

## 원본은 한 곳에서 관리

스킬은 모두 루트 `skills/`에 둡니다. Claude Code와 Codex는 마켓플레이스 및 플러그인 설정이 다르므로 각 환경의 설정 파일을 따로 관리합니다. 지원 환경을 늘릴 때 스킬 내용을 복사하기보다 패키징 설정을 추가합니다.

## Claude Code

목록 파일은 `.claude-plugin/marketplace.json`입니다. [anthropics/skills의 목록](https://github.com/anthropics/skills/blob/main/.claude-plugin/marketplace.json)처럼 루트를 소스로 지정하고 묶음에 포함할 스킬 경로를 나열할 수 있습니다.

예를 들어 실제 `skills/meeting-notes/`를 만든 뒤에는 `plugins`에 다음 항목을 넣는 방식입니다. 아래 항목은 설명용이며 현재 목록에는 포함하지 않았습니다.

```json
{
  "name": "ns-workflows",
  "description": "한국어 회의록과 업무 정리 스킬",
  "source": "./",
  "strict": false,
  "skills": ["./skills/meeting-notes"]
}
```

GitHub에 반영하고 플러그인 항목을 완성한 다음, Claude Code에서 등록·설치를 확인합니다.

```text
/plugin marketplace add nns503/ns_skills
/plugin install ns-workflows@ns-skills
```

## Codex

목록 파일은 `.agents/plugins/marketplace.json`입니다. 루트 `skills/`를 유지하려면 저장소 루트에 `plugin.json`을 추가해 하나의 플러그인으로 패키징하는 구성이 단순합니다. 처음에는 이 방식으로 시작하고, 독립적으로 설치할 묶음이 필요해지면 패키징 구성을 나눕니다.

첫 스킬을 추가할 때 사용할 루트 `plugin.json` 예시입니다.

```json
{
  "$schema": "https://agent-plugins.org/schemas/1.0.0/plugin.schema.json",
  "name": "ns-skills",
  "version": "0.1.0",
  "description": "한국어로 설명하고 관리하는 개인 에이전트 스킬 모음"
}
```

이 형식은 플러그인 루트의 `skills/`에서 스킬을 찾습니다. 그다음 Codex 마켓플레이스의 `plugins`에 다음 항목을 추가합니다.

```json
{
  "name": "ns-skills",
  "source": {
    "source": "local",
    "path": "./"
  },
  "policy": {
    "installation": "AVAILABLE",
    "authentication": "ON_INSTALL"
  },
  "category": "Productivity"
}
```

GitHub 반영 후 CLI에서 마켓플레이스 소스를 추가할 수 있습니다. 설치·표시 지원은 사용하는 클라이언트에서 확인합니다.

```bash
codex plugin marketplace add nns503/ns_skills
```

참고: [OpenAI 플러그인 패키징 문서](https://developers.openai.com/plugins/build/plugins)

## 공개 디렉터리와의 차이

GitHub 저장소를 마켓플레이스 소스로 사용하는 것과 공식 공개 디렉터리에 입점하는 것은 별개입니다. 공개 디렉터리 배포는 각 서비스의 패키징과 심사 요건을 별도로 확인합니다.

참고: [OpenAI 플러그인 제출 문서](https://developers.openai.com/plugins/deploy/submission)
