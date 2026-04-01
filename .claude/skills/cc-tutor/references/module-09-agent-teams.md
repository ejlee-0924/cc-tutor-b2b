# Module 8: Agent Teams

> 공식 문서: https://code.claude.com/docs/ko/agent-teams

## WHY

{name} {title}님, 큰 제안서 프로젝트는 혼자 하지 않죠. 리서처가 시장조사를 하고, 기획자가 커리큘럼을 짜고, QA가 검수합니다. **AI도 혼자보다 팀으로 일할 때 품질이 올라갑니다.**

Claude Code에는 AI 팀을 만드는 **3가지 도구**가 있습니다:

| 도구 | 비유 | 용도 |
|------|------|------|
| **AGENTS.md** | 팀 매뉴얼 | 고정 역할 정의 → 반복 가능한 파이프라인 |
| **team-assemble** | 인력파견 업체 | "이 일 해줘" → 알아서 팀 구성 + 실행 |
| **team-orchestrator** | 회의 퍼실리테이터 | 전문가 관점으로 토론 + 의사결정 |

오늘 3가지를 모두 배웁니다.

**Before:** 제안서 작성 → 검수 → 수정 → 재검수를 혼자 반복 (3일)
**After:** AI TF가 리서치→초안→검수→전문가 토론까지 (3시간)

## EXPLAIN

### 1. AGENTS.md — 팀 구조를 설계하는 설정 파일

> 📖 glossary 참조: AGENTS.md = "프로젝트 TF의 직무기술서(JD)"

AGENTS.md를 작성하면 Claude Code가 각 에이전트의 역할, 전문 분야, 접근 권한을 알고 팀으로 협업합니다.

```markdown
# AGENTS.md 예시

## researcher
- 역할: 시장조사 및 경쟁사 분석
- 전문: 산업 동향, 교육 트렌드, 강사 리서치
- 접근: 웹 검색, 문서 읽기

## writer
- 역할: 교육 제안서 작성
- 전문: 제안서 구조화, 톤앤매너, 커리큘럼 설계
- 접근: 리서치 결과, 템플릿, CLAUDE.md 규칙

## reviewer
- 역할: 제안서 품질 검수
- 전문: 논리 검증, 누락 체크, 고객 관점 검토
- 접근: 최종 제안서, 고객 요구사항 원본
```

**에이전트 간 협업 방식:**

| 방식 | 설명 | 적합한 상황 |
|------|------|-----------|
| 순차형 | A→B→C 순서대로 | 제안서 파이프라인 (리서치→작성→검수) |
| 병렬형 | A, B, C 동시에 | 독립적 리서치 3건 동시 진행 |
| 대립형 | A vs B → C가 종합 | 의사결정 검증 (찬성 vs 반대 → 판정) |

### 2. team-assemble — 작업을 주면 알아서 팀을 만들어 실행

AGENTS.md가 **미리 설계하는 것**이라면, team-assemble은 **즉석에서 팀을 꾸리는 것**입니다.

| 항목 | 내용 |
|------|------|
| 비유 | **인력파견 업체** — "이 프로젝트 해줘" 하면 알맞은 팀을 구성해서 투입 |
| 호출법 | "팀 구성해줘", "team assemble", "전문가 팀으로 해줘", "병렬로 전문가 팀" |
| 실행 방식 | TeamCreate로 실제 별도 에이전트 생성 → 병렬/순차 실행 → 결과 종합 |

**핵심 차이:**
- AGENTS.md: 내가 역할을 **직접 설계** → 반복 사용 가능
- team-assemble: AI가 작업을 분석해서 **알아서 설계** → 일회성 프로젝트에 적합

```
작업 분석 → 팀 구성 제안 → 사용자 승인 → 팀 생성 + 실행 → 결과 종합 + 정리
```

### 3. team-orchestrator — 전문가 관점으로 토론 시뮬레이션

실제 에이전트를 만드는 게 아니라, **Claude가 여러 전문가 역할을 연기하며 토론**합니다.

| 항목 | 내용 |
|------|------|
| 비유 | **회의 퍼실리테이터** — "Product는 이렇게 보고, Growth는 저렇게 봅니다" |
| 호출법 | "팀 미팅", "여러 관점에서 분석해줘", "Product와 Growth 관점으로" |
| 멤버 | product-leader, growth-expert, ceo-advisor, data-scientist, design-director, engineering-lead, marketing-director, strategy-consultant |

**핵심 차이:**
- team-assemble: 실제 에이전트가 **파일/코드를 만드는** 실행 도구
- team-orchestrator: 여러 전문가 관점으로 **생각하는** 사고 도구

