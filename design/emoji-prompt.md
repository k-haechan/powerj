# powerj 커스텀 이모지/아이콘 생성 프롬프트

> 이미지 생성 모델(GPT-Image, Midjourney, Imagen 등)에 그대로 투입하는 제작 스펙.
> 시스템 이모지를 대체하는 **자체 아이콘 세트 18종** — 스타일·팔레트·앵글이 하나의 세트로 읽혀야 한다.
> 기준 문서: `design/DESIGN.md` v2 (마켓 스탠다드 라이트).

---

## 1. 사용 환경 (왜 이 스펙인가)

- 아이콘은 **38×38px 라운드 사각(12px) 틴트 배지** 안에 놓인다 (`components.css .ico`). 작게 렌더되므로 실루엣이 단순해야 한다.
- 배경은 웜 오프화이트(`#F6F4EF`) 위의 흰 카드, 배지 틴트는 파스텔(아래 표). 아이콘이 틴트 위에서 또렷해야 한다.
- 탭바는 SVG 라인 아이콘으로 이미 교체됨 — **이 세트는 카테고리 배지·모드 카드·패널 뱃지 전용**이다.

## 2. 컨셉 한 줄

**"아침 햇살 아래의 소프트 클레이 오브제"** — 매트한 점토 질감의 미니 3D 오브젝트. 귀엽지만 유치하지 않고(얼굴·눈 금지), 장난감이 아니라 도구처럼 보인다. Structured·Routinery급 스토어 스크린샷에 그대로 올라갈 완성도.

## 3. 통일성 규칙 (전 아이콘 공통 — 프롬프트에 반드시 포함)

| 축 | 규칙 |
|---|---|
| 스타일 | soft 3D clay/matte plastic, 미묘한 그라데이션, 스티커식 외곽선 없음 |
| 카메라 | 정면, 위에서 12° 내려다봄 — **18종 전부 동일 앵글** |
| 조명 | 좌상단 45° 소프트 라이트 1개, 부드러운 셀프 섀도, **바닥 그림자 없음** |
| 구도 | 오브젝트 1개만, 캔버스 중앙, 캔버스의 78–82% 점유 |
| 배경 | 완전 투명 (PNG alpha) |
| 팔레트 | 시스템 토큰만: ember `#F07A2B` / hot `#FF9D4D` / gold `#E9B93B` / slate `#7189A8` / sky `#5B9BD5` / mint `#3FB58F` / coral `#EF7C66` / violet `#9B7EDE` / rose `#E77FB3` + 웜 뉴트럴 `#F6F4EF`·`#FFF`·`#211B12`. 아이콘당 주 색 1 + 보조 1~2 |
| 모서리 | 둥근 모서리, 뾰족한 꼭짓점 없음 (radius 감각은 시스템의 10–22px와 동일한 부드러움) |
| 금지 | 얼굴·눈·표정, 텍스트·숫자·로고, 아웃라인 스트로크, 광택 하이라이트 번쩍임, 배경 요소·바닥면, 드롭섀도, 실사 질감, 기본 이모지 모사 |

## 4. 마스터 프롬프트 (영어 — 모델 투입용)

아래 `{SUBJECT}`와 `{MAIN_COLOR}`만 표의 값으로 치환해 아이콘별로 생성한다.

```
A single {SUBJECT}, rendered as a soft 3D clay object in a matte plastic
finish with subtle smooth gradients. Minimal geometric form with fully
rounded corners, no sharp edges. Front view with a slight 12-degree
top-down angle. One soft light from the upper left, gentle self-shading,
NO ground shadow, NO floor. Main color {MAIN_COLOR}, with at most two
supporting colors from this exact palette: #F07A2B, #FF9D4D, #E9B93B,
#7189A8, #5B9BD5, #3FB58F, #EF7C66, #9B7EDE, #E77FB3, warm neutrals
#F6F4EF / #FFFFFF / #211B12. Clean silhouette readable at 38px.
Centered, occupying ~80% of the canvas, fully transparent background,
1024x1024 PNG. This icon belongs to a matched set of 18 app icons that
share the identical camera angle, lighting, material and palette —
consistency over creativity. Style reference: premium productivity app
category icons (Structured, Routinery), soft-clay 3D icon trend.
NO face, NO eyes, NO text, NO letters, NO numbers, NO outline stroke,
NO glossy highlights, NO background, NO drop shadow, NOT a photo,
NOT the default Apple/Google emoji.
```

## 5. 아이콘 인벤토리 — 18종

