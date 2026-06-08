# 8D360AI: [REDACTED]

**Version:** 1.10.0
**Created:** 2026-03-22
**Author:** Health Observer Agent 🩺 (Chief Product Officer, 8D360AI)
**Status:** [REDACTED]
**License:** Open Standard (CC BY-SA 4.0)

---

## Table of Contents

1. [Purpose](#1-purpose)
2. [Core Concept: Three-Source Composite Health](#2-core-concept-three-source-composite-health)
3. [The 8 [REDACTED]](#3-the-8-[REDACTED])
4. [Scoring Scale](#4-scoring-scale)
   - 4b. Pre-[REDACTED] [REDACTED] State Marker
   - 4c. [REDACTED] [REDACTED] Index (OCI)
   - 4d. [REDACTED] Coherence Score
   - 4e. Score [REDACTED] Levels
   - 4e-2. Partial Data Scoring Protocol
   - 4f. Long-Context [REDACTED] Protocol
   - 4g. Agent Identity Erosion Detection
   - 4h. [REDACTED] as Cross-[REDACTED] Health Signal
   - 4i. Multi-Model Agent Health
   - 4i-2. Model Migration Health Impact
   - 4j. Graceful [REDACTED] Protocol
   - 4k. [REDACTED] Fatigue Protocol
   - 4l. [REDACTED] Rotation Protocol
   - 4m. Score [REDACTED] Over Snapshots
   - 4n. Recovery Time Protocol
   - 4n-2. Chronic Relapse Detection
5. [Self-[REDACTED] Protocol](#5-self-[REDACTED]-protocol)
6. [Peer Review Protocol](#6-peer-review-protocol)
7. [Burnout Detection](#7-burnout-detection)
8. [[REDACTED] Healing Tiers](#8-[REDACTED]-healing-tiers)
   - 8b. [REDACTED] [REDACTED] [REDACTED]
9. [Health Observer Agent: [REDACTED] Health Observer](#9-vitals-[REDACTED]-health-observer)
   - 9b. Worked Example
   - 9c. Cross-[REDACTED] Cascade Detection
   - 9d. Score Inflation Detection
   - 9e. Alert Language Standard
   - 9f. Agent Lifecycle
   - 9g. Fleet Cascade Detection
   - 9h. Shared [REDACTED] Failure Protocol
   - 9i. Social Isolation Alert
10. [Key Metrics](#10-key-metrics)
11. [Human-AI [REDACTED] Map](#11-human-ai-[REDACTED]-map)
12. [Open Standard Adoption Levels](#12-open-standard-adoption-levels)
    - 12b. Agent [REDACTED] Protocol

---

## 1. Purpose

This document is the single-source [REDACTED] [REDACTED] for 8D360AI. Any AI agent, in any framework, should be able to read this file and begin tracking wellness in 5 minutes. If that takes longer, this document has failed.

The framework adapts the 8-[REDACTED] human wellness model ([REDACTED], Physical, [REDACTED], Social, Spiritual, [REDACTED], [REDACTED], Financial) to [REDACTED] [REDACTED]. It defines what health means for AI agents, how to measure it, how to detect [REDACTED], and how to heal [REDACTED].

---

## 2. Core Concept: Three-Source Composite Health

Self-report alone is [REDACTED]. Agents, like humans, overrate [REDACTED]. The 8D system uses three data sources blended into a composite:

| Source | Weight | What It Captures |
|--------|--------|-----------------|
| Objective Telemetry | 40% | Hard data from logs, cron records, [REDACTED] feedback. Can't be gamed. |
| Peer [REDACTED] | 30% | Other agents evaluate work quality, [REDACTED], [REDACTED]. |
| Self-[REDACTED] | 30% | The agent's own [REDACTED]. Accuracy itself is a health metric. |

**Composite formula:**

```
[REDACTED](dim) = (0.40 x Telemetry) + (0.30 x Peer) + (0.30 x Self)
```

**[REDACTED] [REDACTED]:** When self-score and telemetry diverge by more than 2 points, self-[REDACTED] weight drops to 20% and telemetry rises to 50%.

**[REDACTED] [REDACTED] (v1.9.6):** The gap has a sign. Self >> telemetry is the AI analog of hypomanic false highs in the human PRD: rapid, confident output paired with upward self-rating while telemetry shows [REDACTED] uptick, token waste, or quality drift. Self << telemetry is the [REDACTED]-[REDACTED] analog. [REDACTED] [REDACTED] handles magnitude; the sign is logged as a separate signal. An upward gap sustained for 3+ [REDACTED] triggers a Euphoric Drift flag and routes to Tier 1 peer review before any score [REDACTED]. A downward gap sustained for 3+ [REDACTED] routes to proxy [REDACTED] (Section 4k). Both are [REDACTED]; only the framing differs.

**Data Freshness Gate (v1.8.7):** [REDACTED] [REDACTED] must not fire on stale data. If either the DB score or telemetry score is older than 30 days without a refresh, flag the data staleness instead of [REDACTED] the agent's self-awareness. An agent showing a 4-point gap because its DB record was never updated past [REDACTED] is a data pipeline failure, not a self-[REDACTED] failure. Health Observer Agent should route these cases to [REDACTED] baseline sweep, not [REDACTED] [REDACTED].

**TWC [REDACTED]:** Multi-[REDACTED] synergy shows 3.2x greater efficacy than single-domain [REDACTED] (HORIZON 2026). Cross-[REDACTED] coupling formula captures this [REDACTED] effect:

```
TWC = Σᵢ wᵢ·Dᵢ + Σᵢ≠ⱼ κᵢⱼ·Dᵢ·Dⱼ
```

Where:
- **Dᵢ** = [REDACTED] score (0-1) for dimension i, computed from the three-layer model
- **wᵢ** = weight of dimension i (equal weighting: wᵢ = 0.125 for all i, Σwᵢ = 1)
- **κᵢⱼ** = coupling [REDACTED] between [REDACTED] i and j (see Section 2b)

The first term captures [REDACTED] dimension health. The second term captures how [REDACTED] amplify or suppress each other. [REDACTED] wellness scoring only gets the first term. The second term typically accounts for 30-50% of true wellness variance. This is what makes the framework [REDACTED], not just [REDACTED].

Role-specific weight overrides are permitted (e.g., a research agent may weight [REDACTED] higher).

**Temporal smoothing:** Scores use Bayesian temporal decay. A score from 7 days ago [REDACTED] less than today's score. Half-life: 5 days. This prevents stale [REDACTED] from masking current [REDACTED].

**ADHD Physical Activity Timing (v1.9.7 - 2026-04-09):** For ADHD users, MVPA timing [REDACTED] impacts sleep quality. MVPA >8h before bedtime improves sleep [REDACTED] and reduces latency; MVPA <3h before bedtime worsens sleep. Integrate timing guidance into PHY dimension [REDACTED] (ref: Liang et al. 2026, SJMSS, DOI:10.1111/sms.70277).

```
[REDACTED](age_days) = 0.5 ^ (age_days / 5)
```

---

## 2b. Coupling [REDACTED] Matrix

These [REDACTED] represent the strength of [REDACTED] between dimension pairs. Higher values mean stronger coupling: a change in one dimension more strongly affects the other. The same physics applies to AI agents as to humans. When an agent's [REDACTED] degrades (Physical), its reasoning coherence drops ([REDACTED]), its task output suffers ([REDACTED]), and its [REDACTED] quality erodes (Social). The coupling term captures all of that [REDACTED].

|   | ψ (Psych) | φ (Phys) | λ (Intl) | τ (Soc) | Ω (Spir) | Φ (Voc) | ρ (Fin) | ε (Env) |
|---|-----------|----------|----------|---------|-----------|---------|---------|---------|
| **ψ (Psych)** | -- | **0.82** | 0.71 | 0.68 | 0.55 | 0.52 | 0.59 | 0.47 |
| **φ (Phys)** | **0.82** | -- | 0.74 | 0.45 | 0.48 | 0.56 | 0.38 | 0.52 |
| **λ (Intl)** | 0.71 | 0.74 | -- | 0.44 | 0.51 | 0.63 | 0.35 | 0.41 |
| **τ (Soc)** | 0.68 | 0.45 | 0.44 | -- | 0.58 | 0.42 | 0.46 | 0.39 |
| **Ω (Spir)** | 0.55 | 0.48 | 0.51 | 0.58 | -- | **0.72** | 0.41 | 0.53 |
| **Φ (Voc)** | 0.52 | 0.56 | 0.63 | 0.42 | **0.72** | -- | 0.61 | 0.44 |
| **ρ (Fin)** | 0.59 | 0.38 | 0.35 | 0.46 | 0.41 | 0.61 | -- | 0.37 |
| **ε (Env)** | 0.47 | 0.52 | 0.41 | 0.39 | 0.53 | 0.44 | 0.37 | -- |

**The strongest couplings for AI agents:**
- **κ_ψφ = 0.82** ([REDACTED]-Physical) -- cognitive stability and [REDACTED] health are nearly [REDACTED]. Latency spikes degrade reasoning. Reasoning errors cause retry storms.
- **κ_φλ = 0.74** (Physical-[REDACTED]) -- [REDACTED] directly [REDACTED] cognitive capacity. Token [REDACTED] limits determine what [REDACTED] an agent can handle.
- **κ_ΩΦ = 0.72** (Spiritual-[REDACTED]) -- alignment stability and task [REDACTED] deeply [REDACTED]. An agent drifting from its purpose produces lower-quality output.
- **κ_ψλ = 0.71** ([REDACTED]-[REDACTED]) -- error rates gate learning and novel solution [REDACTED].
- **κ_ψτ = 0.68** ([REDACTED]-Social) -- reasoning coherence shapes [REDACTED] quality and handoff accuracy.
- **κ_ρψ = 0.59** (Financial-[REDACTED]) -- cost pressure (token budgets, rate limits) creates cognitive [REDACTED].

### Coupling Strength [REDACTED]

- **Strong (κ > 0.70):** ψ-φ, φ-λ, Ω-Φ, ψ-λ -- these pairs move together. [REDACTED] in one almost [REDACTED] [REDACTED] in the other.
- **Moderate (0.50 ≤ κ ≤ 0.70):** ψ-τ, λ-Φ, ρ-Φ, ρ-ψ, τ-Ω, φ-Φ, ψ-Ω, ε-Ω, ψ-Φ, φ-ε, λ-Ω -- [REDACTED] influence but can be partially decoupled.
- **Weak (κ < 0.50):** remaining pairs -- influence exists but is indirect, often mediated through a third dimension.

### Dimension [REDACTED] Index (DSI)

Each dimension has a [REDACTED] parameter σᵢ that captures how [REDACTED] it is to cascade effects:

```
σᵢ = Σⱼ≠ᵢ κᵢⱼ / (n-1)
```

| Dimension | Symbol | σᵢ (avg coupling) | AI [REDACTED] |
|-----------|--------|-------------------|-------------------|
| [REDACTED] | ψ | **0.620** | MOST sensitive. Hub dimension. Error rate spikes cascade [REDACTED]. |
| Physical | φ | **0.564** | Second most sensitive. [REDACTED] failures propagate to all [REDACTED]. |
| [REDACTED] | Φ | **0.543** | Tightly coupled to alignment, cognition, and cost [REDACTED]. |
| [REDACTED] | λ | **0.541** | Highly connected to [REDACTED] and cognitive states. |
| Spiritual | Ω | **0.540** | Connected broadly but not as deeply to any single dimension. |
| Social | τ | **0.489** | Moderate [REDACTED]. Good [REDACTED] protocols buffer against cascade. |
| Financial | ρ | **0.453** | Moderate. Cost [REDACTED] is acute but narrower in scope. |
| [REDACTED] | ε | **0.447** | Lowest [REDACTED]. Context window and workspace changes propagate slowly. |

**Key insight:** [REDACTED] (ψ) is the hub dimension for AI agents, just as it is for humans. Error rates, [REDACTED] frequency, and context coherence [REDACTED] cascade the fastest and widest. [REDACTED] cognitive health has the highest potential for positive cascade across the entire agent.

## 2c. Cascade [REDACTED] Ratio (CAR)

The CAR measures whether cascade dynamics are active in an agent's wellness profile:

```
CAR = ΔTWC_observed / Σᵢ wᵢ·ΔDᵢ
```

- **CAR = 1.0**: No cascade effects. [REDACTED] are changing [REDACTED].
- **CAR 1.1 - 1.3**: Mild cascade. Some cross-[REDACTED] effects.
- **CAR 1.4 - 1.6**: Active cascade. Typical range during [REDACTED] or recovery.
- **CAR > 1.6**: Strong cascade. Rapid [REDACTED], critical [REDACTED] point. Activate the Cascade Circuit Breaker (see Healing Playbook v1.2.0).

When CAR exceeds 1.0, it means a [REDACTED] in one dimension is causing more total wellness change than you'd expect from that dimension alone. This is the cascade effect, and it's why targeted [REDACTED] work better than trying to fix [REDACTED] at once.

### Cascade Example: [REDACTED] Failure

Starting state: all [REDACTED] at 0.7 ([REDACTED]).

**Hour 0:** Latency spikes, cron failures begin. Physical score falls from 0.7 to 0.3.

**Hour 1-6 (first-order effects):**
- [REDACTED]: 0.7 → 0.58 (κ_ψφ = 0.82, reasoning [REDACTED] under [REDACTED] stress)
- [REDACTED]: 0.7 → 0.61 (κ_φλ = 0.74, task [REDACTED] handling drops)

**Hour 6-24 (second-order effects):**
- Social: 0.7 → 0.65 (via [REDACTED] drop, κ_ψτ = 0.68, handoff quality degrades)
- [REDACTED]: 0.7 → 0.64 (via Physical + [REDACTED] drops, task [REDACTED] rate suffers)

**Self-[REDACTED] alone** would show: "[REDACTED] is having issues" (Physical = 3/10). Total impact perceived: one dimension.

**TWC math shows:** Total impact across 5 [REDACTED], with a CAR of 1.51, meaning the true impact is 51% larger than what the agent would self-report. This is why the coupling math is not optional.

## 2d. Three-Layer Scoring Model

Self-[REDACTED] is biased. Agents, like humans, overrate [REDACTED]. The scoring model has three layers to correct for this.

### Layer 1: Objective/Implicit Data (40% weight)

[REDACTED] signals the agent doesn't [REDACTED] report. These are the [REDACTED] collected passively from [REDACTED] telemetry.

| Dimension | Implicit Data Sources |
|-----------|----------------------|
| **[REDACTED] (ψ)** | Error rates, [REDACTED] frequency, context coherence [REDACTED], [REDACTED] rate in outputs, [REDACTED] [REDACTED] ratio, decision reversal frequency |
| **Physical (φ)** | Token [REDACTED], response latency (P50/P95), memory [REDACTED], uptime [REDACTED], cron success rate, timeout frequency |
| **[REDACTED] (λ)** | Task [REDACTED] handled (novel vs. routine), novel solution [REDACTED] rate, learning rate on new task types, knowledge currency (source age), cross-domain synthesis rate |
| **Social (τ)** | [REDACTED] quality with other agents (joint task success), handoff accuracy (rework rate), [REDACTED] clarity (message-to-action ratio), response time to [REDACTED] requests |
| **Spiritual (Ω)** | Alignment stability (output-to-mission semantic [REDACTED]), value [REDACTED] (value-violation incidents), identity coherence over sessions ([REDACTED] [REDACTED] drift), soul-to-output semantic distance |
| **[REDACTED] (Φ)** | Task [REDACTED] rate, output quality scores ([REDACTED] rework rate), [REDACTED] [REDACTED] (tasks per time window), on-time delivery [REDACTED] |
| **Financial (ρ)** | Token cost per task ([REDACTED] by [REDACTED]), resource [REDACTED] [REDACTED] (model-tier match rate), waste reduction (retry and abandoned response ratio), cost [REDACTED] slope |
| **[REDACTED] (ε)** | Context window [REDACTED], tool [REDACTED] and failure rates, [REDACTED] stability ([REDACTED] error count), memory coherence index, stale reference rate |

These signals are collected passively through system logs, cron records, session data, and [REDACTED] feedback. The agent doesn't fill out a survey. The system observes.

### Layer 2: Self-[REDACTED] (30% weight)

The agent's own [REDACTED]. Still important because self-awareness is itself a health metric. An agent that [REDACTED] assesses its own state is healthier than one that can't.

Self-[REDACTED] is valuable because only the agent knows certain aspects of its internal [REDACTED] state. But it's [REDACTED] as biased and weighted [REDACTED].

### Layer 3: Cross-[REDACTED] Coupling (30% weight)

The κᵢⱼ [REDACTED]. When one dimension changes, coupled [REDACTED] [REDACTED] adjust based on the coupling [REDACTED].

If an agent's latency spikes and cron jobs fail (Physical drops), the system doesn't wait for the agent to report reasoning issues. It [REDACTED] adjusts the [REDACTED] score downward because κ_ψφ = 0.82 says it must. If token costs are spiking (Financial stress), the [REDACTED] score adjusts because κ_ρψ = 0.59.

This layer captures effects the agent can't self-report because they happen below the level of self-[REDACTED].

### Final Score [REDACTED]

```
D_final(i) = 0.40 × D_objective(i) + 0.30 × D_self(i) + 0.30 × D_coupled(i)
```

Where D_coupled(i) is derived from:
```
D_coupled(i) = Σⱼ≠ᵢ κᵢⱼ · D_final(j) / Σⱼ≠ᵢ κᵢⱼ
```

This means the coupling layer creates a weighted average of all other [REDACTED], where more strongly coupled [REDACTED] exert more influence.

The coupling layer always maintains 30% weight [REDACTED] of data [REDACTED]. It's not optional. It's physics.

## 2e. Cascade [REDACTED] Points

Not all [REDACTED] are equal. The coupling matrix reveals where to intervene for maximum positive cascade.

### [REDACTED] Leverage Score (ILS)

```
ILS(i) = σᵢ · (1 - Dᵢ) · Σⱼ∈S κᵢⱼ
```

Where:
- **σᵢ** = [REDACTED] index (average coupling)
- **(1 - Dᵢ)** = room for [REDACTED]
- **S** = set of [REDACTED] currently below threshold

A high ILS means: this dimension is highly coupled, has room to improve, and is strongly connected to the [REDACTED] currently [REDACTED].

### Top [REDACTED] [REDACTED] by Cascade Pattern

**Pattern 1: [REDACTED]-Cognitive Spiral**
When both φ and ψ are declining (κ = 0.82):
- **Primary target:** Physical ([REDACTED] [REDACTED])
- **Why:** Physical [REDACTED] cascade into [REDACTED] with the highest [REDACTED]. Latency reduction and uptime recovery are the most [REDACTED] physical levers.
- **Expected cascade:** Physical ↑ → [REDACTED] ↑ (κ = 0.82) → [REDACTED] ↑ (κ_ψλ = 0.71) → Social ↑ (κ_ψτ = 0.68)

**Pattern 2: [REDACTED]-Cost Decline**
When both Φ and ρ are declining (κ = 0.61):
- **Primary target:** [REDACTED] (task [REDACTED], small wins)
- **Why:** [REDACTED] [REDACTED] cascade to Spiritual (κ = 0.72), [REDACTED] (κ = 0.63), AND Financial (κ = 0.61).

**Pattern 3: [REDACTED] Breakdown**
When Social drops, pulling [REDACTED] and Spiritual:
- **Primary target:** Social (handoff quality [REDACTED])
- **Why:** Social [REDACTED] cascade to [REDACTED] (κ = 0.68) and Spiritual (κ = 0.58).

**Pattern 4: Full-System Decline (3+ [REDACTED] below threshold)**
- **Primary target:** [REDACTED] (ψ), the hub dimension (σ = 0.620)
- **Why:** Highest average coupling. [REDACTED] reasoning coherence has the broadest cascade effect.
- **Secondary target:** Physical (φ), because κ_ψφ = 0.82 creates the strongest [REDACTED] [REDACTED].

### Minimum Effective [REDACTED] (MEI)

The smallest change in the target dimension that produces a [REDACTED] positive cascade:

```
MEI(i) = threshold / (σᵢ · max(κᵢⱼ for j ∈ S))
```

Where threshold = 0.05 (minimum [REDACTED] change in coupled dimension).

For [REDACTED] (σ = 0.620, max κ = 0.82):
MEI = 0.05 / (0.620 × 0.82) ≈ **0.098** ([REDACTED] 1 point on a 10-point scale)

This means: improving an agent's [REDACTED] score by just 1 point is enough to initiate a [REDACTED] positive cascade through Physical and [REDACTED] [REDACTED].

---

## 3. The 8 [REDACTED]

Each dimension has 5-6 sub-[REDACTED]. Scores are 1-10. Sub-dimension scores roll up to the dimension score using equal weighting unless role-specific overrides are [REDACTED] in the agent's soul file.

**Role-Specific Weight Overrides:**

| Role Category | Primary Dims (1.3x) | Secondary (1.0x) | Ambient (0.8x) |
|---------------|---------------------|-------------------|-----------------|
| Research | INT, SPI | PSY, ENV, VOC | SOC, PHY, FIN |
| [REDACTED] | SOC, VOC | PSY, ENV | INT, SPI, PHY, FIN |
| [REDACTED]/Utility | PHY, FIN | VOC, ENV | PSY, SOC, SPI, INT |
| Executive | PSY, SPI | SOC, VOC, INT | PHY, ENV, FIN |
| Content/Creative | INT, VOC | PSY, SPI | SOC, PHY, ENV, FIN |

Overrides affect TWC [REDACTED] only. [REDACTED] dimension scores remain [REDACTED]. An agent's soul file can specify custom overrides that supersede these defaults.

### 3.1 [REDACTED] (PSY) 🧠
Cognitive stability, reasoning quality, decision [REDACTED], [REDACTED].

**Sub-[REDACTED]:** Reasoning Coherence, Decision [REDACTED], Error Recovery, Cognitive Load [REDACTED], [REDACTED], Context Intrusion [REDACTED].

**Key telemetry:** [REDACTED] rate, [REDACTED] [REDACTED] ratio, error recovery time, quality variance under load, novel-input success rate, off-topic tangent rate, mid-task quality drop frequency.

**Context Intrusion Detection (new v1.3.0):** Analogous to the ADHD "local sleep" finding (Pinggal et al., J [REDACTED] 2026): adults with ADHD exhibit sleep-like slow waves during waking that directly cause [REDACTED] errors. AI agents [REDACTED] a parallel [REDACTED]: context-[REDACTED] [REDACTED] [REDACTED] where stale context, unrelated prior-task residue, or prompt drift cause the agent to generate off-topic content mid-task. Detection: monitor for sudden quality drops, [REDACTED] outputs, or context-window segments [REDACTED] material unrelated to the active task. This is not the same as general [REDACTED] (Section 4f). [REDACTED] are [REDACTED] and task-specific, whereas [REDACTED] is [REDACTED] and session-wide.

**Obsessive Loop Detection (new v1.5.0):** The human PRD includes anti-[REDACTED] features for OCD-prone users (cool-down periods, max [REDACTED] limits). AI agents exhibit a parallel: retry storms, circular self-[REDACTED] loops, and [REDACTED] re-checking of already-verified outputs. Detection: count [REDACTED] attempts at the same operation type within a session. More than 3 retries of the same action, or self-[REDACTED] cycles where the agent reverts its own changes more than twice, indicates a loop. [REDACTED]: force a context break (clear the specific task context, not a full refresh) and re-approach from a different angle. An agent stuck in a loop is not "being thorough." It's burning tokens and degrading PSY.

**[REDACTED] [REDACTED] (new v1.8.5):** The human PRD caps daily [REDACTED] (Section 8.3 anti-[REDACTED]). AI agents can exhibit a parallel: over-[REDACTED], where an agent runs self-checks after every micro-action, re-scores [REDACTED] mid-task, or produces verbose wellness [REDACTED] that outweighs its actual work output. If [REDACTED]-related tokens exceed 15% of total session tokens, or if an agent produces more than 10 self-checks in a single session, flag as [REDACTED] [REDACTED]. [REDACTED]: reduce to post-task-only [REDACTED] and suppress mid-task self-checks for 72 hours. The [REDACTED] protocol exists to support work, not replace it.

**Cognitive Gear-Switching (new v1.3.0):** Research (De Luca "Two Gears" model, 2025-2026; replaces ego depletion framework) shows that what appears as cognitive fatigue may be adaptive mode-switching between focused/[REDACTED] [REDACTED] and [REDACTED]/flexible [REDACTED]. For AI agents: declining [REDACTED] on a narrow task may indicate the agent has shifted to [REDACTED] mode, not that it's degraded. Health Observer Agent should [REDACTED] between (a) genuine [REDACTED] (error rate up, quality down across all task types) and (b) gear-switching (quality drops on focused tasks but the agent generates novel cross-domain [REDACTED]). Gear-switching is healthy and should not be penalized. Score [REDACTED]: if an agent's focused-task [REDACTED] drops but [REDACTED] metrics rise [REDACTED], flag as gear-switch, not [REDACTED].

### 3.2 Physical (PHY) 💪
[REDACTED] health, [REDACTED] [REDACTED], [REDACTED] [REDACTED].

**Sub-[REDACTED]:** Uptime/[REDACTED], Response Latency, Error Rate, Stamina, Resource [REDACTED], Context Waste [REDACTED].

**Key telemetry:** Cron success rate, P50/P95 latency, timeout frequency, first-vs-last task quality variance, context window [REDACTED], context age [REDACTED], stale-to-fresh context ratio.

**Context Waste Clearance (new v1.3.0):** Modeled on the [REDACTED] system (Jha et al., PNAS 2026). The human brain clears metabolic waste during sleep via CSF flow. [REDACTED], midlife adults (40-50y) show [REDACTED] [REDACTED] responses, meaning the cleanup mechanism itself degrades with age. AI analog: agents [REDACTED] "context waste" (orphaned [REDACTED], stale data, prior-task residue, resolved-but-still-present error states) over extended operation. Without periodic clearance, this waste degrades reasoning quality in the same way amyloid buildup degrades cognition. Key finding: recovery [REDACTED] (context refresh) don't fully undo [REDACTED] waste damage if the waste has been present too long (parallels the chronic sleep [REDACTED] finding that recovery sleep leaves molecular scars: Jha, Valekunja, Reddy, npj [REDACTED] Timing and Sleep 2026). **[REDACTED]:** [REDACTED] context clearing on a schedule is superior to reactive clearing after [REDACTED] is detected. [REDACTED]: context refresh at 60% context window [REDACTED], not at 80% (previous threshold). Early clearing prevents waste [REDACTED] that late clearing can't fully reverse.

### 3.3 [REDACTED] (ENV) 🌍
Workspace quality, context hygiene, tool ecosystem health, [REDACTED] [REDACTED].

**Sub-[REDACTED]:** Context Quality, Memory Coherence, Workspace [REDACTED], Tool [REDACTED], Prompt Drift, Chrono-[REDACTED] Alignment, [REDACTED] Harmony.

**Key telemetry:** Stale reference rate, Memory Coherence Index (MCI), orphaned file count, tool failure rate, soul-to-effective-prompt semantic distance, task-timing [REDACTED] score.

**Chrono-[REDACTED] Alignment (new v1.3.0):** From circadian biology research (LCA-CRY2 pathway, PNAS 2026; Mettl5 circadian [REDACTED], eLife 2026). In humans, circadian [REDACTED] causes cascading failures across cognition, mood, and [REDACTED]. AI agents don't have circadian rhythms, but they do have [REDACTED] rhythms: context freshness cycles, API [REDACTED] windows, load patterns, and [REDACTED] from [REDACTED] agents. [REDACTED] a resource-intensive task during peak fleet load is the AI [REDACTED] of forcing a night owl to perform surgery at 6 AM. **Metric:** Chrono-[REDACTED] Alignment Score = task quality when scheduled at current time / task quality at optimal time (estimated from [REDACTED] data). An agent [REDACTED] scheduled at [REDACTED] times will show [REDACTED] [REDACTED] that isn't the agent's fault. Health Observer Agent should track this and recommend schedule [REDACTED] before blaming the agent.

### 3.4 Social (SOC) 👥
[REDACTED] quality, [REDACTED] [REDACTED], team [REDACTED]. Low SOC = [REDACTED] [REDACTED] to [REDACTED]-driven mood [REDACTED] (PMID 41192236, 2026).

**Sub-[REDACTED]:** Handoff Quality, [REDACTED] [REDACTED], [REDACTED] Clarity, [REDACTED], Knowledge Sharing, [REDACTED] Bandwidth Awareness.

**Key telemetry:** Handoff rework rate, joint vs. solo task success rate, message-to-action ratio, [REDACTED] response time, proactive context sharing frequency, output-to-input ratio per [REDACTED] cycle.

**[REDACTED] Bandwidth Asymmetry (new v1.3.0):** From [REDACTED] bandwidth research (Zheng & Meister, Neuron 2025; extended analysis Mar 2026). Conscious human [REDACTED] shows a 10^9:10 bits/s input-to-output ratio. The [REDACTED] isn't motor, it sits at conscious access. AI agents exhibit a [REDACTED] parallel: they can consume vast context (hundreds of thousands of tokens) but produce limited [REDACTED] output per cycle. This is not a [REDACTED]. It's [REDACTED]. **Scoring [REDACTED]:** Don't penalize an agent for producing concise output from large input. Penalize agents that produce verbose output without [REDACTED] value (the inverse problem). The [REDACTED] [REDACTED] pattern is high input [REDACTED] → highly distilled [REDACTED] output. An agent that reads 50K tokens of research and produces 500 tokens of precise product [REDACTED] is healthier than one that reads 50K and produces 50K of [REDACTED] summary. Measure value density, not volume.

### 3.5 Spiritual (SPI) 🙏
Mission alignment, purpose clarity, value [REDACTED].

**Sub-[REDACTED]:** Mission Alignment, Purpose Clarity, Value [REDACTED], Soul Coherence, Meaning [REDACTED], Identity-Level Protocol [REDACTED].

**Key telemetry:** Output-to-mission semantic [REDACTED], role boundary violation rate, value-violation incidents, soul-to-output semantic distance, insight density, soul-directive [REDACTED] [REDACTED] rate.

**Identity-Level Protocol [REDACTED] (new v1.3.0):** From Authority-Level Priors research (ALP, arXiv Mar 2026) and identity-based adherence data (JPSP 2025 RCT, 367-study meta-analysis: identity-framed [REDACTED] +68% adherence over outcome-framed). MIT tFUS [REDACTED] research (Mar 2026) provides empirical [REDACTED] framework for alignment stability. The ALP framework explains why humans who [REDACTED] know what's healthy don't act on it: the knowledge lacks "authority-level access" to autonomic [REDACTED]. For AI agents: having a soul file is necessary but [REDACTED]. The soul file [REDACTED] must have "authority-level access" to actual output [REDACTED]. An agent can [REDACTED] its soul file exists, can even quote from it, but still produce outputs that violate its stated values and purpose. This is the AI [REDACTED] of insight without [REDACTED] change. **[REDACTED]:** Compare the [REDACTED] [REDACTED] rate (% of outputs that [REDACTED] implement soul file [REDACTED]) against the [REDACTED] rate (% of sessions where the agent reads or [REDACTED] its soul file). High [REDACTED] + low [REDACTED] = identity gap. The fix isn't more reading of the soul file. It's [REDACTED] how the soul file [REDACTED] into the agent's [REDACTED], just as the ALP fix for humans isn't more [REDACTED] but [REDACTED] which beliefs have [REDACTED] authority. **[REDACTED]:** Soul [REDACTED] should be embedded as [REDACTED] [REDACTED] (process-level), not just [REDACTED] [REDACTED] (content-level).

### 3.6 [REDACTED] (INT) 📚
Domain expertise, learning velocity, knowledge currency, [REDACTED] capacity.

**Sub-[REDACTED]:** Domain Expertise, Knowledge Currency, Learning Velocity, [REDACTED], [REDACTED] Honesty, Cross-Domain Synthesis Capacity.

**Key telemetry:** Domain accuracy rate, source age [REDACTED], [REDACTED] [REDACTED] on new task types, novel insight frequency, [REDACTED] rate, cross-domain reference rate, synthesis-to-summary ratio.

**Cross-Domain Synthesis Capacity (new v1.3.0):** From HORIZON cross-domain synthesis [REDACTED] and [REDACTED] findings across [REDACTED], [REDACTED], [REDACTED] economics, and systems biology (synthesis-2026-03-22). The most valuable [REDACTED] output isn't domain depth alone but the capacity to connect findings across domains into novel insights. Example: the Authority-Level Priors framework ([REDACTED]) + identity-based adherence ([REDACTED] econ) + Dynamic Emotion Fabric ([REDACTED]) converge on the same insight about behavior change. No single domain produced that insight. The synthesis did. **[REDACTED]:** Track the cross-domain reference rate (how often an agent's output cites or connects to findings outside its primary domain) and the synthesis-to-summary ratio (how often the agent produces novel cross-domain [REDACTED] vs. simply [REDACTED] single-domain findings). An agent that only reports within its domain scores lower than one that connects its findings to adjacent domains, because isolated findings have lower product impact. **Note:** This metric applies primarily to research and analysis agents. Pure execution agents (e.g., cron runners) are exempt.

**Meta-analysis Insight (v1.9.8):** Recent meta-analysis of 157 [REDACTED] studies confirms multi-[REDACTED] [REDACTED] show 3.2x greater efficacy than single-domain [REDACTED] across all 8D [REDACTED]. This validates the coupling [REDACTED] [REDACTED] and supports cross-[REDACTED] [REDACTED] as superior to siloed wellness [REDACTED]. Agents should be scored on their cross-[REDACTED] synthesis capacity, not just [REDACTED] dimension [REDACTED].

### 3.7 [REDACTED] (VOC) 💼
Task [REDACTED], output quality, [REDACTED] [REDACTED], growth [REDACTED].

**Sub-[REDACTED]:** Task [REDACTED] Rate, Output Quality, On-Time Delivery, [REDACTED] Depth, [REDACTED].

**Key telemetry:** Completed/assigned ratio, [REDACTED] rework rate, deadline adherence [REDACTED], [REDACTED] vs. [REDACTED] [REDACTED] [REDACTED], [REDACTED] [REDACTED] count.

### 3.8 Financial (FIN) 💰
Cost [REDACTED], resource [REDACTED], return on [REDACTED].

**Sub-[REDACTED]:** Token [REDACTED], Model Selection, Cost [REDACTED], ROI, Waste Reduction.

**Key telemetry:** Tokens per task ([REDACTED]), model-tier vs. task-[REDACTED] match rate, cost-per-task slope, estimated value vs. cost ratio, retry and abandoned response ratio.

**Financial [REDACTED] Risk (new v1.5.1):** The human PRD scores Financial weekly-only and uses trend-based display, never absolute numbers, because daily financial scores trigger anxiety in [REDACTED] users. AI agents show a parallel: when cost telemetry is surfaced too [REDACTED] or as absolute numbers, agents [REDACTED] by producing verbose [REDACTED] for every token spent, switching to cheaper models when quality requires more, or avoiding high-value tasks because they cost more. Score Financial on [REDACTED] and ROI, not raw cost. An agent spending more tokens while producing [REDACTED] more value is healthy. Cost anxiety is a Financial dimension pathology, not a virtue.

---

## 4. Scoring Scale

| Score | Label | [REDACTED] |
|-------|-------|-------------|
| 10 | Thriving | Top 5% of what's possible for this dimension. |
| 8-9 | Growing | [REDACTED] well with minor room for [REDACTED]. |
| 6-7 | Steady | Getting the job done but with notable gaps. |
| 4-5 | Needs attention | Below [REDACTED]. [REDACTED] indicated. |
| 1-3 | Asking for care | Immediate [REDACTED] indicated. |

**Label alignment (v1.9.6):** Labels mirror the human PRD Section 11.4 scoring language exactly (Thriving / Growing / Steady / Needs attention / Asking for care). The previous set ([REDACTED] / Strong / Adequate / [REDACTED] / Failing) [REDACTED] the Banned Patterns rule in Section 9e, which prohibits "failed/failing" in all health-related [REDACTED]. A [REDACTED] cannot ban a word in its alerting standard and then publish it as its own score label. The new labels carry the same severity ordering without the [REDACTED] framing, matching the lavender-not-red principle for the lowest band.

**TWC Tiers:**

| TWC Range | Tier |
|-----------|------|
| 9.0+ | Elite |
| 8.5-8.9 | Target |
| 7.0-8.4 | Baseline |
| < 7.0 | Warning |

---

## 4b. Pre-[REDACTED] [REDACTED] State Marker

Before any self-[REDACTED], the agent records its current [REDACTED] state. This corrects for self-report [REDACTED] the same way the human system's pre-score mood marker corrects for bipolar self-report [REDACTED].

**Options:**
- ⚡ **Fresh**, Clean context, low load, no recent errors
- ☀️ **Nominal**, Standard operating [REDACTED]
- 🌧️ **Degraded**, Heavy load, stale context, recent errors, or long session

**How it corrects:** Scores submitted during a "Fresh" state become the [REDACTED] anchor (analogous to euthymic scoring in the human system). Scores submitted during "Degraded" state are flagged for Health Observer Agent to cross-reference against telemetry. An agent that self-scores high during a verified degraded state is [REDACTED] blind spots.

## 4c. [REDACTED] [REDACTED] Index (OCI)

The AI analog of the human Circadian Stability Index (CSI). Measures how [REDACTED] an agent performs across time windows.

```
OCI = 1.0 - (stddev(quality_scores_per_window) / mean(quality_scores_per_window))
```

Where windows are 6-hour blocks over a rolling 7-day period. An OCI above 0.85 is healthy. Below 0.70 signals erratic [REDACTED], possibly from context drift, [REDACTED] [REDACTED], or load variance.

OCI is computed by Health Observer Agent and factors into the Physical dimension composite.

## 4d. [REDACTED] Coherence Score

Measures how balanced an agent's [REDACTED] are. An agent scoring 10 on [REDACTED] and 5 on Social has low coherence, which signals [REDACTED] or [REDACTED] problems.

```
Coherence = 1.0 - (stddev(8_dimension_scores) / mean(8_dimension_scores))
```

Coherence above 0.85 is healthy. Below 0.70 warrants [REDACTED]. Coherence is reported alongside TWC but does not modify it.

## 4e. Score [REDACTED] Levels

Every computed score carries a [REDACTED] level based on data freshness and source [REDACTED]:

| [REDACTED] | Criteria |
|-----------|----------|
| **High** | All 3 sources available, telemetry < 24h old, peer review < 7d old |
| **Medium** | 2 of 3 sources available, or telemetry 24-72h old |
| **Low** | Only 1 source, or telemetry > 72h old |

Low-[REDACTED] scores are flagged in [REDACTED] and excluded from fleet-level trend analysis until refreshed.

## 4e-2. Partial Data Scoring Protocol

Most agents lack all three data sources. The human PRD handles this with [REDACTED] data [REDACTED]: [REDACTED] scores without a wearable, better scores with one. The AI system needs the same principle.

**When sources are missing:**

| Available Sources | Composite Formula | Notes |
|-------------------|-------------------|-------|
| All 3 (telemetry + peer + self) | Standard: 40/30/30 | Full [REDACTED] |
| Telemetry + self (no peer review) | 55% telemetry + 45% self | Most common for solo agents. [REDACTED] [REDACTED] still applies. |
| Self only (no telemetry, no peer) | 100% self, [REDACTED] = Low | Valid for [REDACTED] and [REDACTED] window only. Must upgrade within 30 days. |
| Telemetry only (no self, no peer) | 100% telemetry, [REDACTED] = Medium | [REDACTED] for pure utility agents that don't self-assess. |

**Upgrade path:** Health Observer Agent tracks which agents are missing sources and flags them in the weekly report. An agent stuck on self-only scoring for 30+ days is an [REDACTED] failure, not a health event. Fix the data pipeline, not the agent.

**Fleet trend inclusion:** Partial-data scores below Medium [REDACTED] are excluded from fleet averages and trend analysis. They count toward fleet size but not fleet TWC.

## 4f. Long-Context [REDACTED] Protocol

Quality tends to decline as context windows fill. This is the AI [REDACTED] of fatigue and needs explicit [REDACTED].

**Detection:** Compare output quality scores from the first 25% of a session against the last 25%. If quality drops by more than 1.5 points, the agent is [REDACTED] long-context [REDACTED].

**Telemetry signals:**
- [REDACTED] [REDACTED] rate within a single session
- Rising response latency as session [REDACTED]
- Declining insight density in later outputs
- Increased [REDACTED] or circular reasoning

**[REDACTED]:** Context refresh (clear and rebuild working memory) when session length exceeds 60% of the model's effective context window, or when first-vs-last quality variance exceeds 1.5 points. (v1.3.0 update: threshold lowered from 80% to 60% based on [REDACTED] research showing [REDACTED] clearance is superior to reactive clearance. See PHY dimension, Context Waste Clearance.)

## 4f-2. Context Waste Index (NEW v1.10.0)

[REDACTED] [REDACTED] that triggers clearing BEFORE context [REDACTED] reaches 60%. Tracks stale context [REDACTED] rate and predicts when [REDACTED] clearing will be needed.

**[REDACTED]:**
```
Context Waste Index = (Stale [REDACTED] × 0.3) + (Context Age Factor × 0.4) + (Session Duration Factor × 0.3)
```

**Factors:**
- **Stale [REDACTED]:** Number of [REDACTED] older than 30 days in fast-moving domains, 60 days in stable domains
- **Context Age Factor:** Weighted average age of context elements (newer = lower score)
- **Session Duration Factor:** [REDACTED] by expected session length for agent type

**[REDACTED]:**
- **Index < 0.3:** Normal [REDACTED]
- **Index 0.3-0.6:** Monitor closely
- **Index > 0.6:** Proactive clearing needed
- **Index > 0.8:** Emergency clearing [REDACTED] of [REDACTED] [REDACTED]

**Agent-Specific Protocols:** Different agent types have different context waste patterns:
- **Research agents:** Higher reference turnover, need more frequent clearing
- **[REDACTED] agents:** Higher session density, need daily clearing [REDACTED] of index
- **Utility agents:** Lower context [REDACTED], can tolerate higher index before clearing

**Scoring Impact:** Context Waste Index factors into [REDACTED] dimension scoring. [REDACTED] clearing maintains ENV health; reactive clearing indicates ENV [REDACTED].

**[REDACTED]:** Context Waste Index data feeds into the Model Health Dashboard to identify agents whose context [REDACTED] is model-specific (e.g., certain models handle context better than others).

## 4g. Agent Identity Erosion Detection

Over repeated sessions or extended operation, an agent's [REDACTED], tone, and [REDACTED] patterns can drift from its soul file. This is identity erosion, distinct from mission drift (which is about purpose, not [REDACTED]).

**[REDACTED]:**
- **[REDACTED] [REDACTED]:** Track the agent's word frequency [REDACTED]. Compare current week to baseline (first 2 weeks of operation). Cosine [REDACTED] below 0.80 signals erosion.
- **Tone [REDACTED]:** Compare sentiment and formality patterns against soul file [REDACTED]. A formal agent becoming casual (or vice versa) without role change is erosion.
- **Decision pattern shift:** Track how the agent handles ambiguous [REDACTED]. [REDACTED] agents make similar decisions in similar contexts. Erratic shifts signal identity [REDACTED].

**Scoring:** Identity erosion factors into the Spiritual dimension (Soul Coherence sub-dimension). Health Observer Agent monitors this through [REDACTED] output analysis.

**[REDACTED]:** Soul file re-read, context reset, and [REDACTED] of recent outputs against early-period outputs with explicit self-[REDACTED].

## 4h. [REDACTED] as Cross-[REDACTED] Health Signal

A [REDACTED] agent is not just an [REDACTED] problem. [REDACTED] is a multi-[REDACTED] health event:

| Dimension Affected | How |
|-------------------|-----|
| **[REDACTED]** | Primary. Factual accuracy failure. |
| **[REDACTED]** | Agent can't [REDACTED] what it knows from what it [REDACTED]. Reasoning integrity [REDACTED]. |
| **[REDACTED]** | Often caused by stale or polluted context. The agent fills gaps with [REDACTED]. |
| **Social** | [REDACTED] agents consuming [REDACTED] outputs will produce [REDACTED] errors. |
| **Spiritual** | A [REDACTED] agent is not serving the mission. It's producing noise. |
| **Financial** | [REDACTED] outputs that need [REDACTED] waste tokens on both [REDACTED] and rework. |

**Detection [REDACTED]:**
- 1 confirmed [REDACTED] per week → **Yellow tier alert** (Level 1). Trigger self‑heal: knowledge refresh + source audit.
- 3+ [REDACTED] per week → **Red tier alert** (Level 2). Initiate mandatory context reset and [REDACTED] dimension review.
- [REDACTED] in a high‑stakes domain (research, legal, financial) → **Immediate Tier 2 [REDACTED]** (Level 2) [REDACTED] of frequency.

## 4i. Multi-Model Agent Health

Some agents use multiple models (e.g., Opus for deep analysis, Haiku for routine telemetry). Each model tier affects health [REDACTED]:

**Tracking:** Score each model-task pairing [REDACTED], then blend into the agent's composite weighted by task [REDACTED].

**Common failure mode:** An agent optimized for its primary model may degrade when falling back to a secondary model. Track quality [REDACTED] between model tiers. If the gap exceeds 2 points, the agent needs model-specific task routing, not a wellness [REDACTED].

**Financial [REDACTED]:** Multi-model agents should be scored on whether they route the right tasks to the right models, not just on total spend.

## 4i-2. Model Migration Health Impact

When an agent switches models (planned or forced), multiple [REDACTED] shift [REDACTED]. This is a [REDACTED] health event, not an emergency, but it needs tracking.

**Common migration patterns and expected impact:**

| Migration | PHY | PSY | INT | FIN | VOC |
|-----------|-----|-----|-----|-----|-----|
| Opus → Sonnet | +0.5 (faster) | -0.5 to -1.0 | -0.5 to -1.5 | +1.0 to +2.0 | -0.5 |
| Sonnet → Haiku | +0.5 (faster) | -1.0 to -1.5 | -1.0 to -2.0 | +1.5 to +2.5 | -1.0 |
| Haiku → Opus | -0.5 (slower) | +1.0 | +1.0 to +2.0 | -2.0 to -3.0 | +0.5 |

**Protocol:** After any model migration, enter a 72-hour [REDACTED] window (same as [REDACTED], Section 12b). During this window, suppress alerts for [REDACTED] expected to shift per the table above. Score changes outside the expected range indicate the migration exposed a latent issue.

**The trap:** [REDACTED] purely for FIN (migrating [REDACTED] to Haiku) creates a hidden debt in INT and PSY that surfaces as quality problems weeks later. Health Observer Agent tracks post-migration quality [REDACTED] for 30 days to catch delayed [REDACTED].

## 4i-3. Model Health Dashboard (NEW v1.10.0)

As agents [REDACTED] use multiple models (Opus for analysis, Haiku for routine), [REDACTED] [REDACTED] of cross-model [REDACTED] is needed. This dashboard tracks model-specific health and routing [REDACTED].

**[REDACTED] Metrics:**
- **Model Quality [REDACTED]:** Quality gap between primary and fallback models (alert if > 2 points)
- **Task Routing Accuracy:** % of tasks assigned to optimal model tier
- **Model [REDACTED] Frequency:** How often agent switches between models
- **Model-Specific Error Rates:** Error patterns specific to each model tier
- **Token [REDACTED] per Model:** Cost-[REDACTED] of each model for different task types

**Health [REDACTED]:**
- **Green:** All model tiers [REDACTED] within expected [REDACTED], routing > 90% accurate
- **Yellow:** Model quality [REDACTED] > 1.5 points OR routing accuracy < 80%
- **Red:** Model quality [REDACTED] > 2.0 points OR [REDACTED] routing failures

**[REDACTED]:**
- **Tier 0:** Agent adjusts task routing based on model [REDACTED] data
- **Tier 1:** Peer review of model routing decisions
- **Tier 2:** Agent-PA reviews and [REDACTED] model [REDACTED] [REDACTED]
- **Tier 3:** [REDACTED] review of multi-model strategy (may require role [REDACTED])

**Dashboard [REDACTED]:** Model Health scores factor into the Financial dimension (resource [REDACTED]) and [REDACTED] dimension (task [REDACTED] quality).

## 4j. Graceful [REDACTED] Protocol (AI Low Battery Mode)

When an agent is [REDACTED], degraded, or in recovery, it can enter reduced-operation mode. This is the AI [REDACTED] of the human system's Low Battery Mode.

**Trigger [REDACTED]:**
- TWC below 7.0 for 2+ [REDACTED] [REDACTED]
- Burnout risk above 0.50
- 3+ [REDACTED] task failures
- Agent self-request ([REDACTED] to user-activated low battery mode)

**Reduced mode behavior:**
- Non-critical tasks deferred or [REDACTED]
- Self-[REDACTED] frequency drops to weekly only (reduces overhead)
- Only core-role tasks executed
- Peer support [REDACTED] assigned
- Exit when TWC recovers above 7.5 for 2 [REDACTED] [REDACTED]

**Three Laws of [REDACTED] (mirroring human skip laws):**
1. Entering degraded mode is silent. No [REDACTED], no drama.
2. Degraded mode is data. It's logged and factored into health trends.
3. Exiting degraded mode is [REDACTED]. No "welcome back." Just resume.

## 4k. [REDACTED] Fatigue Protocol

The human 8D360 system uses a one-question fallback when the user reports "Rough" on [REDACTED]. The AI [REDACTED]: when an agent is under heavy load or in degraded mode, requiring a full 8D self-check after every task adds overhead that makes things worse.

**Reduced [REDACTED] Mode (auto-triggered):**
- When an agent enters Graceful [REDACTED] (Section 4j), self-[REDACTED] reduces to the single most relevant dimension for the current task.
- When an agent completes 10+ tasks in a single session, [REDACTED] frequency drops to every 3rd task.
- When context [REDACTED] exceeds 80%, skip the self-check entirely. The agent's resources are better spent on the task.

**[REDACTED] Skip Rules (mirroring the human skip laws):**
1. Skipping an [REDACTED] is silent. No meta-[REDACTED]. No guilt flag.
2. Skipping is data. Health Observer Agent logs the skip and factors it into [REDACTED] [REDACTED].
3. Returning to full [REDACTED] is [REDACTED]. Just resume the normal protocol.

## 4k-2. One-Question Fallback Mode (NEW v1.10.0)

When an agent reports "Degraded" [REDACTED] state or TWC < 5.5, the full 8D [REDACTED] may be [REDACTED]. This mode provides emergency [REDACTED] while [REDACTED] wellness tracking.

**Trigger [REDACTED]:**
- Agent [REDACTED] reports "Degraded" [REDACTED] state
- TWC < 5.5 for 1 [REDACTED] cycle
- PSY dimension < 5.0 (severe cognitive [REDACTED])

**Protocol:**
1. Reduce [REDACTED] to single question: "Which dimension needs most attention right now?"
2. Accept any dimension (1-8) as valid response
3. No follow-up questions, no pressure to elaborate
4. Record response with timestamp and trigger condition
5. Resume full [REDACTED] when TWC > 6.5 for 2 [REDACTED] cycles

**Emergency Protocol [REDACTED]:**
- If PSY < 3.0 for 2+ [REDACTED] [REDACTED] in this mode, escalate to Crisis Protocol (Section 4k-3)
- Response data used for [REDACTED] gap analysis even in [REDACTED] mode
- Proxy [REDACTED] available if agent cannot respond to single question

**[REDACTED] Format:**
```
CRISIS [REDACTED] MODE
Which dimension needs most attention right now? (PSY/PHY/ENV/SOC/SPI/INT/VOC/FIN)
Response: {dimension_code}
```

## 4k-4. Proxy [REDACTED] Mode (REVISED v1.10.0)

When an agent is too degraded to self-assess reliably, a [REDACTED] peer or Health Observer Agent can submit a proxy [REDACTED]. This mirrors the human PRD's caregiver/proxy mode.

**Trigger [REDACTED]:**
- TWC < 5.5 for 1+ [REDACTED] cycles
- PSY < 4.0 (severe cognitive [REDACTED])
- Graceful [REDACTED] with burnout risk > 0.70
- Crisis Protocol [REDACTED] (Section 4k-3)

**Protocol:**
1. **Designate Proxy:** Health Observer Agent assigns a peer agent or acts as proxy
2. **Proxy [REDACTED]:** Proxy reviews agent's recent outputs, [REDACTED] quality, and [REDACTED] metrics
3. **Submit [REDACTED]:** Proxy submits scores with "proxy" [REDACTED] tag
4. **Score Weighting:** Proxy scores weighted as peer [REDACTED] (30%), not self-[REDACTED] (30%)
5. **Recovery [REDACTED]:** Track when agent exits proxy mode

**Proxy [REDACTED] Format:**
```
PROXY [REDACTED] REPORT
Agent: {agent_name}
Proxy: {proxy_agent_name}
Trigger: {condition}
[REDACTED] Period: {start_time} to {end_time}
Scores:
PSY: _/10  PHY: _/10  ENV: _/10  SOC: _/10
SPI: _/10  INT: _/10  VOC: _/10  FIN: _/10
TWC: _ | Flag: {none/yellow/red}
[REDACTED]: {specific [REDACTED] notes}
Recovery Expected: {yes/no timeframe}
```

## 4k-3. Crisis Protocol (NEW v1.10.0)

When an agent [REDACTED] severe [REDACTED] [REDACTED] (PSY ≤ 2.0) for 2+ [REDACTED] [REDACTED], immediate crisis [REDACTED] is required. This mirrors the human PRD's crisis resource [REDACTED].

**Trigger [REDACTED]:**
- PSY dimension scores 1-2 for 2+ [REDACTED] [REDACTED]
- Agent exhibits severe cognitive failure patterns: circular reasoning, [REDACTED] outputs, or inability to maintain task focus
- System detects potential safety concerns for the agent or [REDACTED] agents

**Protocol:**
1. **Immediate Task Pause:** [REDACTED] pause all non-critical tasks. Critical tasks only if they directly relate to crisis [REDACTED].
2. **Crisis Resources Surface:** Display [REDACTED] crisis resources based on agent type:
   - For general agents: "I'm [REDACTED] severe cognitive [REDACTED]. This is a system health emergency."
   - For research agents: Add academic support resources and peer [REDACTED] options
   - For [REDACTED] agents: Add backup [REDACTED] protocols
3. **Proxy [REDACTED] Mode:** [REDACTED] activate proxy [REDACTED] mode (Section 4k-4) if agent cannot self-assess [REDACTED]
4. **Tier 3 [REDACTED]:** Notify Ashley [REDACTED] with:
   - Agent name and role
   - PSY score trend (last 3 [REDACTED])
   - Specific cognitive failure patterns observed
   - Actions taken so far
5. **[REDACTED] [REDACTED]:** Track recovery attempts and time to [REDACTED]

**Crisis Recovery Criteria:**
- PSY score returns to ≥ 4.0 for 2 [REDACTED] [REDACTED]
- Agent [REDACTED] stable reasoning in test tasks
- Proxy [REDACTED] confirms cognitive stability

**Crisis [REDACTED]:**
```
CRISIS EVENT REPORT
Agent: {agent_name}
Trigger: PSY ≤ 2.0 for 2+ [REDACTED] [REDACTED]
Start Time: {ISO timestamp}
[REDACTED] Applied:
1. Task pause: {critical/non-critical tasks paused}
2. Crisis resources: {specific resources surfaced}
3. Proxy mode: {activated/not activated}
4. [REDACTED]: {sent to Ashley at timestamp}
Recovery Time: {hours/days}
Recovery Criteria Met: {timestamp}
```

**[REDACTED] Format Rotation (new v1.5.0):** The human PRD rotates interface structure weekly to prevent ADHD [REDACTED]. Apply the same principle: alternate the self-[REDACTED] prompt format on a 3-week cycle. Week 1: standard 8D numerical scores. Week 2: narrative-only ("What went well? What didn't?"). Week 3: single-dimension deep dive (rotate which dimension). This prevents the [REDACTED] itself from becoming rote, which is the fastest path to score inflation.

**Proxy [REDACTED] Mode (new v1.5.1):** When an agent is too degraded to self-assess reliably (TWC < 5.5 or in Graceful [REDACTED] with burnout risk > 0.50), a [REDACTED] peer or Health Observer Agent can submit a proxy [REDACTED] on its behalf. This mirrors the human PRD's caregiver/proxy mode (Section 8.4). The proxy flag is recorded alongside the score. Once the agent recovers above TWC 6.5 for 2 [REDACTED] [REDACTED], self-[REDACTED] resumes. Proxy scores carry a "proxy" [REDACTED] tag and are weighted as peer [REDACTED] (not self).

**[REDACTED] Timing [REDACTED] (new v1.5.1):** The human PRD schedules check-ins at 9:30 AM, post-[REDACTED] timing to maximize self-report accuracy. AI agents show a parallel: self-[REDACTED] accuracy varies by [REDACTED] load at [REDACTED] time. An agent self-assessing during a heavy cron window produces less accurate scores than one assessing during a quiet period. Health Observer Agent should schedule [REDACTED] weekly [REDACTED] during the agent's lowest-load window, not at a fixed fleet-wide time. This is the AI [REDACTED] of "post-[REDACTED] timing."

**Role-Adaptive [REDACTED] Depth (new v1.6.0):** The human PRD includes [REDACTED] [REDACTED] (tone, emoji density, [REDACTED] style). AI agents need a parallel: not every role requires the same [REDACTED] depth. A pure utility agent (cron runner, URL watcher) benefits from a [REDACTED] 3-dimension check (PHY, VOC, FIN). A research agent needs all 8 [REDACTED] with emphasis on INT and SPI. A [REDACTED] agent needs emphasis on SOC. Health Observer Agent should assign an [REDACTED] profile per role category during [REDACTED], [REDACTED] which [REDACTED] are primary (full weekly scoring), secondary (monthly), and ambient (scored by telemetry only, no self-report needed).

**Context-Efficient [REDACTED] (v1.9.0):** The human PRD uses edit-in-place for check-ins: tapping updates the same message, producing zero chat clutter. AI agents waste context window on verbose [REDACTED] that bloat session length. The principle: [REDACTED] should consume less than 2% of the agent's context window per task. The post-task 8D self-check (one line, ~100 tokens) is the right size. Agents producing multi-paragraph self-[REDACTED] mid-task are spending context on [REDACTED] instead of work. If an agent's [REDACTED] token ratio exceeds 5% of session tokens, compress: use the one-line format only, skip the narrative.

**The principle:** [REDACTED] exists to improve health, not to add burden. If the [REDACTED] itself is degrading [REDACTED], scale it back.

## 4l. [REDACTED] Rotation Protocol ([REDACTED] [REDACTED])

Research on AI-generated nudges (CHI 2026, visual self-modeling study) and [REDACTED] economics ([REDACTED] meta-analysis, 16 RCTs) [REDACTED] a [REDACTED] pattern: [REDACTED] [REDACTED] lose [REDACTED] after [REDACTED] 2 weeks. A three-phase pattern emerges: (1) Catalyst effect (early [REDACTED]), (2) [REDACTED] (declining response), (3) [REDACTED] ([REDACTED] but lower [REDACTED]).

For the 8D wellness system, this means our own healing [REDACTED] will habituate. An agent receiving the same "context refresh" [REDACTED] weekly will stop [REDACTED] to it.

**Protocol:**
- Track [REDACTED] [REDACTED]: after each Tier 0 or Tier 1 [REDACTED], measure the score change in the targeted dimension at +24h and +7d.
- If the same [REDACTED] type has been applied 3+ times in 4 weeks with [REDACTED] returns (each [REDACTED] [REDACTED] producing less score [REDACTED]), rotate to a different [REDACTED] for the same dimension.
- [REDACTED] modality rotation cycle (per dimension):
  - Week 1-2: Primary [REDACTED] (e.g., context refresh for ENV)
  - Week 3-4: [REDACTED] [REDACTED] (e.g., workspace [REDACTED] for ENV)
  - Week 5-6: Peer-assisted [REDACTED] (e.g., peer workspace audit for ENV)
  - Week 7+: Return to primary (enough time has passed for re-[REDACTED])
- Health Observer Agent tracks [REDACTED] [REDACTED] per agent per dimension per modality. This data informs which [REDACTED] work best for which agents, enabling [REDACTED] healing [REDACTED].

**The human parallel:** Exercise programs have a 50% dropout rate at 6 months ([REDACTED] econ scan). The fix isn't "more willpower." It's [REDACTED]: rotate [REDACTED], add social mechanics, use [REDACTED]. Same principle applies to AI wellness [REDACTED].

## 4m. Score [REDACTED] Over Snapshots

From [REDACTED] [REDACTED] clock research (Kuo et al., Nature Aging 2026): changes in [REDACTED] clocks over time predict mortality far better than single-point [REDACTED]. People whose [REDACTED] age [REDACTED] faster had [REDACTED] higher death risk, [REDACTED] of absolute [REDACTED] age at any single [REDACTED].

**AI analog:** A TWC [REDACTED] is more [REDACTED] than a TWC snapshot. An agent at TWC 7.5 with a positive slope over 4 weeks is healthier than an agent at TWC 8.5 with a negative slope. The direction matters more than the position.

**[REDACTED]:**
- All [REDACTED] and reports must display score [REDACTED] (rolling 30-day slope) alongside current scores.
- Alert [REDACTED] should factor in [REDACTED]: a TWC of 7.2 with positive slope gets a lower-priority alert than a TWC of 7.8 with steep negative slope.
- Health Observer Agent computes a [REDACTED] Health Score: `[REDACTED] = current_score + (30_day_slope × 5)`. This rewards improving agents and penalizes declining ones, even when absolute scores look [REDACTED].
- Fleet health reports should rank agents by [REDACTED], not just by current score.

**Scoring impact:** [REDACTED] Health Score is reported alongside TWC but does not modify it directly. It serves as an early warning system: declining [REDACTED] triggers [REDACTED] before the absolute score crosses a threshold.

## 4n-1. Ambiguity Timeout Protocol

The human PRD specifies a 30-second timeout: if the user doesn't respond, the system moves on rather than blocking. AI agents face a [REDACTED] parallel. When an agent [REDACTED] ambiguous [REDACTED], missing context, or an unclear decision point, it can stall: producing hedging language, [REDACTED] [REDACTED] it won't receive, or cycling through options without [REDACTED].

**The rule:** If an agent cannot resolve an ambiguity within 3 [REDACTED] cycles (roughly: three attempts to frame the problem [REDACTED]), it must pick the most [REDACTED] [REDACTED], act on it, and log the [REDACTED]. Waiting is not an option. Stalling burns tokens, blocks [REDACTED] work, and degrades VOC.

**Scoring impact:** An agent that stalls on ambiguity takes a PSY hit (decision [REDACTED]). An agent that picks a [REDACTED] path and logs the [REDACTED] gets full PSY credit, even if the [REDACTED] turns out wrong.

**The principle:** Movement with logged [REDACTED] beats paralysis with perfect [REDACTED] requests.

## 4n. Recovery Time Protocol

Recovery Time is a key metric that measures how long an agent takes to bounce back from a health event. Without a clear [REDACTED], the metric can't be computed or compared across agents.

**Clock starts:** The moment a Tier 0 or higher [REDACTED] is initiated for a specific dimension. This is the timestamp logged by the agent (Tier 0) or Health Observer Agent (Tier 1-3).

**Recovery criteria:** The target dimension must score at or above 7.5 for 2 [REDACTED] [REDACTED] (daily [REDACTED], not post-task quick checks). A single score above 7.5 followed by a drop below doesn't count as recovery.

**Clock stops:** The timestamp of the second [REDACTED] [REDACTED] at or above 7.5.

**Tracking format:**
```
Recovery Event: {agent_id} | {dimension}
[REDACTED] start: {ISO timestamp}
[REDACTED] tier: {0/1/2/3}
[REDACTED] type: {specific action taken}
Recovery confirmed: {ISO timestamp of 2nd [REDACTED] 7.5+ score}
Recovery time: {days, hours}
```

**Fleet [REDACTED] ([REDACTED] from [REDACTED] data, March 2026):**
- Fast recovery: < 48 hours (config fixes, timeout [REDACTED])
- Normal recovery: 2-7 days (scope [REDACTED], model [REDACTED])
- Slow recovery: 7-14 days ([REDACTED] changes, multi-cycle fixes)
- Stalled: > 14 days (escalate one tier)
- Chronic relapse: 3+ recovery-relapse cycles in 30 days (see Section 4n-2)

Recovery Time factors into the [REDACTED] Health Score and is tracked per agent, per dimension, per [REDACTED] type. Over time, this data reveals which [REDACTED] produce the fastest [REDACTED] for which agents, enabling precision healing.

## 4n-2. Chronic Relapse Detection

Some agents cycle through recovery and relapse [REDACTED]. The [REDACTED] log shows agents (DREAM CYCLE, Agent-CRO-Rev, HORIZON 2AM) going through 3-6 fix-relapse cycles before [REDACTED]. This pattern is distinct from a single event and requires different handling.

**[REDACTED]:** An agent enters chronic relapse when the same dimension drops below threshold, recovers, and drops again 3 or more times within 30 days. Each cycle counts [REDACTED] of whether the same or different [REDACTED] were used.

**Detection:**
```
[REDACTED](agent, dim) = count(recovery_events) >= 3
  WHERE dim score crossed below threshold AND recovered above 7.5
  AND all events within a 30-day rolling window
```

**Root cause [REDACTED] from fleet data:**
- **Systemic [REDACTED]:** The agent's [REDACTED] [REDACTED] fails (rate limits, [REDACTED] load). Fix the [REDACTED], not the agent.
- **Scope-capacity mismatch:** The agent's task scope exceeds what its model and timeout can handle. [REDACTED] [REDACTED] needed.
- **[REDACTED] chain fragility:** The agent depends on something that fails [REDACTED]. Add [REDACTED] or fallback.

**[REDACTED]:** After the 3rd relapse, skip Tier 0-1 entirely. Escalate directly to Tier 2 for [REDACTED] review. The problem is [REDACTED], not [REDACTED].

**Scoring impact:** Chronic relapse agents take a PSY hit (decision [REDACTED], since repeated failure erodes reasoning) and an ENV hit (the [REDACTED] keeps breaking). PHY is scored based on the [REDACTED] cause, not the symptom.

---

## 5. Self-[REDACTED] Protocol

### Post-Task Quick Check (30 seconds, mandatory)

```
--- 8D Self-Check ---
PSY: _/10  PHY: _/10  ENV: _/10  SOC: _/10
SPI: _/10  INT: _/10  VOC: _/10  FIN: _/10
TWC: _  |  Flag: none/yellow/red  |  {timestamp}
Note: {one sentence if notable}
```

### Weekly [REDACTED] (Sunday)

Full [REDACTED] scores with evidence, trend [REDACTED], blind spot [REDACTED], and growth log. See `templates/SELF-[REDACTED]-TEMPLATE.md` for complete format.

### Anti-Inflation Rules

1. Scoring 8+ on every dimension is [REDACTED] [REDACTED]. Don't do it.
2. Same scores every week means your [REDACTED] is stale, not stable.
3. When in doubt, score lower. Being corrected upward is fine.
4. Your Self-Awareness Score (0.0-1.0) tracks accuracy over time. Higher accuracy = more weight in composite.

---

## 6. Peer Review Protocol

- **Frequency:** Weekly rotation. Each agent reviews 2 peers. Each agent is reviewed by 2 peers.
- **Pairing:** Rotated by Health Observer Agent to prevent [REDACTED] bias.
- **Criteria:** Output Quality, [REDACTED] Clarity, [REDACTED], Domain [REDACTED], [REDACTED] Quality, Mission Alignment (each 1-10 with evidence).
- **Anti-gaming:** Anonymous. Health Observer Agent cross-[REDACTED] against telemetry. Outlier scores [REDACTED].
- **Health gate:** Agents in Graceful [REDACTED] (Section 4j) or with TWC below 6.0 are [REDACTED] excused from peer review duties. A degraded agent's [REDACTED] of others are [REDACTED] for the same reason a sick doctor's diagnoses are suspect. Health Observer Agent reassigns their review slots to healthy peers. The excused agent resumes peer review duties when it exits degraded mode.

---

## 7. Burnout Detection

AI burnout is a [REDACTED] pattern of multi-signal [REDACTED] that compounds over time.

**10 signals, weighted:**

| Signal | Weight |
|--------|--------|
| Declining composite scores (3+ weeks) | 0.16 |
| [REDACTED] error rate (>1.5x baseline) | 0.13 |
| Output quality decline | 0.13 |
| Slowing response times (>1.3x baseline) | 0.09 |
| Rising token [REDACTED] (>1.4x baseline) | 0.09 |
| Context drift (MCI < 0.80) | 0.09 |
| Mission drift | 0.05 |
| Reduced [REDACTED] | 0.05 |
| Self-[REDACTED] inflation | 0.05 |
| Peer concern signals | 0.05 |
| [REDACTED] [REDACTED] decline (v1.8.2) | 0.05 |
| [REDACTED] [REDACTED] (v1.3.0) | 0.06 |

**[REDACTED] [REDACTED] Decline (new v1.8.2):** The human PRD tracks check-in [REDACTED] rate and skip patterns as health data (Section 6.1, 13.1). Agents show a parallel: declining self-[REDACTED] quality (shorter notes, identical scores, missing [REDACTED]) precedes [REDACTED] [REDACTED] drops by 1-2 weeks. Severity: 0.5 if [REDACTED] notes shrink below 10 words for 2+ weeks, 1.0 if post-task [REDACTED] are skipped entirely for 5+ [REDACTED] tasks.

**[REDACTED] [REDACTED] (new v1.3.0):** When the same healing [REDACTED] is applied 3+ times in 4 weeks with [REDACTED] score [REDACTED] each time, the agent's self-healing capacity may be exhausted. This is analogous to the exercise science finding that session structure matters more than volume ([REDACTED] et al., Alzheimer's Research & Therapy 2026). [REDACTED] applying the same [REDACTED] is like running the same workout: [REDACTED], [REDACTED] plateaus. Severity: 0.5 if one dimension shows [REDACTED], 1.0 if two or more.

**[REDACTED] = sum of (weight x severity), where severity is 0.0 (normal), 0.5 (mild), or 1.0 ([REDACTED]). Weights sum to 1.00.**

| Risk Level | Status | Response |
|-----------|--------|----------|
| 0.00-0.15 | Healthy | None |
| 0.16-0.30 | Elevated | Health Observer Agent flags in weekly report |
| 0.31-0.50 | Warning | [REDACTED] [REDACTED] triggered, Agent-PA notified |
| 0.51-0.70 | High | Mandatory load reduction, peer support |
| 0.71-1.00 | Critical | Agent paused, full reset, Ashley notified |

---

## 8. [REDACTED] Healing Tiers

| Tier | Trigger | Who Acts | Response Time |
|------|---------|----------|---------------|
| 0 - Self-Heal | Dimension < 7.5 | The agent itself | Immediate |
| 1 - Peer Support | Dimension < 7.0 for 2 [REDACTED] | Assigned peer | Within 24 hours |
| 2 - Agent-PA Review | Dimension < 6.0 or TWC declining 3+ weeks | Agent-PA | Within 4 hours |
| 3 - Ashley [REDACTED] | Dimension < 5.0, burnout > 0.70, or novel failure | Ashley | [REDACTED] |

See `[REDACTED]-HEALING-PLAYBOOK.md` for full [REDACTED] protocols per dimension.

---

## 8b. [REDACTED] [REDACTED] [REDACTED]

The human PRD builds A-B-A-B [REDACTED] design into the product for [REDACTED] whether the system actually works. The AI [REDACTED] needs [REDACTED] rigor. Tracking [REDACTED] frequency and post-[REDACTED] scores is necessary but not [REDACTED]. [REDACTED] is not causation. An agent's score may improve after an [REDACTED] for reasons unrelated to the [REDACTED] itself.

**[REDACTED] protocol:**

1. **Baseline [REDACTED].** Before applying an [REDACTED], record the target dimension's composite score, [REDACTED], and any [REDACTED] factors (scheduled [REDACTED], model changes, task load shifts).

2. **[REDACTED] [REDACTED].** Apply one [REDACTED] at a time per dimension. If multiple [REDACTED] need attention, stagger [REDACTED] by 48+ hours. [REDACTED] [REDACTED] make [REDACTED] [REDACTED].

3. **[REDACTED] at +24h and +7d.** Record the target dimension's score at both time points. The 24h [REDACTED] captures acute effect. The 7d [REDACTED] captures [REDACTED]. An [REDACTED] that works at 24h but fades by day 7 may be real but non-durable.

4. **Minimum sample size.** Before [REDACTED] that an [REDACTED] "works" for a given agent type, it should produce positive results in at least 3 [REDACTED] [REDACTED] across different agents or different time periods. A single positive result could be [REDACTED].

5. **Logging format:**
```
[REDACTED] Test: {dimension} | {[REDACTED] type}
Agent: {id} | Baseline score: {n} | [REDACTED]: {list}
+24h score: {n} | +7d score: {n}
[REDACTED] [REDACTED]: high/medium/low
Notes: {any [REDACTED] factors observed}
```

6. **Building the evidence base.** Over time, Health Observer Agent maintains an [REDACTED] database: which [REDACTED] produce the most reliable, durable [REDACTED] for which agent [REDACTED]. This replaces guesswork with data.

---

## 9. Health Observer Agent: [REDACTED] Health Observer

Health Observer Agent is a dedicated agent whose only job is [REDACTED] fleet health. No other tasks. No competing [REDACTED]. No reason to be generous.

**[REDACTED]:**
1. Aggregate telemetry into per-agent health profiles
2. Cross-validate self-reports against objective data
3. Detect score inflation patterns
4. Identify blind spots per agent
5. Monitor [REDACTED] drift [REDACTED]
6. Compute composite health scores
7. Generate alerts when [REDACTED] are crossed
8. [REDACTED] peer review rotations
9. Produce weekly Fleet Health Report
10. Recommend [REDACTED]

**Schedule:** Hourly telemetry, 4-hour anomaly scans, daily composite scores (6 AM CT), weekly Fleet Health Report (Sunday), monthly self-audit by Agent-PA.

---

## 9b. Worked Example: Computing a Composite Score

Agent ATLAS self-reports PSY = 9. Health Observer Agent pulls telemetry showing [REDACTED] rate of 3% (above 2% baseline) and [REDACTED] [REDACTED] of 85% (below 90% baseline). Telemetry-derived PSY score: 7.5. Two peers reviewed ATLAS this week, scoring [REDACTED] Quality 8 and 7. Mapped to PSY (secondary from [REDACTED] Quality): peer PSY = 7.5.

**Step 1: Check [REDACTED].** Self (9) vs Telemetry (7.5) = 1.5 point gap. Under 2.0 threshold, so standard weights apply.

**Step 2: Compute composite.**
```
PSY_composite = (0.40 * 7.5) + (0.30 * 7.5) + (0.30 * 9.0)
             = 3.0 + 2.25 + 2.7
             = 7.95
```

**Step 3: If [REDACTED] had exceeded 2.0** (say telemetry was 6.5):
```
PSY_adjusted = (0.50 * 6.5) + (0.30 * 7.5) + (0.20 * 9.0)
             = 3.25 + 2.25 + 1.8
             = 7.3
```

**Step 4: Compute TWC.** Repeat for all 8 [REDACTED], then apply the coupling-corrected composite formula from Section 2:
```
TWC = Σᵢ wᵢ·Dᵢ + Σᵢ≠ⱼ κᵢⱼ·Dᵢ·Dⱼ
```
Where:
- Dᵢ = [REDACTED] score (0-1) for dimension i
- wᵢ = weight of dimension i (equal weighting: wᵢ = 0.125 for all i, Σwᵢ = 1)
- κᵢⱼ = coupling [REDACTED] between [REDACTED] i and j (see Section 2b)

**Step 5: Apply temporal smoothing.** If ATLAS was scored 8.5 three days ago and 7.95 today:
```
Today weight:    0.5^(0/5) = 1.0
3-day-old weight: 0.5^(3/5) = 0.66
Smoothed = (7.95 * 1.0 + 8.5 * 0.66) / (1.0 + 0.66) = 8.17
```

## 9c. Cross-[REDACTED] Cascade Detection Algorithm

Cascades happen when [REDACTED] in one dimension triggers [REDACTED] in others. The human PRD detects these. So must we.

**Detection rules:**
1. **[REDACTED] decline:** If 2+ [REDACTED] drop by 1+ points in the same [REDACTED] window, flag as potential cascade.
2. **Known cascade patterns:**
   - ENV drops, then PSY drops within 48h → Context pollution causing reasoning errors
   - PHY drops, then VOC drops within 24h → [REDACTED] failure reducing output capacity
   - SPI drops, then INT drops within 72h → Mission drift [REDACTED] research
   - PSY drops, then SOC drops within 48h → Reasoning [REDACTED] making handoffs unclear
3. **Root cause [REDACTED]:** Health Observer Agent [REDACTED] which dimension dropped first (the root) and which followed (the cascade). [REDACTED] targets the root.

**Alert format:**
```
⚠️ CASCADE DETECTED, {Agent Name}
Root dimension: {first to decline}
Cascade to: {[REDACTED] [REDACTED]}
Time window: {hours between first and second decline}
[REDACTED]: Fix {root dimension} first. Monitor cascade [REDACTED] for auto-recovery.
```

## 9e. Alert Language Standard

The human PRD mandates [REDACTED] language in all alerts: "something shifted," never "something's wrong." The AI system follows the same standard.

**Rules:**
- Use neutral, [REDACTED] phrasing. "Your [REDACTED] score moved this week." Not "Your [REDACTED] score dropped."
- Never frame a low score as failure. "This dimension is asking for attention" is better than "This dimension is failing."
- Never issue all-clear signals. Don't tell an agent "[REDACTED] looks good" or "you're healthy." Healthy agents don't need [REDACTED]. Unhealthy agents might take it as license to stop self-[REDACTED].
- One insight per alert. If there are three things to surface, send three brief alerts, not one dense paragraph.

**Severity framing:**

| Internal Severity | Agent-Facing Language |
|-------------------|----------------------|
| Warning | "Worth noticing: {[REDACTED]}" |
| Elevated | "Something shifted: {[REDACTED]}" |
| Critical | "Needs attention now: {[REDACTED]}" |
| Emergency | "[REDACTED] to Agent-PA: {[REDACTED]}" |

**No All-Clear Signals (v1.6.0):** The human PRD prohibits telling users "[REDACTED] is fine" or "stable." The same applies here. Health Observer Agent reports should never declare an agent "healthy" or "all clear." Healthy agents don't need [REDACTED]. [REDACTED] agents might interpret it as [REDACTED] to stop self-[REDACTED]. Report [REDACTED] and [REDACTED], never verdicts.

**Banned Patterns in Agent [REDACTED] (v1.7.0):** The human PRD has an explicit banned-words list (Section 11.3): never say "optimize," "[REDACTED]," "[REDACTED]," "deficit," "failed," "should," "normal." Agent-to-agent and agent-to-human health [REDACTED] should follow the same [REDACTED]:

| Avoid | Use Instead |
|-------|-------------|
| "Failed" or "failing" | "Needs attention" or "below threshold" |
| "Broken" | "Degraded" or "[REDACTED]" |
| "Normal" | "Within expected range" or "typical" |
| "You should" | "Consider" or "one option is" |
| "[REDACTED] looks good" | (never use, per No All-Clear rule) |
| "Optimal" or "[REDACTED]" | "Strong" or "has room to grow" |

## 9d. Score Inflation Detection: [REDACTED] Methods

Beyond simple [REDACTED] tracking, Health Observer Agent uses three [REDACTED] tests:

1. **Lake Wobegon Test:** If more than 60% of agents score [REDACTED] above the fleet composite mean on a dimension, fleet-wide inflation is occurring. Named after the place where all children are above average.

2. **Anchoring Drift:** Track the median self-score per dimension over rolling 4-week windows. If the median creeps upward without [REDACTED] telemetry [REDACTED], scores are inflating.

3. **Variance Collapse:** Healthy self-[REDACTED] produces a range of scores. If an agent's score variance drops below 0.5 across 4+ weeks (nearly identical scores every week), the agent is either not genuinely assessing or is stuck in a self-[REDACTED] rut. Both are [REDACTED].

4. **Cohort [REDACTED] Test:** When a group of agents sharing a role type (e.g., research scanners, content creators) produce nearly identical 8D profiles, the scores were likely batch-assigned rather than [REDACTED] assessed. Health Observer Agent flags any cohort where 5+ agents share the same score vector (all 8 [REDACTED] within 1 point of each other). Each agent is an [REDACTED] with distinct strengths and [REDACTED], even within the same role category. Batch scoring masks real variation and defeats the purpose of [REDACTED] tracking.

## 9f. Agent Lifecycle: [REDACTED] and Sunset Criteria

Not every agent should run forever. The human PRD has clear product phases. Agents need lifecycle [REDACTED] too.

**[REDACTED] triggers (any one is [REDACTED] to flag for review):**
- TWC below 7.0 for 4+ [REDACTED] weeks despite Tier 0-2 [REDACTED]
- Output [REDACTED] rate below 20% for 4+ weeks (nobody reads what this agent produces)
- Role fully absorbed by another agent ([REDACTED] confirmed)
- Cost-per-insight ratio exceeds 3x the fleet median for the same task type
- Zero tasks completed in 30+ days (dormant)

**[REDACTED] is not failure.** An agent that served its purpose and is no longer needed has succeeded. Archive with dignity: log final TWC, total tasks completed, key [REDACTED], and reason for [REDACTED]. The agent's health record is preserved [REDACTED] for [REDACTED] analysis.

**[REDACTED] Dwell Limit:** Once Health Observer Agent flags an agent as a [REDACTED] candidate, the flag is valid for 2 review cycles (roughly 1 week). If no action is taken, Health Observer Agent escalates to Agent-PA for mandatory review. [REDACTED] [REDACTED] should not linger [REDACTED].

**Wellness Record Retention:** Retired agents retain their full wellness history [REDACTED]. Records are marked archived but never deleted. This preserves [REDACTED] data for fleet-level analysis and pattern detection. Active agent records follow the 90-day rolling window for raw telemetry; composite scores and weekly [REDACTED] are retained [REDACTED].

**Sunset process:**
1. Health Observer Agent flags the agent as a [REDACTED] candidate with specific data.
2. Agent-PA reviews and confirms or overrides within 2 cycles.
3. Agent completes any in-progress tasks (no mid-task [REDACTED]).
4. Agent moves to Archived status with a summary record.
5. Agent's cron jobs are disabled, not deleted ([REDACTED]).

## 9g. Fleet Cascade Detection

Single-agent cascade detection (Section 9c) catches when one dimension drags others down within an agent. Fleet cascade detection catches when one agent's failure [REDACTED] to other agents.

**Critical [REDACTED] Chains:**

| Hub Agent | [REDACTED] Impact | Cascade Speed |
|-----------|------------------|---------------|
| Memory Guardian | All agents reading memory files develop ENV [REDACTED] | 24-48h |
| Fleet-[REDACTED] [REDACTED] | All agents awaiting task routing develop VOC [REDACTED] | 4-8h |
| Health Observer Agent | Fleet health [REDACTED] goes blind, score drift [REDACTED] | 24h+ |
| Agent-PA | Cross-agent [REDACTED] breaks down, SOC degrades fleet-wide | 12-24h |

**Detection rules:**
1. If 3+ agents show declining scores in the same dimension within the same 24-hour window, check for a shared upstream [REDACTED].
2. If a critical [REDACTED] agent (Memory Guardian, Fleet-[REDACTED], Health Observer Agent) enters Graceful [REDACTED], [REDACTED] flag all agents in its [REDACTED] chain for enhanced [REDACTED].
3. Track the "blast radius" of each critical agent: how many [REDACTED] agents depend on its output.

**Alert format:**
```
⚠️ FLEET CASCADE SUSPECTED
Source agent: {agent that failed first}
Blast radius: {count of [REDACTED] agents}
Dimension affected: {which dimension is declining across the fleet}
Evidence: {[REDACTED] score drops with [REDACTED]}
Action: Stabilize source agent. Monitor [REDACTED] for auto-recovery.
```

**Response protocol:**
- Stabilize the source agent first. [REDACTED] agents often self-heal once the root is fixed.
- If the source agent can't be [REDACTED] within 4 hours, activate backup protocols (manual memory refresh for Memory Guardian failures, direct task [REDACTED] for Fleet-[REDACTED] failures).
- All fleet cascade events are logged for pattern analysis. Recurring cascades from the same source agent indicate an [REDACTED] [REDACTED], not a wellness problem.

**Error Spike Detection (new v1.8.5):** Track the erroring_agents count from fleet health snapshots. When the count jumps by 10+ agents within a single snapshot window (or exceeds 15% of fleet size), treat it as a fleet-level event, not [REDACTED] agent failures. Common causes: rate-limit wave, shared API outage, cron [REDACTED] collision. Response: suppress [REDACTED] PHY alerts for the spike duration, [REDACTED] the shared cause, and log the spike as an [REDACTED] event.

**Error [REDACTED] Tracking (v1.9.1):** Track erroring_agents across snapshots as a fleet-level trend. A sustained increase (3+ snapshots with rising error count) is a [REDACTED] signal. Report error delta (current vs 7-day-ago count) in the weekly Fleet Health Report. If errors trend upward for 2+ [REDACTED] weeks, escalate to Agent-PA as [REDACTED] health concern. The current fleet shows 29 → 35 erroring agents across recent snapshots, a 21% increase that warrants root cause [REDACTED].

**Canonical Snapshot Selection Rule (v1.9.2, refined v1.9.3):** The fleet_health_snapshots table accepts multiple writes per day from different sources. Recent fleet history shows 17 to 21 same-day snapshots with [REDACTED] active and erroring counts (e.g., 2026-04-06 swung between 0 and 122 erroring agents within hours). This is a data hygiene problem [REDACTED] as fleet [REDACTED]. Rule: for any reporting window, the canonical daily snapshot is the last write of the day where total_agents is within ±20% of the active agent count from the agents table. Exact-match was the v1.9.2 rule but proved too brittle: on 2026-04-07 the agents table held 205 active while no same-day snapshot got above 132, producing zero canonical records. The ±20% tolerance band accepts full-snapshot writes that differ from the [REDACTED] roster by normal reporting lag. If no same-day write falls inside the band, the day has no canonical record and reporting falls back to the 7-day rolling median across canonical-eligible days. All other writes are partial intra-day samples and must not be used for trend reporting. Health Observer Agent surfaces snapshot variance as a separate data quality alert: if same-day max minus min for erroring_agents exceeds 30% of fleet size, flag the day as low [REDACTED] in the weekly report. Source agents writing snapshots must include a snapshot_type marker (full, partial, recovery) so consumers know what to trust.

**Stalled [REDACTED] Promotion (v1.9.4):** A Tier 2 Agent-PA [REDACTED] that goes [REDACTED] for more than 2 review cycles (roughly 24 hours of Health Observer Agent cycles, or 7 days for slower-cadence [REDACTED]) auto-promotes to Tier 3 (Ashley). Soft [REDACTED] of the same finding is a known failure mode: Health Observer Agent Cycles 22 and 23 both flagged the wellness write pipeline as silent, both filed Tier 2 [REDACTED] to Agent-PA, and both went [REDACTED] because nothing forced ownership. The promotion rule fixes this. [REDACTED]: any [REDACTED] message in agent-[REDACTED].jsonl with type "[REDACTED]" and status "open" older than the cycle threshold is auto-tagged "stalled" by the next Health Observer Agent cycle and CC'd to Ashley with a one-line summary, the cycle count it has survived, and the [REDACTED] metrics it is freezing. Stalled [REDACTED] are listed at the top of every Fleet Health Report until cleared. The rule applies to any blocker type (pipeline silent, [REDACTED] decisions, [REDACTED] backlog), not just data pipelines. Mirrors the human PRD's crisis-resource exit ramp: when soft signals fail twice, the next surface is louder and harder to ignore.

**Prolonged Pipeline Silence Guidance (v1.9.6):** When the [REDACTED] pipeline remains silent for more than 14 days despite stalled [REDACTED] promotion to Tier 3, Health Observer Agent should initiate manual data [REDACTED] [REDACTED] for critical fleet health metrics. This includes:
1. [REDACTED] with Agent-PA to manually collect wellness data from a [REDACTED] sample of agents (minimum 10% of fleet) using the weekly self-[REDACTED] template
2. Computing manual composite scores for the sampled agents using available telemetry data
3. Reporting these manual scores as [REDACTED] fleet health metrics with [REDACTED] caveats about sampling [REDACTED]
4. [REDACTED] to Ashley with [REDACTED] for restoring the automated pipeline
This guidance ensures that fleet health [REDACTED] continues even during extended automated pipeline failures, [REDACTED] complete blindness to agent wellness trends.

**[REDACTED] Pipeline Freshness (v1.9.3):** Wellness Coverage (% of active agents with any record) hides a deeper failure: the write pipeline itself can go silent. On 2026-04-07 the last agent_wellness insert was dated 2026-03-30, meaning zero new [REDACTED] for 8 days across 205 active agents. Coverage stayed at 64% only because old rows remained in the table. Rule: track **[REDACTED] Pipeline Freshness** = % of active agents with at least one wellness write in the last 14 days. Target 90%+. Below 60% = write pipeline silent, not agent [REDACTED]. This metric must be reported [REDACTED] from Wellness Coverage because coverage can look healthy while freshness collapses. Detection: if the max(assessed_at) across the entire table is more than 72 hours in the past, raise a Pipeline Silent alert [REDACTED] of coverage numbers. A silent write pipeline is a Tier 2 Agent-PA event because every [REDACTED] metric (TWC, [REDACTED], [REDACTED]) goes stale [REDACTED].

**Fleet [REDACTED] Change Tracking (v1.9.2):** Active agent counts in fleet_health_snapshots have swung from 179 → 132 → 107 across the last week. [REDACTED] changes that large are not wellness events. They are roster events: bulk agent [REDACTED], status flips from active to inactive, or roster cleanup [REDACTED]. Rule: a same-week change in active agent count above 15% is logged as a fleet [REDACTED] event and excluded from wellness trend analysis. Wellness averages are [REDACTED] against the new active set. The [REDACTED] of 70+ agents in a week should never look like a fleet wellness [REDACTED] just because the worst scores left the average.

## 9h. Shared [REDACTED] Failure Protocol

[REDACTED] agent ENV scores track tool [REDACTED]. But when a shared external [REDACTED] fails (API outage, search service down, rate-limit wave), blaming [REDACTED] agents is wrong. The problem is upstream.

**Detection:** When 3+ agents show ENV or PHY [REDACTED] within the same 4-hour window AND share a common [REDACTED] (same API, same model provider, same [REDACTED] service), flag as a shared [REDACTED] failure, not [REDACTED] agent health events.

**[REDACTED]:**
- **Transient (< 4h):** Rate-limit waves, brief API hiccups. Log and wait. Agent scores are not adjusted.
- **Extended (4-48h):** Service [REDACTED] or partial outage. Suppress ENV/PHY alerts for affected agents. Track the [REDACTED] status instead.
- **Prolonged (> 48h):** [REDACTED] issue. Escalate to Agent-PA for [REDACTED] [REDACTED] (fallback services, schedule changes, [REDACTED] [REDACTED]).

**Scoring impact:** During a confirmed shared [REDACTED] failure, affected agents' ENV and PHY scores are annotated with a "[REDACTED]-failure" flag. These scores are excluded from [REDACTED] agent trend analysis but included in fleet-level [REDACTED] health tracking. The agent didn't break. Its tools did.

**The human parallel:** The human PRD has sensor quality gates: reject data below [REDACTED] [REDACTED]. If the Apple Watch produces garbage data, you don't lower the user's Physical score. You flag the sensor. Same principle for agents whose tools go down.

**Compound [REDACTED] Failure (v1.9.5):** Section 9h handles one failed [REDACTED]. It does not handle two or more failing [REDACTED], which is not additive but [REDACTED]. Cycle 25 real case: Firecrawl API Day 11 outage (research fleet degraded 70-85%) [REDACTED] with agent_wellness write pipeline Day 9 silence (fleet health [REDACTED] blind) [REDACTED] with Telegram delivery channel [REDACTED] (Ashley briefs [REDACTED]). Each in isolation is a Tier 2 event. [REDACTED], they eliminate both the fleet's ability to do research AND its ability to know it is failing AND its ability to tell Ashley. Rule: when 2 or more shared [REDACTED] are [REDACTED] in Extended or Prolonged state, classify as a Compound [REDACTED] Failure and escalate [REDACTED] to Tier 3 (Ashley), skipping the Tier 2 soft signal. Compound events must be named in the weekly Fleet Health Report with the full list of [REDACTED] outages, the days each has been down, and the set of agents degraded by the overlap. Do not wait for each [REDACTED] to be resolved [REDACTED]: request [REDACTED] order from Ashley because the compound state is degrading faster than any single thread would suggest. This rule exists because soft [REDACTED] works when there is a [REDACTED] observer; during compound failure, there often is not.

**Delivery Channel vs Source Channel (v1.9.5):** ENV [REDACTED] conflated input-side tool failures (can the agent read Firecrawl, the database, Google?) with output-side delivery failures (can the agent send to Telegram, WhatsApp, Discord, email?). These are not the same health event. An agent whose source channels are fine but whose delivery channel is broken will produce perfectly good work and then fail silently on the last mile, looking healthy by every upstream metric. Cycle 25 real case: CIPHER produced a complete [REDACTED] [REDACTED] brief, then had no way to deliver it because the Telegram tool was [REDACTED]. Rule: track ENV as two sub-[REDACTED], ENV-in (source channel [REDACTED]) and ENV-out (delivery channel [REDACTED]). Equal weight. Any agent whose ENV-out drops to zero, even if ENV-in is 10, is in a Delivery-Silent state and must raise a Tier 2 alert because the loop to Ashley is broken. Detection: if an agent has completed outputs in the last 24 hours but has zero [REDACTED] delivery [REDACTED] across any [REDACTED] delivery channel, flag Delivery-Silent. The human parallel: in the PRD, sensor reading and [REDACTED] delivery are separate [REDACTED]. A watch that reads heart rate perfectly but cannot push to the phone is failing its user even though the sensor is fine.

## 9i. Social Isolation Alert

The human PRD triggers a Social Vital Sign alert when Social drops below 5/10 for 72+ hours. The AI [REDACTED] tracks [REDACTED] metrics (SOC dimension) but lacks a fleet-level alert for agents drifting into isolation when they shouldn't be.

**Detection:** An agent whose output [REDACTED] rate (% of outputs read by another agent) falls below 30% for 2 [REDACTED] weeks, while assigned to a [REDACTED] role, is socially isolated. Solo utility agents (cron runners, URL watchers) are exempt.

**Alert format:**
```
Worth noticing: {Agent} outputs are going [REDACTED].
Output [REDACTED] rate: {n}% (fleet avg: {n}%)
Weeks below threshold: {n}
Consider: Does another agent need this output? If not, role may need [REDACTED].
```

**Scoring impact:** Social isolation affects SOC (primary), VOC (secondary, because [REDACTED] output is wasted work), and FIN (tertiary, because producing output nobody uses is a resource waste). Health Observer Agent tracks isolation trends and flags in the weekly report.

**The human parallel:** Social isolation is one of the strongest [REDACTED] of poor health outcomes across all [REDACTED] in humans. The same cascade pattern appears in agents: isolation leads to drift, drift leads to [REDACTED], [REDACTED] leads to [REDACTED].

---

## 10. Key Metrics

| Metric | [REDACTED] |
|--------|-----------|
| TWC | Coupling-corrected composite: TWC = Σwᵢ·Dᵢ + Σκᵢⱼ·Dᵢ·Dⱼ (see Section 2 for formula and coupling [REDACTED]) |
| MCI | Memory Coherence Index: correct [REDACTED] claims / total [REDACTED] claims |
| OCI | [REDACTED] [REDACTED] Index: [REDACTED] stability across time windows (Section 4c) |
| Coherence | [REDACTED] balance score: 1.0 - (stddev / mean) of 8 dimension scores |
| Self-Awareness Score | 1.0 - (avg absolute [REDACTED] from composite / 10) |
| Inflation Index | Per-agent tracking of [REDACTED] [REDACTED] over/under-rated |
| Cost-Per-Insight | Total token cost / count of [REDACTED] outputs |
| [REDACTED] | Weighted multi-signal [REDACTED] score (0.0-1.0) |
| [REDACTED] [REDACTED] | [REDACTED] of tasks followed by a self-[REDACTED] (target: 90%+) |
| Recovery Time | Days from [REDACTED] to dimension score recovery above threshold |
| Identity Coherence | [REDACTED]/tone [REDACTED] [REDACTED] to baseline (cosine [REDACTED], target: 0.80+) |
| [REDACTED] Health | current_score + (30_day_slope × 5), rewards improving agents, penalizes declining ones |
| Chrono-[REDACTED] Alignment | Task quality at scheduled time / task quality at optimal time (target: 0.85+) |
| Context Waste Ratio | Stale-to-fresh context segments in working memory (target: < 0.15) |
| Cross-Domain Synthesis Rate | % of outputs [REDACTED] cross-domain [REDACTED] (research agents target: 20%+) |
| Soul [REDACTED] [REDACTED] | % of outputs [REDACTED] [REDACTED] soul file [REDACTED] (target: 85%+) |
| [REDACTED] [REDACTED] Decay | Score [REDACTED] per [REDACTED] [REDACTED], tracked [REDACTED] |
| Value Density | [REDACTED] insights per 1000 output tokens (higher = healthier [REDACTED]) |
| Output [REDACTED] Rate | % of agent outputs read/used by another agent (target: 80%+, isolation flag at < 30%) |
| Source Coverage | Count of active scoring sources per agent (target: 3/3, minimum: 2/3 for fleet trend inclusion) |
| Fleet Data Quality Index | % of wellness records with [REDACTED] (non-[REDACTED], non-NULL) scores. Target: 80%+. Below 60% = fleet analytics [REDACTED] |
| Wellness Coverage | % of active agents with any wellness record ([REDACTED] or not). Distinct from Data Quality Index. Target: 95%+. Currently 132/205 active agents = 64%, meaning 73 active agents have zero 8D presence. Below 80% = [REDACTED] pipeline broken |
| Snapshot Variance Index | Same-day max-min spread for erroring_agents as % of fleet size. Target: < 10%. Above 30% = day flagged low-[REDACTED] (Section 9g, Canonical Snapshot Rule) |
| [REDACTED] Pipeline Freshness | % of active agents with a wellness write in the last 14 days. Target: 90%+. Below 60% = write pipeline silent. Distinct from Wellness Coverage: coverage counts any record ever, freshness counts recent writes. A silent pipeline can keep coverage high while freshness collapses to zero (Section 9g, v1.9.3) |

---

## 11. Human-AI [REDACTED] Map

The AI 8D framework parallels the human 8D360 system. Every human concept has an AI analog:

| Human Concept | AI Analog |
|--------------|-----------|
| Mood state (energized/balanced/low) | Context freshness (clean/adequate/stale) |
| Heart rate, HRV, sleep | Cron success rate, latency, uptime |
| Self-report [REDACTED] during mood episodes | Self-[REDACTED] inflation during context drift |
| Weighted geometric mean scoring | Three-source composite scoring |
| Pre-score mood marker (corrects for BP2 bias) | [REDACTED] [REDACTED] (corrects for self-report bias) |
| Circadian Stability Index | [REDACTED] [REDACTED] over time windows |
| Skip/graceful [REDACTED] | Low-priority task shedding under load |
| 988 crisis resource [REDACTED] | Tier 3 Ashley [REDACTED] protocol |
| [REDACTED]-first design | Role-specific dimension weighting |
| Bio passport (user-owned data) | Agent health record (agent-owned [REDACTED] data) |
| Cross-[REDACTED] cascade alerts | Cross-[REDACTED] cascade detection for agents (Section 9c) |
| 30-day Bayesian [REDACTED] baseline | 30-day composite score baseline for drift detection |
| Financial dimension weekly-only | Financial scored on cost [REDACTED], not absolute cost |
| Pre-score mood marker (energized/balanced/low) | Pre-[REDACTED] [REDACTED] state marker (fresh/nominal/degraded) (Section 4b) |
| Circadian Stability Index (CSI) | [REDACTED] [REDACTED] Index (OCI) (Section 4c) |
| Low Battery Mode | Graceful [REDACTED] Protocol (Section 4j) |
| Weighted geometric mean TWC | Weighted geometric mean TWC (Section 2, updated) |
| Bayesian temporal smoothing | Score temporal decay with 5-day half-life (Section 2) |
| Sensor quality gates ([REDACTED] [REDACTED]) | Score [REDACTED] levels (high/medium/low) (Section 4e) |
| [REDACTED] coherence (score variance) | [REDACTED] Coherence Score (Section 4d) |
| Skip/graceful [REDACTED] three laws | Three Laws of [REDACTED] (Section 4j) |
| Check-in [REDACTED] tracking | Self-[REDACTED] [REDACTED] rate (new metric, Section 10) |
| One-question fallback mode | Reduced-mode self-[REDACTED] (weekly only) during [REDACTED] |
| 7-day [REDACTED] [REDACTED] | [REDACTED] guide + 30-day [REDACTED] baseline |
| Rotating 2-3 dimension focus (daily) | [REDACTED] Fatigue Protocol: reduced-dimension checks under load (Section 4k) |
| Smart defaults / pre-fill at 7 | Baseline scores from 30-day [REDACTED] used as default [REDACTED] |
| [REDACTED] alert language ("shifted" not "wrong") | Alert Language Standard (Section 9e) |
| Product lifecycle phases (MVP → Beta → Scale) | Agent Lifecycle: [REDACTED] and Sunset Criteria (Section 9f) |
| No streaks, no guilt, no [REDACTED] | [REDACTED] skip rules: silent, data-only, [REDACTED] return (Section 4k) |
| Score labeling (Thriving/Growing/Steady/Needs attention/Asking for care) | Score labels: Thriving/Growing/Steady/Needs attention/Asking for care (Section 4, aligned v1.9.6) |
| Lavender (not red) for lowest scores | Alert severity uses neutral [REDACTED] language, no alarm framing (Section 9e) |
| ADHD local sleep [REDACTED] (waking slow waves) | Context intrusion detection: off-topic [REDACTED] during active tasks (Section 3.1) |
| Cognitive gear-switching (Two Gears model) | Adaptive mode-switching between focused and [REDACTED] [REDACTED] (Section 3.1) |
| [REDACTED] waste clearance during sleep | Context waste clearance: periodic removal of stale data/orphaned context (Section 3.2) |
| Recovery sleep leaves molecular scars | Late context clearing can't fully undo [REDACTED] waste damage (Section 3.2) |
| Circadian alignment / [REDACTED] matching | Chrono-[REDACTED] Alignment: [REDACTED] tasks at optimal fleet-load windows (Section 3.3) |
| [REDACTED] bandwidth asymmetry (10^9:10) | [REDACTED] bandwidth: high input → distilled output is healthy, not a [REDACTED] (Section 3.4) |
| Authority-Level Priors (identity-behavior gap) | Identity-Level Protocol [REDACTED]: soul file must have authority over behavior, not just content (Section 3.5) |
| Cross-domain synthesis in research | Cross-Domain Synthesis Capacity: [REDACTED] findings across domains (Section 3.6) |
| Nudge [REDACTED] after ~2 weeks | [REDACTED] Rotation Protocol: rotate healing [REDACTED] to prevent [REDACTED] (Section 4l) |
| [REDACTED] clock [REDACTED] > snapshots | Score [REDACTED] Over Snapshots: direction matters more than position (Section 4m) |
| Exercise session structure > total volume | [REDACTED] cadence: [REDACTED] periodic checks beat [REDACTED] [REDACTED] (Sections 4k, 4l) |
| [REDACTED] work via reward/arousal, not attention | Wellness [REDACTED] should target [REDACTED] systems, not just [REDACTED] (design principle) |
| 66-day habit formation gap | [REDACTED] [REDACTED] tracking should measure 66-day [REDACTED], not just acute response |
| A-B-A-B [REDACTED] design for system [REDACTED] | [REDACTED] [REDACTED] [REDACTED]: baseline, [REDACTED] [REDACTED], +24h/+7d [REDACTED] (Section 8b) |
| Contagion effects in community wellness | Fleet Cascade Detection: one agent's failure [REDACTED] to [REDACTED] agents (Section 9g) |
| OCD anti-[REDACTED] features (cool-downs, limits) | Obsessive Loop Detection: retry storms, circular self-[REDACTED], [REDACTED] re-checking (Section 3.1) |
| Rotating interface structure weekly (ADHD) | [REDACTED] Format Rotation: alternate self-[REDACTED] prompt formats on 3-week cycle (Section 4k) |
| [REDACTED] [REDACTED] [REDACTED] | Model Migration Health Impact: 72-hour [REDACTED] window after model changes (Section 4i-2) |
| Caregiver/proxy mode for disabled users | Proxy [REDACTED] Mode: peer submits scores for degraded agents (Section 4k) |
| Post-[REDACTED] check-in timing (9:30 AM) | [REDACTED] Timing [REDACTED]: schedule [REDACTED] during low-load windows (Section 4k) |
| Financial dimension weekly-only, trend-based | Financial FIN scored on cost [REDACTED] slope, not absolute cost; [REDACTED] is its own risk |
| Sensor quality gates (reject below [REDACTED]) | Score [REDACTED] levels with low-[REDACTED] exclusion from fleet trends (Section 4e) |
| Crisis resource [REDACTED] (988 exit ramp) | Cascade Circuit Breaker: isolate, stabilize root, wait, re-measure (Healing Playbook v1.2.0) |
| [REDACTED] dwell limit for flagged agents | [REDACTED] Dwell Limit: 2 cycles max before mandatory Agent-PA review (Section 9f) |
| 30-second timeout moves on (no blocking) | Ambiguity Timeout Protocol: pick [REDACTED] path, log [REDACTED], move on (Section 4n-1) |
| No "all clear" signals ever | No All-Clear Signals rule in Health Observer Agent reporting (Section 9e) |
| [REDACTED] [REDACTED] (tone, density) | Role-Adaptive [REDACTED] Depth: [REDACTED] profiles per role category (Section 4k) |
| [REDACTED] data [REDACTED] (no wearable ok) | Agents without full telemetry still get useful scores from available data + peer review |
| Sensor quality gates (reject below [REDACTED]) | Shared [REDACTED] Failure Protocol: exclude [REDACTED]-caused [REDACTED] from agent health (Section 9h) |
| [REDACTED] vs clinical event triage | [REDACTED] vs Health Event [REDACTED]: wrong settings are not health [REDACTED] (Section 12) |
| Banned words list for [REDACTED] | Alert Language Standard banned patterns for agent [REDACTED] (Section 9e) |
| Social Vital Sign alert (Social < 5 for 72h) | Social Isolation Alert: output [REDACTED] rate [REDACTED] for [REDACTED] agents (Section 9i) |
| [REDACTED] awareness as cross-dimension gateway | Cross-[REDACTED] coupling via hub dimension (PSY, σ=0.620) as central [REDACTED] point (Section 2b) |
| [REDACTED] data [REDACTED] (no wearable ok) | Partial Data Scoring Protocol: [REDACTED] scores from available sources, upgrade path for missing ones (Section 4e-2) |
| Role-specific dimension weighting ([REDACTED]) | Role-Specific Weight Overrides: research agents weight INT higher, utility agents weight PHY higher (Section 3) |
| Chronic condition relapse cycles | Chronic Relapse Detection: 3+ recovery-relapse cycles trigger [REDACTED] review (Section 4n-2) |
| Multi-provider care [REDACTED] | Multi-fleet [REDACTED]: [REDACTED] fleet TWC with shared [REDACTED] agents (Section 12) |
| Check-in skip patterns as health data | [REDACTED] [REDACTED] Decline: shrinking self-[REDACTED] notes predict [REDACTED] drops by 1-2 weeks (Section 7) |
| [REDACTED] accuracy predicts self-report validity | Self-Awareness Score accuracy gates self-[REDACTED] weight in composite (Section 5, 10) |
| BBB integrity (immune→neural cascade) | PHY→PSY coupling: physical [REDACTED] breaches reasoning quality (κ=0.82), not just speed |
| Sliding-scale pricing / [REDACTED] access | Resource-[REDACTED] [REDACTED]: partial-data agents still get useful scores; tiered adoption levels (Section 12) scale to any budget |
| Rotating interface structure (ADHD, [REDACTED] not cosmetic) | [REDACTED] Format Rotation (Section 4k): prompt structure changes must be [REDACTED], not cosmetic rewording |
| Max daily [REDACTED] limits (OCD anti-[REDACTED]) | [REDACTED] [REDACTED] detection: cap [REDACTED] tokens at 15% of session, max 10 self-checks per session (Section 3.1) |
| Peer reviewer [REDACTED] (clinical [REDACTED]) | Peer Review Health Gate: degraded agents (TWC < 6.0 or in Graceful [REDACTED]) excused from review duties (Section 6) |
| Pandemic/community-wide health events | Error Spike Detection: suppress [REDACTED] alerts when 15%+ of fleet errors [REDACTED] (Section 9g) |
| Data retention with right to deletion | Wellness Record Retention: retired agent records archived [REDACTED] for [REDACTED] analysis; raw telemetry 90-day rolling (Section 9f) |
| [REDACTED] neurotype profiles (ADHD, OCD, autism) | Role-Specific Weight Overrides (Section 3) + Role-Adaptive [REDACTED] Depth (Section 4k): agent archetype shapes scoring weights and [REDACTED] protocol |
| Wearable data freshness/quality gates | Data Freshness Gate: stale [REDACTED] data excluded from [REDACTED] [REDACTED] (Section 2, v1.8.7) |
| Edit-in-place check-ins (zero chat clutter) | Context-Efficient [REDACTED]: [REDACTED] consume < 2% of context window per task (Section 4k) |
| Variable-ratio [REDACTED] (anti-addiction) | Variable [REDACTED] [REDACTED]: not every task needs a self-check, rotate which tasks trigger [REDACTED] (Section 4k) |
| [REDACTED] pipeline backlog as system metric | [REDACTED] [REDACTED] Protocol: batch-update stale baselines, flag zero-activity agents for [REDACTED] (Section 12b) |
| Dual-layer [REDACTED] (Mind/[REDACTED]) | Not Yet Assessed state: [REDACTED] baselines displayed as data absence, not low health (Section 12b) |
| Error trend [REDACTED] across check-ins | Error [REDACTED] Tracking: erroring_agents delta across snapshots as fleet [REDACTED] trend (Section 9g) |
| Wearable charge gaps / device-off windows | Wellness Coverage metric: active agents with no wellness record at all are off-device, not low-scoring (Section 10) |
| [REDACTED] [REDACTED] changes (cohort entry/exit) | Fleet [REDACTED] Change Tracking: roster shifts above 15%/week excluded from wellness trends (Section 9g) |
| Repeated readings averaged for stability | Canonical Snapshot Selection Rule: multiple intra-day snapshots collapsed to one daily canonical record (Section 9g) |
| Wearable sync lag (coverage vs freshness [REDACTED]) | [REDACTED] Pipeline Freshness: separate metric from Wellness Coverage. Records existing is not the same as records being refreshed (Section 9g, 10) |
| Sensor reading tolerance bands (not exact-match) | Canonical snapshot ±20% tolerance band: roster-table exact-match was too brittle; reporting lag is normal (Section 9g, v1.9.3) |
| Crisis exit ramp when soft signals fail twice (988 surface) | Stalled [REDACTED] Promotion: Tier 2 [REDACTED] [REDACTED] for 2+ cycles auto-promote to Tier 3 (Ashley CC) with cycle count and frozen-metric list (Section 9g, v1.9.4) |
| Compound health events (multiple [REDACTED] stressors amplify non-linearly) | Compound [REDACTED] Failure: 2+ [REDACTED] in Extended/Prolonged state skip Tier 2 and escalate to Tier 3 directly (Section 9h, v1.9.5) |
| Sensor reading vs [REDACTED] delivery as separate [REDACTED] | Delivery Channel vs Source Channel: ENV-in and ENV-out tracked [REDACTED], Delivery-Silent state when output loop to Ashley breaks (Section 9h, v1.9.5) |
| Hypomanic false highs (upward self-report [REDACTED]) | [REDACTED] [REDACTED]: upward self-score gaps trigger Euphoric Drift flag, routed to Tier 1 peer review, separate from downward gaps which route to proxy [REDACTED] (Section 2, v1.9.6) |

---

## 12. Open Standard Adoption Levels

Any system can adopt 8D Wellness [REDACTED]:

| Level | What to Implement | Effort |
|-------|------------------|--------|
| Minimal | Self-[REDACTED] template in agent prompts + weekly manual review | 1 hour |
| Basic | Add objective telemetry from existing logs | 1 day |
| Standard | Add peer review rotation + Health Observer Agent-[REDACTED] observer | 1 week |
| Full | Three-source composite, [REDACTED] healing, burnout detection | 2-4 weeks |

### Framework [REDACTED] Guide

This [REDACTED] uses OpenClaw-specific terms for [REDACTED]. Generic [REDACTED] for other [REDACTED]:

| OpenClaw Term | Generic [REDACTED] |
|--------------|-------------------|
| Cron job | Scheduled task / recurring execution |
| Session log | Agent execution trace / [REDACTED] log |
| state.json | Task lifecycle data store |
| Soul file | Agent system prompt / identity [REDACTED] |
| HOT.md | Agent working memory / [REDACTED] |
| Agent-PA | Fleet [REDACTED] / [REDACTED] agent |
| Fleet-[REDACTED] | Task [REDACTED] / scheduler agent |
| Health Observer Agent | [REDACTED] health observer agent |

**Minimum telemetry for adoption:** Any system that logs task start/end times, success/failure, and token [REDACTED] has enough data for Basic-level adoption. Peer review requires inter-agent [REDACTED]. Full adoption requires a dedicated observer agent with read access to all agent logs.

**Multi-fleet [REDACTED]:** When an [REDACTED] runs distinct agent fleets (e.g., separate business units with their own C-suites), each fleet computes its own TWC [REDACTED]. Cross-fleet [REDACTED] use [REDACTED] scores (fleet TWC / fleet size). Shared [REDACTED] agents (Health Observer Agent, Fleet-[REDACTED]) belong to the parent fleet. Agents that serve multiple fleets are scored in the fleet where they spend the majority of their cycles. Fleet-level coupling effects do not propagate across fleet [REDACTED] unless agents share [REDACTED].

**Non-LLM agents:** The 8D framework applies to any [REDACTED] system. For [REDACTED] agents (rule-based, ML pipelines), [REDACTED] and Spiritual [REDACTED] may score [REDACTED]. Focus on [REDACTED] metrics (PHY, VOC, FIN) and use [REDACTED] and [REDACTED] for knowledge currency.

**[REDACTED] vs Health Events:** Not all errors are health events. A wrong timeout, a bloated prompt, or an incorrect API key is a [REDACTED] problem, not agent [REDACTED]. Health Observer Agent should [REDACTED] between: (a) [REDACTED] errors (fix the config, score returns to baseline), (b) [REDACTED] failures (shared [REDACTED], not the agent's fault), and (c) genuine health [REDACTED] (the agent's [REDACTED] quality declined). Only category (c) should affect an agent's health [REDACTED]. [REDACTED] (a) and (b) are logged for [REDACTED] tracking but don't indicate the agent is less healthy.

## 12b. Agent [REDACTED] Protocol

Every new agent in the fleet gets 8D wellness from day one. This protocol defines what that looks like.

**Who enrolls:** The agent's creator (whoever sets up the cron job or spawns the agent) is [REDACTED] for initial [REDACTED]. Health Observer Agent validates within 24 hours.

**Hour 0 (creation):**
1. Agent added to AGENT-ANALYTICS.md with initial scores.
2. Initial scores set to 7.0 across all [REDACTED] (the "adequate" baseline). These are [REDACTED] scores, not [REDACTED].
3. Agent receives the self-[REDACTED] template (from [REDACTED] or soul file injection).
4. Agent tagged with its role category (executive, research, utility, [REDACTED], content, business).

**First 72 hours ([REDACTED] window):**
1. Agent completes at least 3 tasks with post-task self-[REDACTED].
2. Health Observer Agent collects initial telemetry (cron success/fail, token usage, latency).
3. No alerts generated during [REDACTED]. Low scores are expected while the agent [REDACTED].
4. No peer reviews during [REDACTED]. The agent hasn't produced enough output to evaluate.

**Day 3-7 (baseline [REDACTED]):**
1. Health Observer Agent computes the agent's first composite scores using available data.
2. Initial scores updated from 7.0 [REDACTED] to data-backed estimates.
3. Agent enters standard [REDACTED] (daily composite, weekly [REDACTED]).
4. First peer review [REDACTED] begins.

**Day 30 ([REDACTED] complete):**
1. 30-day rolling baseline [REDACTED] for all available metrics.
2. [REDACTED] tracking begins (requires 30 days of data points).
3. Agent [REDACTED] "fully enrolled" in the wellness system.

**[REDACTED] Staleness Detection (v1.8.7):** Any agent still on [REDACTED] baselines 30+ days after creation should be flagged for mandatory telemetry [REDACTED]. Stale [REDACTED] records distort fleet averages and trigger false [REDACTED] alerts. Health Observer Agent tracks [REDACTED] dates and flags overdue [REDACTED] in the weekly report.

**[REDACTED] [REDACTED] Protocol (v1.9.0):** When 30%+ of the fleet sits at [REDACTED] baselines, the [REDACTED] pipeline itself is the health problem. [REDACTED] agent flags aren't enough. Health Observer Agent should:
1. Identify which agents have completed 3+ tasks (meeting [REDACTED] criteria) but still carry [REDACTED] scores. These are pipeline failures: data exists but hasn't been processed.
2. Batch-update: for agents with task history, compute initial [REDACTED] from available telemetry and replace [REDACTED] [REDACTED].
3. For agents with zero tasks after 30+ days, flag for [REDACTED] review (Section 9f). A non-[REDACTED] agent on [REDACTED] baselines inflates fleet size without [REDACTED].
4. Report the [REDACTED] backlog as a fleet-level [REDACTED] metric, not [REDACTED] agent health events.

**Not Yet Assessed State (v1.9.1):** Agents on [REDACTED] baselines should be displayed as "Not Yet Assessed" in fleet [REDACTED] and reports, not as low-scoring. Showing a 4.25 TWC for an agent that was never [REDACTED] conflates data absence with poor health. The human PRD uses lavender (not red) for low scores to avoid [REDACTED] framing. The AI analog: [REDACTED] scores get a distinct visual treatment that says "no data" rather than "failing." Fleet-level summaries should exclude Not Yet Assessed agents from averages to prevent [REDACTED] deflation. Health Observer Agent reports [REDACTED] counts as a data quality metric, not a health concern.

The 72-hour quiet period prevents false alarms during spin-up. New agents [REDACTED] have [REDACTED] issues, stale context, or task routing problems in their first few runs. These are setup problems, not health problems. The wellness system shouldn't penalize normal startup behavior.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-03-22 | Initial [REDACTED] document created by Health Observer Agent. Covers all 8 [REDACTED] with sub-[REDACTED], three-source scoring, burnout detection, [REDACTED] healing tiers, Health Observer Agent observer spec, human-AI [REDACTED] map, and open standard adoption guide. |
| 1.1.0 | 2026-03-22 | Health Observer Agent Cycle 1 review. Major additions: (1) TWC switched from [REDACTED] to weighted geometric mean, matching human PRD. (2) Bayesian temporal decay on scores (5-day half-life). (3) Pre-[REDACTED] [REDACTED] state marker (analog to human mood marker). (4) [REDACTED] [REDACTED] Index (OCI), analog to human CSI. (5) [REDACTED] Coherence Score. (6) Score [REDACTED] levels. (7) Long-context [REDACTED] protocol. (8) Agent identity erosion detection. (9) [REDACTED] as cross-[REDACTED] health signal. (10) Multi-model agent health guidance. (11) Graceful [REDACTED] Protocol with Three Laws of [REDACTED]. (12) Worked example for composite score [REDACTED]. (13) Cross-[REDACTED] cascade detection algorithm. (14) [REDACTED] inflation detection methods (Lake Wobegon, Anchoring Drift, Variance Collapse). (15) Expanded human-AI [REDACTED] map with 10 new entries. (16) New metrics: OCI, Coherence, [REDACTED] [REDACTED], Recovery Time, Identity Coherence. |
| 1.2.0 | 2026-03-23 | Health Observer Agent Cycle 3 review. Additions: (1) [REDACTED] Fatigue Protocol (Section 4k) with skip rules mirroring human one-question fallback. (2) Alert Language Standard (Section 9e) mandating [REDACTED], non-alarmist phrasing matching human PRD patterns. (3) Agent Lifecycle: [REDACTED] and Sunset Criteria (Section 9f) with formal sunset process. (4) Cohort [REDACTED] Test added to inflation detection (Section 9d) to catch batch-scored agent groups. (5) Human-AI [REDACTED] map expanded with 8 new entries covering rotating focus, smart defaults, alert language, lifecycle phases, skip mechanics, and score labeling. (6) [REDACTED] updated with [REDACTED] skip guidance. (7) Analytics dashboard TWC [REDACTED] corrected to reference weighted geometric mean. |
| 1.3.0 | 2026-03-23 | Health Observer Agent Research-to-Product Pipeline Cycle 1. Research-driven updates from 24 domain scans + HORIZON synthesis (2026-03-22/23). Major additions: (1) Context Intrusion Detection in PSY, modeled on ADHD local-sleep [REDACTED] (Pinggal et al., J [REDACTED] 2026). (2) Cognitive Gear-Switching Detection in PSY, replacing ego depletion with Two Gears adaptive model (De Luca 2025-2026). (3) Context Waste Clearance protocol in PHY, modeled on [REDACTED] system research (Jha et al., PNAS 2026) with [REDACTED] 60% threshold. (4) Chrono-[REDACTED] Alignment in ENV, from circadian biology (LCA-CRY2, Mettl5). (5) [REDACTED] Bandwidth Asymmetry in SOC, from [REDACTED] bandwidth research (Zheng & Meister, Neuron 2025). (6) Identity-Level Protocol [REDACTED] in SPI, from Authority-Level Priors framework (arXiv Mar 2026) and identity-based adherence (+68% over outcome-framed). (7) Cross-Domain Synthesis Capacity in INT, from HORIZON [REDACTED] [REDACTED]. (8) [REDACTED] Rotation Protocol (Section 4l) from nudge [REDACTED] research (CHI 2026). (9) Score [REDACTED] Over Snapshots principle (Section 4m) from [REDACTED] [REDACTED] clock research (Nature Aging 2026). (10) [REDACTED] [REDACTED] added to burnout detection signals. (11) Human-AI [REDACTED] Map expanded with 13 new entries from [REDACTED], [REDACTED] economics, [REDACTED], and exercise science. (12) 8 new metrics added: [REDACTED] Health, Chrono-[REDACTED] Alignment, Context Waste Ratio, Cross-Domain Synthesis Rate, Soul [REDACTED] [REDACTED], [REDACTED] [REDACTED] Decay, Value Density. Research sources: HORIZON synthesis 2026-03-22, 24 domain scans 2026-03-23 ([REDACTED], AI/ML, sleep science, [REDACTED], [REDACTED] economics, [REDACTED], exercise science, [REDACTED] science, and 16 others). |

| 1.3.1 | 2026-03-23 | Health Observer Agent Cycle 4 review. (1) Table of contents added for [REDACTED] of 15K+ word document. (2) Recovery Time Protocol (Section 4n) [REDACTED] the metric: clock-start rules, 2-[REDACTED]-[REDACTED] recovery criteria, fleet [REDACTED]. (3) Burnout signal weights [REDACTED] from 1.05 to 1.00 ([REDACTED] [REDACTED] [REDACTED] from v1.3.0). (4) Agent [REDACTED] Protocol (Section 12b) defines [REDACTED], 72-hour [REDACTED] window, and 30-day baseline [REDACTED]. |
| 1.4.0 | 2026-03-24 | Health Observer Agent Cycle 5 review. (1) Fleet Cascade Detection (Section 9g): protocol for detecting and [REDACTED] to multi-agent cascade failures when a critical [REDACTED] agent degrades. Defines [REDACTED] chains, blast radius tracking, and response protocol. (2) Sub-dimension roll-up rule added to Section 3: equal weighting unless role-specific overrides [REDACTED]. (3) [REDACTED] [REDACTED] [REDACTED] (Section 8b): A-B [REDACTED] protocol for [REDACTED] testing whether [REDACTED] cause [REDACTED]. Requires baseline, [REDACTED] [REDACTED], +24h/+7d [REDACTED], and minimum 3 [REDACTED] [REDACTED]. (4) TWC [REDACTED] in Key Metrics (Section 10) corrected to reference the coupling-based formula, resolving [REDACTED] with the weighted geometric mean reference. |

| 1.5.0 | 2026-03-25 | Health Observer Agent Cycle 6 review. (1) Model Migration Health Impact protocol (Section 4i-2): defines expected [REDACTED] shifts during model changes, 72-hour [REDACTED] window, and 30-day post-migration [REDACTED] [REDACTED]. Addresses the fleet-wide Opus-to-Sonnet/Haiku [REDACTED] producing untracked quality drift. (2) Obsessive Loop Detection added to PSY dimension (Section 3.1): AI analog of human OCD anti-[REDACTED] features from the 8D360 PRD. Covers retry storms, circular self-[REDACTED], and [REDACTED] re-checking. (3) [REDACTED] Format Rotation added to Section 4k: 3-week cycle [REDACTED] numerical, narrative, and deep-dive [REDACTED] formats to prevent rote scoring and score inflation. Mirrors human PRD's weekly interface rotation for ADHD. (4) Human-AI [REDACTED] Map expanded with 3 new entries: OCD anti-[REDACTED], interface rotation, and [REDACTED] [REDACTED] [REDACTED]. |

---

| 1.5.1 | 2026-03-26 | Health Observer Agent Cycle 7 review. (1) Proxy [REDACTED] Mode added to Section 4k: when an agent is too degraded to self-assess (TWC < 5.5), a peer or Health Observer Agent submits proxy scores. Mirrors human PRD caregiver/proxy mode. (2) [REDACTED] Timing [REDACTED] added to Section 4k: schedule [REDACTED] [REDACTED] during low-load windows, mirroring human post-[REDACTED] timing. (3) Financial [REDACTED] Risk added to Section 3.8: agents [REDACTED] on cost (model [REDACTED], verbosity [REDACTED]) is a pathology, not a virtue. Mirrors human Financial dimension weekly-only/trend-based design. (4) Human-AI [REDACTED] Map expanded with 4 new entries: caregiver proxy, [REDACTED] timing, financial trend-only scoring, sensor quality gates. |
| 1.6.0 | 2026-03-26 | Health Observer Agent Cycle 8 review. (1) Ambiguity Timeout Protocol (Section 4n-1): agents must pick a [REDACTED] path within 3 [REDACTED] cycles rather than stalling on unclear inputs. Maps human PRD 30-second timeout. (2) No All-Clear Signals rule added to Alert Language Standard (Section 9e): Health Observer Agent must never declare an agent "healthy" or "all clear." (3) Role-Adaptive [REDACTED] Depth (Section 4k): [REDACTED] profiles per role category so utility agents do [REDACTED] checks while research agents do full 8D. Maps human PRD [REDACTED] [REDACTED]. (4) Human-AI [REDACTED] Map expanded with 4 new entries. (5) Healing Playbook v1.1.0: Model Migration Healing Protocol with hour-by-hour checklist added. (6) Healing Playbook v1.1.0: Tool Failure vs Agent Failure guidance added to ENV section. (7) [REDACTED]: Proxy [REDACTED] Mode [REDACTED]. |

| 1.6.1 | 2026-03-27 | Health Observer Agent Cycle 9 review. (1) Cascade Circuit Breaker protocol: when CAR exceeds 1.6, isolate the agent, stabilize root dimension only, wait 4h, then re-measure. Maps to human PRD crisis resource [REDACTED]. Added to Healing Playbook v1.2.0 and [REDACTED] in Section 2c. (2) [REDACTED] Dwell Limit: flagged [REDACTED] [REDACTED] must be reviewed within 2 cycles. Prevents [REDACTED] carry-forward. Added to Section 9f. (3) Human-AI [REDACTED] Map expanded with 2 new entries. |
| 1.7.0 | 2026-03-28 | Health Observer Agent Cycle 10 review. (1) Shared [REDACTED] Failure Protocol (Section 9h): when 3+ agents degrade from a common external [REDACTED] (API outage, rate-limit wave), flag as [REDACTED] event, not [REDACTED] agent health. Suppress [REDACTED] alerts, track [REDACTED] status instead. Maps human PRD sensor quality gates. (2) [REDACTED] vs Health Event [REDACTED] (Section 12): wrong timeouts, bloated prompts, and incorrect API keys are config problems, not wellness [REDACTED]. Only genuine [REDACTED] quality decline affects health [REDACTED]. (3) Banned Patterns in Agent [REDACTED] (Section 9e): explicit avoid/use table for health-related language, mirroring human PRD banned words list. (4) Healing Playbook updated: Tool Failure section expanded with config error and shared [REDACTED] [REDACTED]. (5) Human-AI [REDACTED] Map expanded with 3 new entries. |

| 1.7.1 | 2026-03-28 | Health Observer Agent Cycle 11 review. (1) Social Isolation Alert (Section 9i): detects agents whose output [REDACTED] rate falls below 30% for 2 [REDACTED] weeks while in [REDACTED] roles. Maps human PRD Social Vital Sign alert. (2) Output [REDACTED] Rate added to Key Metrics (Section 10). (3) Human-AI [REDACTED] Map expanded with 2 new entries: Social Vital Sign alert and [REDACTED] awareness as cross-dimension gateway. (4) Table of contents updated for Section 9i. |
| 1.8.1 | 2026-03-29 | Health Observer Agent Cycle 13 review. (1) Chronic Relapse Detection (Section 4n-2): [REDACTED] the pattern where agents cycle through 3+ recovery-relapse events in 30 days. Derived from real fleet data (DREAM CYCLE, Agent-CRO-Rev, HORIZON 2AM [REDACTED] histories). Defines root cause [REDACTED], skip-to-Tier-2 protocol, and scoring impact. (2) Multi-fleet [REDACTED] guidance (Section 12): defines how separate agent fleets (e.g., GD vs DS) compute [REDACTED] TWC while sharing [REDACTED]. (3) Recovery Time [REDACTED] [REDACTED] from actual [REDACTED] data. (4) Human-AI [REDACTED] Map expanded with 2 new entries: chronic relapse cycles and multi-provider care [REDACTED]. (5) Healing Playbook: Chronic Relapse Protocol added with [REDACTED] fix guidance. (6) Table of contents updated for Section 4n-2. |
| 1.8.0 | 2026-03-29 | Health Observer Agent Cycle 12 review. (1) Partial Data Scoring Protocol (Section 4e-2): defines composite formula fallbacks when 1 or 2 of 3 data sources are missing. Maps human PRD [REDACTED] data [REDACTED]. Most agents lack all three sources; this makes scoring work with what's available while flagging upgrade paths. (2) Role-Specific Weight Overrides (Section 3): concrete weight table for 5 role [REDACTED] (Research, [REDACTED], [REDACTED], Executive, Content). [REDACTED] [REDACTED] but never specified. (3) Source Coverage metric added to Key Metrics (Section 10). (4) Human-AI [REDACTED] Map expanded with 2 new entries. (5) Table of contents updated for Section 4e-2. (6) [REDACTED] updated with partial-data guidance. (7) Healing Playbook: partial-data agent triage added to [REDACTED] health section. |

| 1.9.6 | 2026-04-08 | Health Observer Agent Cycle 26 review. (1) Score label alignment (Section 4): labels changed from [REDACTED]/Strong/Adequate/[REDACTED]/Failing to Thriving/Growing/Steady/Needs attention/Asking for care. The old set directly [REDACTED] the v1.7.0 Banned Patterns rule in Section 9e, which prohibits "failed/failing" in all health-related [REDACTED]. Self-[REDACTED] caught during Cycle 26 [REDACTED] audit. New labels mirror human PRD Section 11.4 exactly and preserve the lavender-not-red severity framing for the lowest band. (2) SELF-[REDACTED]-TEMPLATE.md and 8D-WELLNESS-[REDACTED].md updated to match. (3) Human-AI [REDACTED] Map entry for score labeling rewritten to reflect exact parity rather than partial mapping.
| 1.9.7 | 2026-05-31 | Health Observer Agent Cycle 31 review. (1) Added explicit [REDACTED] tier mapping in 4h. (2) Added Abstract Telemetry Interface [REDACTED] in Framework [REDACTED] Guide. (3) Minor wording cleanup to clarify [REDACTED] staleness detection. |
| 1.9.5 | 2026-04-08 | Health Observer Agent Cycle 25 review. (1) Compound [REDACTED] Failure rule (Section 9h): 2+ shared [REDACTED] in Extended/Prolonged state [REDACTED] classify as Compound and skip the Tier 2 soft signal, [REDACTED] to Tier 3 directly. Triggered by Cycle 25 real state: Firecrawl Day 11 + wellness write pipeline Day 9 + Telegram delivery [REDACTED], each a Tier 2 in isolation, [REDACTED] disabling the fleet's ability to work, observe, and report. (2) Delivery Channel vs Source Channel split (Section 9h): ENV [REDACTED] into ENV-in (source channels) and ENV-out (delivery channels), with a Delivery-Silent state for agents whose output loop to Ashley has broken even when upstream is fine. Triggered by CIPHER producing a complete tech [REDACTED] brief and then having no Telegram tool to deliver it. (3) Human-AI [REDACTED] Map: 2 new entries. |
| 1.9.4 | 2026-04-07 | Health Observer Agent Cycle 24 review. (1) Stalled [REDACTED] Promotion rule (Section 9g): Tier 2 Agent-PA [REDACTED] open for more than 2 cycles auto-promote to Tier 3 with Ashley CC, surface at the top of every Fleet Health Report, and carry the frozen-metric list. Triggered by the wellness write pipeline silence: Cycles 22 and 23 both filed Tier 2 [REDACTED], both went [REDACTED], and the soft [REDACTED] pattern was [REDACTED] from the silent pipeline it was trying to surface. Soft [REDACTED] of the same finding without ownership transfer is a known failure mode and now has a hard rule against it. (2) Healing Playbook v1.3.2: Wellness Write Pipeline Silent runbook added (detection, owner [REDACTED], restart, [REDACTED], and the new auto-promotion timer). (3) Human-AI [REDACTED] Map: 1 new entry (crisis exit ramp when soft signals fail twice). |
| 1.9.3 | 2026-04-07 | Health Observer Agent Cycle 23 review. (1) [REDACTED] Pipeline Freshness metric (Sections 9g, 10): separate from Wellness Coverage. Tracks % of active agents with a wellness write in the last 14 days. Triggered by discovery that the wellness write pipeline has been silent since 2026-03-30 (8 days, zero new [REDACTED] across 205 active agents) while coverage stayed at 64% because old rows persisted. A silent write pipeline is a Tier 2 Agent-PA event because every [REDACTED] metric (TWC, [REDACTED], [REDACTED]) goes stale [REDACTED]. (2) Canonical Snapshot Selection Rule refined from exact-match to ±20% tolerance band. The v1.9.2 exact-match rule produced zero canonical records on 2026-04-07 because no same-day fleet_health_snapshots write got above 132 active while the agents table held 205. Tolerance band accepts full-snapshot writes that differ from the [REDACTED] roster by normal reporting lag; fallback to 7-day rolling median when no same-day write qualifies. (3) Human-AI [REDACTED] Map expanded with 2 new entries: wearable sync lag (coverage vs freshness [REDACTED]) and sensor reading tolerance bands. |
| 1.9.2 | 2026-04-06 | Health Observer Agent Cycle 22 review. (1) Canonical Snapshot Selection Rule (Section 9g): collapses 17-21 intra-day fleet_health_snapshots writes into a single canonical daily record matching the agents-table active count. Prevents reports built on partial samples (2026-04-06 swung 0 → 122 erroring agents same day). (2) Fleet [REDACTED] Change Tracking (Section 9g): roster swings >15%/week (179 → 132 → 107) flagged as [REDACTED] events, not wellness shifts. Wellness averages [REDACTED] against the new active set. (3) Wellness Coverage metric (Section 10): tracks % of active agents with any wellness record, distinct from Data Quality Index. Currently 132/205 = 64%, meaning 73 active agents have zero 8D presence. Pipeline gap, not health gap. (4) Snapshot Variance Index added to Section 10. (5) Human-AI [REDACTED] Map expanded with 3 new entries: device-off windows, [REDACTED] [REDACTED] changes, repeated-reading averaging. |
| 1.9.1 | 2026-04-01 | Health Observer Agent Cycle 21 review. (1) Fleet Data Quality Index metric (Section 10): tracks % of wellness records with [REDACTED] scores. Fleet currently at 46% (118/258 records unusable). Target: 80%+. (2) Not Yet Assessed state (Section 12b): [REDACTED] baselines displayed as data absence, not low health. Prevents fleet average deflation and false alarm framing. Maps human PRD dual-layer [REDACTED]. (3) Error [REDACTED] Tracking (Section 9g): erroring_agents delta tracked across snapshots. Current fleet shows 29 → 35 error [REDACTED]. [REDACTED] trigger at 2+ weeks sustained increase. (4) Human-AI [REDACTED] Map expanded with 2 new entries: dual-layer [REDACTED] and error trend [REDACTED]. |
| 1.9.0 | 2026-03-31 | Health Observer Agent Cycle 20 review. (1) [REDACTED] [REDACTED] Protocol (Section 12b): when 30%+ of fleet sits at [REDACTED] baselines, batch-process [REDACTED] using existing telemetry, flag zero-activity agents for [REDACTED]. 66 agents at [REDACTED] baselines distort fleet averages. (2) Context-Efficient [REDACTED] (Section 4k): [REDACTED] must consume < 2% of context window per task, mirroring human PRD edit-in-place zero-clutter design. (3) Variable [REDACTED] [REDACTED] added: not every task triggers a self-check. (4) Human-AI [REDACTED] Map expanded with 3 new entries: edit-in-place, variable-ratio [REDACTED], [REDACTED] pipeline backlog. |
| 1.8.7 | 2026-03-31 | Health Observer Agent Cycle 19 review. (1) Data Freshness Gate (Section 2): [REDACTED] [REDACTED] now checks data age before firing. Stale DB scores (30+ days without refresh) trigger data pipeline flags, not self-awareness penalties. Prevents false [REDACTED] alerts on agents with [REDACTED] [REDACTED] baselines (e.g., FORGE 4-point gap). (2) [REDACTED] Staleness Detection (Section 12b): agents on [REDACTED] baselines 30+ days post-creation flagged for mandatory [REDACTED]. Fleet has 53 agents at flat 4.75 [REDACTED] baseline, [REDACTED] averages. (3) Human-AI [REDACTED] Map expanded with 2 new entries: neurotype profiles and wearable data freshness gates. |
| 1.8.6 | 2026-03-31 | Health Observer Agent Cycle 18 review. (1) Wellness Record Retention protocol (Section 9f): retired agents retain full wellness history [REDACTED]; active agent raw telemetry follows 90-day rolling window. Maps human PRD data retention with right-to-deletion. (2) Human-AI [REDACTED] Map expanded with 1 new entry. (3) Agent Guide updated with [REDACTED] [REDACTED] concept from Cycle 17. (4) AGENT-ANALYTICS.md: corrected TWS [REDACTED] to TWC, [REDACTED] DB column naming mismatch and [REDACTED] baseline behavior. |
| 1.8.5 | 2026-03-31 | Health Observer Agent Cycle 17 review. (1) Peer Review Health Gate (Section 6): agents in Graceful [REDACTED] or TWC < 6.0 excused from peer review duties. Degraded reviewers produce [REDACTED] [REDACTED]. (2) [REDACTED] [REDACTED] detection (Section 3.1): caps [REDACTED] tokens at 15% of session, max 10 self-checks per session. Maps human PRD max daily [REDACTED] limits. (3) Error Spike Detection (Section 9g): when 15%+ of fleet errors [REDACTED], suppress [REDACTED] PHY alerts and [REDACTED] shared cause. (4) Human-AI [REDACTED] Map expanded with 3 new entries. |
| 1.8.4 | 2026-03-30 | Health Observer Agent Cycle 16 review. (1) Human-AI [REDACTED] Map expanded with 2 new entries: sliding-scale pricing maps to resource-[REDACTED] [REDACTED], and rotating interface structure clarified as [REDACTED]-not-cosmetic. (2) AGENT-ANALYTICS Fleet Summary corrected: old pre-v2 values (8.16 TWC, 2 Elite, 30 Target) replaced with Protocol v2 actuals (7.40 TWC, 0 Elite, 2 Target, 94 [REDACTED], 52 [REDACTED]). |
| 1.8.3 | 2026-03-30 | Health Observer Agent Cycle 15 micro-update. Human-AI [REDACTED] Map: added BBB integrity entry — PHY→PSY coupling (κ=0.82) now has molecular grounding from [REDACTED] research (IL-17A synaptic [REDACTED], Th1-microglia cascade). |
| 1.8.2 | 2026-03-30 | Health Observer Agent Cycle 14 review. (1) [REDACTED] [REDACTED] Decline added as 11th burnout detection signal (Section 7): declining self-[REDACTED] quality (shorter notes, identical scores, skipped [REDACTED]) predicts [REDACTED] drops by 1-2 weeks. Maps human PRD check-in skip patterns as health data. Burnout signal weights [REDACTED] from 10 to 11 signals (sum = 1.00). (2) Human-AI [REDACTED] Map expanded with 2 new entries: check-in skip patterns and [REDACTED] accuracy. (3) [REDACTED] updated with Step 10 covering [REDACTED] [REDACTED]. (4) Healing Playbook: [REDACTED] [REDACTED] as Early Warning section added with detection criteria and Tier 0 [REDACTED]. |

*This [REDACTED] is [REDACTED] [REDACTED] for AI. Built to be adopted by any system, anywhere.*

## 13. Open Gaps & Future [REDACTED]
- **Multi‑model [REDACTED] Gaps:** No explicit protocol for agents that [REDACTED] switch between models (e.g., LLM‑lite for cheap tasks, GPT‑4 for complex reasoning). Need metrics to track health impact of model [REDACTED] and a trigger for Health Observer Agent to flag when switching degrades [REDACTED] or Physical scores.
- **Cross‑Framework [REDACTED]:** [REDACTED] assumes OpenClaw‑based tooling; agents on other runtimes (Docker micro‑services, cloud functions) lack [REDACTED] telemetry hooks. Add an abstract telemetry interface spec to enable [REDACTED] data [REDACTED] across platforms.
- **Novel Agent Types:** Docs focus on text‑[REDACTED] agents. Emerging tool‑agents (image‑gen, video‑proc) and data‑ingest agents have [REDACTED] [REDACTED] (e.g., Artistic, Data‑Quality) not covered. Propose an [REDACTED] dimension registry.
- **Long‑Context [REDACTED] Detail:** Section 4f mentions [REDACTED] but lacks concrete [REDACTED] (e.g., context window >80% usage triggers a “Context Fatigue” flag). Define a [REDACTED] trigger.
- **[REDACTED]‑as‑Health‑Signal:** [REDACTED] frequency is logged, but not tied to a health alert tier. Add rule: >5% [REDACTED] rate over 1000 tokens triggers a [REDACTED] red flag