**미팅 패턴:**

| 패턴 | 목적 | 예시 |
|------|------|------|
| 의사결정 | Go/No-go 결정 | "이 기능 만들까?" |
| 전략 세션 | 장기 방향 설정 | "성장 전략은?" |
| 문제 해결 | 특정 문제 진단 | "이탈률이 올라가고 있어" |
| 트레이드오프 | 상충 우선순위 해결 | "속도 vs 품질?" |

### 3가지 도구 정리

```
📋 AGENTS.md ─── "우리 팀 역할은 이렇다" (설정)
       │
       ├──▶ 🔧 team-assemble ─── "이 일을 팀으로 나눠서 실행해줘" (실행)
       │    실제 에이전트 생성, 파일/코드 산출물
       │
       └──▶ 💬 team-orchestrator ─── "전문가들이 토론하면?" (사고)
            관점 시뮬레이션, 의사결정 지원
```

---

## EXECUTE

---

### STEP 8-1: Agent Teams로 제안서 파이프라인 TF 구성

## WHY

AGENTS.md는 **반복 가능한 팀 구조**를 만드는 것입니다. 한 번 설계하면 어떤 제안서에도 같은 품질 파이프라인을 적용할 수 있습니다.

## EXECUTE

📋 아래를 복사해서 입력하세요:

    SK하이닉스에서 "반도체 엔지니어를 위한 AI 활용" 교육을 요청했어.

    Agent Teams로 3명의 TF를 구성해서 제안서를 만들어줘:

    1. 시장조사 에이전트
       - 반도체 산업의 AI 활용 동향
       - 경쟁사 교육 프로그램 분석
       - 최신 AI 교육 트렌드

    2. 제안서 작성 에이전트
       - 리서치 결과를 바탕으로 제안서 초안
       - 우리 팀 CLAUDE.md 규칙 따르기
       - 6섹션 구조

    3. QA 에이전트
       - 논리 흐름 검증
       - 누락 항목 체크
       - 톤앤매너 일관성 확인

    먼저 AGENTS.md를 작성하고, 실제로 End-to-End 실행해줘.

