# 최초 과제 연결

이 프롬프트는 과제 시작 시 한 번 준비자료를 연결하는 절차다. 반복 운영·승인·검증 규칙은 [KIT_ROOT의 AGENTS.md](../AGENTS.md)를 따른다. 전체 Skill 설치·활성화 절차가 아니다.

## 연결 순서

1. 사용자가 지정한 `KIT_ROOT`와 `TASK_ROOT`를 각각 실제 경로로 확인한다. 현재 디렉터리 이름만으로 판단하지 말고 준비자료 구조와 과제 파일을 확인한다. 두 위치가 같거나 부모·자식이라고 가정하지 않는다. TASK_ROOT가 미지정이거나 잘못된 루트로 보이면 의존 작업을 시작하기 전에 확인한다. 준비자료 폴더에 과제 작업 문서를 대신 만들지 않는다.
2. TASK_ROOT에 적용되는 기존 지침(상위·하위 경로의 적용 범위 포함), README, 과제 안내·평가·제출 조건을 먼저 읽는다. 그다음 KIT_ROOT/AGENTS.md를 참고 운영 규칙으로 명시적으로 읽는다. 과제 지침과 충돌하면 과제 지침을 우선하고 충돌·영향을 보고한다. 중요 미결사항을 조용히 건너뛰지 않는다.
3. 준비자료 AGENTS.md가 다른 프로젝트에 자동 적용된다고 가정하지 않는다. 과제 AGENTS.md를 덮어쓰거나 매번 생성하지 않는다. 이번 세션에서 읽은 공통 규칙과 과제 지침의 연결을 짧게 기록한다.
4. [SOURCES.md](../SOURCES.md), AGENTS.md 및 아래 단계별 참조 파일의 존재를 확인한다. 출처·고정 커밋·확보 상태는 SOURCES.md를 기준으로 확인하되 전체 450개 파일을 매번 읽지 않는다. 필요한 문서가 없으면 경로·영향을 알리고 해당 자료에 의존하는 작업을 보류한다. 자동 다운로드나 다른 버전 대체를 하지 않는다.
5. 기존 실행 방법·런타임·설정·포트·검증 명령을 README와 프로젝트 파일에서 확인한다. 불필요하게 설치하거나 준비자료의 스크립트·훅을 실행하지 않는다. 연습 환경의 3000 포트나 Node 구성을 과제에 강제하지 않는다. TASK_ROOT에 기존 실행 가능한 예제가 있으면 허용된 실행 명령으로 구동하고, 실제 안내된 주소·health 엔드포인트 등 제공되는 확인 지점에서 응답과 최소 동작을 검사한다. 주소나 health 경로를 임의로 가정하지 않는다. 사용자 브라우저 화면 확인은 사용자 보고로, 에이전트의 응답·동작 검사는 직접 검사로 구분해 기록한다. 기존 예제가 없으면 해당 없음, 예제는 있지만 실행할 수 없으면 이유와 미검증을 기록한다. 새 앱 구현이나 불필요한 설치를 setup 조건으로 삼지 않는다. 확인만 한 실행 명령은 미실행으로 표시하고, 실제 실행·검사는 허용 범위와 도구 권한을 확인한 뒤 수행한다.
6. AGENTS.md의 작업 문서 책임에 따라 같은 역할의 기존 문서를 찾아 재사용하고 실제 경로를 매핑한다. 없으면 TASK_ROOT의 기본 경로를 사용한다. progress/findings는 첫 기록이 필요할 때, implementation-plan은 분석 후 승인 묶음을 준비할 때 만든다. 기존 문서는 초기화하지 않는다. 템플릿을 새로 복사할 경우 작업용 progress의 계획 참조만 실제 implementation-plan으로 연결하고 조정 사실을 표시한다.
   TASK_ROOT의 progress에 KIT_ROOT·TASK_ROOT·적용 지침 경로, 현재 단계·다음 행동, 원래 시작 시각·확인된 마감 시각(시간대 포함)·승인 상태와 승인 범위를 기록한다. 확인되지 않은 값은 미확인으로 표시한다. 개인 PC의 실제 경로는 공개 키트 문서에 쓰지 않고 과제 작업 기록에만 남긴다.
7. 현재 모델과 reasoning 설정을 실제로 확인할 수 있을 때만 기록한다. 권장 선택은 제공되는 **6.1 Sol medium**이며 없으면 제공 모델·기본값을 사용한다. 모델명·reasoning 옵션을 추정하거나 자동 변경하지 않는다. 연결을 위해 업데이트·API 키·로그인을 요구하지 않는다. 확인 수단이 없으면 미확인으로 기록한다.
8. 아래 연결 결과를 짧게 보고하고 분석 단계로 진행한다. 제품 구현은 AGENTS.md의 묶음 승인 후 시작한다. 연결은 5분 목표이며 측정 전 달성했다고 쓰지 않는다. 각 작업 시작·종료와 검증 후 시간은 AGENTS.md에 따라 확인한다. 시간 확인이 안 되면 현재 남은 시간만 사용자에게 확인해 기록한다.

