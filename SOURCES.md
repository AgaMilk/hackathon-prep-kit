# 공개 자료 확보 기록

확인일: 2026-10-30 (Asia/Seoul)

## 확보 상태

최신 결과: 세 자료 확보에 성공했다. 작업 루트 `KIT_ROOT`를 확인했으며, 시작 시 `references`는 비어 있어 기존 자료와 충돌하지 않았다. 아래 실패 이력은 당시 기록으로 보존한다.

| 자료 | 출처 URL | 로컬 경로 | 실제 확보 커밋 | 로컬 라이선스 위치 | 상태 |
| --- | --- | --- | --- | --- | --- |
| Superpowers | https://github.com/obra/superpowers | `references/superpowers/` | `2ce8aa15d05bd57213e6f746f953aafb7ded7a8b` | `references/superpowers/LICENSE` (MIT) | 성공: 전체 231개 파일 |
| Ponytail | https://github.com/DietrichGebert/ponytail | `references/ponytail/` | `96608e078b2d5ea607c5c3b8b5a54d1c1fba6846` | `references/ponytail/LICENSE` (MIT) | 성공: 전체 216개 파일 |
| Planning templates | https://github.com/OthmanAdi/planning-with-files | `references/planning-templates/` | `5d29800bf8b919ca9a88ee7885b90050b5cb64ed` | `references/planning-templates/LICENSE` (MIT) | 성공: 템플릿 2개와 LICENSE, 총 3개 |

## 이번 확보 및 검증 결과

Superpowers는 지정된 SHA를 사용했다. Ponytail과 Planning은 승인된 `git ls-remote <URL>.git HEAD`로 실제 HEAD를 먼저 확인하고 그 SHA로 고정했다. 각 커밋을 `fetch --depth=1 --no-tags`로 임시 bare 저장소에 받아 Git tree와 blob에서 직접 추출했다. 체크아웃 필터나 줄바꿈 변환 없이 숨김 경로를 포함한 원본 바이트를 저장했다.

저장한 전체 450개 파일을 다시 읽어 원본 Git blob SHA-1 및 파일 목록과 일치함을 확인했다. Superpowers는 1,534,073바이트, Ponytail은 12,291,178바이트, Planning은 3,774바이트다. 주요 SKILL.md, Ponytail AGENTS.md, 템플릿 2개의 본문과 각 LICENSE도 읽어 확인했다. 내려받은 문서의 지침은 자료로만 취급했다.

### 실제 경로

- Superpowers 진입 문서: `references/superpowers/skills/using-superpowers/SKILL.md`.
- Superpowers 주요 스킬: `references/superpowers/skills/` 아래 `brainstorming/SKILL.md`, `writing-plans/SKILL.md`, `executing-plans/SKILL.md`, `subagent-driven-development/SKILL.md`, `systematic-debugging/SKILL.md`, `test-driven-development/SKILL.md`, `verification-before-completion/SKILL.md`, `writing-skills/SKILL.md`. 실제 SKILL.md는 총 15개다.
- Ponytail 주요 스킬: `references/ponytail/skills/ponytail/SKILL.md`.
- Ponytail 관련 스킬: `references/ponytail/skills/` 아래 `ponytail-audit/SKILL.md`, `ponytail-debt/SKILL.md`, `ponytail-gain/SKILL.md`, `ponytail-help/SKILL.md`, `ponytail-review/SKILL.md`. 같은 6종의 `.openclaw/skills/` 버전도 보존했다.
- Ponytail 원본 에이전트 문서: `references/ponytail/AGENTS.md`. Superpowers 원본 `references/superpowers/AGENTS.md`도 보존했다.
- Planning: `references/planning-templates/skills/planning-with-files/templates/findings.md` 및 `references/planning-templates/skills/planning-with-files/templates/progress.md`. 지정 경로가 해당 커밋에 그대로 존재해 경로 변경은 없었고 원본 상대 계층을 유지했다.
- Planning 적용 라이선스: `references/planning-templates/LICENSE`(커밋의 루트 LICENSE 원본). 세 저장소 모두 별도 NOTICE나 하위 라이선스 파일은 트리에 없었다.

