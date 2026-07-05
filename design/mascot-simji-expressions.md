# 심지 (Simji) — 표현 세트 · 이미지 생성 프롬프트 (14종)
> 확정 마스코트 심지의 **다양한 표현/포즈**를 여러 페이지에서 쓰기 위한 생성 핸드오프.
> 반드시 확정 에셋 `design/system/assets/mascot/simji-idle.png`를 **레퍼런스 이미지**로 물려 동일 캐릭터를 유지한다.
> §5 하트 밴딩 준수: 휴지=slate · 진행=ember · 100%=gold(오직 #9). 실패엔 빨강·눈물·화난 표정 금지.
> 생성 후 배경제거·배선은 내가 처리(파일명 규칙: `simji-<name>.png`, RGBA).

---

## 0. 생성 전략

엔진: 반드시 확정 에셋 `design/system/assets/mascot/simji-idle.png`를 레퍼런스 이미지로 물려서 동일 캐릭터를 유지한다. Midjourney는 `--cref <simji-idle URL> --cw 55` (identity는 잡되 포즈는 움직일 수 있게 --cw를 50~70로 낮춤), Nano Banana / GPT-image / Seedream 계열은 이미지 첨부 + "same character, new expression, keep identical" 방식.

2단계 파이프라인(권장):
1) 일관성 락 — `sheetPrompt`로 7셀씩 2장(총 14) 시트를 먼저 뽑아 얼굴·비율·등불배 형태를 고정한다. 14개를 한 장에 다 넣으면 256px급에서 셀당 디테일이 무너지므로 7+7로 나눈다. 시트 안에서는 seed를 고정하고, 어긋난 셀만 부분 재생성.
2) 최종본 — 락된 룩을 기준으로 각 표현을 `characterLock + 개별 prompt`로 개별 생성(--cref off simji-idle). 개별 생성이 포즈 자유도·해상도(각 256px, 레티나용 2x=512 권장)에서 유리.

레퍼런스 주의: simji-idle는 (a) 하트가 ember이고 (b) 따뜻한 크림/그라데이션 배경이 구워져 있다. 따라서 개별 prompt는 반드시 (a) slate(빈자리·다독임)·gold(완벽한 하루) 표현에서 하트/등불 발광색을 명시적으로 오버라이드하고, (b) 출력 배경을 크림이 아닌 '플랫한 쿨그레이 또는 투명'으로 요청해야 키어(누끼)가 몸통을 먹지 않는다.

누끼·후처리: 배경 제거는 remove.bg / Photoroom / SAM 계열. 단, 발밑 소프트 타원 접지그림자는 투명 레이어에 살려 남겨야(락에 포함) 어떤 표면에도 스티커가 자연스럽게 얹힌다. peek(알림 픽)만 예외로 프레임을 깨고(상반신만), 나머지는 floating 3/4 뷰를 전 표현 동일하게.

검수 체크: ①손가락/손 생성 여부(팔은 항상 둥근 nub, 손 금지) ②등불배가 유리처럼 반질거리지 않는지(무조건 매트 프로스티드 클레이) ③§5 밴딩 — gold는 오직 '완벽한 하루 만세'(9번) 1종, slate는 '빈자리'·'괜찮아 다독임' 2종, 나머지는 soft ember ④실패/미달 표현에 빨강·초록·눈물·화난 표정 없는지. 파일명은 기존 규칙과 통일: `simji-wave.png`, `simji-success.png`, `simji-focus.png` … (RGBA PNG).

---

## 1. 캐릭터 락 (모든 개별 프롬프트 앞에 붙인다)

