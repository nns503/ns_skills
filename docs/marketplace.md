# 마켓플레이스 설치·구성 안내

## 현재 패키지

`ns-skills` 플러그인 하나에 `skills/`의 8개 스킬을 포함합니다. `template/`와 프로젝트별 작업 기록은 스킬 목록에 포함하지 않습니다.

- 루트 `plugin.json`: 이름·버전·설명과 패키지 식별 정보
- `.agents/plugins/marketplace.json`: Codex용 플러그인 소스 목록
- `.claude-plugin/marketplace.json`: Claude Code용 목록과 포함할 스킬 경로

스킬 원본은 중복 복사하지 않습니다. 새 스킬을 추가하면 Claude Code 목록의 경로도 갱신합니다. Codex의 루트 플러그인은 `skills/`에서 스킬을 찾습니다.

현재 초안은 로컬 파일의 형식·연결을 확인한 단계이며, 실제 클라이언트 설치와 실행은 미검증입니다. 아래 설치 명령은 지원되는 환경에서 사용하는 안내이며 실행 완료 기록이 아닙니다.

## 로컬 초안 확인

지원되는 Codex CLI에서는 저장소 루트에서 로컬 마켓플레이스를 등록할 수 있습니다.

```bash
codex plugin marketplace add .
codex plugin marketplace list
```

사용하는 클라이언트의 플러그인 목록에서 `NS Skills · 한국어 스킬 모음` 소스와 `ns-skills`를 확인하고 설치합니다. 클라이언트별 표시·설치 지원은 해당 버전의 안내를 확인합니다. 설치된 복사본이 사용될 수 있으므로 수정 후 소스 갱신·재설치·재시작 필요 여부를 확인합니다.

## GitHub 소스 사용

로컬 변경을 GitHub에 반영한 뒤 아래 명령으로 원격 소스를 등록할 수 있습니다. 푸시 전에는 원격 설치에 새 스킬이 포함되지 않습니다.

Codex CLI:

```bash
codex plugin marketplace add nns503/ns_skills
codex plugin marketplace list
```

Claude Code:

```text
/plugin marketplace add nns503/ns_skills
/plugin install ns-skills@ns-skills
```

설치 후 실제 스킬 식별자를 확인합니다. 플러그인 이름이 접두사로 붙는 등 표시 방식이 다를 수 있으므로 이름만으로 호출 성공을 가정하지 않습니다.

## 설치 검증

1. 새 대화에서 8개 스킬이 표시되고 작성 템플릿은 표시되지 않는지 확인합니다.
2. `kickoff`를 단독 사용해 한국어 기획 결과와 요청 범위를 확인합니다.
3. `app-orchestrator`로 작은 변경을 요청해 내부 단계와 참고 자료를 찾는지 확인합니다.
4. 작업 기록이 대상 앱에 남고 설치 폴더에는 쓰이지 않는지 확인합니다.
5. 외부 플러그인·배포 연결이 없어도 없는 실행을 성공으로 보고하지 않는지 확인합니다.

검증 결과와 한계는 [초기 검증 시나리오](workflow.md)에 기록합니다.

## 공개 디렉터리

저장소를 마켓플레이스 소스로 사용하는 것과 공식 공개 디렉터리 입점은 별도입니다. 이 초안은 공개 심사·등재를 완료한 패키지가 아닙니다. 입점하려면 당시의 메타데이터·아이콘·테스트·심사 요건을 별도로 확인합니다.

## 참고

- [OpenAI 플러그인 패키징 안내](https://developers.openai.com/plugins/build/plugins)
- [OpenAI 플러그인 제출 안내](https://developers.openai.com/plugins/deploy/submission)
- [Anthropic 스킬 마켓플레이스 예시](https://github.com/anthropics/skills/blob/main/.claude-plugin/marketplace.json)
