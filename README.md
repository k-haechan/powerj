# powerj — 극한 계획/실행 앱

하루를 **프로세스 체인**으로 설계하고, 각 프로세스에 **정량 목표**를 걸고, 실행은 **타이머·방해금지**로 측정하며, 전환마다 **달성률·실패 원인 검증을 강제**하고, 하루를 **일기+대시보드로 마감**해 내일에 되먹이는 앱.

**종합 페이지 (GitHub Pages)**: `index.html` — 문제 · 여정 · 디자인시스템 · 화면 · 와이어플로우

## 구조

```
index.html                      종합 허브
docs/
  problem.md / problem.html     문제 정의
  journey.md / journey.html     고객 여정지도 (페르소나 4)
  wireframe.html                와이어플로우 보드 (F0–F4, 실제 화면 축소 삽입)
design/
  DESIGN.md / DESIGN.html       디자인시스템 스펙 — 마켓 스탠다드 라이트 v2 (단일 진실 원천)
  PROPOSAL.md                   방향 결정 과정 아카이브 (v1 → v2 개정 경위)
  sample.html                   방향 검토 시안 5종 (목업 — 레이아웃 복사 금지)
  system/
    tokens.css                  디자인 토큰 SoT
    components.css              공유 컴포넌트
    assets/mascot/              심지 마스코트 3-상태 PNG (rest·idle·gold)
    screens/S-01 ~ S-15         단독 실행 화면 15종 (온보딩~설정 · 완벽한 하루 · 빈 기록)
```

## 디자인시스템 핵심 규칙

- 달성 = **ember heat** (채워지는 게 아니라 뜨거워진다) · **100% = gold 전용**
- **실패는 데이터** — 빨강 금지, slate로 렌더 · `--danger`는 파괴적 액션 전용
- 숫자는 전부 IBM Plex Mono(tabular) · 한글 UI는 Wanted Sans · 일기만 MaruBuri
- 마스코트 **심지(Simji)** — 배 속 하트가 §5 밴딩(휴지 slate · 진행 ember · 100% gold)을 나른다
