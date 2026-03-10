# Module 10: 팀 전파 + GitHub + 지식 축적

## WHY

{name} {title}님이 지금까지 만든 것들 — CLAUDE.md 규칙, 제안서 스킬, Agent Teams 설정. **이걸 {team} 팀원 전체가 쓸 수 있게 하려면?**

이 모듈에서는 개인의 성과를 팀 자산으로 만들고, 팀원에게 배포하는 방법을 배웁니다.

**Before:** {name} {title}님만 Claude Code를 잘 쓰고, 팀원들은 처음부터 다시 설정
**After:** `npx skills add` 한 줄이면 팀원 전원이 {name} {title}님이 만든 모든 것을 사용

## EXPLAIN

### 이 모듈의 4가지 주제

| 단계 | 주제 | 비유 |
|------|------|------|
| 10-1 | Compound + Session Wrap | 업무 일지 + 인사이트 축적 |
| 10-2 | GitHub 기초 | 팀 공유 드라이브 |
| 10-3 | 팀 스킬 배포 | 전사 표준 도구 배포 |
| 10-4 | 팀 온보딩 설계 | 신입 교육 매뉴얼 |

## EXECUTE

### 실습 10-1: Compound + Session Wrap

> 📖 glossary 참조: Compound = "컨설팅 인사이트 자동 축적", Session Wrap = "업무 일지"

**Compound란?**

작업하면서 검증된 인사이트가 자동으로 지식 베이스에 쌓이는 것입니다.

```
제안서 작성 중 발견:
"삼성전자는 항상 ROI 수치를 요구한다"
    │
    ▼
Compound (자동 축적)
    │
    ▼
다음 삼성 제안서에 자동 반영
```

**Session Wrap란?**

세션이 끝날 때 "오늘 뭘 했고, 뭘 배웠고, 다음에 뭘 할 것인지" 자동으로 정리하는 기능입니다.

Claude Code에 이렇게 요청하세요:

    이번 세션에서 배운 내용을 정리해줘.
    - 오늘 한 작업 요약
    - 새로 배운 것
    - 다음에 할 것

Session Wrap이 자동으로 세션 요약을 만들어주는 것을 확인하세요.

### 실습 10-2: GitHub 기초

> 📖 glossary 참조: GitHub = "팀 공유 드라이브 (버전 관리 포함)"

GitHub은 코드와 문서를 팀 전체가 공유하고, 변경 이력을 추적하는 플랫폼입니다. 개발자만의 도구가 아닙니다 — {team}의 스킬과 설정을 팀원에게 배포하는 데 쓸 수 있습니다.

**GitHub 계정 확인:**

    GitHub 계정이 있는지 확인해줘.
    없으면 만드는 방법을 알려줘.

**새 저장소(repo) 만들기:**

Claude Code에 이렇게 요청하세요:

    GitHub에 "{team}-cc-skills" 이름의 새 repo를 만들어줘.
    설명은 "{team} Claude Code 스킬 & 설정 모음"으로.

**기본 흐름 체험:**

    지금까지 만든 스킬과 설정을 GitHub에 올리는 방법을 알려줘.
    git add → git commit → git push 기본 흐름을 하나씩 설명해줘.

### 실습 10-3: 팀 스킬 배포

**만든 스킬을 repo에 올리기:**

    모듈 8에서 만든 제안서 스킬과
    모듈 9에서 만든 Agent Teams 설정을
    GitHub repo에 push해줘.

**팀원 입장에서 설치 체험:**

    팀원이 우리가 만든 스킬을 설치하려면 어떻게 하면 되는지 보여줘.
    "npx skills add" 한 줄로 설치하는 과정을 시뮬레이션해줘.

핵심: **팀원이 이 한 줄만 실행하면 내가 만든 모든 것을 쓸 수 있습니다.**

```
팀원의 터미널:
$ npx skills add {team}-cc-skills

설치 완료!
- ✅ 제안서 자동 생성 스킬
- ✅ Agent Teams 설정
- ✅ CLAUDE.md 팀 규칙
```

### 실습 10-4: 팀 온보딩 설계

