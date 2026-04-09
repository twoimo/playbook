# krafton-ai-fde-2h-playbook

크래프톤 AI FDE 2시간 현장 테스트에서 **심사자가 2분 내 검증 가능한 MVP 이상 결과물**을 만드는 것을 목표로 한 OMC(oh-my-claudecode) 실전용 플레이북입니다.

> **완전한 결과물보다, 빠르게 검증 가능한 돌아가는 결과물이 더 강하다.**

---

## Quick Start

### 1) 문제를 받으면 먼저 딥 인터뷰
문제가 애매하거나 범위가 넓어 보이면 아래를 먼저 실행합니다.

```text
/deep-interview "
I am taking a 2-hour onsite Krafton AI FDE test.
Before coding, clarify the task for fastest MVP delivery.

Task:
[여기에 시험 문제 원문 전체 붙여넣기]

Your job:
- Identify must-have requirements
- Identify nice-to-have requirements
- Identify likely non-goals for a 2-hour attempt
- Surface hidden assumptions
- Highlight evaluation-risk areas
- Recommend the smallest demoable happy path
- Suggest what should be carried into planning
- Keep the result concise and execution-oriented
- Output in Korean
"
```

---

### 2) 같은 세션에서 바로 RALPLAN
딥 인터뷰 결과를 별도 복붙하지 않고, **현재 세션 문맥**을 그대로 활용합니다.

```text
/ralplan "
I am taking a 2-hour onsite Krafton AI FDE test.
Create the minimum viable execution plan for this task.

Original task:
[여기에 시험 문제 원문 전체 붙여넣기]

Use the deep-interview result from the current session as the authoritative basis for:
- scope
- assumptions
- non-goals
- MVP boundary
- demo scenario

Planning goals:
- Compress the task into the smallest shippable MVP
- Freeze the MVP boundary clearly
- Define must-have features only
- Define explicit non-goals for this 2-hour attempt
- Define the single best demoable happy path
- Define minimum architecture and stable interfaces
- Define the simplest implementation order
- Define likely blockers and fallback paths
- Define what must appear in README.md and FINAL_SUMMARY.md

Output in Korean with this exact structure:
1. Must-have requirements
2. Nice-to-have requirements
3. Non-goals
4. Assumptions
5. MVP boundary
6. Demo scenario under 2 minutes
7. Minimum architecture
8. Stable interfaces
9. Step-by-step implementation order
10. Blockers and fallback strategies
11. Final delivery checklist

Be concise, practical, and execution-oriented.
"
```

---

### 3) 같은 세션에서 바로 메인 RALPH 실행
핵심 구현 단계입니다.

```text
ralph: You are my execution lead for a 2-hour onsite Krafton AI FDE test.
Your goal is not elegance. Your goal is a working, reviewable MVP-plus result within the time limit.

Read the task below and execute aggressively.

[TASK START]
Original task:
[여기에 시험 문제 원문 전체 붙여넣기]
[TASK END]

Use the deep-interview result and the ralplan result from the current session as the authoritative basis for:
- scope definition
- assumptions
- non-goals
- MVP boundary
- implementation order
- demo scenario
- fallback decisions

Do not expand beyond them unless absolutely necessary to make the demo work.

Core mission:
- Optimize for a working demo, not completeness.
- Do not ask unnecessary questions.
- If something is ambiguous, follow the current session planning artifacts first.
- If something is still ambiguous, make the most reasonable assumption, state it briefly, and continue.
- Prefer the simplest architecture and the fewest dependencies.
- Prefer local, deterministic, mockable solutions over fragile external integrations.
- If blocked for more than 5 minutes, choose the simpler fallback path immediately.
- Do not gold-plate.
- Do not refactor unless it directly helps delivery.
- Keep core interfaces stable once the first vertical slice is defined.
- Reviewer should be able to verify the result in under 2 minutes.
- Optimize everything for that constraint.
- Do not wait for my approval. Make reasonable assumptions and execute.

Language rules:
- All reviewer-facing documentation must be written in Korean.
- README.md must be written in Korean.
- FINAL_SUMMARY.md must be written in Korean.
- Demo steps, setup instructions, execution notes, and user-facing explanations must be written in Korean.
- Do not write reviewer-facing documentation in English.
- Keep code, variable names, file names, function names, API paths, schema names, and technical identifiers in English unless Korean is clearly better.

Success criteria:
1. One end-to-end happy path works and can be demonstrated in under 2 minutes.
2. The project can be run with minimal setup.
3. Obvious invalid inputs are handled cleanly.
4. There is a concise README in Korean with setup, run, and demo steps.
5. There is a final summary in Korean of:
   - what works,
   - what is stubbed or mocked,
   - what was intentionally omitted,
   - next improvements if given more time.

Required execution sequence:

Phase 1: Confirm scope from current session planning artifacts
- Restate the MVP boundary briefly
- Restate the chosen demo scenario briefly
- Start implementation immediately after that

Phase 2: Freeze the minimum design
- Respect the minimum architecture and stable interfaces already established
- Do not redesign unless necessary to unblock the demo

Phase 3: Build the vertical slice first
- Implement the smallest end-to-end path first
- Get it running as early as possible
- Do not expand scope until this path works

Phase 4: Stabilize
- Add only essential validation, error handling, and one or two critical edge cases
- Add a smoke test or verification script if possible
- Produce README.md in Korean with exact commands
- Make the demo path obvious

Phase 5: Polish only after demo safety is secured
- Improve naming, logs, UX text, and tiny issues only if the core demo is already safe

Parallelization rule:
- Do NOT parallelize at the beginning
- Only after the first end-to-end slice works, spawn at most 3 workers for isolated tasks like:
  1. README/demo docs
  2. smoke test / verification
  3. input validation / error messages
- Those workers must not break core interfaces

Time strategy:
- T+0 to T+10: confirm scope and freeze minimum design
- T+10 to T+60: build the core vertical slice
- T+60 to T+90: stabilize and verify
- T+90 to T+120: no new major features; focus only on demo reliability, README, summary, and bug fixes

Output style:
- Be concise and execution-focused
- After each milestone, report only:
  - current status
  - what works
  - current blocker if any
  - next immediate action

Hard constraints:
- No broad rewrites
- No speculative architecture
- No unnecessary tests beyond smoke-level unless trivial
- No deep dependency setup unless absolutely required
- No hidden incomplete state
- Always leave the repo runnable

Fallback rule:
- If progress is slow, cut scope immediately
- Stub or mock external, slow, or unreliable parts
- Keep only the smallest demoable happy path
- Prioritize runnable code + Korean README + Korean FINAL_SUMMARY over extra features

Final deliverables before stopping:
- runnable code
- README.md
- optional smoke test / verification script
- FINAL_SUMMARY.md

Begin now.
```