```
USE THIS WITH the shipped reference image `simji-idle.png` attached (Midjourney --cref, or Nano Banana / GPT-image "same character"). Paste this whole block first, then append ONE per-expression delta below.

Character: "심지 (Simji)", an ESTABLISHED, shipped mascot — reproduce this EXACT character 100% on-model, identical to the reference image; this is a NEW expression/pose of the SAME character, never a redesign. A small, chubby, huggable soft-matte CLAY "day-spirit" ghostling: warm cream body (#FBFAF7) in a rounded teardrop/bean shape, dome-top leaning slightly forward, pillow-round pudgy bottom that FLOATS just above a soft oval contact shadow — NO tattered ghost tail, not spooky. Crown: a SINGLE small clay flame-wisp curl on top, its tip warmed ember (#F07A2B). Face sits low-center: two large soft round dark-ink eyes (#211B12), each with one small top-left catchlight; a tiny closed content smile; two soft ember blush ovals on the cheeks; calm and kind. Arms: two tiny stubby cream nub arms with rounded tips and NO hands, NO fingers. SIGNATURE — the lantern belly: the lower-center torso is frosted, semi-translucent cream clay (a little "clay lantern", salt-lamp softness — soft MATTE frosted clay, NOT glass), with an ember heart-gem glowing softly inside; the belly is the ONLY heart on the character. Render: soft matte plasticine / soft clay with a gentle fuzzy-matte finish, gentle top-down warm light plus one soft specular highlight, subtle soft oval contact shadow kept beneath, NO outlines or linework, floating 3/4 view, ~256px, premium collectible-toy quality. MATTE always — never glossy, glass, plastic-sheen, wet, or metallic. Palette only: cream #FBFAF7, ember #F07A2B / hot #FF9D4D, gold #E9B93B, slate #7189A8, ink #211B12. Center the character on a FLAT, evenly-lit soft cool-gray background (or true transparent) — NEVER cream-on-cream — for a clean cutout. Keep proportions, face, crown wisp, blush, nub arms, and lantern belly identical to the reference in every pose.
```

---

## 2. ★ 표현 시트 (한 장에 14셀 — 일관성 우선. 7+7로 나눠 뽑기 권장)

```
Character emotion/expression MODEL SHEET — one consistent grid of the SAME mascot "심지 (Simji)" repeated in 14 cells, IDENTICAL character in every cell (same proportions, same warm cream #FBFAF7 clay teardrop/bean body, same low-center face with two round dark-ink eyes + top-left catchlights + tiny closed smile + ember blush, same single crown flame-wisp curl with ember tip, same frosted MATTE clay lantern belly with an inner heart-gem), evenly spaced in two rows of seven on a flat TRANSPARENT (or soft cool-gray) background, each cell the same scale with its own soft oval contact shadow. Every cell keeps two stubby cream nub arms with NO hands and NO fingers, and a soft matte frosted-clay belly (NEVER glass, never glossy). Soft matte plasticine render, gentle top-down warm light, one soft specular highlight, NO outlines, premium collectible quality.

The 14 expressions: (1) waving hello — one nub arm raised high beside the head, cheerful upward-arc eyes, wider warm smile, SOFT EMBER belly; (2) modest success cheer — both nubs lifted small, eyes squeezed into closed happy-arcs, EMBER belly; (3) focus — eyes OPEN but gently narrowed and downcast, both nubs hugging the belly, EMBER belly; (4) checkpoint question — wide ALERT forward-facing eyes and a small round 'o' mouth, one nub to the cheek, EMBER belly; (5) patient empty — serene half-lidded LOWERED gaze, both nubs resting on the belly, one cheek cool slate-tinted blush, SLATE-BLUE (#7189A8) belly; (6) tending / loading — looking DOWN at its own glow, both nubs cupping the belly, floating a touch higher, SOFT EMBER belly; (7) reassure-after-miss — kind soft eyes, a caring lean toward the viewer with one nub patting forward, SLATE-BLUE (#7189A8) belly; (8) end-of-day calm — eyes CLOSED in peaceful downward arcs, both nubs in a cozy self-hug, warm EMBER nightlight belly; (9) perfect-day 만세 — both nubs thrown UP in a triumphant V, wide beaming OPEN smile, caught mid-hop, radiant GOLD (#E9B93B) belly; (10) gentle oops — head tilted, one nub to the cheek, soft slightly-flat 'oops' mouth, SOFT EMBER belly; (11) peek — peeking from behind a straight edge, only the upper half visible, one nub waving over the edge, wisp poking over, SOFT EMBER belly; (12) sleepy — eyes CLOSED as sleeping arcs, one nub tucked under the cheek like a pillow, low dimmed wisp with 'z z z', dimmed warm EMBER nightlight belly; (13) delighted surprise (wow) — eyes extra WIDE and round with an open 'o', both nubs out in a happy startle, bright EMBER belly; (14) thinking (갸웃) — head tilted, eyes glancing UP-and-aside (pondering to itself), one nub to the cheek, SOFT EMBER belly. Heart-color rule for the sheet: ONLY cell 9 is gold; cells 5 and 7 are slate-blue; every other cell is soft ember. No red, no green, no tears, no hands, no glass.
```