**팀 공용 CLAUDE.md 설계:**

    {team} 팀 전체가 쓸 공용 CLAUDE.md를 설계해줘.
    포함할 내용:
    - 제안서 작성 규칙 (톤, 구조, 금액 표기)
    - 강사 분류 체계
    - 고객 응대 원칙
    - 자주 쓰는 용어 정의

**Hook 설정 체험:**

> 📖 glossary 참조: Hook = "자동 품질 체크 프로세스"

    "제안서 파일이 저장될 때 자동으로 QA 에이전트가 검수하는" Hook을 설계해줘.
    어떻게 설정하면 되는지 단계별로 알려줘.

**팀원 온보딩 가이드 작성:**

    새 팀원이 {team}에 합류했을 때 Claude Code를 바로 쓸 수 있도록
    온보딩 가이드를 만들어줘:

    1단계: Claude Code 설치 (터미널에서 claude 입력)
    2단계: 팀 스킬 설치 (npx skills add {team}-cc-skills)
    3단계: /cc-tutor로 기초 학습 시작
    4단계: 첫 제안서 작성 도전

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "만든 스킬을 팀원에게 배포하는 가장 쉬운 방법은?",
    "header": "Quiz 10-1",
    "options": [
      {"label": "GitHub repo에 올리고 npx skills add로 설치", "description": "한 줄이면 전체 팀이 설치"},
      {"label": "파일을 이메일로 보낸다", "description": "수동 전달?"},
      {"label": "팀원이 직접 처음부터 만든다", "description": "처음부터 다시?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. GitHub repo에 올려두면 팀원은 `npx skills add` **한 줄**이면 모든 스킬과 설정을 설치할 수 있습니다.

```json
AskUserQuestion({
  "questions": [{
    "question": "Compound의 목적은 무엇인가요?",
    "header": "Quiz 10-2",
    "options": [
      {"label": "작업 중 검증된 인사이트를 자동으로 지식 베이스에 축적", "description": "일하면서 자연스럽게 쌓이는 지식"},
      {"label": "파일을 여러 개 합치는 것", "description": "파일 병합?"},
      {"label": "Claude의 응답 속도를 높이는 것", "description": "성능 향상?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. **Compound**는 작업하면서 발견한 인사이트(예: "삼성은 ROI 수치 필수")가 자동으로 축적되어, 다음 작업에 반영되는 시스템입니다.

## LEADER-TIP

> 💡 **{name} {title}님을 위한 리더 팁**
>
> - 🎖️ **축하합니다! AI 전도사 배지를 획득했습니다.**
> - 이제 {name} {title}님은 {team}의 **AI 워크플로우를 설계하고 팀원에게 배포**할 수 있습니다
>
> - **즉시 할 수 있는 3가지:**
>   1. 팀 공용 CLAUDE.md 배포 → 모든 팀원의 Claude가 같은 규칙을 따름
>   2. 제안서 스킬 배포 → 주니어도 시니어급 제안서 가능
>   3. 팀원 온보딩 가이드 공유 → 새 팀원도 첫 날부터 Claude 활용
>
> - **다음 스텝:**
>   - {leader} 팀장님에게 "AI 팀 워크플로우" 보고서를 작성해보세요
>   - 팀원들에게 `/cc-tutor`를 안내하고, Essential Path부터 시작하게 하세요
>   - 월 1회 "스킬 리뷰 데이"를 만들어 팀 스킬을 점검하고 개선하세요
>
> - **{name} {title}님의 여정 요약:**
>   - 🔧 Module 1: Claude Code 시작
>   - 📁 Module 2: 파일 다루기
>   - 📄 Module 3: CLAUDE.md로 팀 규칙 설정
>   - 🎯 Module 4: Skill로 전문 역량 활용
>   - 👥 Module 5: Subagent로 병렬 작업
>   - 🔌 Module 6: MCP로 외부 시스템 연결
>   - 📋 Module 7: Clarify로 요구사항 구조화
>   - ⚡ Module 8: skill-creator로 노하우 스킬화
>   - 🤝 Module 9: Agent Teams로 AI TF 구성
>   - 🎖️ Module 10: 팀 전파 + 온보딩 완성