## 중단 후 새 세션에서 재개

TASK_ROOT의 기존 적용 지침→progress→progress에 기록된 KIT_ROOT/AGENTS.md→현재 단계의 implementation-plan·findings·필요한 참고 문서 순서로 확인한다. progress의 원래 시작 시각·확인된 마감 시각·승인 상태를 유지하고, 미완료 작업과 다음 행동부터 이어간다. 완료된 setup과 승인된 계획을 처음부터 반복하거나 새 세션에서 시간 예산을 초기화하지 않는다. 경로·승인·현재 상태가 누락되거나 달라진 부분만 확인한다. 재개 시에도 남은 시간을 확인하고 검증·산출물·제출 여유를 고려해 다음 작업을 정한다.

## 단계별 참조 연결

아래 링크는 이 파일 기준 상대 경로다. 실제 과제에서 접근할 때는 확인한 KIT_ROOT를 기준으로 해석한다. 원문을 읽는 것은 설치·활성화가 아니다. 필수 참조 문서는 해당 주제가 필요해질 때 읽는다.

| 단계 | 원문과 필수·조건부 참조 | 사용할 관점 |
| --- | --- | --- |
| 문제·아이디어 | [brainstorming/SKILL.md](../references/superpowers/skills/brainstorming/SKILL.md), 설계 자기 점검 시 [builder-check-prompt.md](../references/superpowers/skills/brainstorming/builder-check-prompt.md) | 의도·범위·대안·설계 누락. 독립 에이전트 dispatch 대신 자기 점검은 해커톤용 조정 |
| 구현 계획 | [writing-plans/SKILL.md](../references/superpowers/skills/writing-plans/SKILL.md) | 파일·인터페이스·검증 가능한 작업·완료 조건. 원본 Skill 호출 헤더는 복사하지 않음 |
| 단계별 개발 | [executing-plans/SKILL.md](../references/superpowers/skills/executing-plans/SKILL.md), [Ponytail SKILL.md](../references/ponytail/skills/ponytail/SKILL.md) | 승인된 계획 연속 실행, 결정 근거 기록, 작은 완전한 구현. 전용 스크립트·모드·훅은 제외 |
| 테스트 | [test-driven-development/SKILL.md](../references/superpowers/skills/test-driven-development/SKILL.md), 테스트 작성·변경 시 [writing-good-tests.md](../references/superpowers/skills/test-driven-development/writing-good-tests.md) | 테스트 우선과 사후 검증의 구분, 실제 동작·독립 기대값. 엄격한 TDD 전체 채택은 아님 |
| 디버깅 | [systematic-debugging/SKILL.md](../references/superpowers/skills/systematic-debugging/SKILL.md). 깊은 호출 문제는 [root-cause-tracing.md](../references/superpowers/skills/systematic-debugging/root-cause-tracing.md), 입력 검증은 [defense-in-depth.md](../references/superpowers/skills/systematic-debugging/defense-in-depth.md), 비동기 대기는 [condition-based-waiting.md](../references/superpowers/skills/systematic-debugging/condition-based-waiting.md) | 재현·원인·단일 가설·최소 수정. 실제 위험에 필요한 검사로 범위를 정하며 원문 예제 명령은 실행하지 않음 |
| 완료·리뷰·산출물 | [verification-before-completion/SKILL.md](../references/superpowers/skills/verification-before-completion/SKILL.md), 자기 검토 관점은 [code-reviewer.md](../references/superpowers/skills/requesting-code-review/code-reviewer.md), [delivery.md](delivery.md) | 주장 전 증거, 요구사항·안전·검증 누락 확인. 별도 reviewer가 없으면 자기 검토로 표시 |
| 작업 기록 | [findings.md 원본](../references/planning-templates/skills/planning-with-files/templates/findings.md), [progress.md 원본](../references/planning-templates/skills/planning-with-files/templates/progress.md) | 작업용 사본만 활용하고 참조를 implementation-plan으로 변경. Planning 전체 Skill·별도 task_plan.md는 제외 |

## 연결 결과 보고 형식

- 확인한 KIT_ROOT / TASK_ROOT, 시간 측정 여부.
- 적용되는 과제 지침·시험 규정과 공통 규칙, 발견한 충돌 및 처리.
- 한 에이전트의 역할 순서와 실제 계획/findings/progress 문서 경로 또는 생성 예정 시점.
- 확인된 실행 방법·포트·검증 명령, 각각의 확인/실행 여부.
- 모델·설정 등 미확인 항목, 누락 자료·권한 제약.
- 다음 단계: 문제·아이디어·설계·계획의 묶음 승인 준비.

이 보고만으로 환경 실행 성공·테스트 통과·5분 연결 달성·Skill 활성화를 주장하지 않는다.