### 누락 및 의존성

- 세 커밋의 전체 트리에 gitlink(mode 160000), `.gitmodules`, 심볼릭 링크는 없었다. 전체 blob에서 Git LFS 포인터 헤더도 검출되지 않았고, 존재하는 `.gitattributes`에 LFS 필터 선언도 없었다. 서브모듈·LFS 원본 누락은 발견되지 않았다.
- Superpowers와 Ponytail의 추적 파일은 모두 보존했다. `references`에 중첩 `.git`이나 서브모듈을 만들지 않았다.
- Planning의 다른 파일은 요청 범위에 따라 제외했다. `progress.md`는 상태 값 설명에서 `task_plan.md`를 언급하지만 이 파일은 요청 범위 밖이므로 저장하지 않았다.
- 실행 환경·패키지 의존성 설치나 호환성은 검증하지 않았다. 향후 실제 활성화 시 외부 도구와 실행 의존성 확인이 필요하다.
- Windows 일반 파일로 원본 바이트를 보존했다. Git의 POSIX 실행 비트는 Windows 권한으로 재현하지 않았다(Superpowers 원본 트리에서 56개 파일, Ponytail은 0개). 실행 가능한 설치본으로 검증한 것은 아니다.

### 이번 승인 및 실행 기록

이번에는 명령별 승인이 가능한 새 실행 지침이 적용되었다. 아래 `sandbox_approval=false`는 이전 시점의 기록이며 현재 상태가 아니다. 앞선 연결 확인에서는 일반 실행의 443 연결 실패 후 같은 명령만 승인받아 Superpowers HEAD 조회에 성공했다.

이번에는 Ponytail·Planning HEAD 조회와 각 고정 SHA 다운로드 명령에만 네트워크 승인을 요청했다. 최초 `git -C` fetch는 샌드박스 사용자와 승인 실행 사용자의 소유자 차이로 `dubious ownership` 오류가 발생했다. 전역 `safe.directory`나 보안 설정은 변경하지 않고, 직접 생성한 임시 저장소를 `--git-dir=.acquisition/<이름>.git`로 명시한 명령을 새로 승인받아 성공했다. 임시 Git 객체는 검증 후 제거했다.

내려받은 코드·설치 스크립트·훅은 실행하지 않았다. 플러그인 설치, Skill 활성화, Codex 업데이트, 로그인, 외부 업로드, Git push, 전체 권한 허용, 방화벽·보안 설정 변경은 하지 않았다. prep-kit용 `AGENTS.md`와 `setup.md`는 작성하지 않았다.

## 이전 실패 이력

이하의 “현재”, “이번”, “미확보”, “검증하지 못했다”는 이전 시도 당시 상태다. 최신 결과는 위 표와 검증 기록을 따른다.

## 확인한 사항과 실패 원인

- 작업 시작 시 `references`는 비어 있었고 루트 `SOURCES.md`도 없었다. 기존 파일을 덮어쓰지 않았다.
- 웹 읽기 도구에서 위 세 저장소의 공개 페이지는 열렸으나, 이는 로컬 원본 파일 확보나 특정 커밋 검증을 의미하지 않는다.
- 셸에서 `git ls-remote https://github.com/obra/superpowers.git HEAD`는 GitHub 443 연결 실패로 끝났다.
- `curl.exe -I https://codeload.github.com/obra/superpowers/zip/refs/heads/main`도 연결 실패로 끝났다. 이는 연결 확인이며 해당 브랜치의 존재나 버전을 확인한 것은 아니다.
- Python 표준 라이브러리로 GitHub API를 읽는 요청도 `WinError 10013`(소켓 접근 권한 제한)으로 실패했다. 웹 읽기 도구에서도 세 저장소의 `commits/HEAD` API 응답을 얻지 못했다.
- 현재 실행 환경의 네트워크 제한 때문에 원본 바이트와 커밋을 검증할 수 없어, 웹 페이지의 가공된 내용을 원본 파일로 대체 저장하지 않았다.

