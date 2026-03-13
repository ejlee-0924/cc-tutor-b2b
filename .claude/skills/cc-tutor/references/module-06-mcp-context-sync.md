# Module 6: MCP + Context Sync

> 공식 문서: https://code.claude.com/docs/ko/mcp

## WHY

{name} {title}님, 제안서 쓸 때 고객사 정보가 어디에 흩어져 있나요?

슬랙에서 고객 요청을 확인하고, 노션에서 이전 제안서를 찾고, 메일에서 일정을 확인하고... **MCP는 이 모든 곳을 Claude가 직접 연결해서 정보를 가져오게 하는 파이프**입니다.

**Before:** 슬랙·노션·메일 3개 채널을 뒤져서 고객 정보 취합 (30분+)
**After:** "고객사 관련 정보 모아줘" 한 마디로 자동 수집

## EXPLAIN

### MCP란?

> 📖 glossary 참조: MCP = "CRM 연동"

MCP(Model Context Protocol)는 Claude가 외부 시스템과 실시간으로 소통할 수 있게 해주는 파이프라인입니다.

```
{name} {title}님: "고객사 교육 관련 정보 모아줘"
    │
    ▼
Claude Code
    │
    ├──▶ Slack MCP ──▶ #고객사 채널 대화 수집
    ├──▶ Notion MCP ──▶ 이전 제안서/회의록 검색
    └──▶ Gmail MCP ──▶ 고객 메일 확인
    │
    ▼
통합 문서 생성
```

### 주요 MCP 서버

| MCP 서버 | B2B 비유 | 활용 예시 |
|----------|---------|----------|
| Slack | 팀 대화방 연결 | "고객 채널에서 요청사항 가져와" |
| Notion | 사내 위키 연결 | "이전 제안서 찾아줘" |
| Gmail | 메일함 연결 | "고객 메일에서 일정 확인해줘" |
| Calendar | 일정표 연결 | "다음 주 고객 미팅 확인해줘" |

### MCP 설정법

```bash
# MCP 서버 추가
claude mcp add slack -- npx -y @anthropic/mcp-slack

# 설치된 MCP 서버 확인
claude mcp list
```

### Context Sync란?

> 📖 glossary 참조: Context Sync = "여러 소스에서 한 문서로 통합"

여러 MCP 소스에서 가져온 정보를 **하나의 문서로 정리**하는 것입니다. 고객사별로 흩어진 정보를 제안서 작성에 바로 쓸 수 있게 모아줍니다.

| 단계 | 설명 |
|------|------|
| 1. 수집 | 여러 MCP 소스에서 관련 정보 가져오기 |
| 2. 정제 | 중복 제거, 시간순 정리 |
| 3. 통합 | 하나의 구조화된 문서로 정리 |

## EXECUTE

아래 순서대로 실행해보세요:

---

### 실습 1: MCP 서버 목록 확인

Claude Code에 이렇게 요청하세요:

📋 아래를 복사해서 입력하세요:

    현재 연결된 MCP 서버가 뭐가 있는지 보여줘.

---

### 실습 2: Slack MCP 활용 (Slack이 연결된 경우)

> 💡 모듈 2에서 넣은 RFP의 고객사를 기억하시죠? 그 고객 관련 정보를 MCP로 수집합니다.

📋 아래를 복사해서 입력하세요:

    슬랙에서 모듈 2 RFP의 고객사 관련 최근 대화를 검색해서 정리해줘.

Slack MCP가 없다면 Claude에게 시뮬레이션을 요청하세요:

📋 아래를 복사해서 입력하세요:

    Slack MCP가 연결되어 있다고 가정하고,
    모듈 2에서 다룬 RFP 고객사 관련 정보를 수집하는 시나리오를 보여줘.
    어떤 채널에서 어떤 정보를 가져올 수 있는지 시뮬레이션해줘.

---

### 실습 3: Context Sync 체험

📋 아래를 복사해서 입력하세요:

    proposals 폴더의 제안서 초안을 보강하기 위해
    아래 소스에서 정보를 모아서 한 문서로 정리해줘:

    1. RFP 원문의 핵심 요구사항
    2. proposals 폴더의 기존 제안서 내용
    3. 해당 산업/고객사의 최신 교육 트렌드

    제안서 보강에 바로 쓸 수 있는 "고객 브리핑 문서" 형태로 정리해줘.

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "MCP의 역할은 무엇인가요?",
    "header": "Quiz 6-1",
    "options": [
      {"label": "Claude가 외부 도구(Slack, Notion 등)와 연결되는 파이프", "description": "실시간으로 외부 시스템의 정보를 가져옴"},
      {"label": "Claude의 내부 메모리를 확장하는 기능", "description": "메모리 관련?"},
      {"label": "Claude의 응답 속도를 높이는 기능", "description": "성능 관련?"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. MCP는 Claude가 Slack, Notion, Gmail 등 **외부 시스템과 실시간으로 연결되는 파이프**입니다. {name} {title}님의 업무 도구들을 Claude가 직접 활용할 수 있게 해줍니다.

```json
AskUserQuestion({
  "questions": [{
    "question": "여러 소스의 정보를 한 문서로 모으는 것을 뭐라고 하나요?",
    "header": "Quiz 6-2",
    "options": [
      {"label": "Context Sync", "description": "여러 소스에서 한 문서로 통합"},
      {"label": "Auto Memory", "description": "Claude가 스스로 기록하는 메모"},
      {"label": "MCP", "description": "외부 연결 파이프"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번. Context Sync는 여러 MCP 소스에서 가져온 정보를 **하나의 구조화된 문서로 통합**하는 과정입니다.

## LEADER-TIP

> 💡 **{name} {title}님을 위한 리더 팁**
>
> - **팀 전체가 같은 MCP 설정**을 쓰면, 누가 제안서를 써도 같은 정보 소스에 접근합니다
> - 고객사별 Context Sync를 자동화하면 **제안서 준비 시간이 절반**으로 줄어듭니다
> - MCP 설정은 팀 공용 CLAUDE.md에 가이드를 넣어두면, 새 팀원도 바로 설정할 수 있습니다
> - {leader} 팀장님에게 "팀 MCP 표준 설정"을 제안해보세요 — 정보 접근이 균일해집니다
