# Module 4: Skill 사용

> 공식 문서: https://code.claude.com/docs/ko/skills

## WHY

{name} {title}님이 특정 분야 교육이 필요할 때 검증된 강사 풀에서 바로 섭외하시죠? **Skill도 그런 겁니다** — 검증된 전문 역량을 필요할 때 "/스킬명" 한 줄로 바로 꺼내 씁니다.

매번 긴 프롬프트를 작성하는 대신, 누군가 이미 만들어둔 전문 스킬을 설치해서 바로 쓸 수 있습니다.

**Before:** "제안서 작성해줘. 근데 이런 형식으로, 이런 톤으로, 이런 구조로..." 매번 길게 설명
**After:** `/proposal` 한 줄이면 전문가급 제안서 초안 완성

## EXPLAIN

### Skill이란?

> 📖 glossary 참조: Skill = "검증된 강사 풀"

특정 업무에 특화된 전문 역량을 패키징한 것입니다. Claude Code에 설치하면 `/스킬명`으로 바로 호출할 수 있습니다.

| 항목 | 내용 |
|------|------|
| 비유 | 검증된 강사 풀 — 특정 분야 전문가를 필요할 때 바로 투입 |
| 설치법 | `npx skills add [패키지명]` |
| 호출법 | `/스킬명` 또는 관련 키워드로 대화 |
| 확인법 | `npx skills list` |

### 스킬의 구조

스킬은 `SKILL.md` 파일 하나로 이루어져 있습니다:

```
.claude/skills/
├── my-skill/
│   ├── SKILL.md        ← 스킬의 본체 (지시문 + 로직)
│   └── references/     ← 참고 자료 (선택)
```

### 스킬 생태계

이미 수많은 스킬이 공개되어 있습니다. 필요한 걸 찾아서 설치하면 됩니다:
- `npx skills find [검색어]` — 스킬 검색
- `npx skills add [패키지]` — 설치
- `npx skills list` — 설치된 스킬 목록
- `npx skills remove [이름]` — 삭제

## EXECUTE

아래 순서대로 실행해보세요:

**실습 1: 현재 설치된 스킬 확인**

    npx skills list

어떤 스킬들이 설치되어 있는지 확인해보세요.

**실습 2: Content Digest 스킬 체험**

> Content Digest는 콘텐츠를 퀴즈로 먼저 테스트하고, 모르는 부분을 집중 학습하는 스킬입니다.

Claude Code에 이렇게 요청해보세요:

    2026년 기업교육 트렌드에 대해 알려주고,
    Content Digest 방식으로 학습하게 해줘.
    먼저 퀴즈부터 내줘.

**실습 3: 스킬에게 제안서 초안 요청**

Claude Code에 이렇게 요청해보세요:

    LG전자에서 "AI 리터러시" 주제로 전 임직원 대상 교육을 요청했어.
    대상: 비개발 직군 500명
    기간: 2일 (총 16시간)
    예산: 미정

    이 정보를 바탕으로 교육 제안서 초안을 작성해줘.

Claude가 모듈 3에서 설정한 CLAUDE.md 규칙을 따라 작성하는지 확인해보세요!

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Skill을 설치하는 명령어는 무엇인가요?",
    "header": "Quiz 4-1",
    "options": [
      {"label": "npx skills add [패키지명]", "description": "npm 패키지처럼 설치"},
      {"label": "claude install [스킬명]", "description": "claude 명령어로 설치?"},
      {"label": "/install [스킬명]", "description": "슬래시 명령어로 설치?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. `npx skills add [패키지명]`으로 설치합니다. GitHub 저장소나 npm 패키지를 바로 설치할 수 있습니다.

```json
AskUserQuestion({
  "questions": [{
    "question": "Skill과 일반 대화의 차이는 무엇인가요?",
    "header": "Quiz 4-2",
    "options": [
      {"label": "스킬은 사전 정의된 전문 워크플로우가 있다", "description": "특정 업무에 최적화된 지시문"},
      {"label": "차이가 없다", "description": "그냥 대화와 동일?"},
      {"label": "스킬은 더 비싸다", "description": "비용 차이?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. 스킬은 특정 업무에 최적화된 **사전 정의된 워크플로우**입니다. 일반 대화는 매번 새로 시작하지만, 스킬은 검증된 프로세스를 바로 실행합니다.

## LEADER-TIP

> 💡 **{name} {title}님을 위한 리더 팁**
>
> - 팀에 유용한 스킬을 발견하면 **팀 전체가 설치**하게 하세요 — `npx skills add` 한 줄이면 됩니다
> - 현재 쓸 수 있는 스킬 중 {team}에 유용한 것들:
>   - Content Digest: 산업 리포트나 트렌드 자료를 퀴즈로 빠르게 학습
>   - Clarify: 모호한 고객 요구사항을 구조화 (모듈 7에서 배웁니다)
> - **모듈 8에서 우리 팀만의 스킬을 직접 만들 겁니다** — 제안서 자동화, 강사 리서치 등
> - 스킬은 팀의 **표준 업무 프로세스(SOP)를 AI에 인코딩**하는 것과 같습니다
