# 심지 (Simji) — powerj 마스코트 · 이미지 생성 프롬프트 패키지

> 디자인 LLM(Midjourney · DALL·E · Nano Banana · Stitch 등)에 그대로 붙여넣는 핸드오프 문서.
> 캐릭터의 시각 규격은 `design/DESIGN.md`(§5 색 밴딩, §8 아이콘 체계)와 1:1로 맞춘다.
> 기존 3D 클레이 아이콘 18종(`design/system/assets/icons/ico-*.png`) 옆에 놓아도 "같은 손에서 나온" 것처럼 보여야 한다.

---

## 1. 캐릭터 한 줄

**심지(Simji)** — 밤새 곁을 지키는 작고 통통한 클레이 **등불 요정**. 잔소리하지 않고 그저 곁에 있으며, 하루가 채워질수록 배 속 하트가 **은은한 ember로 데워지고**, 완벽한 100%의 날에만 **온몸이 금빛 등불**로 물든다. 목표를 놓친 날엔 슬퍼하지도 혼내지도 않고 하트가 차분한 **slate(중립 데이터)**로 내려앉을 뿐.

- 이름 뜻: **심지** = 불씨를 붙드는 심지(wick) + 굳센 심지(steadfast core) — ember 훅과 "규율 있는 동반자" 성격을 한 단어로.
- 톤: 돌봄형(caretaker), 차분하고 다정함. 하이프 머신 아님.

## 2. 팔레트 (정확 hex — 이 색만 사용)

| 역할 | hex |
|---|---|
| 몸(크림) | `#FBFAF7` / `#FFFFFF` |
| 크림 그림자(웜) | `#FEF1E6` |
| ember(진행·발열) | `#F07A2B` |
| hot ember(코어) | `#FF9D4D` |
| **gold(100% 전용)** | `#E9B93B` (+ soft `#FBF3DC`) |
| slate(휴지/미달성) | `#7189A8` |
| 잉크(눈·이목구비) | `#211B12` |
| 배경광(웜 오프화이트) | `#F6F4EF` |

빨강(`#D8542F`)·초록·보라 **금지**. gold는 **오직 100%**에만.

---

## 3. ★ 마스터 프롬프트 (일상 상태 = ember 중간 발열 · 복붙용)

```
A soft matte clay (plasticine) mascot character named "Simji", premium App-Store
3D product-render quality, a single character, floating 3/4 view, centered, on a
fully transparent background, high detail, no outlines.

SUBJECT — a small, chubby, huggable "day-spirit" nightlight companion; a caretaker,
not a hype mascot. Rounded teardrop/bean body, about as tall as it is wide with a
touch more height. A gently rounded dome-top leans slightly forward (attentive,
leaning-in), widening into a soft pillow-round pudgy bottom that floats just above a
small soft oval contact shadow. NO tattered wavy ghost tail, not spooky at all.

MATERIAL & STYLE — soft matte plasticine / Play-Doh clay with a very fine ceramic
micro-texture and gentle smooth gradients; bulbous, rounded, chubby forms; premium
clay-icon render, in the exact lineage of a matching set of soft clay productivity
icons (a clay target, a clay stopwatch, a clay diary). No outlines. Matte — never
glossy plastic, never glass, never metallic.

BODY — warm cream clay (#FBFAF7) with soft warm ember-tinted shadows (#FEF1E6). A
single small clay flame-wisp curl rises from the crown, its very tip warmed ember
(#F07A2B).

FACE (set low-center on the belly) — two large soft round eyes in warm dark ink
(#211B12), each with a single soft top-left catchlight; gentle relaxed arc-shaped
eyes; a tiny closed content smile; two subtle soft ember blush ovals on the cheeks.
Calm, kind, steady, quietly dignified — not grinning, no eyelashes, no sparkles, no
googly eyes.

ARMS — two tiny stubby cream nub arms with NO hands; one lifted in a soft, gentle
"I'm here" wave, the other resting on its belly.

SIGNATURE — THE LANTERN HEART — the lower-center torso is FROSTED, semi-translucent
cream clay, like a little clay lantern or the softness of a salt-lamp (NOT glass,
NOT a glossy gem — keep it matte clay with a soft inner glow). Inside it a small
rounded ember heart-gem glows warmly: ember #F07A2B with a hot #FF9D4D core, its
warmth softly bleeding into the surrounding cream and flushing the belly gently
warm. Diffuse glow only, never a hard light source.

LIGHTING & RENDER — one gentle top-down warm morning-kitchen key light, a single
soft specular highlight, and a subtle soft oval contact shadow directly beneath.
Cozy, warm, huggable, with quiet dignity. Transparent background, centered.

PALETTE (use ONLY these) — cream #FBFAF7 / #FFFFFF, ember #F07A2B, hot ember
#FF9D4D, ember-soft #FEF1E6, slate #7189A8 (resting accent only), ink #211B12, warm
off-white light #F6F4EF. Gold #E9B93B is reserved for the 100% variant only. No red,
no green, no other colors.
```

## 4. 압축판 (Midjourney 등 길이 제한 도구용 · 한 문단)

