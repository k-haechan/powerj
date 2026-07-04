# powerj

극한 계획/실행 앱. 하루를 프로세스 체인으로 설계하고, 각 프로세스에 정량 목표를 걸고, 실행은 타이머·방해금지 모드로 측정하며, 전환 시 달성률·실패 원인 검증을 강제하고, 하루를 일기+대시보드로 마감한다.

- 제품 문제 정의: `docs/problem.md`
- 고객 여정지도(페르소나 4종): `docs/journey.md`
- 디자인 시스템: `design/DESIGN.md` (엠버 크로노그래프 — B안 확정, 시스템만 차용·페이지는 재설계 예정)
- 플랫폼: 모바일 우선
- 기억될 한 가지(memorable thing): **매일 쌓이는 성취의 쾌감** — 하루 마감 대시보드가 주는 보상감

## Skill routing

When the user's request matches an available skill, invoke it via the Skill tool. When in doubt, invoke the skill.

Key routing rules:
- Product ideas/brainstorming → invoke /office-hours
- Strategy/scope → invoke /plan-ceo-review
- Architecture → invoke /plan-eng-review
- Design system/plan review → invoke /design-consultation or /plan-design-review
- Full review pipeline → invoke /autoplan
- Bugs/errors → invoke /investigate
- QA/testing site behavior → invoke /qa or /qa-only
- Code review/diff check → invoke /review
- Visual polish → invoke /design-review
- Ship/deploy/PR → invoke /ship or /land-and-deploy
- Save progress → invoke /context-save
- Resume context → invoke /context-restore
- Author a backlog-ready spec/issue → invoke /spec

## Design System

Always read design/DESIGN.md before making any visual or UI decisions.
All font choices, colors, spacing, and aesthetic direction are defined there.
Do not deviate without explicit user approval.
In QA mode, flag any code that doesn't match design/DESIGN.md.
Note: design/sample.html is a throwaway direction mockup — do NOT copy its layouts; build screens fresh on the DESIGN.md system.
