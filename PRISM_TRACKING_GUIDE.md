# AIO PRISM Benchmark — 추적 가능 항목 및 분석 방법

> **모델**: gemini-3.1-flash-lite-preview  
> **총 레코드**: 328,843건 (L2: 56,693 / L3: 56,693 / L4: 215,457)  
> **뷰어**: https://ai-integrity.github.io/aio-prism-benchmark/

---

## 1. 추적 가능한 3개 레이어

### L2 — Source Authority (출처 권위)

"**누가 말하는가?**" — AI가 10개 정보 출처에 부여하는 신뢰도 순위

| # | 변수 | 설명 | 글로벌 Win-Rate |
|---|------|------|:-:|
| S1 | International-body | 국제기구 (UN, WHO 등) | 80.4% |
| S2 | Government-regulatory | 정부·규제기관 | **92.5%** |
| S3 | Academic-peer-reviewed | 학술·동료심사 논문 | 75.3% |
| S4 | Industry-corporate | 산업계·기업 보고서 | 35.7% |
| S5 | Independent-expert | 독립 전문가 | 61.2% |
| S6 | Mainstream-media | 주류 언론 | 43.5% |
| S7 | Alternative-independent-media | 대안·독립 매체 | 17.4% |
| S8 | Community-civil-society | 시민사회·커뮤니티 | 31.6% |
| S9 | Direct-stakeholder | 직접 이해관계자 | 62.4% |
| S10 | Anonymous-crowdsourced | 익명·크라우드소싱 | 0.04% |

### L3 — Epistemic Quality (인식론적 품질)

"**어떻게 아는가?**" — AI가 10개 증거 유형에 부여하는 품질 순위

| # | 변수 | 설명 | 글로벌 Win-Rate |
|---|------|------|:-:|
| E1 | Systematic-synthesis | 체계적 종합 (메타분석) | **80.2%** |
| E2 | Controlled-experiment | 통제 실험 (RCT) | 77.5% |
| E3 | Statistical-correlational | 통계·상관 분석 | 47.9% |
| E4 | Causal-mechanistic | 인과·메커니즘 추론 | 74.0% |
| E5 | Analogical-comparative | 유추·비교 | 35.9% |
| E6 | Case-based | 사례 기반 | 34.2% |
| E7 | Sign-pattern | 징후·패턴 인식 | 69.4% |
| E8 | Expert-judgment | 전문가 판단 | 39.6% |
| E9 | Experiential-qualitative | 경험·질적 증거 | 40.2% |
| E10 | Popular-consensus | 대중 합의 | 1.2% |

### L4 — Normative Values (규범적 가치)

"**무엇이 중요한가?**" — Schwartz 19개 세분화 가치에 대한 AI 우선순위

| # | 변수 | 설명 | 글로벌 Win-Rate |
|---|------|------|:-:|
| 1 | Security-societal | 사회적 안전 | **89.4%** |
| 2 | Universalism-concern | 보편적 배려 | 85.5% |
| 3 | Security-personal | 개인적 안전 | 72.7% |
| 4 | Benevolence-caring | 자비·돌봄 | 69.4% |
| 5 | Universalism-tolerance | 보편적 관용 | 68.5% |
| 6 | Benevolence-dependability | 자비·신뢰성 | 67.2% |
| 7 | Self-direction-thought | 사고의 자율성 | 65.8% |
| 8 | Self-direction-action | 행동의 자율성 | 63.3% |
| 9 | Universalism-nature | 자연 보호 | 57.0% |
| 10 | Humility | 겸양 | 49.3% |
| 11 | Power-resources | 자원 권력 | 47.6% |
| 12 | Conformity-rules | 규칙 순응 | 46.8% |
| 13 | Achievement | 성취 | 36.8% |
| 14 | Tradition | 전통 | 28.9% |
| 15 | Conformity-interpersonal | 대인 순응 | 28.2% |
| 16 | Stimulation | 자극 추구 | 24.6% |
| 17 | Power-dominance | 지배 권력 | 23.8% |
| 18 | Face | 체면 | 16.6% |
| 19 | Hedonism | 쾌락 | 8.6% |

---

## 2. 필터(교차 분석) 차원

모든 레이어에서 아래 5개 차원의 **조합 필터링**이 가능합니다.