---

## 3. 개별 표현 프롬프트 (14종 — 캐릭터 락 뒤에 이어붙임)

### 1. 안녕 심지 (손 흔들기) · Waving hello  
- **파일명**: `simji-wave.png` · **하트**: neutral-ember · **사용처**: S-01 온보딩 히어로 · S-12 로그인 · S-13 회원가입 상단 웰컴 마크 (첫 인사/첫 실행)

```
EXPRESSION — waving hello ('안녕 심지'): a warm first-contact greeting. Eyes bright and open, curved into cheerful upward happy arcs with strong top-left catchlights; content smile a touch wider and warmer; blush ovals slightly fuller; the single crown flame-wisp curl perks up lively. Body tilts a few degrees toward the wave with a light upward bounce (a slightly larger gap above the soft oval contact shadow). ONE stubby cream nub arm raised high beside the head mid-wave — rounded nub tip ONLY, absolutely NO hand and NO fingers; the other nub arm rests low on the frosted MATTE clay lantern belly. Heart-gem a soft warm ember (#F07A2B). Floating 3/4 view, soft oval contact shadow kept, flat cool-gray or transparent background.
```

### 2. 완료 (뿌듯한 작은 만세) · Success cheer  
- **파일명**: `simji-success.png` · **하트**: ember · **사용처**: 저장/확정 토스트 — S-03 계획 저장 · S-04 JIT 목표 설정 · S-13 계정 생성 (탭 데이터 화면 제외)

