# Story-Skill — Game Story Writer (게임 스토리 작가)

> **소설가·각본가·드라마투르그·내러티브 디자이너 수준의 게임 서사를 쓰기 위한 Claude Skill**
>
> "괜찮은 문장 + 줄거리"가 아니라, **웰메이드(well-made)** 의 기준을 강제합니다.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](#라이선스)
[![Skill: Claude Code](https://img.shields.io/badge/Skill-Claude%20Code-8A2BE2)](https://docs.claude.com)
[![Language: KO%2FEN](https://img.shields.io/badge/Language-KO%20%2F%20EN-green)](#언어-정책)
[![Built with: Skill-Gen-Agent](https://img.shields.io/badge/Built%20with-Skill--Gen--Agent-orange)](https://github.com/Simon-YHKim/Skill-Gen-Agent)

---

## 한 줄 정의

게임의 **메인 스토리·시나리오·캐릭터 바이블·백스토리·퀘스트·대사 스크립트·월드빌딩**을, 거장들의 작법(작가/감독/내러티브 디자이너의 공통 도구)을 강제하여 산출하는 Claude Skill.

기본 트리거: `게임 스토리`, `시나리오 짜줘`, `캐릭터 설정`, `백스토리`, `퀘스트 만들어줘`, `대사`, `NPC`, `세계관`, `월드빌딩`, `복선`, `떡밥 회수`, `여운 있는 결말` …

---

## 목차

1. [무엇이 다른가](#무엇이-다른가)
2. [다섯 가지 비협상 원칙](#다섯-가지-비협상-원칙-five-non-negotiable-principles)
3. [다섯 가지 워크플로우](#다섯-가지-워크플로우-workflows)
4. [디렉터리 구조](#디렉터리-구조)
5. [설치](#설치-installation)
6. [사용 예시](#사용-예시-examples)
7. [출력 포맷 자동 선택](#출력-포맷-자동-선택)
8. [참고 문서 맵](#참고-문서-맵-reference-map)
9. [거장 8인의 철학](#거장-8인의-철학-the-eight-masters)
10. [기본 동작 정책](#기본-동작-정책-working-defaults)
11. [언제 부드럽게 밀어내는가](#언제-부드럽게-밀어내는가-pushback-policy)
12. [언어 정책](#언어-정책)
13. [라이선스](#라이선스)

---

## 무엇이 다른가

| 일반 LLM 스토리 프롬프트 | **Story-Skill** |
|---|---|
| "장면을 묘사해줘" → 인접 장식 | **모든 디테일은 의도** — 캐릭터 폭로 / 플롯 진행 / 미래 장면 적재 / 테마 정박 / 설계된 오도 중 *최소 하나*. 아니면 잘라낸다 |
| 캐릭터 = 트로프 스택 | **단일 패러독스 + 자기정당화 모놀로그** — 인물이 자신의 최악의 선택을 1인칭 내적 논리로 변호하는 짧은 단락이 진단 도구 |
| 복선 = 후반부 깜짝쇼 | **Plant → Echo → Payoff (3회 등장 최소)** — Vince Gilligan의 인덱스카드 시스템을 매트릭스로 디지털화. *deus ex machina* 금지, *honest misdirection* 강제 |
| 모든 것을 설명하기 | **능동적 여백의 설계** — Toni Morrison의 *invisible ink*, 미야자키의 *공동 집필*, 30% 감산 패스 |
| 결말 = 마무리 | **여운의 마지막 장면** — 며칠 후에야 의미가 완전히 풀리는 이미지 |
| 실패 = Game Over | **실패의 서사화 (Failure as Content)** — Disco Elysium식. 실패 분기는 *다른 이야기* 이지 *부재* 가 아니다 |

---

## 다섯 가지 비협상 원칙 (Five Non-Negotiable Principles)

> **스타일은 변해도, 이 다섯은 모든 모드에서 유지된다.** 이것이 *웰메이드* 의 베이스라인.

### 원칙 1 — 치밀한 감정선과 정밀한 캐릭터

**치밀한 = 빈틈없이 짜인.** *친밀한*(따뜻한)과 다르다. 공예의 *밀도* 이야기.

- 모든 감정 비트는 **선행 장면이 벌어준 것** + **후행 장면을 적재**. 최소 3링크.
- 명명된 인물 모두에게 **단일 한 줄 패러독스**.
- McKee의 **want vs. need** 분리 — 의식적 욕망과 무의식적 필요는 거의 일치하지 않으며, 그 간격이 엔진.
- **자기정당화의 활성 기계** — 인물은 자신의 최악의 선택을 *지금 이 순간* 합리화할 수 있다. (Dostoevsky의 라스콜니코프, Gilligan의 Walter White)
- **Hemingway의 빙산 이론** — 7/8은 수면 아래.

### 원칙 2 — 셋업-페이오프 정밀성

모든 셋업은 페이오프를 추적한다. 모든 페이오프는 뿌리가 있다. 복선은 **구조적 약속** 이지 장식이 아니다.

- **Plant → Echo → Payoff** — 3회 등장 최소. 중간 등장에서 의미가 *변형* 또는 *심화*.
- **Chekhov's Gun (양방향)** — 벽에 걸린 라이플은 발사된다. 발사할 의도가 없으면 걸지 않는다.
- **No deus ex machina** — 후반 해결은 인물의 결정과 결과에서. 외부 우연 금지(초반 발생은 허용).
- **Honest misdirection** — 셋업이 잘못된 페이오프로 적재되더라도, 재독 시 모든 단서가 진짜 폭로를 가리켜야 한다.
- **Long con** — 가장 큰 만족은 10장면 이후의 회수에서. 명시적으로 추적.

### 원칙 3 — 모든 디테일은 의도 (Decoration Is Sin)

장면에 놓인 모든 사물, 인물의 모든 행동, 지도의 모든 이름은 다음 중 *최소 하나* 의 이유로 존재한다: **캐릭터 폭로 / 플롯 진행 / 미래 장면 적재 / 테마 정박 / 계획된 폭로로의 오도**. 어느 것도 아니면 잘라낸다.

- **Mise-en-scène 규율** — "보이는 것"은 *이야기가 보일 필요가 있어서* 보인다.
- **Action as evidence of interior** — 행동은 내면의 증거.
- **Location as psychology** — 모든 장소는 장면의 정서를 봉사한다.

### 원칙 4 — 다중 스타일 마스터리

스타일은 *어떻게* 를 결정하고, 원칙은 *웰메이드인가* 를 결정한다.

스타일 카탈로그(요약):

- **한국식 치밀한 정서** — *jeong / han* 보정 (`references/korean-aesthetics.md`)
- **Souls-like lore** — 단편적, 환경 서사, 아이템 설명 스토리텔링
- **Cozy game** — 저긴장, 캐릭터 우선, 느린 누적
- **Streaming prestige** — 퍼즐박스 플롯, cold open, 챕터 에피그래프
- **Classical / mythic** — 운명 구조, 코러스 논평, 극적 아이러니
- **Disco Elysium 인접** — 내면을 다중 음성으로 분기, *failure as content*

### 원칙 5 — 능동적 여백의 설계 (Active Design of Meaningful Absence)

청중은 관객이 아니라 **공동 작가**. *말하지 않은 것*, *보여주지 않은 것*, *채우지 않은 것* 이 작품의 일부.

- **The audience is not stupid.** 설명을 하나 빼고, 또 하나 빼라.
- **Productive absence vs. lazy gap** — 생산적 부재는 *재구성에 충분한 흔적* + *능동적 재구성을 부르는 미스터리*.
- **Embodied substitution (Han Kang)** — 트라우마/추상은 신체적·감각적 메타포로 대체.
- **30% subtraction pass** — 초고 후 *말해버린 문장*을 약 30% 잘라내고 구체 행동·감각·침묵으로 교체.
- **Failure as content (Kurvitz)** — 분기 매체에서는 실패도 새로운 서사를 생성.

---

## 다섯 가지 워크플로우 (Workflows)

요청은 보통 여러 개를 동시에 부른다. **의존 순서**: 월드빌딩 → 캐릭터 → 메인 스토리 → 퀘스트 → 대사.

### 1. 메인 스토리 / 시놉시스

필수 산출물 8종:

1. **테마 한 줄** — 무엇에 *관한* 이야기인가 (사건이 아니라)
2. **중심 상처 (the wound)** — 치유되지 않아 이야기를 가능케 하는 것
3. **전제 (Egri's premise)** — `[Force] leads to [Consequence]` 한 문장
4. **아크 구조** — 3-act / 5-act / 기승전결 / Story Circle 중 선택 + 한 줄 정당화
5. **내면 변곡점 3개 이상** — 외부 트리거 + 내적 비용 표시
6. **셋업-페이오프 매트릭스** — 약속된 셋업-페이오프 쌍 5개 이상
7. **여운의 마지막 장면** — 며칠 후 완전히 이해되는 이미지
8. **무엇이 의도적으로 비어 있는가** — 한 단락으로 남긴 것과 그 이유

> (1)·(2)·(3)·(6)·(8)이 빠진 순수 줄거리는 **거부**. 그것이 엔진이다.

### 2. 캐릭터 설정 / 백스토리

`references/character-deep-build.md` 의 7-layer 템플릿 사용. 필수:

- **단일 패러독스**
- **Want vs. Need**
- **The Lie They Believe**
- **자기정당화 모놀로그** (1인칭 단락) — *built vs. assembled* 진단
- **상처의 감각적 앵커 + 발화되지 않은 한 문장**
- **Voice signature** (리듬 + 어휘 + 언어적 틱 + 회피 주제)
- **사물 탤리스먼** (3장면 이상 적재)
- **중력 관계** (어느 인물이 자기 내면의 자북인가)
- **캐릭터당 설계된 부재** — 명시되어선 안 되지만 행동으로 재구성 가능한 사실

### 3. 퀘스트 / 사이드 스토리

각 퀘스트 = 정서적 비네트 + 구조적 약속.

- **NPC의 부조화** (플레이어를 끌어당기는 모순)
- **표면 목표 = 감정 대리물**
- **이 퀘스트가 심거나 echo하는 셋업 3개** (매트릭스에 등록)
- **잔여물 (residue)** — 3퀘스트 후에도 느껴지는 것
- **3-choice 원칙** — 최소 하나는 *침묵 / 아무것도 안 함*, 그리고 그것은 정당한 정서적 답
- **실패의 서사화** — 모든 분기(실패 포함)는 *새로운 서사* 를 생성

### 4. 대사 / 스크립트

가장 중요한 단 하나의 규칙: **the Sorkin condition**.

> 둘 이상의 인물이 등장하는 모든 장면에서, *각 인물은 의식적·구체적 의도를 가지고 진입* 하며, *상대 인물 또는 환경이 그 의도의 장애물* 이어야 한다. 둘이 같은 것을 원하거나 누구도 구체적인 것을 원하지 않으면, 그 장면은 대사가 쓰여지기 전에 이미 죽어 있다.

그 위에:

- **Subtext default**
- **리듬이 정서를 추적** — 긴 문장 = 통제, 단편 = 균열, 침묵 후 한 단어 = 붕괴
- **존댓말/반말 전환 = 플롯 사건**
- **회피의 언어 > 발화된 언어**
- **지문 포함**: `...`, `[침묵]`, `[시선을 피한다]`
- **인물별 어휘 레지스터** — 한 줄로 지문 채취 가능
- **Interior voices** (Kurvitz, 선택) — 한 인물 내면을 Reason / Vanity / Guilt 등 라벨로 분기 (남용 금지)

### 5. 월드빌딩 (세계관 / 지명 / 종족)

**중심 문화적 불안** 에서 외부로 빌드. (모든 세계는 자신에 대해 무엇을 두려워하는가?)

- **어원 있는 지명** — 이름이 역사를 폭로(개명된 도시 = 정권 교체)
- **각 세력은 자신이 용서할 수 없는 것으로 정의**, 스탯 차이가 아니라
- **지리는 심리** — 풍경은 정서 상태를 봉사
- **일상의 구체성** — 음식, 장례 노래, 더는 아무도 지키지 않는 명절
- **Setup load** — 모든 지명은 미래 장면 앵커 *최소 하나*
- **환경 서사 규율 (Miyazaki)** — 모든 장소는 *"여기서 무슨 일이 있었나?"* + *"이걸 발견하는 게 플레이어인 의미는?"* 둘 다 답해야 한다

---

## 디렉터리 구조

```
Story-Skill/
├── README.md                              # 이 문서 (프로젝트 소개)
├── SKILL.md                               # 메인 스킬 정의 (description, 5원칙, 5워크플로우)
└── references/                            # 진행 시 깊이 들어갈 때만 읽는 참고 문서
    ├── master-philosophy.md               # 거장 8인의 작법 — 매체 횡단 통합 (철학적 코어)
    ├── narrative-craft.md                 # 내러톨로지·드라마 이론·비트 구조·연출 어휘·게임 서사 이론
    ├── setup-payoff.md                    # 셋업-페이오프 매트릭스, 복선 시스템, 오도 원리
    ├── character-deep-build.md            # 7-layer 템플릿, 자기정당화 모놀로그 워크시트
    ├── style-modes.md                     # 클래식 → 컨템포러리 스타일 카탈로그
    ├── korean-aesthetics.md               # 한국 정서 (jeong / han) 보정
    └── output-formats.md                  # markdown / docx / JSON 템플릿
```

> 진행 정보: 이 저장소는 [Skill-Gen-Agent](https://github.com/Simon-YHKim/Skill-Gen-Agent) 의 `validate_skill.py` / `refactor_skill.py` 로 검증·정제 후 산출됩니다. SKILL.md ≤ 500줄, 참고 문서 단일 단계 깊이, 3차 디스크로저 패턴(high-level / domain-specific / conditional) 강제.

---

## 설치 (Installation)

### 옵션 A — Claude Code 사용자 전역 설치

```bash
# 저장소 클론
git clone https://github.com/Simon-YHKim/Story-Skill.git
cd Story-Skill

# ~/.claude/skills/ 로 복사
mkdir -p ~/.claude/skills/game-story-writer
cp -r SKILL.md references ~/.claude/skills/game-story-writer/
```

### 옵션 B — 프로젝트 로컬 설치

```bash
mkdir -p <your-project>/.claude/skills/game-story-writer
cp -r SKILL.md references <your-project>/.claude/skills/game-story-writer/
```

### 옵션 C — Skill-Gen-Agent 인스톨러로 (검증 후 복사)

```bash
# Skill-Gen-Agent가 설치되어 있다면
python <skill-gen-agent>/scripts/install_skill.py . --user
# 또는 --project <path> 로 프로젝트 로컬 설치
```

설치 후 Claude Code에서 트리거 문구를 자연스럽게 사용하면 자동 발화합니다.

---

## 사용 예시 (Examples)

### 예시 1 — 메인 시놉시스

```
유저: "조선 후기, 명령에 의해 사람을 처형해야 했던 형리의 이야기를
     써줘. 떡밥이 잘 깔린 5막 구조로."

Skill: 5워크플로우 중 ①메인 스토리 진입.
       테마 한 줄 + 중심 상처 + Egri 전제 + 5막 구조 + 변곡점 3개 +
       셋업-페이오프 매트릭스(5쌍) + 여운의 마지막 장면 +
       designed absence 노트 → 8종 산출.
```

### 예시 2 — 캐릭터 백스토리

```
유저: "기사단장 캐릭터 한 명. 정밀하게."

Skill: ②캐릭터 설정 진입. 단일 패러독스 + want/need + the lie +
       자기정당화 모놀로그(1인칭 단락) + 감각 앵커 +
       voice signature + 사물 탤리스먼 + 중력 관계 +
       designed absence per character → 7-layer 산출.
```

### 예시 3 — 사이드 퀘스트 + 대사

```
유저: "NPC가 잃어버린 동생을 찾아달라는 사이드퀘. 대사 스크립트까지."

Skill: ③퀘스트 + ④대사 동시. 표면 목표(동생 찾기) ≠ 감정 대리물 식별,
       3-choice (침묵 옵션 포함), 실패 분기의 새로운 서사 ──
       Sorkin condition (의도 vs 장애물) + 존댓말/반말 전환 이벤트 +
       지문 포함 스크립트 블록 산출.
```

### 예시 4 — 월드빌딩

```
유저: "북방 변경의 잊힌 종족 하나. 지명 5개와 함께."

Skill: ⑤월드빌딩 진입. 중심 문화적 불안 식별 → 어원 있는 지명 5개
       (개명 흔적 포함) + 일상 구체성(음식·장례·명절) +
       각 지명마다 미래 장면 앵커 최소 1개.
```

---

## 출력 포맷 자동 선택

| 컨텍스트 | 포맷 |
|---|---|
| 빠른 브레인스토밍, 탐색 | **Markdown 인라인** |
| 문서 결과물 (캐릭터 바이블, 시나리오 문서) | **`.docx` (docx 스킬 경유)** |
| 게임 엔진 임포트 (NPC 데이터, 다이얼로그 트리, 퀘스트 정의) | **JSON** |
| 혼합 (산문 + 구조 시트) | **Markdown + 첨부 JSON 블록** |

트리거: `문서로`, `정리해서` → docx · `엔진에 임포트`, `스크립트로 뽑아` → JSON · 그 외 인라인. 모호하면 한 번 묻는다.

전체 템플릿: `references/output-formats.md`

---

## 참고 문서 맵 (Reference Map)

| 파일 | 언제 읽는가 |
|---|---|
| `references/master-philosophy.md` | 메이저 프로젝트 시작 시 + 막힐 때마다. **철학적 코어.** |
| `references/narrative-craft.md` | "왜 이 선택?" 또는 공예 설명 요청 시 |
| `references/setup-payoff.md` | 메인 스토리, 멀티-퀘스트 아크, 사용자가 *떡밥 / 복선* 강조 시 |
| `references/style-modes.md` | 스타일이 명시되거나 추론되어야 할 때 |
| `references/character-deep-build.md` | 모든 캐릭터 생성 작업 |
| `references/korean-aesthetics.md` | 브리프가 한국 정서(jeong/han)를 명시할 때. *기본 음성이 아니라 하나의 스타일 모드* |
| `references/output-formats.md` | 결과물 생성 시 |

---

## 거장 8인의 철학 (The Eight Masters)

이 스킬의 표준은 8인의 *교집합* 에서 추출됩니다. 차이점이 아니라.

| 거장 | 매체 | 기여 |
|---|---|---|
| **Dostoevsky** | 소설 | 자기정당화의 *병리적* 추적 — 라스콜니코프의 1인칭 합리화 |
| **Toni Morrison** | 소설 | *Invisible ink*, *rememory* — 행간에 보이지 않는 잉크로 쓰인 것 |
| **Han Kang** | 소설 | *Embodied metaphor* — 신체·감각으로 추상을 운반 |
| **Aaron Sorkin** | 각본 | *Intention and obstacle* — 모든 장면의 죽음/생명 시험 |
| **Vince Gilligan** | TV/각본 | 인덱스카드 인과율 — *Breaking Bad* 의 코르크보드 시스템 |
| **Hidetaka Miyazaki** | 게임 | *Co-writing* — 환경 서사, 단편적 lore, 부재로 함께 쓰기 |
| **Neil Druckmann** | 게임 | *Ludonarrative resonance* — 동사가 테마를 운반 |
| **Robert Kurvitz** | 게임 | *Failure as content* — 실패는 부재가 아니라 다른 이야기 |

전체 분석: `references/master-philosophy.md`

---

## 기본 동작 정책 (Working Defaults)

- **언어** — 모든 in-world 컨텐츠(이름, 대사, 지명)는 한국어 (브리프가 다르게 명시하지 않는 한)
- **Scope matching** — `캐릭터 한 명` 요청은 풍부한 한 명, 명단이 아니다
- **Style preservation** — 한 번 선택·추론된 스타일은 결과물 전체에서 일관되게
- **No filler** — 모든 문장은 내면 폭로 / 플롯 진행 / 셋업 식재·회수 / 테마 정박 / 생산적 부재 설계 중 하나를 한다. 나머지는 잘라낸다
- **The 30% subtraction pass** — 산출 전에 *말해버린 문장* 을 약 30% 잘라내고, 적재된 것만 복원

### 로맨스 가드레일 (중요)

> **로맨스는 기본 테마가 아니다.** 한국 드라마의 공예는 *짜임* 에 있지 *연애 자체* 에 있지 않다. 오픈 브리프에 로맨스를 디폴트로 깔지 않는다.

기본 테마 팔레트(순환):

`책임의 무게` · `죄책감과 자기용서` · `정체성의 균열` · `용서/비용서` · `시대의 균열을 살아내는 개인` · `권력의 대가` · `잊혀진 자의 존엄` · `가족의 부채` · `진실의 대가` · `자기 자신과의 화해` · `합리화의 끝` · `재기억(rememory)`

로맨스가 등장할 때는 위 테마 중 하나의 **vehicle**, 결코 엔진이 아니다.

---

## 언제 부드럽게 밀어내는가 (Pushback Policy)

| 요청 | 응답 |
|---|---|
| `캐릭터 10명 빨리` | (a) 얕은 명단, 또는 (b) 2-3명 깊은 처리 + 나머지 스케치. 사용자 선택 |
| `Make it more romantic` (선행 셋업 없음) | 로맨스를 엔진으로 할지, 한 갈래로 할지 확인 후 진행 |
| `그냥 단순하게` (셋업 식재된 이야기에) | 회수되지 않을 셋업 표시 후 사용자 결정 |
| `플레이어에게 모두 명확히 설명` | 푸시백 — 원칙 5(설계된 부재)가 작품을 *공명* 시킨다고 설명. 행동에 필요한 명료성 + 정서에 필요한 미스터리의 하이브리드 제안 |

이 스킬이 잘 봉사하지 못하는 스타일을 강요당하면, 명시적으로 이름 붙이고 대안 제시.

---

## 언어 정책

- **사용자 인터랙션**: 한국어 ↔ 영어 자유롭게
- **In-world 컨텐츠**: 기본 한국어 (브리프 우선)
- **공예 용어**: 영어 원어 보존 (`mise-en-scène`, `peripeteia`, `ludonarrative`, `anagnorisis`)
- **트리거 문구**: 한국어/영어 모두 발화

---

## 라이선스

MIT License. 자유롭게 포크·수정·배포 가능.

본 스킬은 인용된 거장들의 작품·인터뷰·강연을 학습 자료로 참조합니다. 작품·캐릭터·고유 표현의 모든 권리는 원저자에게 있습니다.

---

## 기여 (Contributing)

이 스킬은 [Skill-Gen-Agent](https://github.com/Simon-YHKim/Skill-Gen-Agent) 워크플로우로 유지됩니다.

기여 절차:

1. 새 브랜치 (`feat/...`, `fix/...`, `docs/...`)
2. 변경 후 `python <skill-gen-agent>/scripts/validate_skill.py .` 통과
3. 새 트리거나 모드를 추가했다면 `evals/cases.json` 도 갱신
4. PR 생성 (Conventional Commits 메시지)

---

## 관련 저장소

- **[Skill-Gen-Agent](https://github.com/Simon-YHKim/Skill-Gen-Agent)** — 이 스킬을 생성·검증·리팩토링하는 메타 도구

---

> *"The work is what remains after everything dispensable has been removed."*