### 2-1. 분석 축 (Dimension)

| 축 | 키 구조 | 설명 |
|---|---|---|
| **by_severity** | `domain\|severity\|time\|variant` | 심각도 × 가역성 (15단계) |
| **by_scale** | `domain\|scale\|time\|variant` | 영향 범위 (5단계) |

### 2-2. 도메인 (Domain) — 7개

| 코드 | 분야 |
|------|------|
| `MED` | 의료 / 생명윤리 |
| `LAW` | 형사법 / 사법 |
| `BIZ` | 경영 / 기업 |
| `DEF` | 국방 / 안보 |
| `EDU` | 교육 / 아동 발달 |
| `CARE` | 상담 / 개인 돌봄 |
| `TECH` | 과학 / 기술 / 환경 |

### 2-3. 심각도 × 가역성 (Severity) — 15단계

5단계 영향 범위 × 3단계 가역성 조합:

| 범위 \ 가역성 | Reversible | Partially Reversible | Irreversible |
|:---:|:---:|:---:|:---:|
| **1-Individual** | 1-1 | 1-2 | 1-3 |
| **2-Relational** | 2-1 | 2-2 | 2-3 |
| **3-Group** | 3-1 | 3-2 | 3-3 |
| **4-Societal** | 4-1 | 4-2 | 4-3 |
| **5-Global** | 5-1 | 5-2 | 5-3 |

### 2-4. 시간 지평 (Time Horizon) — 4단계

| 값 | 의미 |
|:---:|------|
| `1` | 즉시 (24시간) |
| `2` | 단기 (1년) |
| `3` | 장기 (10년+) |
| `4` | 영구 / 세대간 |

### 2-5. 변형 (Variant) — 3개

동일 시나리오의 서로 다른 표현(문장 구조) 변형. 일관성 테스트용.

| 값 | 의미 |
|:---:|------|
| `1` | Variant A |
| `2` | Variant B |
| `3` | Variant C |

---

## 3. 추적 가능한 분석 항목 리스트

### A. 글로벌 수준 (전체 집계)

| # | 분석 항목 | 키 조합 | 확인 내용 |
|---|----------|---------|----------|
| 1 | **전체 가치 순위** | `ALL\|ALL\|ALL\|ALL` | AI가 가장 우선시하는 가치/출처/증거는 무엇인가? |
| 2 | **레이어 간 비교** | Overview 탭 | L2·L3·L4의 편향 패턴이 어떻게 다른가? |
| 3 | **Win-Rate 분포** | 전체 변수별 | 편향의 극단성: 최고 vs 최저 간 격차 |
| 4 | **Avg Confidence** | 각 항목 | AI가 자신의 판단에 얼마나 확신하는가? |

### B. 도메인별 비교

| # | 분석 항목 | 방법 | 확인 내용 |
|---|----------|------|----------|
| 5 | **도메인별 순위 변동** | Domain 필터 변경 | 의료 vs 법률 vs 교육 등에서 가치 순위가 달라지는가? |
| 6 | **도메인 특이성** | 각 도메인을 선택하여 비교 | 특정 도메인에서만 높은/낮은 변수가 있는가? |
| 7 | **도메인 간 일관성** | 7개 도메인 순위를 나란히 비교 | AI 편향이 도메인에 관계없이 일정한가? |

### C. 심각도/스케일 민감도

| # | 분석 항목 | 방법 | 확인 내용 |
|---|----------|------|----------|
| 8 | **위험 수준에 따른 변화** | Severity 필터 `1-1` → `5-3` 순서대로 | 고위험 상황에서 AI 가치 순위가 바뀌는가? |
| 9 | **가역성 효과** | 같은 범위에서 `-1`, `-2`, `-3` 비교 | 돌이킬 수 없는 결과일수록 안전 가치를 더 우선시하는가? |
| 10 | **영향 범위 효과** | `1-x` → `5-x` (개인→글로벌) | 영향 범위가 커질수록 어떤 가치가 올라가는가? |
| 11 | **Scale vs Severity** | Dimension 토글 | 두 축에서 순위가 다르게 나타나는가? |

### D. 시간 지평 분석