Agent Teams가 순차적으로 작업하는 과정을 관찰하세요. 리서치 → 초안 → 검수 흐름이 자동으로 진행됩니다.

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "AGENTS.md의 역할은 무엇인가요?",
    "header": "Quiz 8-1",
    "options": [
      {"label": "각 에이전트의 역할, 전문 분야, 접근 권한을 정의하는 팀 매뉴얼", "description": "프로젝트 TF의 직무기술서"},
      {"label": "Claude Code의 시스템 설정 파일", "description": "시스템 설정?"},
      {"label": "에이전트의 대화 로그", "description": "로그 파일?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. **AGENTS.md**는 각 에이전트의 역할, 전문 분야, 접근 권한을 정의하는 파일입니다. 한 번 작성하면 어떤 프로젝트에도 같은 파이프라인을 반복 적용할 수 있습니다.

## LEADER-TIP

> 💡 이 구조를 **{team} 정규 워크플로우**로 만들면, 모든 제안서가 3중 검증을 거치게 됩니다. 주니어 컨설턴트도 이 TF를 쓰면 시니어급 제안서를 낼 수 있습니다.

---

### STEP 8-2: team-assemble로 동적 팀 실행

## WHY

AGENTS.md는 미리 설계해야 하지만, team-assemble은 **작업을 주면 알아서 팀을 구성**합니다. 일회성 프로젝트나 "어떤 팀 구성이 좋을지 모르겠을 때" 유용합니다.

## EXECUTE

📋 아래를 복사해서 입력하세요:

    팀 구성해줘.

    삼성전자 DS부문에서 "AI 반도체 설계 교육" RFP를 보내왔어.
    RFP 마감이 이번 주 금요일이라 빠르게 움직여야 해.

    필요한 작업:
    1. AI 반도체 설계 교육 시장 리서치 (경쟁사, 트렌드)
    2. 커리큘럼 초안 설계 (2일 16시간 구성)
    3. 강사 후보 3명 프로필 정리
    4. 제안서 초안 작성 (CLAUDE.md 규칙 적용)

    병렬로 할 수 있는 건 병렬로 하고, 최대한 빠르게 완성해줘.

**관찰 포인트:**
- team-assemble이 작업을 분석하여 팀 구성을 **제안**하는 과정
- 사용자 **승인 후** 실제 에이전트가 생성되는 과정
- 독립 작업(리서치, 강사 프로필)은 **병렬**, 의존 작업(제안서)은 **순차** 실행
- 모든 결과가 **종합 보고**되는 과정

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "AGENTS.md와 team-assemble의 핵심 차이는?",
    "header": "Quiz 8-2",
    "options": [
      {"label": "AGENTS.md는 내가 직접 설계, team-assemble은 AI가 알아서 구성", "description": "설계 주체가 다르다"},
      {"label": "같은 기능의 다른 이름이다", "description": "이름만 다른 같은 도구?"},
      {"label": "team-assemble이 더 정확하다", "description": "정확도 차이?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. AGENTS.md는 **내가 역할을 직접 설계**하여 반복 사용하는 팀 매뉴얼이고, team-assemble은 **AI가 작업을 분석해서 즉석으로 팀을 구성**합니다. 정해진 워크플로우에는 AGENTS.md, 일회성 프로젝트에는 team-assemble이 적합합니다.

## LEADER-TIP

> 💡 team-assemble은 **"어떤 팀 구성이 좋을지 모르겠을 때"** 가장 유용합니다. AI가 작업을 분석해서 최적의 팀 구성을 제안하니까요. 처음 Agent Teams를 도입할 때 team-assemble로 시작하고, 반복되는 패턴이 보이면 AGENTS.md로 고정화하세요.

---

### STEP 8-3: team-orchestrator로 전문가 토론

## WHY

8-1에서 제안서를 만들었고, 8-2에서 빠르게 실행했습니다. 이제 **"이 제안서가 진짜 좋은가?"**를 검증해야 합니다. team-orchestrator는 여러 전문가 관점으로 토론을 시뮬레이션합니다. {group_leader} 그룹장님 앞에서 발표하기 전에, **AI로 미리 "품평회"를 여는 것**입니다.

## EXECUTE

📋 아래를 복사해서 입력하세요:

    방금 만든 제안서를 전문가 팀 미팅으로 검증해줘.

    참석자:
    - Product Leader: 이 교육 상품의 시장 경쟁력과 차별화 포인트
    - Growth Expert: 이 제안이 수주되면 후속 확장 가능성
    - Strategy Consultant: 삼성전자 DS부문의 전략적 맥락에서 제안의 적합성

    각 전문가 관점을 보여주고,
    의견이 엇갈리는 부분은 트레이드오프를 분석해줘.
    마지막에 종합 추천을 내려줘.

**관찰 포인트:**
- 각 전문가가 **고유한 프레임워크**로 분석하는 과정
- 전문가 간 **의견 충돌**이 나타나는 부분 (이게 핵심 인사이트)
- 충돌을 **트레이드오프**로 분석하는 과정
- 최종 **종합 추천**이 나오는 과정

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "team-orchestrator와 team-assemble의 핵심 차이는?",
    "header": "Quiz 8-3",
    "options": [
      {"label": "team-orchestrator는 관점 시뮬레이션(사고 도구), team-assemble은 실제 팀 실행(실행 도구)", "description": "생각 vs 실행"},
      {"label": "team-orchestrator가 더 많은 에이전트를 만든다", "description": "에이전트 수 차이?"},
      {"label": "같은 기능이지만 속도가 다르다", "description": "속도 차이?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. team-orchestrator는 **여러 전문가 관점으로 생각하는 사고 도구**이고, team-assemble은 **실제 에이전트를 만들어서 작업을 실행하는 도구**입니다. 제안서를 **만들 때**는 team-assemble, 제안서를 **검증할 때**는 team-orchestrator가 적합합니다.

## LEADER-TIP

> 💡 **{name} {title}님을 위한 리더 팁**
>
> 3가지 도구를 조합하면 **완전한 제안서 파이프라인**이 됩니다:
>
> 1. 📋 **AGENTS.md** — {team}의 표준 제안서 프로세스를 팀 매뉴얼로 고정
> 2. 🔧 **team-assemble** — 급한 RFP가 오면 즉석 팀으로 빠르게 초안 실행
> 3. 💬 **team-orchestrator** — 제출 전 전문가 품평회로 최종 검증
>
> **팀 적용 순서 추천:**
> - 먼저 team-assemble로 시작 (팀 구조를 몰라도 됨)
> - 반복 패턴이 보이면 AGENTS.md로 고정화
> - 중요 제안서는 team-orchestrator로 최종 검증
>
> 🤝 **AI 설계자 배지를 획득했습니다!** 이제 AI TF를 설계하고 운영할 수 있습니다.