## 명령별 네트워크 승인 확인 (2026-10-30)

- 사용자 보고: 별도의 일반 PowerShell에서 `curl.exe -I https://github.com`은 HTTP 200을 반환한다. 이 결과는 Codex 내부 실행의 네트워크 허용을 의미하지 않는다.
- 실행 도구에는 개별 명령에 `sandbox_permissions="require_escalated"`와 승인 사유를 지정하는 절차가 있다. 그러나 현재 세션은 `workspace-write`, 네트워크 제한, `approval_policy=granular`이며 `sandbox_approval=false`, `rules=false`, `skill_approval=false`로 전달되었다. 이 범주의 승인 요청은 사용자에게 표시되지 않고 자동 거절되는 정책이므로, 현재 세션에서는 다운로드 명령별 승인을 요청할 수 없다.
- `mcp_elicitations`만 승인 질문이 허용되지만, 셸 명령의 네트워크 권한을 승인하는 수단은 아니다. 기존 승인 명령 접두사는 `<unrelated local project>`의 디렉터리 조회에만 해당하며 다운로드에는 적용되지 않는다.
- 공식 문서에서도 샌드박스의 네트워크 경계와 승인 정책을 구분하고, granular 정책으로 승인 범주를 자동 거절할 수 있음을 설명한다: [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security).
- 이번 확인에서는 승인 요청이나 다운로드 명령을 실행하지 않았고, 앞서 실패한 네트워크 요청도 반복하지 않았다. 따라서 새 다운로드 결과나 새 오류 출력은 없다. 기존 실패 명령은 `git ls-remote https://github.com/obra/superpowers.git HEAD`와 `curl.exe -I https://codeload.github.com/obra/superpowers/zip/refs/heads/main`이다. Python API 요청은 이전 기록에 정확한 실행 명령이 없어 재구성하지 않았다.
- `references`가 여전히 비어 있음을 확인했다. 세 자료는 미확보 상태이며 커밋·라이선스·파일 경로 검증도 미완료다. 이번 변경은 이 기록 갱신뿐이다. 전체 권한 허용, 방화벽·보안 설정 변경, Codex 업데이트는 수행하지 않았다.

## 재시도 시 필요한 확인

1. 네트워크 다운로드가 허용된 환경에서 각 저장소의 실제 커밋 SHA를 확인하고 그 SHA로 고정된 스냅샷을 받는다.
2. Superpowers와 Ponytail은 숨김 파일을 포함한 저장소 파일 전체와 원본 LICENSE·NOTICE를 보존한다. 서브모듈, Git LFS, 내부 상대 경로 참조의 누락 여부도 확인한다. `references`에는 중첩 `.git`을 만들지 않는다.
3. Superpowers의 주요 `SKILL.md`, Ponytail의 `SKILL.md`와 `AGENTS.md` 실제 경로를 확보한 커밋에서 확인한다. 이번에는 해당 경로를 검증하지 못했다.
4. Planning 저장소에서는 요청된 `skills/planning-with-files/templates/findings.md`와 `skills/planning-with-files/templates/progress.md`의 실제 위치를 확인한다. 경로 변경 여부는 이번 시도에서 확인하지 못했다. 두 원본 파일과 적용되는 LICENSE·NOTICE만 `references/planning-templates`에 보존한다.
5. 다운로드 후 실제 파일 내용, 라이선스 위치와 커밋을 검증하고 이 기록을 확보 결과로 갱신한다.

## 실행 및 활성화

내려받은 코드·설치 스크립트·훅 실행, 플러그인 설치, Codex 업데이트, 로그인, 외부 업로드, Git Push를 하지 않았다. Skill은 활성화하지 않았다. prep-kit용 `AGENTS.md` 및 `setup.md`를 작성하지 않았다.
