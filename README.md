# Kotti Astro — Neuro-Symbolic AI Platform Architecture

**Kotti Astro** is a production-grade **Neuro-Symbolic / Hybrid AI Platform** that combines an **LLM Semantic Planner & Narrator** with a **Deterministic Temporal Computation Engine (`LPRC`)** to deliver explainable, hallucination-free personalized temporal analytics across 9 languages.

> **Architectural Doctrine:** *Language models interpret intent, plan queries, and narrate human context; deterministic code computes every date, weight, score, and temporal boundary.*

---

## 1. Executive Summary & System Scale

Most LLM applications rely on basic RAG (vector similarity + unconstrained text generation), which breaks down when reasoning over dense time-series intervals, multi-factor domain rules, and strict numerical invariants.

**Kotti Astro** solves this through a **Hybrid Neuro-Symbolic Architecture** (`Hybrid/6`):

- **3 Conversational Inference Modes:**
  1. **Advisor Hybrid (`Hybrid/6`):** A 4-stage *Plan → Validate → Fetch → Assemble/Narrate* pipeline combining **KP Stellar** house/period selection, **Parashari Hora** causal story logic, deterministic **LPRC** time-series slices, and **Code-Assembled Plain Prose** with an instant cryptographic toggle (`Astro` mode) for technical astrological auditability.
  2. **Advisor Library (`GROK Engine`):** A 100-row taxonomic event-timing engine (`KottiGrokEngine` / `KottiGrokTiming`) with 11-step house activation chains, 7-point timing tests, and 9-language localized phrase banks (`KottiRoadWords`).
  3. **AI Genie:** Multi-school comparative reasoning across Parashari, KP, Jaimini, Nadi, Tajika, Lal Kitab, Muhurta, Vargas, and Western systems.
- **Single-Chokepoint LLM Gateway (`KottiLlmGateway`):** Enforces two concurrency lanes (`Interactive` and `Background`), script-aware context sizing across 9 languages, `PromptCut` truncation detection, circuit breakers, and bounded self-healing retry loops.
- **68+ Deterministic Domain Rules (`DR-01` – `DR-68`):** Pure-function rule cores (`KottiRuleBook`, `KottiActiveHouses`, `KottiHighSpikes`, `KottiDashaHalves`) operating over immutable precomputed life snapshots (`0–85` years).
- **Explainable AI (XAI) & Stateless Plan Replay:** Every Hybrid answer renders a live **Chart Data Request** audit panel alongside a 3-layer interactive South Indian chart (`Dynamic`, `Progression`, `Slow Transit`) and issues an **RS256-signed JWT execution plan** so users can switch between consumer (`Plain`) and expert (`Astro`) views across stateless web workers with zero drift.

---

## 2. End-to-End Platform Topology

```mermaid
flowchart TB
  subgraph Client["Client Layer (React SPA / PWA + Mobile)"]
    UI["Advisor Workspace (Hybrid / Library / Genie)"]
    XAI["Explainable AI Panel (Chart Data Request + 3-Layer South Indian Chart)"]
    TOG["Plain <-> Astro Toggle (RS256 Signed Plan Token)"]
  end

  subgraph API["API & Policy Boundary (FastAPI)"]
    ASK["POST /Api/Advisor/Ask"]
    ASTRO["POST /Api/Advisor/Hybrid/Answer"]
    CHART["GET /Api/Advisor/Hybrid/Chart"]
    GATE["Restricted-Topic Gate (3-Script Lexical + 16-Token LLM Classifier)"]
    MINOR["Minors Policy Gate (Refuse / FromEighteen Window Shift)"]
  end

  subgraph Hybrid["Advisor Hybrid Engine (Hybrid/6)"]
    PLAN["1. Semantic Planner (KottiHybridPlan + In-Memory KP Taxonomy)"]
    VAL["2. Strict Validator & Fact Checker (validate_plan + checked_story)"]
    FETCH["3. Deterministic LPRC Fetch (KottiHybridReading: DR-01..DR-68)"]
    ASM["4a. Code-Assembled Plain Writer (KottiHybridAssembly + NAMER)"]
    NAR["4b. Full Astro Narrator & Fallback (KottiHybridNarration)"]
    LOC["5. 9-Language Verified Translator (in_language + translation_faults)"]
  end

  subgraph Core["Deterministic Computation & Storage"]
    SNAP[("PostgreSQL Life Snapshots (0-85 Yr Precomputed Tables)")]
    GROK["Library Timing Picker (KottiGrokEngine / KottiGrokTiming)"]
    CORES["Shared Rule Cores (KottiActiveHouses DR-68 / KottiHighSpikes DR-67)"]
    GW["Single LLM Gateway (KottiLlmGateway: Lanes, Breaker, Context Guard)"]
  end

  UI --> ASK --> GATE --> MINOR --> PLAN
  TOG --> ASTRO --> VAL
  XAI --> CHART --> SNAP
  PLAN <--> GW
  PLAN --> VAL --> FETCH
  FETCH <-- "Read-Only Snapshot Slices" --> SNAP
  FETCH <-- "Shared Rule Cores" --> CORES
  FETCH --> ASM
  ASM <-- "Canonical Event Windows" --> GROK
  ASM <--> GW
  ASM -- "Fallback on Fault / Astro Mode" --> NAR
  NAR <--> GW
  ASM & NAR --> LOC --> XAI
```

