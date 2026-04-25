# Hackathon Agent Harness

8시간 Vibe Coding Hackathon을 위한 에이전트 협업 템플릿입니다.  
사람이 제품 방향과 계약을 정하고, 에이전트는 그 계약 안에서 작게 구현하고 검증합니다.

## 목적

- Track: Business & Applications
- Team size: 3
- Default stack: Next.js + FastAPI + Supabase
- Deploy: Vercel frontend + Railway backend
- Priority: 데모 happy path 완성

## 시작 순서

1. 해커톤 주제를 정합니다.
2. [ARCHITECTURE.md](ARCHITECTURE.md)를 먼저 채웁니다.
3. 역할별 브랜치를 나눕니다.
4. 가장 작은 동작 단위를 구현합니다.
5. 관련 검증 스크립트를 실행합니다.
6. API, env, 데이터 모델, FE/BE 경계가 바뀌면 같은 PR에서 문서를 갱신합니다.

## 핵심 문서

- [ARCHITECTURE.md](ARCHITECTURE.md): 제품 약속, API 계약, 데이터 모델, env, FE/BE 경계
- [docs/harness/OPERATING_MODEL.md](docs/harness/OPERATING_MODEL.md): 8시간 운영 방식, 역할, 브랜치, PR 규칙
- [docs/harness/QUALITY_GATES.md](docs/harness/QUALITY_GATES.md): 병렬 개발, 통합, 배포, 데모 품질 기준
- [AGENTS.md](AGENTS.md): Codex용 프로젝트 지침
- [CLAUDE.md](CLAUDE.md): Claude Code용 프로젝트 지침
- [.env.example](.env.example): 로컬 및 배포 환경 변수 예시

## 기본 작업 분리

- Frontend owner: `feat/frontend`
- Backend owner: `feat/backend`
- Integration/demo owner: `feat/integration`

짧은 PR을 유지하고, 계약과 smoke check가 맞으면 빠르게 병합합니다. `main`은 항상 배포 가능한 상태로 유지합니다.

## 검증 명령

```bash
scripts/verify
scripts/smoke
scripts/deploy-check
scripts/qa-loop
```

### 명령 용도

- `scripts/verify`: 하네스 문서 존재 여부, frontend/backend 빌드와 테스트 확인
- `scripts/smoke`: backend `/health`와 frontend 접근성 확인
- `scripts/deploy-check`: 배포 필수 env와 빌드/import 가능 여부 확인
- `scripts/qa-loop`: `verify` 실패를 최대 3회 반복 확인한 뒤 smoke check 실행

## 환경 변수

`.env.example`을 기준으로 각 앱에 필요한 값을 설정합니다.

```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=

DATABASE_URL=
SUPABASE_URL=
SUPABASE_SERVICE_KEY=
CORS_ORIGINS=http://localhost:3000
```

새 환경 변수가 필요하면 `.env.example` 또는 [ARCHITECTURE.md](ARCHITECTURE.md)에 반드시 추가합니다. secret 값은 코드, 로그, 스크린샷, 커밋, 문서에 남기지 않습니다.

## API 응답 규칙

모든 backend 응답은 표준 envelope를 사용합니다.

```json
{
  "data": {},
  "error": null,
  "status": "ok"
}
```

오류 응답은 다음 형식을 사용합니다.

```json
{
  "data": null,
  "error": {
    "code": "STRING_CODE",
    "message": "Human readable message"
  },
  "status": "error"
}
```

## 비협상 원칙

- `main`에 직접 push하지 않습니다.
- API shape을 추측하지 않습니다. [ARCHITECTURE.md](ARCHITECTURE.md)를 기준으로 작업합니다.
- secret을 코드, 로그, 스크린샷, 커밋, 문서에 남기지 않습니다.
- 새 env var는 `.env.example` 또는 `ARCHITECTURE.md`에 기록합니다.
- 파괴적인 명령과 파일 삭제는 명시적인 승인 후 진행합니다.
- 기능 개수보다 데모 happy path를 우선합니다.
