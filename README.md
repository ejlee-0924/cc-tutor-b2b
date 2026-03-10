# CC-Tutor: 기업교육 컨설턴트를 위한 Claude Code 학습 튜터

비개발자 기업교육 컨설턴트(파트장/팀장)가 Claude Code를 실무에 활용할 수 있도록 안내하는 **10모듈 인터랙티브 학습 스킬**입니다.

## Quick Start

### 1. 스킬 설치

```bash
npx skills add ejlee-0924/cc-tutor-b2b
```

> 또는 이 저장소를 클론하여 `.claude/skills/cc-tutor/` 폴더를 프로젝트에 복사해도 됩니다.

### 2. 조직도 파일 준비 (선택)

개인화된 학습을 위해 `~/work/docs/org-context.md`에 조직도를 작성합니다.
없어도 학습은 가능하며, 이름/팀/직책을 수동으로 입력할 수 있습니다.

### 3. 학습 시작

Claude Code에서 아래 중 하나를 입력하세요:

```
/cc-tutor
학습
튜터
```

## 커리큘럼

### Essential (순차 해금)

| # | 모듈 | 배우는 것 | 배지 |
|---|------|----------|------|
| 1 | Setup & 첫 대화 | Claude Code 설치, 기본 대화 | 🌱 입문자 |
| 2 | 파일 다루기 + 스마트 조작법 | Read/Write/Glob/Grep, Plan 모드, Think harder | — |
| 3 | CLAUDE.md | 팀 규칙 설정, Auto Memory | 📄 실무 기초 |
| 4 | Skill 사용 | 스킬 설치/호출, Pre-built 스킬 | — |
| 5 | Subagent | 병렬 작업, 에이전트 지시 | 🏆 AI 실무자 |

### Advanced (자유 선택)

| # | 모듈 | 배우는 것 | 배지 |
|---|------|----------|------|
| 6 | MCP + Context Sync | 외부 시스템 연동 | — |
| 7 | Plugin + Clarify | 요구사항 구조화 | 📋 분석가 |
| 8 | skill-creator | 나만의 스킬 만들기 | ⚡ AI 빌더 |
| 9 | Agent Teams | AI TF 구성, 의사결정 검증 | 🤝 AI 설계자 |
| 10 | 팀 전파 + GitHub | 팀 배포, 지식 축적 | 🎖️ AI 전도사 |

## 학습 방식

- **2턴 STOP 프로토콜**: 설명+실습 → 퀴즈+피드백, 한 모듈씩 차근차근
- **조직 맥락 개인화**: 학습자의 팀, 직책, 동료 이름이 시나리오에 반영됩니다
- **진도 자동 저장**: `.cc-tutor-progress.json`에 학습 현황이 기록됩니다

## 사전 요구사항

- [Claude Code](https://claude.ai/code) 설치
- Node.js 18+ (npx 사용 시)

## 다른 도메인 버전

| 대상 | 저장소 |
|------|--------|
| **기업교육 컨설턴트** | 이 저장소 |
| HR 채용 담당자 | [cc-tutor-hr](https://github.com/ejlee-0924/cc-tutor-hr) |
| B2B 마케터 | [cc-tutor-marketing](https://github.com/ejlee-0924/cc-tutor-marketing) |

> 3개 버전 모두 동일한 10모듈 구조이며, 실습 시나리오와 용어 비유만 도메인에 맞게 다릅니다.

## 라이선스

MIT