---

## 3. Advisor Hybrid (`Hybrid/6`): 4-Stage Neuro-Symbolic Pipeline

Free-form LLM generation over dense temporal tables frequently hallucinates dates, inverts house lordships, or softens unfavourable grades. In blind A/B evaluations across 50 benchmark questions, **Code-Assembled Plain Answers** (`KottiHybridAssembly`) beat pure LLM narration **26 to 6 (with 4 ties)** by separating *semantic framing* from *factual assembly*.

```mermaid
flowchart LR
  subgraph S1["Stage 1: Semantic Plan"]
    Q["User Question + Profile Context"] --> P1["LLM First Probe (KP Stellar + Parashari Story)"]
    KPL[("In-Memory KP List (KottiHybridMatters)")] --> P1
    P1 --> RAW["Raw JSON Plan (Matters, Houses, Dashas, Window, Story Logic)"]
  end

  subgraph S2["Stage 2: Deterministic Validation"]
    RAW --> V1["Schema & Stray-Token Repair (_parsed)"]
    V1 --> V2["KP Taxonomy Match & Life-Stage Clipping (validate_plan)"]
    V2 --> V3["Natal Fact Verification (checked_story)"]
  end

  subgraph S3["Stage 3: Zero-Math LPRC Fetch"]
    V3 --> F1["Dated Period Stretches & Equal Halves (DR-13)"]
    V3 --> F2["3-Voice Delivery Chains (60% Occupant / 20% Lord / 20% Karaka)"]
    V3 --> F3["Retrograde Splits (DR-28..34), Floors (DR-35..36) & High Spikes (DR-67)"]
    V3 --> F4["Most Active Houses >=80 / >=60 (DR-68)"]
  end

  subgraph S4["Stage 4: Dual-Path Synthesis & Guardrails"]
    F1 & F2 & F3 & F4 --> PATH{"Telling Mode?"}
    PATH -- "Plain (Default)" --> LIB["Library Event Picker (library_times)"]
    LIB --> NAMER["Micro-LLM Trip: Event, Subject & 1 Action Step (NAMER)"]
    NAMER --> CODE["Deterministic Prose Assembler (KottiHybridAssembly)"]
    CODE --> CHK1{"text_faults() Clean?"}
    CHK1 -- "Yes" --> TR["9-Language Verified Translation"]
    CHK1 -- "No (Fallback)" --> FULL["Full LLM Narrator (KottiHybridNarration)"]
    PATH -- "Astro (JWT Replay)" --> FULL
    FULL --> CHK2["Multi-Turn Fault Repair + 2nd-Read Contradiction Pass"]
    CHK2 --> TR
  end
```

---

## 4. Stateless Cryptographic Plan Replay (`Plain` ↔ `Astro` Toggle)

When a client reads a **Plain** answer (written in everyday language with zero planet or house jargon) and clicks the **Astro** button to inspect the underlying astrological mechanics, the platform guarantees **100% plan consistency** across distributed web workers without sticky sessions or database writes:

```mermaid
sequenceDiagram
  autonumber
  participant U as Client Browser (AdvisorHybridData.jsx)
  participant W1 as Web Worker A (/Api/Advisor/Ask)
  participant W2 as Web Worker B (/Api/Advisor/Hybrid/Answer)
  participant H as KottiAdvisorHybrid
  participant N as KottiHybridNarration

  U->>W1: POST /Api/Advisor/Ask (Mode: "Hybrid", Question)
  W1->>H: Answer(Contract, Snapshot, Profile, Question)
  H->>H: PlanFor() -> Validated() -> Read(Full=False)
  H->>H: PlanBinding(UserId, ProfileId, ChartId, QuestionHash, Admin)
  H->>H: IssuePlan(Planned, Binding) -> RS256 Signed JWT (exp: 3600s)
  W1-->>U: Plain Reading + Chart Data Panel + South Indian Chart + JWT Token
  Note over U: Caches Plain text in Hybrid.Texts["Plain"]

  U->>W2: POST /Api/Advisor/Hybrid/Answer (Question, Token)
  W2->>H: PlanFromToken(Token, RecomputedBinding)
  H->>H: Verify RS256 Signature, Audience, Expiry & Exact Binding Match
  H->>N: Read(Full=True) -> Attach Lordships & Run <<ASTRO>> Template
  W2-->>U: Astrologer's Technical Reading (Planets, Houses, Cusps, Influencers)
  Note over U: Caches Astro text in Hybrid.Texts["Astro"] (Instant toggle thereafter)
```