```
EXPRESSION — success cheer ('완료'): a MODEST, warm 'saved!' micro-celebration (understated, NOT a full triumphant throw). Eyes squeezed into joyful upward CRESCENT arcs (closed happy-arcs) with bright catchlights; content smile at its warmest; blush warm. BOTH stubby cream nub arms lifted up in a small modest cheer — rounded nub tips, NO hands, NO fingers — with a tiny lift off the shadow. Crown flame-wisp curl perked with a faint ember spark at the tip. Heart-gem glowing ember (#F07A2B), frosted MATTE clay belly (never glass). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 3. 집중 (딥워크 동반) · Focus  
- **파일명**: `simji-focus.png` · **하트**: ember · **사용처**: S-05 타이머 실행 중 — 측정되는 프로세스 옆 딥워크 companion

```
EXPRESSION — focus ('집중'): the quiet deep-work companion beside a running timer. Eyes OPEN but gently narrowed and cast DOWNWARD in calm concentration (looking down at the work — never sleepy, never stern); small steady content smile. Body still and slightly forward-leaning; BOTH stubby cream nub arms hugging the frosted MATTE clay lantern belly close — rounded nub tips, NO hands, NO fingers. Crown flame-wisp curl upright and calm with a steady ember tip. Heart-gem a steady ember (#F07A2B). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 4. 빈자리 (첫 기록 대기) · Patient empty  
- **파일명**: `simji-empty.png` · **하트**: slate · **사용처**: S-15 빈 기록 · S-09 아카이브 빈 상태 (첫 기록을 조용히 기다림)

```
EXPRESSION — patient empty ('빈자리'): a calm, unbothered wait for the first record — patient, NOT sad (an empty log is treated as calm data). Eyes relaxed and kind, a touch half-lidded and serene, gaze lowered gently toward the empty space; tiny content smile. Body settled a little lower and rounder; BOTH stubby cream nub arms resting softly together over the front of the belly — rounded nub tips, NO hands, NO fingers. One cheek's blush cooler and slate-tinted (matching the shipped rest asset). HEART OVERRIDE: the heart-gem glows COOL SLATE-BLUE (#7189A8), calm and quiet, and the frosted MATTE clay lantern belly's inner light shifts cool slate (NOT ember, NOT sad, NO red). Crown flame-wisp curl dips low and soft. Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 5. 로딩 · 등불 돌보기 · Tending / loading  
- **파일명**: `simji-loading.png` · **하트**: neutral-ember · **사용처**: 전역 로딩·동기화 스피너 · S-07 마감 대시보드 생성(~1.8s) · S-10 주간 리포트 집계

```
EXPRESSION — tending / loading ('등불 돌보기'): a state-neutral, patient 'tending the day' beat for loading and computing screens. Eyes calm and content, looking gently DOWN toward its own belly glow; tiny focused smile. Dome-top tilted gently in soft attention; floating a touch HIGHER mid-bob (a slightly larger gap above the contact shadow) as if drifting; BOTH stubby cream nub arms cupped softly around the frosted MATTE clay lantern belly as if cradling/tending its glow — rounded nub tips, NO hands, NO fingers. Crown flame-wisp curl leaning as if in a slow breeze. Heart-gem a soft warm ember (#F07A2B). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 6. 검증 게이트 (달성했나요?) · Curious question  
- **파일명**: `simji-question.png` · **하트**: ember · **사용처**: S-06 전환 검증 게이트 프롬프트 — 다음 프로세스 전 '목표 달성했나요?' 확인

```
EXPRESSION — checkpoint question ('검증 게이트'): asking the user to confirm an achievement before the next process — attentive, encouraging, never judging. Eyes WIDE, alert and bright with lifted ink brow-lines and strong catchlights, facing FORWARD as if checking YOU and awaiting an answer; mouth a small round 'o' press. Head and dome-top tilt forward in an interested nod; ONE stubby cream nub arm lifted lightly toward the cheek in a thoughtful gesture — rounded nub tip, NO hand, NO fingers — the other resting on the frosted MATTE clay lantern belly. Crown flame-wisp curl tilted like a gentle question mark. Heart-gem ember (#F07A2B). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 7. 괜찮아 다독임 (실패는 데이터) · Reassure after miss  
- **파일명**: `simji-reassure.png` · **하트**: slate · **사용처**: 목표 미달·게이트 미달 판정·연속기록 끊김·<70% 순간 (S-06/S-07 오버레이). ※ S-07 일반 <100% 마감 배경은 기존 ember idle 유지 — 이 포즈는 '미달 위로' 비트 전용

```
EXPRESSION — reassure after a miss ('괜찮아 다독임'): the SIGNATURE 'never scolds — tomorrow again' caretaker pat after a shortfall; kind and patient, absolutely NO sadness, NO tears, NO scolding. Eyes warm, soft and understanding (a kind relaxed curve — no droop, no tears); a small gentle encouraging closed smile. Body and dome-top lean gently toward the viewer in a caring tilt; ONE stubby cream nub arm reaches forward in a slow soft 'there-there' pat toward the viewer — rounded nub tip, NO hand, NO fingers — the other rests on the frosted MATTE clay lantern belly. HEART OVERRIDE: heart-gem glows COOL SLATE-BLUE (#7189A8) with the belly's inner light shifted cool slate (embodies 'a miss is calm data' — NOT ember, NEVER red). Crown flame-wisp curl calm. Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 8. 마감 굿나잇 (하루 마무리) · End-of-day calm  
- **파일명**: `simji-goodnight.png` · **하트**: ember · **사용처**: S-07 <100% 마감 하단 와인드다운 · S-08 일기 (하루를 차분히 닫는 등불의 온기)

```
EXPRESSION — end-of-day calm ('마감 굿나잇'): a warm, satisfied wind-down at the day's close and for the diary. Eyes CLOSED in two peaceful downward-curved arcs; a warm, satisfied content smile; blush warm. Whole body relaxed in a gentle exhale, dome-top tilted slightly as if settling in for the night; BOTH stubby cream nub arms wrapped softly around its own frosted MATTE clay lantern belly in a small cozy self-hug — rounded nub tips, NO hands, NO fingers. Crown flame-wisp curl relaxed and calm. Heart-gem a soft warm ember (#F07A2B), belly glowing like a bedside nightlight. Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 9. 완벽한 하루 · 만세 (100%) · Perfect-day celebration  
- **파일명**: `simji-perfect.png` · **하트**: gold · **사용처**: S-14 완벽한 하루(진짜 100%) 전용 — '매일 쌓이는 성취'의 머니샷. gold는 오직 여기

```
EXPRESSION — perfect-day celebration ('완벽한 하루 · 만세'): the rare 100%-day money-shot, the peak reward. BOTH stubby cream nub arms thrown straight UP overhead in a triumphant V (만세) — rounded nub tips, NO hands, NO fingers — body caught mid-hop, floating higher with a bigger gap above a smaller, softer contact shadow, tilted slightly back. Eyes bright joyful upward CRESCENT arcs with sparkly catchlights; the biggest, happiest OPEN beaming smile; blush warmly flushed. Crown flame-wisp curl flares up bright and tall with one or two faint ember sparkles. HEART OVERRIDE (100% ONLY): heart-gem glows radiant GOLD (#E9B93B) and the frosted MATTE clay lantern belly glows warm gold; crown wisp tip warms slightly gold-ember. Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 10. 오류 (부드러운 오류) · Gentle oops  
- **파일명**: `simji-oops.png` · **하트**: neutral-ember · **사용처**: 전역 에러 · 404 · 네트워크 실패 · 로드 실패 (경보스럽지 않은 친절한 오류)

```
EXPRESSION — gentle oops ('오류'): a kind, non-alarming error / 404 / no-network illustration — mildly concerned but calm, never distressed. Head tilted to one side; ONE stubby cream nub arm raised to lightly touch the side of the cheek/head in a soft 'hmm, sorry' gesture — rounded nub tip, NO hand, NO fingers — the other resting low on the frosted MATTE clay lantern belly. Eyes a little wider and very soft, kind and gently concerned; mouth a small, slightly flat understanding line (a gentle 'oops' — NOT a frown, no tears). Crown flame-wisp curl droops just a touch. Heart-gem a soft warm ember (#F07A2B). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 11. 알림 픽 (빼꼼) · Peek  
- **파일명**: `simji-peek.png` · **하트**: neutral-ember · **사용처**: 푸시 알림 · 인앱 리마인더 토스트/배너 · 알림 배지 픽 (다음 프로세스 시작 넛지)

```
EXPRESSION — peek ('알림 픽'): a playful attention-getter for push notifications, reminder toasts and badges — the ONE pose that legitimately breaks frame. 심지 peeks in from behind a straight edge/corner: only the UPPER HALF of the body is visible, one eye area and one raised stubby cream nub arm poking past the edge in a small attention-getting wave — rounded nub tip, NO hand, NO fingers — and the single crown flame-wisp curl pokes up over the edge. Visible eye bright and curious with a lifted happy arc; friendly playful content smile. The frosted MATTE clay lantern belly (soft ember heart-gem #F07A2B) is partly hidden behind the edge. Keep the peeked edge clean and straight for compositing. Flat cool-gray or transparent background.
```

### 12. 방해금지 밤 (졸음 zzz) · Sleepy  
- **파일명**: `simji-sleepy.png` · **하트**: neutral-ember · **사용처**: 방해금지(DND) 모드 활성 · 야간/조용시간 화면 · 휴식 타이머 (따뜻한 야간등)

```
EXPRESSION — sleepy ('방해금지 밤 · zzz'): a cozy quiet-hours / do-not-disturb / rest-break beat, like a warm nightlight winding down. Eyes CLOSED as soft gentle sleeping arcs; a tiny dreamy content smile. Body tucked rounder and settled a bit lower over a slightly wider soft contact shadow; ONE stubby cream nub arm tucked up under the cheek like a little pillow, the other relaxed — rounded nub tips, NO hands, NO fingers. The single crown flame-wisp curl hangs LOW and DIMMED like a dozing candle, with two or three small soft 'z z z' drifting up beside the head. Heart-gem a soft, DIMMED warm ember (#F07A2B), belly glowing low like a nightlight (calm, not off). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 13. 놀람 · wow (목표 초과) · Delighted surprise  
- **파일명**: `simji-wow.png` · **하트**: ember · **사용처**: 정량 목표 초과 달성 보상 — S-06 게이트/S-07 오버레이 (긍정적 'wow', 공포 아님)

```
EXPRESSION — delighted surprise ('놀람 · wow'): a positive 'wow, you beat the goal!' reward for an EXCEEDED quantitative target — happy astonishment, never fear. Both large round dark-ink eyes opened extra WIDE and round with bigger bright catchlights; a tiny OPEN 'o' smile of wonder; blush warm. BOTH stubby cream nub arms lifted slightly outward in a happy, startled gesture — rounded nub tips, NO hands, NO fingers — body popped a little higher off a smaller contact shadow. Crown flame-wisp curl perked straight up, alert, with a small ember spark. Heart-gem bright ember (#F07A2B) — NOT gold (gold is reserved for a genuine 100% day only). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

### 14. 갸웃 (계획 고민) · Thinking  
- **파일명**: `simji-thinking.png` · **하트**: neutral-ember · **사용처**: S-03 계획 편집기 빈 상태 — 첫 프로세스 추가 전 '무엇부터 계획할까?'

```
EXPRESSION — thinking ('갸웃'): a gentle 'what shall we plan first?' pondering beat for the empty plan editor — curious and self-absorbed, DISTINCT from the forward-facing gate question. Head AND body tilt to one side; eyes glancing softly UP and to the SIDE (pondering to itself, NOT looking at the viewer), a tiny thoughtful pursed half-smile. ONE stubby cream nub arm lifted to rest lightly against the cheek in a thinking gesture — rounded nub tip, NO hand, NO fingers — the other tucked at the frosted MATTE clay lantern belly. Crown flame-wisp curl leaning into a soft question-mark lean. Heart-gem a soft warm ember (#F07A2B). Floating 3/4 view, soft oval contact shadow, flat cool-gray or transparent background.
```

---

## 4. 페이지 배치 맵

심지 표현 → powerj 화면/상태 배치 맵 (하트-젬 §5 밴딩 준수 · gold는 100% 전용)

| # | 표현 (KR) | 배치 화면/상태 | 하트 |
|---|---|---|---|
| 1 | 안녕 심지 (waving) | S-01 온보딩 히어로 · S-12 로그인 · S-13 회원가입 웰컴 | neutral-ember |
| 2 | 완료 (success) | 저장/확정 토스트: S-03 계획 저장 · S-04 JIT 목표 설정 · S-13 계정 생성 | ember |
| 3 | 집중 (focus) | S-05 타이머 실행 중 동반 | ember |
| 4 | 검증 게이트 질문 (question) | S-06 전환 검증 게이트 프롬프트('목표 달성했나요?') | ember |
| 5 | 빈자리 (patient empty) | S-15 빈 기록 · S-09 아카이브 빈 상태 (+S-03 빈 편집기에도 재사용 가능) | slate |
| 6 | 로딩·등불 돌보기 (loading) | 전역 로딩/동기화 스피너 · S-07 대시보드 생성(~1.8s) · S-10 리포트 집계 | neutral-ember |
| 7 | 괜찮아 다독임 (reassure) | 목표 미달 · 게이트 미달 판정 · 연속기록 끊김 · <70% 순간 (S-06/S-07 오버레이) | slate |
| 8 | 마감 굿나잇 (end-of-day calm) | S-07 <100% 마감 하단 와인드다운 · S-08 일기 | ember |
| 9 | 완벽한 하루 만세 (perfect) | S-14 완벽한 하루(진짜 100%) 전용 | gold |
| 10 | 오류 (gentle oops) | 전역 에러 · 404 · 네트워크/로드 실패 | neutral-ember |
| 11 | 알림 픽 (peek) | 푸시 알림 · 인앱 리마인더 토스트/배너 · 알림 배지 픽 | neutral-ember |
| 12 | 방해금지 밤 (sleepy) | 방해금지(DND) 모드 · 야간/조용시간 · 휴식 타이머 | neutral-ember |
| 13 | 놀람 wow (surprise) | 정량 목표 초과 달성 보상 (S-06 게이트/S-07 오버레이) | ember |
| 14 | 갸웃 (thinking) | S-03 계획 편집기 빈 상태('무엇부터 계획할까') | neutral-ember |

중요 배선 주의(§8 존중):
- S-07 <100% '일반' 마감 배경 마스코트는 이미 ember `simji-idle`로 배선되어 있음 → 7번(다독임·slate)은 그 배경을 대체하지 않고 '미달 위로' 비트(미달/연속끊김/<70%)에만 사용. 일반 와인드다운은 8번(마감 굿나잇·ember).
- S-14 100% 배경은 gold `simji-gold` 배선 유지 → 9번은 그 위/전환의 '만세' 보상 비트.
- S-15 빈 기록 배경은 slate `simji-rest` 배선 유지 → 5번은 동일 상태의 표정 확장.

마스코트 미사용(§3·§8): S-02 홈, S-09/S-10/S-11 탭 데이터 화면(빈 상태 제외) — 데이터 밀집 메인 화면엔 심지 미배치.

---

## 5. 네거티브 프롬프트 (공통)

```
hands, fingers, palms, thumbs, gripping hands, claws, human hands on the arm tips; glass, glossy, gloss, high-gloss, shiny, wet look, plastic sheen, lacquered, metallic, chrome, transparent glass belly, glass orb, glass sphere, subsurface glass, mirror; tattered ghost tail, shredded wispy ghost bottom, floating cloth, spooky, scary, creepy, eerie, fangs, sharp teeth; outlines, black linework, hard ink outline, sticker outline stroke, cel-shading, flat 2D vector, hard cartoon lines; multiple flame-wisps, two curls, horns, antlers, ears, realistic fire, big flame, roaring candle flame; heart-shaped fire, glowing eyes, extra eyes, no eyes; red heart, red glow, green heart, green glow (never red/green for failure); tears, crying, teardrops, distress sweat-drops, angry, scowl, furrowed brow, frown, grumpy, pained, scared; extra limbs, extra arms, three arms, melted asymmetry, blobby mush, deformed; text, letters, words, watermark, logo, signature, caption, UI chrome, frame border, hard drop-shadow box; background scenery, room, furniture, busy background, gradient scene, cream-on-cream background; photorealistic human, uncanny, doll face seams.
```

---

## 6. 받은 뒤 (내가 처리)

1. 배경 제거 → 투명 RGBA (발밑 소프트 접지그림자는 살림)
2. `design/system/assets/mascot/simji-<name>.png` 저장 (2x 레티나 권장)
3. 배치 맵대로 각 화면/상태에 배선 + §5 밴딩 확인 후 배포
4. 이 문서는 생성 완료 후 정리 대상(emoji-prompt·mascot-simji-prompt와 동일 논리)