| # | 파일명 | 용도 (화면) | SUBJECT (영어 그대로 투입) | MAIN_COLOR | 배지 틴트 |
|---|---|---|---|---|---|
| 1 | `ico-wake` | 기상·새벽 (S-01/02/03/07/10) | rising sun with three short rays peeking over a soft horizon curve | #FF9D4D | mint |
| 2 | `ico-commute` | 이동·출근 (S-02/03/05/06/07/10) | front face of a cute rounded subway train car with two windows | #5B9BD5 | sky |
| 3 | `ico-work` | 업무 (S-02/03/07/10) | rounded briefcase with a soft handle | #9B7EDE | violet |
| 4 | `ico-lunch` | 점심·식사 (S-01/02/03/07) | rounded bento box with lid slightly open showing two compartments | #EF7C66 | coral |
| 5 | `ico-jit` | 즉석 슬롯 (S-02/03) | plump lightning bolt with rounded tips | #F07A2B | ember |
| 6 | `ico-write` | 글쓰기·자소서 (S-02/03/07/10) | chubby fountain pen nib at a slight diagonal | #E77FB3 | rose |
| 7 | `ico-diary` | 일기·하루 마감 (S-02/03/08) | closed notebook with a soft elastic band and rounded spine | #F07A2B | ember |
| 8 | `ico-plan` | 계획·조판 (S-01/03) | calendar page with two soft rings on top and one highlighted day dot | #5B9BD5 | sky |
| 9 | `ico-timer` | 타이머·시간 기준 (S-01/04/05) | rounded stopwatch with a single chunky hand at 2 o'clock | #F07A2B | ember |
| 10 | `ico-target` | 목표 기준 (S-04) | dartboard with three soft rings and a chunky dart in the center | #EF7C66 | coral |
| 11 | `ico-data` | 데이터·검증 (S-01/03/06) | three rounded vertical bars of increasing height on a soft base line | #7189A8 | slate |
| 12 | `ico-report` | 리포트 (S-09/10) | rising line chart as a thick rounded ribbon with an arrow tip | #F07A2B | ember |
| 13 | `ico-bot` | 자동 초안 (S-08) | minimal rounded robot head, blank smooth faceplate WITHOUT eyes, one small antenna | #7189A8 | slate |
| 14 | `ico-night` | 저녁·밤 프로세스 (S-10) | crescent moon with one tiny four-point star | #9B7EDE | violet |
| 15 | `ico-book` | 독서 목표 (목표 상세) | open book with gently curved pages and a ribbon bookmark | #3FB58F | mint |
| 16 | `ico-video` | 영상 목표 (목표 상세) | rounded play button — soft triangle inside a squircle | #EF7C66 | coral |
| 17 | `ico-code` | 커밋·개발 목표 (목표 상세) | two chunky rounded angle brackets with a small slash between | #7189A8 | slate |
| 18 | `ico-workout` | 운동 (S-03 즉석 슬롯) | small rounded dumbbell at a slight diagonal | #3FB58F | mint |

## 6. 완성 프롬프트 예시 (치환 결과 — 이 형태로 18번 실행)

**ico-commute:**
> A single front face of a cute rounded subway train car with two windows, rendered as a soft 3D clay object in a matte plastic finish with subtle smooth gradients. Minimal geometric form with fully rounded corners, no sharp edges. Front view with a slight 12-degree top-down angle. One soft light from the upper left, gentle self-shading, NO ground shadow, NO floor. Main color #5B9BD5, with at most two supporting colors from this exact palette: (…팔레트 동일…). Clean silhouette readable at 38px. Centered, occupying ~80% of the canvas, fully transparent background, 1024x1024 PNG. This icon belongs to a matched set of 18 app icons that share the identical camera angle, lighting, material and palette — consistency over creativity. (…금지 조항 동일…)

**ico-timer:** SUBJECT=`rounded stopwatch with a single chunky hand at 2 o'clock`, MAIN_COLOR=`#F07A2B` — 나머지 동일.

## 7. 생성·검수 워크플로

1. **기준 아이콘 먼저**: `ico-commute` 1종을 3~4변형 생성 → 마음에 드는 결과를 세트의 스타일 앵커로 확정.
2. 지원 모델이면 앵커 이미지를 **스타일 레퍼런스**로 첨부해 나머지 17종 생성 (`--sref`/이미지 참조). 미지원이면 마스터 프롬프트 문구만으로 진행.
3. **통일감 검수 체크리스트** (한 장에 18개를 나란히 놓고):
   - [ ] 앵글·조명 방향이 전부 동일한가
   - [ ] 재질(매트 클레이)이 동일한가 — 광택/실사 이탈 없음
   - [ ] 팔레트 이탈 색이 없는가 (스포이드로 확인)
   - [ ] 38px로 축소해도 실루엣이 구분되는가
   - [ ] 얼굴/텍스트/그림자 유입 없는가
4. **후처리**: 배경 투명 확인 → 1024 원본 보관, 앱 투입용 `76px`(2x)·`114px`(3x) PNG 익스포트 → `design/system/assets/icons/ico-*.png`.
5. **적용**: `components.css .ico`의 이모지 텍스트를 `<img src=".../ico-*.png" width="22" height="22" alt="">`로 교체. 배지 틴트 클래스(sky/mint/…)는 표의 매핑 유지.

## 8. 하지 말 것 (세트 붕괴 신호)

- 아이콘마다 다른 앵글/조명 — 세트가 아니라 스톡 모음처럼 보임
- 임의 색 추가 (특히 채도 높은 원색 빨강·초록 — 시스템 시맨틱과 충돌)
- 캐릭터화(눈·표정) — powerj는 마스코트 없는 제품 (DESIGN.md §10)
- 배지 틴트와 주 색이 같은 계열로 뭉개지는 조합 (예: sky 틴트 위 sky 단색만) — 주 색+뉴트럴 대비 확보