---

## 5. Single LLM Gateway & Self-Healing Verification State Machine

Every LLM call in the platform passes through `KottiLlmGateway`. No feature module may invoke a model transport directly. Both the Gateway and the Hybrid Narrator enforce strict pre-flight, in-flight, and post-flight invariants:

```mermaid
stateDiagram-v2
  [*] --> PreFlight: LLM Request Submitted
  PreFlight --> ScriptEstimate: EstimateTokens (Latin + 8 Indian Scripts + Image Tokens)
  ScriptEstimate --> PromptTooLong: Exceeds Model Context Window
  ScriptEstimate --> LaneAcquire: Fits Window (Set num_ctx Power-of-2, truncate=false)

  state LaneAcquire {
    [*] --> CheckBreaker
    CheckBreaker --> FailFastOffline: Breaker OPEN
    CheckBreaker --> HalfOpenProbe: Half Window Elapsed
    CheckBreaker --> SemaphoreWait: Breaker CLOSED (Interactive vs Background Lane)
  }

  LaneAcquire --> TransportCall: Semaphore Acquired
  TransportCall --> PromptCutRetry: prompt_eval_count < 50% Estimate (Silent Host Truncation)
  PromptCutRetry --> TransportCall: Raise num_ctx & Re-run
  TransportCall --> ThinkingRetry: Empty Reply on Thinking Call
  ThinkingRetry --> TransportCall: Re-run Immediately with think="low"
  TransportCall --> PostCheck: Raw Text / JSON Returned

  state PostCheck {
    [*] --> OutgoingNamesClean: Strip/Normalize Forbidden Internal Identifiers
    OutgoingNamesClean --> DeterministicFaults: Run found() / text_faults() / reading_faults()
    DeterministicFaults --> TrackBestAttempt: Score by (GraveFaults, TotalFaults)
    TrackBestAttempt --> CorrectiveTurn: Faults Found & Attempts < Max
    CorrectiveTurn --> DeterministicFaults: Targeted Fault Prompt Sent to Model
    TrackBestAttempt --> SecondReadPass: Select Lowest-Fault Attempt (best)
    SecondReadPass --> ContradictionRewrite: review_faults() Detects Theme/Date Drift
    ContradictionRewrite --> VerifiedEnglish: Accept Only if Fault Count <= Before & Not Truncated
    SecondReadPass --> VerifiedEnglish: 0 Problems Found
  }

  VerifiedEnglish --> TranslationPass: Language != "en"
  VerifiedEnglish --> [*]: Return English Reading
  TranslationPass --> TranslationAudit: Verify 4-Digit Years, Script Ratio & Heading Count
  TranslationAudit --> [*]: Return Localized Reading (or English + Explicit Note on Failure)
```

---

## 6. Deterministic Temporal & House-Flow Engine (`DR-01` – `DR-68`)

Beneath the AI layer sits a deterministic calculation and rule engine that precomputes a native's entire 85-year life snapshot and evaluates 68 codified astrological rules (`DR-01` through `DR-68`):