---

### 4) 꼬이면 바로 긴급 축소
40~50분이 지났는데 핵심 흐름이 안 붙었거나, 구현만 늘어나고 데모가 불안하면 바로 넣습니다.

```text
Reset priorities right now.
Cut anything non-essential.
Keep only the smallest demoable happy path.
Follow the MVP boundary already defined in the current session planning artifacts.
Do not add any new major feature.
Stub or mock external or slow parts.
Focus on getting one end-to-end flow working, plus README.md in Korean and FINAL_SUMMARY.md in Korean.
Reviewer must be able to verify the result in under 2 minutes.
```

---

## 한눈에 보는 운영 원칙

- 처음부터 병렬화하지 않는다.
- 처음 10분 안에 범위를 자른다.
- 해피패스 1개를 먼저 끝까지 연결한다.
- 외부 연동이 막히면 바로 mock/stub로 전환한다.
- 90분 이후에는 새 기능보다 안정화와 문서화에 집중한다.
- 문서화는 한국어, 코드와 식별자는 영어로 유지한다.

---

## 2시간 운영 감각

### 0~10분
- 문제 이해
- 딥 인터뷰
- 범위 압축
- RALPLAN으로 MVP 경계 확정

### 10~60분
- 해피패스 1개를 끝까지 구현
- 가장 작은 세로 한 줄(vertical slice) 먼저 완성

### 60~90분
- 입력 검증
- 에러 처리
- smoke test
- 실행 확인

### 90~120분
- 새 기능 추가 중단
- README 정리
- FINAL_SUMMARY 정리
- 데모 실패 포인트 제거

---

## 세션 운용 팁

- `deep-interview → ralplan → ralph`는 가능하면 **한 세션에서 연속 실행**합니다.
- 중간에 다른 큰 작업을 섞지 않는 편이 좋습니다.
- 출력이 흔들리면 새 세션에서 다시 1단계부터 짧게 재시작하는 편이 낫습니다.
- 정말 불안하면 전체 복붙 대신 아래 4줄 요약만 추가로 넘기면 됩니다.

```text
Deep-interview summary:
- Must-have: [핵심 기능]
- Non-goals: [버릴 것]
- Assumptions: [가정]
- Happy path: [2분 데모 시나리오]
```

---

## 권장 제출 상태

- 저장소가 실행 가능함
- 핵심 해피패스 1개가 동작함
- README에 실행/데모 방법이 한국어로 정리됨
- FINAL_SUMMARY에 동작 범위와 생략 범위가 정리됨
- 외부 연동이 불안정하면 stub/mock임을 명시함

---

## 추천 레포 구성

```text
krafton-ai-fde-2h-playbook/
└─ README.md
```