```
3D soft matte clay mascot "Simji", a chubby cream plasticine day-spirit nightlight
companion, rounded bean body leaning slightly forward, big calm dark-ink eyes with
tiny top-left catchlights, small closed content smile, soft ember blush, a little
clay flame-wisp curl on the crown with an ember tip, two stubby handless nub arms
(one waving "I'm here"), a frosted semi-translucent cream-clay lantern belly with a
glowing ember heart-gem inside (soft diffuse inner glow, matte, not glass), floating
3/4 view, gentle top-down warm morning light, soft specular highlight, soft oval
contact shadow, transparent background, no outlines, premium app-icon render, cozy
warm huggable with quiet dignity, palette cream #FBFAF7 + ember #F07A2B/#FF9D4D +
ink #211B12, gold #E9B93B only for 100% --no glossy glass metallic photoreal
ghost-tail spooky text outline red green
```

---

## 5. 상태 변형 (하루의 계기판 — DESIGN.md §5 밴딩과 동일)

마스터 프롬프트에서 **하트-젬(과 크라운 심지 끝)** 문장만 아래로 교체한다. 얼굴·자세는 상태에 맞춰 미세 조정.

| 상태 | 교체 문장 | 표정/자세 |
|---|---|---|
| **휴지·미기록 (0%)** | `the lantern-heart holds a cool SLATE-tinted inner glow (#7189A8), unlit and patient; the crown-wisp tip is barely warm` | 고요하고 인내하는 눈, 절대 슬프지 않음 |
| **진행 중 (마스터 기본)** | `ember heart-gem glowing #F07A2B with a hot #FF9D4D core, warmth bleeding into the cream belly` | 다정한 미소, 한 팔 "여기 있어" 손짓 |
| **완벽한 날 (100% · 희소 보상)** | `the heart-gem AND the crown-wisp tip bloom FULL GOLD #E9B93B with a soft #FBF3DC golden lantern glow lighting the entire belly, and a faint warm gold rim-light around the whole body` | 눈이 행복한 아치, 두 팔 살짝 들어 올림 |

> **핵심**: gold는 100%에만. 실패 상태에 빨강·눈물·찡그림 금지 — slate는 "차분한 데이터"이지 벌이 아니다.

## 6. 포즈·용도 변형 (프롬프트 델타)

마스터에 아래 지시를 덧붙인다.

- **앱 아이콘** `+ tighter crop, near-front 3/4, slightly larger face, ember heart mid-glow, silhouette and lantern-heart must stay legible at 48–64px, sits well on a rounded-square #F6F4EF or white tile`
- **빈 화면 / 무기록** `+ full body with generous empty space around it, resting SLATE heart state, one arm in a gentle "I'm here" wave, calm and inviting`
- **로딩** `+ ember heart and crown-wisp tip in a soft mid-glow (still frame); for animation, glow opacity only — never move/scale the body`
- **표정 시트(expression sheet)** `a consistent character sheet of the same clay mascot "Simji": 6 head/pose variants on one transparent sheet — (1) calm default, (2) content smile, (3) happy gold-arc eyes (100%), (4) gentle "I'm here" wave, (5) sleepy night, (6) patient-after-a-miss (calm, not sad); identical clay material, lighting and palette across all`
- **스티커 시트** `+ 3–4 full-body poses (waving, hugging its own lantern belly, peeking, sleeping), same style, transparent background`

## 7. 네거티브 프롬프트

```
outline stroke, hard black outlines, glossy plastic, glass, crystal gem, metallic,
chrome, photorealistic, rough handmade clay, visible fingerprints, tattered wavy
ghost tail, bed-sheet ghost, spooky, scary, open screaming mouth, fangs, teeth,
Halloween, Duolingo owl, any bird, generic slime, formless blob, anime sparkle eyes,
teary eyes, eyelashes, blush stickers, floating hearts, tongue out, confetti,
particles, sparkles, text, letters, watermark, busy background, hard drop-shadow
box, red #D8542F, green, purple, neon, oversaturated
```

## 8. ⚠️ 렌더 주의 (가장 잘 틀리는 지점)

1. **반투명 배 = "유리"가 아니라 "클레이 등불"** — 유리/보석/광택으로 렌더되면 매트 클레이 세트와 즉시 이질감. `frosted semi-translucent cream clay, soft diffuse inner glow, salt-lamp softness`를 반드시 명시하고 스펙큘러는 하나만.
2. **유령 클리셰 회피** — 너덜너덜한 물결 꼬리·괴기한 입 금지. 밑단은 **베개처럼 둥근 통통한 형태**, 몸은 새하양이 아니라 **웜 크림**, 표정은 다정.
3. **접지 그림자는 유지** — 기존 아이콘(target·timer·bot)이 실제로 은은한 소프트 그림자를 갖고 있으므로, "no shadow"라고 쓰지 말 것.
4. **웜 색이 코랄/빨강으로 새는 것 방지** — ember는 정확히 `#F07A2B`. `ico-target`의 코랄-살몬(`#EF7C66`)이나 위험색 빨강(`#D8542F`)으로 드리프트 금지.
5. **보상은 콘페티가 아니라 "심지가 금빛 등불이 되는 것"** — 파티클/반짝이 추가 금지.

## 9. 앱 내 사용 규칙

- **넣는 곳**: 온보딩(S-01) 히어로 곁 · 빈 화면/무기록 상태 · 하루 마감 100% 보상 순간(S-07) · 로딩 · 앱 아이콘 후보.
- **안 넣는 곳**: 하단 탭바가 있는 데이터 밀집 메인 화면(오늘·기록·리포트·설정) — 순위권 앱의 절제를 유지한다.
- **상태 = DESIGN.md §5 밴딩**: 미기록/휴지 = slate 심장 · 진행 = ember · 100% = gold(희소). 실패에 빨강·슬픈 표정 금지.
- **모션**: 빛(glow) opacity와 transform만 — reduced-motion 존중.
