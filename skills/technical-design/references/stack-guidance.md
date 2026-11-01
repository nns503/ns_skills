# 실제 기술 구성에 따른 전문 지침 선택

해당 기술이 프로젝트에 확인되고 이번 변경에 관련될 때만 읽는다. 아래 이름은 참고한 원본의 이름이며, 설치 환경의 실제 식별자·버전·사용 가능 여부는 별도로 확인한다.

| 실제 구성·작업 | 전문 지침 후보 | 적용 범위 |
| --- | --- | --- |
| 웹 UI의 사용성·접근성 검토 | Vercel web-design-guidelines | 변경 화면의 탐색·입력·상태·관련 웹 지침 |
| React·Next.js 화면·데이터 흐름 | Vercel React best practices | 요청 직렬 대기·서버/클라이언트 경계·번들·관련 렌더링 |
| React Native·Expo 앱 | Vercel React Native skills | 해당 앱의 목록·입력·상태·플랫폼 차이 |
| PostgreSQL 스키마·쿼리·마이그레이션 | Supabase Postgres best practices | 데이터 제약·조회·연결·잠금·관련 보안 |
| Supabase의 인증·클라이언트 통합 | 현재 환경에서 제공되는 Supabase 지침·공식 자료 | 실제 사용하는 제품·SDK와 인증 경계 |

설정·의존성·lockfile·실제 코드를 보고 적용 여부를 판단한다. Next.js의 서버 API를 일반 React·다른 웹 프레임워크에 적용하거나 PostgreSQL 지침을 다른 DB에 그대로 적용하지 않는다. 다른 스택이면 해당 프로젝트의 공식 자료와 사용 가능한 전문 스킬을 찾는다.

## 웹·앱 설계에 반영

외부 요청의 의존 관계와 실제 병목을 보고 병렬화·로딩 경계를 정한다. 사용자별 데이터를 공유 상태나 캐시에 섞지 않도록 권한·수명 범위를 확인한다. 현재 요구와 측정 근거에 맞게 최적화하고, 예제의 캐시·상태·UI 라이브러리를 자동 도입하지 않는다.

모바일은 실제 프레임워크·버전·대상 기기에서 목록·상태·상호작용을 확인한다. 특정 목록·애니메이션·이미지 라이브러리를 사용하는 규칙은 해당 의존성과 필요가 확인된 경우에만 적용한다.

## 데이터 설계에 반영

데이터 제약과 기존 데이터를 확인한 뒤 마이그레이션을 설계한다. 재실행 가능성이 필요하면 실제 DB 버전·스키마 범위·중복 및 동시 실행 조건을 확인한다. 예제 SQL을 운영에서 그대로 실행하지 않는다.

행·사용자·테넌트별 접근 통제가 필요한 경우 실제 읽기·쓰기 경로와 실행 역할을 확인한다. PostgreSQL·Supabase의 RLS를 사용하는 프로젝트에서는 일반 사용자·다른 사용자·해당하는 관리 역할의 동작을 확인한다. 권한을 우회하는 역할로 성공한 조회를 사용자 격리 검증으로 간주하지 않는다. RLS 도입 여부 자체는 프로젝트의 보안 설계에 따른다.

실제 조회·실행 계획·입력 규모를 근거로 인덱스·연결·쿼리 개선을 판단한다. 근거 없이 모든 컬럼에 인덱스를 추가하거나 별도 운영 도구를 도입하지 않는다.

## 참고한 판본

- [Vercel React](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/react-best-practices/SKILL.md)
- [Vercel Web Interface Guidelines 스킬](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/web-design-guidelines/SKILL.md)
- [Vercel React Native](https://github.com/vercel-labs/agent-skills/blob/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills/react-native-skills/SKILL.md)
- [Supabase Postgres](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/SKILL.md)
- [Supabase RLS 참고](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/references/security-rls-basics.md)
- [Supabase 제약·마이그레이션 참고](https://github.com/supabase/agent-skills/blob/c9be0e931b7930f7d02126d04774d904c381e7d7/skills/supabase-postgres-best-practices/references/schema-constraints.md)

특정 SQL·SDK·최적화 방식은 실제 실행 시 해당 버전의 공식 자료와 프로젝트 동작으로 확인한다. 위 스킬의 설치나 기술 채택은 필수 조건이 아니다.