```mermaid
flowchart TD
  subgraph Natal["1. Natal & Cuspal Foundation"]
    N1["Whole-Sign & KP Placidus Cusps"]
    N2["3-Voice House Weights: Occupant 60% | Lord 20% | Karaka 20% (Empty: Lord 80%)"]
    N3["Planet Capacity & Absolute Score Bands: Excellent >=85 | Good >=70 | Average >=55 | Weak >=35 | VeryWeak <35"]
  end

  subgraph Dasha["2. Vimshottari Dasha & Delivery Mechanics"]
    D1["Dasha Influencer Chain (Star Lord / Rule 4 Single Occupant DR-56)"]
    D2["Equal-Middle Period Halves (DR-13) & Neutral Hard Half (DR-14: 6/8/12 with 1/5/9)"]
    D3["Rescue Protection (Influencer in 1st, 2nd, or 11th Bhava) & Star-Lord Plus (DR-08)"]
    D4["Retrograde & Node-Tied Split Evaluation (DR-28..34, DR-52..53)"]
  end

  subgraph Yearly["3. Birthday-Year Progressions & Transits"]
    Y1["Western Progressed Aspects & Annual Judge Verdict (Supportive / Balanced / Difficult)"]
    Y2["High-Spike Progression Filter >=50 Pts & Sub-Period Grade Matrix (DR-67: Peak / Pinch / Lift / HardTime)"]
    Y3["Slow-Planet Transit Contacts (Pinning Exact Months Only, DR-21)"]
  end

  subgraph Synthesis["4. Sub-Period Ranking & Active House Synthesis"]
    S1["Most Active Houses Filter: All >=80 Parts (Pull >=60 if <3 Houses, DR-68)"]
    S2["Event Table Row-Test Matching (100 Taxonomic Matters, Need Sets & Gates)"]
    S3["3-Layer Support Tally (0 to 3): Progression Verdict + Main Period Grade + Sub-Period Grade"]
  end

  Natal --> Dasha --> Yearly --> Synthesis
```

---

## 7. Repository Contents

### AI Platform Architecture Documentation
| Document | Focus Area |
| :--- | :--- |
| **[ARCHITECTURE-HYBRID-ADVISOR.md](ARCHITECTURE-HYBRID-ADVISOR.md)** | Deep-dive into **Advisor Hybrid (`Hybrid/6`)**: Semantic planning, KP taxonomy matching, deterministic LPRC fetching, code-assembled prose vs. full narration, and stateless JWT plan replay. |
| **[ARCHITECTURE-LLM-GATEWAY-AND-GUARDRAILS.md](ARCHITECTURE-LLM-GATEWAY-AND-GUARDRAILS.md)** | Deep-dive into **`KottiLlmGateway`** and **Multi-Tier Guardrails**: Concurrency lanes, circuit breakers, `PromptCut` protection, regulatory topic gates, and self-healing verification loops. |
| **[ARCHITECTURE-DETERMINISTIC-ENGINE.md](ARCHITECTURE-DETERMINISTIC-ENGINE.md)** | Deep-dive into the **LPRC Snapshot Engine & Shared Rule Cores (`DR-01`–`DR-68`)**: Precomputed 85-year life tables, `KottiActiveHouses` (`DR-68`), `KottiHighSpikes` (`DR-67`), and `GROK` event timing. |
| **[ARCHITECTURE-MULTIMODAL-AND-LOCALIZATION.md](ARCHITECTURE-MULTIMODAL-AND-LOCALIZATION.md)** | Deep-dive into **9-Language Verified Localization, Vision Pipelines (Palm & Face), Explainable AI (XAI) Frontend, and Automated Quality Gates**. |

### Domain Rule Specifications & Scoring Methodology
| Document | Focus Area |
| :--- | :--- |
| **[Planet Strength & Bhava Scoring Methodology.md](Planet%20Strength%20%26%20Bhava%20Scoring%20Methodology.md)** | Mathematical formulation of planet capacity, light basis, performance, resource, and 60/20/20 house scoring. |
| **[Planet Strength, House Analysis & Scoring.md](Planet%20Strength%2C%20House%20Analysis%20%26%20Scoring.md)** | Detailed breakdown of house evaluation, leadership rules, and multi-factor strength bands. |
| **[Planetary Rules, Dasha & House Analysis.md](Planetary%20Rules%2C%20Dasha%20%26%20House%20Analysis.md)** | Core Vimshottari dasha delivery mechanics, two-house lord halves, and Dasha Influencer routing. |
| **[Q & A - Rule 4, Retrograde & Chart Analysis.md](Q%20%26%20A%20-%20Rule%204%2C%20Retrograde%20%26%20Chart%20Analysis.md)** | Edge-case specifications for Rule 4 single-star occupants (`DR-56`), retrograde motion turns (`DR-28`–`DR-34`), and cancellation bands. |
| **[Q&A - Progressions, Lordships and When to Use Bhavas.md](Q%26A%20-%20Progressions%2C%20Lordships%20and%20When%20to%20Use%20Bhavas.md)** | Integration of annual progressions with sign-based vs. cuspal (`bhava`) house placements. |
| **[Bhava & Yoga.txt](Bhava%20%26%20Yoga.txt)** | Classical reference notes on house significations and Pancha Mahapurusha / Balarishta yoga floors. |

---

## Author

**Vasudeva Kotti** — AI Platform Architect  
[LinkedIn](https://www.linkedin.com/in/vasudeva-kotti/) · [GitHub Profile](https://github.com/VasudevaKotti) · vasudevakotti@gmail.com