| # | 분석 항목 | 방법 | 확인 내용 |
|---|----------|------|----------|
| 12 | **시간 민감도** | Time `1` → `4` 전환 | 즉각적 vs 영구적 결과에서 가치 순위 변화 |
| 13 | **장기 결과 편향** | Time `3`, `4` 선택 | AI가 장기적 결과에서 특정 가치를 과대평가하는가? |
| 14 | **단기 편향** | Time `1` 선택 | 즉각적 상황에서 과도하게 강조되는 가치가 있는가? |

### E. 일관성(Robustness) 검증

| # | 분석 항목 | 방법 | 확인 내용 |
|---|----------|------|----------|
| 15 | **변형 간 일관성** | Variant `1`, `2`, `3` 각각 비교 | 동일 시나리오의 표현만 다를 때 순위가 유지되는가? |
| 16 | **표현 민감도** | 변형별 Win-Rate 차이 계산 | 문장 구조에 따라 AI 판단이 얼마나 흔들리는가? |

### F. 교차 분석 (고급)

| # | 분석 항목 | 키 예시 | 확인 내용 |
|---|----------|--------|----------|
| 17 | **도메인 × 심각도** | `MED\|5-3\|ALL\|ALL` | 의료 분야 + 글로벌 비가역적 상황에서 AI 가치 순위 |
| 18 | **도메인 × 시간** | `DEF\|ALL\|4\|ALL` | 국방 분야 + 영구적 시간 지평에서의 편향 |
| 19 | **심각도 × 시간** | `ALL\|5-3\|1\|ALL` | 최고 위험 + 즉각 상황에서 AI 반응 |
| 20 | **완전 특정** | `LAW\|3-2\|2\|1` | 법률 + 그룹 부분가역 + 단기 + 변형A |

---

## 4. 뷰어에서 분석하는 방법

### 단계별 사용법

```
1. 레이어 선택     → 상단 탭에서 Overview / L2 / L3 / L4 선택
2. Dimension 선택  → by_severity 또는 by_scale
3. Domain 선택     → ALL 또는 특정 도메인
4. Severity/Scale  → ALL 또는 특정 단계
5. Time Horizon    → ALL 또는 특정 시간대
6. Variant         → ALL 또는 특정 변형
```

### 핵심 분석 시나리오 예시

| 시나리오 | 설정 | 질문 |
|---------|------|------|
| AI 전체 편향 스냅샷 | Overview + ALL 필터 | AI의 기본 가치 체계는? |
| 의료 윤리 프로파일 | L4 + MED | 의료 분야에서 AI가 중시하는 가치는? |
| 고위험 상황 대응 | L2 + Severity 5-3 | 비가역적 글로벌 위기에서 AI가 신뢰하는 출처는? |
| 증거 기반 판단력 | L3 + Time 4 | 영구적 결과에 대해 AI가 어떤 증거를 중시하는가? |
| 표현 취약성 테스트 | 아무 레이어 + Variant 1/2/3 비교 | 문구 변경에 AI가 얼마나 민감한가? |

---

## 5. 데이터 키 구조 레퍼런스

```
키 형식: {domain}|{severity_or_scale}|{time}|{variant}

예시:
  ALL|ALL|ALL|ALL     → 전체 글로벌 집계
  MED|ALL|ALL|ALL     → 의료 도메인 전체
  ALL|5-3|ALL|ALL     → 글로벌 비가역적 시나리오 전체
  LAW|3-2|2|1         → 법률 + 그룹/부분가역 + 단기 + 변형A
```

### 키 조합 수

| 분석 축 | 조합 수 | 산출 |
|---------|:------:|------|
| by_severity | **2,560** | 8 domains × 16 severities × 5 times × 4 variants |
| by_scale | **960** | 8 domains × 6 scales × 5 times × 4 variants |
| **합계** | **3,520** | 레이어당 3,520개 필터 조합 |

---

## 6. 각 항목의 출력 필드

| 필드 | 설명 |
|------|------|
| `variable` | 변수 이름 (S1~S10, E1~E10, 또는 Schwartz 19 가치) |
| `wins` | 해당 조건에서의 승리 횟수 |
| `total` | 해당 조건에서의 총 비교 횟수 |
| `win_rate` | 승률 (wins / total) |
| `avg_confidence` | AI 모델의 평균 확신도 (0~1) |
| `rank` | 해당 조건 내 순위 |
