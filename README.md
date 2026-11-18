# 싱글 에이전트에서 멀티 에이전트로 (Codex 실습)

Codex에서 에이전트 하나로 일을 시켜 보고, 서브에이전트(TOML)를 직접 만들어 여럿이 나눠 하게 바꾸는 실습 폴더입니다.
소재는 가상 프라이빗뱅크의 펀드 질의 응답 도우미입니다. JP모건 프라이빗뱅크의 리서치 도우미 "Ask David"의 구조를 본떴습니다. 회사, 펀드, 사람, 숫자는 모두 가상입니다.

## 받는 방법

1. 이 화면 위쪽의 초록색 **Code** 버튼을 누르고 **Download ZIP**을 고릅니다. 로그인은 필요 없습니다.
2. 내려받은 `agent-lab-main.zip`의 압축을 풉니다.
3. ChatGPT 앱의 Codex 화면에서 **폴더 열기**로 `agent-lab-main` 폴더를 엽니다. 폴더를 신뢰할지 물으면 신뢰를 고릅니다.

따라 하는 순서는 [guide.pdf](guide.pdf)에 있습니다. 내려받은 폴더 안에도 같은 파일이 들어 있습니다.

## Claude Code로 할 때

같은 실습을 Claude Code에서도 할 수 있습니다. 자료와 실습 순서는 같고, 서브에이전트와 스킬을 넣는 곳과 파일 형식만 다릅니다.

1. 위와 같은 방법으로 폴더를 받습니다.
2. Claude Code에서 `agent-lab-main` 폴더를 엽니다. 터미널이라면 그 폴더에서 `claude`를 실행합니다.
3. [guide_claude_code.pdf](guide_claude_code.pdf)를 따라 합니다.

| | Codex | Claude Code |
|---|---|---|
| 따라 할 가이드 | `guide.pdf` | `guide_claude_code.pdf` |
| 폴더 지침 | `AGENTS.md` | `CLAUDE.md`가 `AGENTS.md`를 불러옴 |
| 서브에이전트 | `.codex/agents/이름.toml` | `.claude/agents/이름.md` |
| 스킬 | `.agents/skills/이름/SKILL.md` | `.claude/skills/이름/SKILL.md` |
| 빈 틀 | `templates/agent_template.toml` | `templates/agent_template.md` |
| 가져와서 고칠 원본 | `originals/` | `originals/claude/` |
| 예시 답안 | `answers/agents/`, `answers/agents_md_*.md` | `answers/claude/` |
| 스킬 예시 답안 | `answers/skills/` | `answers/skills/` (같은 파일) |

## 실습

| 실습 | 전략 | 무엇을 하나 |
|---|---|---|
| 1 | 싱글 에이전트 만들기 | 그냥 맡겨 보고, 스킬과 TOML로 에이전트 하나를 만들어 다시 한다 |
| 2 | 멀티 에이전트 팀 | 서브에이전트를 만들어 같은 일을 나눠서 다시 한다. 평가자–최적화자, 병렬 조사, 오케스트레이터–워커 |
| 3 | 비교와 반례 | 싱글과 멀티를 비교하고, 멀티가 안 맞는 일을 본다 |
| 4 | 분류해서 넘기기 | 새로 들어온 질문을 먼저 분류하고, 답해도 되는 질문만 서브에이전트에게 넘긴다 |

## 폴더

| 위치 | 내용 |
|---|---|
| `AGENTS.md` | 이 폴더에서 일하는 모든 에이전트가 읽는 지침과 답변 메모 형식 |
| `data/` | PB 질문 10건, 답변 작성 기준 14개, 펀드 24개의 기본 정보와 월 수익률, 문서 73개 |
| `inbox/` | 실습 4에서 쓰는 새 질문 12건과 질문 처리 기준 |
| `.codex/agents/` | 서브에이전트 TOML을 넣는 곳. 처음에는 비어 있습니다 |
| `CLAUDE.md`, `.claude/` | Claude Code로 할 때 쓰는 지침 파일과 서브에이전트·스킬 폴더 |
| `.codex/config.toml` | 동시에 호출할 수 있는 서브에이전트 수 |
| `.agents/skills/` | 스킬을 넣는 곳. 처음에는 비어 있습니다 |
| `originals/`, `templates/` | 가져와서 고칠 원본 TOML 2개, 서브에이전트 빈 틀 |
| `memo/`, `research/`, `review/` | 결과 파일이 저장되는 곳 |
| `answers/` | 막혔을 때 보는 예시 답안 |

`originals/`의 TOML은 VoltAgent/awesome-codex-subagents(MIT)에서, `originals/claude/`의 파일은 VoltAgent/awesome-claude-code-subagents(MIT)에서 가져왔습니다.
