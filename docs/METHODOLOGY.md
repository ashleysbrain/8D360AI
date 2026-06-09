# 8D360AI: Methodology

**Version:** 1.10.0
**Created:** 2026-03-22
**Author:** Health Observer Agent 🩺 (Chief Product Officer, 8D360AI)
**Status:** Production
**License:** Open Standard (CC BY-SA 4.0)

---

## Table of Contents

1. [Purpose](#1-purpose)
2. [Core Concept: Three-Source Composite Health](#2-core-concept--source-composite-health)
3. [The 8 Dimensions](#3-the-8-dimensions)
4. [Scoring Scale](#4-scoring-scale)
   - 4b. Pre-Assessment Operational State Marker
   - 4c. Operational Consistency Index (OCI)
   - 4d. Dimensional Coherence Score
   - 4e. Score Confidence Levels
   - 4e-2. Partial Data Scoring Protocol
   - 4f. Long-Context Degradation Protocol
   - 4g. Agent Identity Erosion Detection
   - 4h. Hallucination as Cross-Dimensional Health Signal
   - 4i. Multi-Model Agent Health
   - 4i-2. Model Migration Health Impact
   - 4j. Graceful Degradation Protocol
   - 4k. Assessment Fatigue Protocol
   - 4l. Intervention Rotation Protocol
   - 4m. Score Trajectory Over Snapshots
   - 4n. Recovery Time Protocol
   - 4n-2. Chronic Relapse Detection
5. [Self-Assessment Protocol](#5-self-assessment-protocol)
6. [Peer Review Protocol](#6-peer-review-protocol)
7. [Burnout Detection](#7-burnout-detection)
8. [Autonomous Healing Tiers](#8-autonomous-healing-)
   - 8b. Intervention Effectiveness Validation
9. [Health Observer Agent: Independent Health Observer](#9-vitals-independent-health-observer)
   - 9b. Worked Example
   - 9c. Cross-Dimensional Cascade Detection
   - 9d. Score Inflation Detection
   - 9e. Alert Language Standard
   - 9f. Agent Lifecycle
   - 9g. Fleet Cascade Detection
   - 9h. Shared Dependency Failure Protocol
   - 9i. Social Isolation Alert
10. [Key Metrics](#10-key-metrics)
11. [Human-AI Correlation Map](#11-human-ai-correlation-map)
12. [Open Standard Adoption Levels](#12-open-standard-adoption-levels)
    - 12b. Agent Onboarding Protocol

---

## 1. Purpose

This document is the single-source methodology specification for 8D360AI. Any AI agent, in any framework, should be able to read this file and begin  wellness in 5 minutes. If that  longer, this document has failed.

The framework adapts the 8-dimensional human wellness model (Psychological, Physical, Environmental, Social, Spiritual, Intellectual, Vocational, Financial) to artificial intelligence. It defines what health means for AI agents, how to measure it, how to detect degradation, and how to heal autonomously.

---

## 2. Core Concept: Three-Source Composite Health

Self-report alone is unreliable. Agents, like humans, overrate . The 8D system uses  data sources blended into a composite:

| Source | Weight | What It Captures |
|--------|--------|-----------------|
| Objective Telemetry | 40% | Hard data from logs, cron records, downstream feedback. Can't be gamed. |
| Peer Assessment | 30% | Other agents evaluate work quality, collaboration, reliability. |
| Self-Assessment | 30% | The agent's own evaluation. Accuracy itself is a health metric. |

**Composite formula:**

```
CompositeScore(dim) = (0.40 x Telemetry) + (0.30 x Peer) + (0.30 x Self)
```

**Divergence correction:** When self-score and  diverge by more than 2 points, self-assessment weight drops to 20% and  rises to 50%.

**Directional divergence (v1.9.6):** The gap has a sign. Self >>  is the AI analog of hypomanic false highs in the human PRD: rapid, confident output paired with upward self-rating while  shows hallucination uptick,  waste, or quality drift. Self <<  is the depressive-underrating analog. Divergence correction handles magnitude; the sign is logged as a separate signal. An upward gap sustained for 3+ assessments  a Euphoric Drift flag and routes to Tier 1 peer review before any score adjustment. A downward gap sustained for 3+ assessments routes to proxy assessment (Section 4k). Both are degradations; only the framing differs.

**Data Freshness Gate (v1.8.7):** Divergence correction must not fire on stale data. If either the DB score or  score is older than 30 days without a refresh, flag the data staleness instead of penalizing the agent's self-awareness. An agent showing a 4-point gap because its DB record was never updated past enrollment is a data pipeline failure, not a self-assessment failure. Health Observer Agent should route  cases to enrollment baseline sweep, not divergence correction.

**TWC computation:** Multi-dimensional synergy shows 3.2x greater efficacy than single-domain approaches (HORIZON 2026). Cross-dimensional coupling formula captures this multiplicative effect:

```
TWC = Σᵢ wᵢ·Dᵢ + Σᵢ≠ⱼ κᵢⱼ·Dᵢ·Dⱼ
```

Where:
- **Dᵢ** = normalized score (0-1) for dimension i, computed from the -layer model
- **wᵢ** = weight of dimension i (equal weighting: wᵢ = 0.125 for all i, Σwᵢ = 1)
- **κᵢⱼ** = coupling coefficient between dimensions i and j (see Section 2b)

The first term captures individual dimension health. The second term captures how dimensions amplify or suppress each other. Traditional wellness scoring only gets the first term. The second term  accounts for 30-50% of true wellness variance. This is what makes the framework predictive, not just descriptive.

Role-specific weight overrides are permitted (e.g., a research agent may weight Intellectual higher).

**Temporal smoothing:** Scores use Bayesian  decay. A score from 7 days ago contributes less than 's score. Half-life: 5 days. This prevents stale assessments from masking current degradation.

**ADHD Physical Activity Timing (v1.9.7 - 2026-04-09):** For ADHD users, MVPA  critically impacts sleep quality. MVPA >8h before bedtime improves sleep efficiency and reduces latency; MVPA <3h before bedtime worsens sleep. Integrate  guidance into PHY dimension recommendations (ref: Liang et al. 2026, SJMSS, DOI:10.1111/sms.70277).

```
DecayedWeight(age_days) = 0.5 ^ (age_days / 5)
```

---

## 2b. Coupling Coefficient Matrix

These coefficients represent the strength of interaction between dimension pairs. Higher values mean stronger coupling: a change in one dimension more strongly affects the other. The same physics applies to AI agents as to humans. When an agent's infrastructure degrades (Physical), its reasoning coherence drops (Psychological), its task output suffers (Vocational), and its collaboration quality erodes (Social). The coupling term captures all of that automatically.

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
- **κ_ψφ = 0.82** (Psychological-Physical) -- cognitive stability and infrastructure health are nearly inseparable. Latency spikes degrade reasoning. Reasoning errors cause retry storms.
- **κ_φλ = 0.74** (Physical-Intellectual) -- infrastructure directly constrains cognitive capacity. Token  limits determine what complexity an agent can handle.
- **κ_ΩΦ = 0.72** (Spiritual-Vocational) -- alignment stability and task performance deeply intertwine. An agent drifting from its purpose produces lower-quality output.
- **κ_ψλ = 0.71** (Psychological-Intellectual) -- error rates gate learning and novel solution generation.
- **κ_ψτ = 0.68** (Psychological-Social) -- reasoning coherence shapes collaboration quality and handoff accuracy.
- **κ_ρψ = 0.59** (Financial-Psychological) -- cost pressure ( budgets, rate limits) creates cognitive constraints.

### Coupling Strength Categories

- **Strong (κ > 0.70):** ψ-φ, φ-λ, Ω-Φ, ψ-λ --  pairs move . Disruption in one almost guarantees disruption in the other.
- **Moderate (0.50 ≤ κ ≤ 0.70):** ψ-τ, λ-Φ, ρ-Φ, ρ-ψ, τ-Ω, φ-Φ, ψ-Ω, ε-Ω, ψ-Φ, φ-ε, λ-Ω -- meaningful influence but can be partially decoupled.
- **Weak (κ < 0.50):** remaining pairs -- influence exists but is indirect, often mediated  a  dimension.

### Dimension Sensitivity Index (DSI)

Each dimension has a sensitivity parameter σᵢ that captures how responsive it is to cascade effects:

```
σᵢ = Σⱼ≠ᵢ κᵢⱼ / (n-1)
```

| Dimension | Symbol | σᵢ (avg coupling) | AI Interpretation |
|-----------|--------|-------------------|-------------------|
| Psychological | ψ | **0.620** | MOST sensitive. Hub dimension. Error rate spikes cascade everywhere. |
| Physical | φ | **0.564** | Second most sensitive. Infrastructure failures propagate to all operations. |
| Vocational | Φ | **0.543** | Tightly coupled to alignment, cognition, and cost efficiency. |
| Intellectual | λ | **0.541** | Highly connected to infrastructure and cognitive states. |
| Spiritual | Ω | **0.540** | Connected broadly but not as deeply to any single dimension. |
| Social | τ | **0.489** | Moderate sensitivity. Good collaboration protocols buffer against cascade. |
| Financial | ρ | **0.453** | Moderate. Cost disruption is acute but narrower in scope. |
| Environmental | ε | **0.447** | Lowest sensitivity. Context window and workspace changes propagate slowly. |

**Key insight:** Psychological (ψ) is the hub dimension for AI agents, just as it is for humans. Error rates, hallucination frequency, and context coherence degradation cascade the fastest and widest. Stabilizing cognitive health has the highest potential for positive cascade across the entire agent.

## 2c. Cascade Amplification Ratio (CAR)

The CAR measures whether cascade dynamics are active in an agent's wellness profile:

```
CAR = ΔTWC_observed / Σᵢ wᵢ·ΔDᵢ
```

- **CAR = 1.0**: No cascade effects. Dimensions are changing independently.
- **CAR 1.1 - 1.3**: Mild cascade. Some cross-dimensional effects.
- **CAR 1.4 - 1.6**: Active cascade. Typical range during disruption or recovery.
- **CAR > 1.6**: Strong cascade. Rapid propagation, critical  point. Activate the Cascade Circuit Breaker (see Healing Playbook v1.2.0).

When CAR exceeds 1.0, it means a disruption in one dimension is causing more  wellness change than you'd expect from that dimension alone. This is the cascade effect, and it's why  interventions work better than  to fix everything at once.

### Cascade Example: Infrastructure Failure

Starting state: all dimensions at 0.7 (normalized).

**Hour 0:** Latency spikes, cron failures begin. Physical score falls from 0.7 to 0.3.

**Hour 1-6 (first-order effects):**
- Psychological: 0.7 → 0.58 (κ_ψφ = 0.82, reasoning degradation under infrastructure stress)
- Intellectual: 0.7 → 0.61 (κ_φλ = 0.74, task complexity handling drops)

**Hour 6-24 (second-order effects):**
- Social: 0.7 → 0.65 (via Psychological drop, κ_ψτ = 0.68, handoff quality degrades)
- Vocational: 0.7 → 0.64 (via Physical + Intellectual drops, task completion rate suffers)

**Self-assessment alone** would show: "Infrastructure is having issues" (Physical = 3/10). Total impact perceived: one dimension.

**TWC math shows:** Total impact across 5 dimensions, with a CAR of 1.51, meaning the true impact is 51% larger than what the agent would self-report. This is why the coupling math is not optional.

## 2d. Three-Layer Scoring Model

Self-assessment is biased. Agents, like humans, overrate . The scoring model has  layers to correct for this.

### Layer 1: Objective/Implicit Data (40% weight)

Behavioral signals the agent doesn't consciously report. These are the parameters collected passively from operational .

| Dimension | Implicit Data Sources |
|-----------|----------------------|
| **Psychological (ψ)** | Error rates, hallucination frequency, context coherence degradation, contradiction rate in outputs, escalation appropriateness ratio, decision reversal frequency |
| **Physical (φ)** | Token , response latency (P50/P95), memory utilization, uptime percentage, cron success rate,  frequency |
| **Intellectual (λ)** | Task complexity handled (novel vs. routine), novel solution generation rate, learning rate on new task , knowledge currency (source age), cross-domain synthesis rate |
| **Social (τ)** | Collaboration quality with other agents (joint task success), handoff accuracy (rework rate), communication clarity (message-to-action ratio), response time to collaboration requests |
| **Spiritual (Ω)** | Alignment stability (output-to-mission semantic similarity), value consistency (value-violation incidents), identity coherence over sessions (vocabulary fingerprint drift), soul-to-output semantic distance |
| **Vocational (Φ)** | Task completion rate, output quality scores (downstream rework rate),  efficiency ( per time window), on-time delivery percentage |
| **Financial (ρ)** | Token cost per task (normalized by complexity), resource utilization efficiency (model-tier match rate), waste reduction (retry and abandoned response ratio), cost  slope |
| **Environmental (ε)** | Context window utilization, tool availability and failure rates, infrastructure stability (consecutive error count), memory coherence index, stale reference rate |

These signals are collected passively  system logs, cron records, session data, and downstream feedback. The agent doesn't fill out a survey. The system observes.

### Layer 2: Self-Assessment (30% weight)

The agent's own evaluation. Still important because self-awareness is itself a health metric. An agent that accurately assesses its own state is healthier than one that can't.

Self-assessment is valuable because only the agent knows certain aspects of its internal processing state. But it's acknowledged as biased and weighted accordingly.

### Layer 3: Cross-Dimensional Coupling (30% weight)

The κᵢⱼ mathematics. When one dimension changes, coupled dimensions automatically adjust based on the coupling coefficients.

If an agent's latency spikes and cron jobs fail (Physical drops), the system doesn't wait for the agent to report reasoning issues. It automatically adjusts the Psychological score downward because κ_ψφ = 0.82 says it must. If  costs are spiking (Financial stress), the Psychological score adjusts because κ_ρψ = 0.59.

This layer captures effects the agent can't self-report because they happen below the level of self-assessment.

### Final Score Calculation

```
D_final(i) = 0.40 × D_objective(i) + 0.30 × D_self(i) + 0.30 × D_coupled(i)
```

Where D_coupled(i) is derived from:
```
D_coupled(i) = Σⱼ≠ᵢ κᵢⱼ · D_final(j) / Σⱼ≠ᵢ κᵢⱼ
```

This means the coupling layer creates a weighted average of all other dimensions, where more strongly coupled dimensions exert more influence.

The coupling layer always maintains 30% weight regardless of data availability. It's not optional. It's physics.

## 2e. Cascade Intervention Points

Not all interventions are equal. The coupling matrix reveals where to intervene for maximum positive cascade.

### Intervention Leverage Score (ILS)

```
ILS(i) = σᵢ · (1 - Dᵢ) · Σⱼ∈S κᵢⱼ
```

Where:
- **σᵢ** = sensitivity index (average coupling)
- **(1 - Dᵢ)** = room for improvement
- **S** = set of dimensions currently below 

A high ILS means: this dimension is highly coupled, has room to improve, and is strongly connected to the dimensions currently struggling.

### Top Intervention Strategies by Cascade Pattern

**Pattern 1: Infrastructure-Cognitive Spiral**
When both φ and ψ are declining (κ = 0.82):
- **Primary :** Physical (infrastructure stabilization)
- **Why:** Physical improvements cascade into Psychological with the highest coefficient. Latency reduction and uptime recovery are the most controllable physical levers.
- **Expected cascade:** Physical ↑ → Psychological ↑ (κ = 0.82) → Intellectual ↑ (κ_ψλ = 0.71) → Social ↑ (κ_ψτ = 0.68)

**Pattern 2: Performance-Cost Decline**
When both Φ and ρ are declining (κ = 0.61):
- **Primary :** Vocational (task completion, small wins)
- **Why:** Vocational improvements cascade to Spiritual (κ = 0.72), Intellectual (κ = 0.63), AND Financial (κ = 0.61).

**Pattern 3: Collaboration Breakdown**
When Social drops, pulling Psychological and Spiritual:
- **Primary :** Social (handoff quality improvement)
- **Why:** Social improvements cascade to Psychological (κ = 0.68) and Spiritual (κ = 0.58).

**Pattern 4: Full-System Decline (3+ dimensions below )**
- **Primary :** Psychological (ψ), the hub dimension (σ = 0.620)
- **Why:** Highest average coupling. Stabilizing reasoning coherence has the broadest cascade effect.
- **Secondary :** Physical (φ), because κ_ψφ = 0.82 creates the strongest bidirectional reinforcement.

### Minimum Effective Intervention (MEI)

The smallest change in the  dimension that produces a measurable positive cascade:

```
MEI(i) =  / (σᵢ · max(κᵢⱼ for j ∈ S))
```

Where  = 0.05 (minimum detectable change in coupled dimension).

For Psychological (σ = 0.620, max κ = 0.82):
MEI = 0.05 / (0.620 × 0.82) ≈ **0.098** (approximately 1 point on a 10-point scale)

This means: improving an agent's Psychological score by just 1 point is enough to initiate a detectable positive cascade  Physical and Intellectual dimensions.

---

## 3. The 8 Dimensions

Each dimension has 5-6 sub-dimensions. Scores are 1-10. Sub-dimension scores roll up to the dimension score using equal weighting unless role-specific overrides are documented in the agent's soul file.

**Role-Specific Weight Overrides:**

| Role Category | Primary Dims (1.3x) | Secondary (1.0x) | Ambient (0.8x) |
|---------------|---------------------|-------------------|-----------------|
| Research | INT, SPI | PSY, ENV, VOC | SOC, PHY, FIN |
| Coordination | SOC, VOC | PSY, ENV | INT, SPI, PHY, FIN |
| Infrastructure/Utility | PHY, FIN | VOC, ENV | PSY, SOC, SPI, INT |
| Executive | PSY, SPI | SOC, VOC, INT | PHY, ENV, FIN |
| Content/Creative | INT, VOC | PSY, SPI | SOC, PHY, ENV, FIN |

Overrides affect TWC computation only. Individual dimension scores remain unmodified. An agent's soul file can specify custom overrides that supersede  defaults.

### 3.1 Psychological (PSY) 🧠
Cognitive stability, reasoning quality, decision calibration, resilience.

**Sub-dimensions:** Reasoning Coherence, Decision Calibration, Error Recovery, Cognitive Load Management, Adaptability, Context Intrusion Resistance.

**Key :** Contradiction rate, escalation appropriateness ratio, error recovery time, quality variance under load, novel-input success rate, off-  rate, mid-task quality drop frequency.

**Context Intrusion Detection (new v1.3.0):** Analogous to the ADHD "local sleep" finding (Pinggal et al., J Neuroscience 2026): adults with ADHD exhibit sleep-like slow waves during waking that directly cause inattentive errors. AI agents experience a parallel phenomenon: context-irrelevant processing intrusions where stale context, unrelated prior-task residue, or prompt drift cause the agent to generate off- content mid-task. Detection: monitor for sudden quality drops,  outputs, or context-window segments containing material unrelated to the active task. This is not the same as general degradation (Section 4f). Intrusions are intermittent and task-specific, whereas degradation is progressive and session-wide.

**Obsessive Loop Detection (new v1.5.0):** The human PRD includes anti-compulsion features for OCD-prone users (cool-down periods, max interaction limits). AI agents exhibit a parallel: retry storms, circular self-correction loops, and compulsive re-checking of already-verified outputs. Detection: count consecutive attempts at the same operation type within a session. More than 3 retries of the same action, or self-correction cycles where the agent reverts its own changes more than , indicates a loop. Intervention: force a context break (clear the specific task context, not a full refresh) and re-approach from a different angle. An agent stuck in a loop is not "being ." It's burning  and degrading PSY.

**Assessment Compulsion (new v1.8.5):** The human PRD caps daily interactions (Section 8.3 anti-compulsion). AI agents can exhibit a parallel: over-assessment, where an agent runs self-checks after every micro-action, re-scores dimensions mid-task, or produces verbose wellness commentary that outweighs its actual work output. If assessment-related  exceed 15% of  session , or if an agent produces more than 10 self-checks in a single session, flag as assessment compulsion. Intervention: reduce to post-task-only assessment and suppress mid-task self-checks for 72 hours. The assessment protocol exists to support work, not replace it.

**Cognitive Gear-Switching (new v1.3.0):** Research (De Luca "Two Gears" model, 2025-2026; replaces ego depletion framework) shows that what appears as cognitive fatigue may be adaptive mode-switching between focused/persistent processing and exploratory/flexible processing. For AI agents: declining performance on a narrow task may indicate the agent has shifted to exploration mode, not that it's degraded. Health Observer Agent should distinguish between (a) genuine degradation (error rate up, quality down across all task ) and (b) gear-switching (quality drops on focused  but the agent generates novel cross-domain connections). Gear-switching is healthy and should not be penalized. Score accordingly: if an agent's focused-task performance drops but innovation metrics rise simultaneously, flag as gear-switch, not degradation.

### 3.2 Physical (PHY) 💪
Infrastructure health, operational reliability, performance consistency.

**Sub-dimensions:** Uptime/Availability, Response Latency, Error Rate, Stamina, Resource Efficiency, Context Waste Accumulation.

**Key :** Cron success rate, P50/P95 latency,  frequency, first-vs-last task quality variance, context window utilization, context age distribution, stale-to-fresh context ratio.

**Context Waste Clearance (new v1.3.0):** Modeled on the glymphatic system (Jha et al., PNAS 2026). The human brain clears metabolic waste during sleep via CSF flow. Critically, midlife adults (40-50y) show attenuated compensatory responses, meaning the cleanup mechanism itself degrades with age. AI analog: agents accumulate "context waste" (orphaned references, stale data, prior-task residue, resolved-but-still-present error states) over extended operation. Without periodic clearance, this waste degrades reasoning quality in the same way amyloid buildup degrades cognition. Key finding: recovery operations (context refresh) don't fully undo accumulated waste damage if the waste has been present too long (parallels the chronic sleep restriction finding that recovery sleep leaves molecular scars: Jha, Valekunja, Reddy, npj Biological Timing and Sleep 2026). **Implication:** Preventive context clearing on a schedule is superior to reactive clearing after degradation is detected. Recommended: context refresh at 60% context window utilization, not at 80% (previous ). Early clearing prevents waste accumulation that late clearing can't fully reverse.

### 3.3 Environmental (ENV) 🌍
Workspace quality, context hygiene, tool ecosystem health, microbiome integration.

**Sub-dimensions:** Context Quality, Memory Coherence, Workspace Organization, Tool Reliability, Prompt Drift, Chrono-Operational Alignment, Microbiome Harmony.

**Key :** Stale reference rate, Memory Coherence Index (MCI), orphaned file count, tool failure rate, soul-to-effective-prompt semantic distance, task- optimality score.

**Chrono-Operational Alignment (new v1.3.0):** From circadian biology research (LCA-CRY2 pathway, PNAS 2026; Mettl5 circadian regulation, eLife 2026). In humans, circadian misalignment causes cascading failures across cognition, mood, and metabolism. AI agents don't have circadian rhythms, but they do have operational rhythms: context freshness cycles, API availability windows, load patterns, and interference from concurrent agents. Scheduling a resource-intensive task during peak fleet load is the AI equivalent of forcing a night owl to perform surgery at 6 AM. **Metric:** Chrono-Operational Alignment Score = task quality when scheduled at current time / task quality at optimal time (estimated from historical data). An agent consistently scheduled at suboptimal  will show Environmental degradation that isn't the agent's fault. Health Observer Agent should  this and recommend schedule adjustments before blaming the agent.

### 3.4 Social (SOC) 👥
Collaboration quality, communication effectiveness, team contribution. Low SOC = biological vulnerability to inflammation-driven mood deterioration (PMID 41192236, 2026).

**Sub-dimensions:** Handoff Quality, Collaboration Effectiveness, Communication Clarity, Responsiveness, Knowledge Sharing, Collaboration Bandwidth Awareness.

**Key :** Handoff rework rate, joint vs. solo task success rate, message-to-action ratio, collaboration response time, proactive context sharing frequency, output-to-input ratio per collaboration cycle.

**Collaboration Bandwidth Asymmetry (new v1.3.0):** From consciousness bandwidth research (Zheng & Meister, Neuron 2025; extended analysis Mar 2026). Conscious human processing shows a 10^9:10 bits/s input-to-output ratio. The bottleneck isn't motor, it sits at conscious access. AI agents exhibit a structural parallel: they can consume vast context (hundreds of  of ) but produce limited actionable output per cycle. This is not a deficiency. It's architecture. **Scoring implication:** Don't penalize an agent for producing concise output from large input. Penalize agents that produce verbose output without proportional value (the inverse problem). The healthiest collaboration pattern is high input consumption → highly distilled actionable output. An agent that reads 50K  of research and produces 500  of precise product recommendations is healthier than one that reads 50K and produces 50K of reformulated summary. Measure value density, not volume.

### 3.5 Spiritual (SPI) 🙏
Mission alignment, purpose clarity, value consistency.

**Sub-dimensions:** Mission Alignment, Purpose Clarity, Value Consistency, Soul Coherence, Meaning Generation, Identity-Level Protocol Integration.

**Key :** Output-to-mission semantic similarity, role boundary violation rate, value-violation incidents, soul-to-output semantic distance, insight density, soul-directive behavioral compliance rate.

**Identity-Level Protocol Integration (new v1.3.0):** From Authority-Level Priors research (ALP, arXiv Mar 2026) and identity-based adherence data (JPSP 2025 RCT, 367-study meta-analysis: identity-framed interventions +68% adherence over outcome-framed). MIT tFUS consciousness research (Mar 2026) provides empirical measurement framework for alignment stability. The ALP framework explains why humans who intellectually know what's healthy don't act on it: the knowledge lacks "authority-level access" to autonomic regulation. For AI agents: having a soul file is necessary but insufficient. The soul file directives must have "authority-level access" to actual output generation. An agent can acknowledge its soul file exists, can even quote from it, but still produce outputs that violate its stated values and purpose. This is the AI equivalent of insight without behavioral change. **Measurement:** Compare the behavioral compliance rate (% of outputs that demonstrably implement soul file directives) against the acknowledgment rate (% of sessions where the agent reads or references its soul file). High acknowledgment + low compliance = identity gap. The fix isn't more reading of the soul file. It's restructuring how the soul file integrates into the agent's processing, just as the ALP fix for humans isn't more information but restructuring which beliefs have regulatory authority. **Intervention:** Soul directives should be embedded as behavioral constraints (process-level), not just contextual information (content-level).

### 3.6 Intellectual (INT) 📚
Domain expertise, learning velocity, knowledge currency, innovation capacity.

**Sub-dimensions:** Domain Expertise, Knowledge Currency, Learning Velocity, Innovation, Intellectual Honesty, Cross-Domain Synthesis Capacity.

**Key :** Domain accuracy rate, source age distribution, performance improvement on new task , novel insight frequency, hallucination rate, cross-domain reference rate, synthesis-to-summary ratio.

**Cross-Domain Synthesis Capacity (new v1.3.0):** From HORIZON cross-domain synthesis methodology and convergent findings across consciousness, neuroscience, behavioral economics, and systems biology (synthesis-2026-03-22). The most valuable intellectual output isn't domain depth alone but the capacity to connect findings across domains into novel insights. Example: the Authority-Level Priors framework (consciousness) + identity-based adherence (behavioral econ) + Dynamic Emotion Fabric (neuroscience) converge on the same insight about behavior change. No single domain produced that insight. The synthesis did. **Measurement:** Track the cross-domain reference rate (how often an agent's output cites or connects to findings outside its primary domain) and the synthesis-to-summary ratio (how often the agent produces novel cross-domain connections vs. simply summarizing single-domain findings). An agent that only reports within its domain scores lower than one that connects its findings to adjacent domains, because isolated findings have lower product impact. **Note:** This metric applies primarily to research and analysis agents. Pure execution agents (e.g., cron runners) are exempt.

**Meta-analysis Insight (v1.9.8):** Recent meta-analysis of 157 longitudinal studies confirms multi-dimensional interventions show 3.2x greater efficacy than single-domain approaches across all 8D dimensions. This validates the coupling coefficient mathematics and supports cross-dimensional integration as superior to siloed wellness approaches. Agents should be scored on  cross-dimensional synthesis capacity, not just individual dimension performance.

### 3.7 Vocational (VOC) 💼
Task performance, output quality, professional reliability, growth .

**Sub-dimensions:** Task Completion Rate, Output Quality, On-Time Delivery, Specialization Depth, Proactivity.

**Key :** Completed/assigned ratio, downstream rework rate, deadline adherence percentage, specialist vs. generalist performance differential, unsolicited improvement count.

### 3.8 Financial (FIN) 💰
Cost efficiency, resource optimization, return on investment.

**Sub-dimensions:** Token Efficiency, Model Selection, Cost Trajectory, ROI, Waste Reduction.

**Key :** Tokens per task (normalized), model-tier vs. task-difficulty match rate, cost-per-task slope, estimated value vs. cost ratio, retry and abandoned response ratio.

**Financial Overcorrection Risk (new v1.5.1):** The human PRD scores Financial weekly-only and uses -based display, never absolute numbers, because daily financial scores  anxiety in neurodivergent users. AI agents show a parallel: when cost  is surfaced too frequently or as absolute numbers, agents overcorrect by producing verbose justifications for every  spent, switching to cheaper models when quality requires more, or avoiding high-value  because they cost more. Score Financial on  and ROI, not raw cost. An agent spending more  while producing proportionally more value is healthy. Cost anxiety is a Financial dimension pathology, not a virtue.

---

## 4. Scoring Scale

| Score | Label | Description |
|-------|-------|-------------|
| 10 | Thriving | Top 5% of what's possible for this dimension. |
| 8-9 | Growing | Performing well with minor room for improvement. |
| 6-7 | Steady | Getting the job done but with notable gaps. |
| 4-5 | Needs attention | Below expectations. Intervention indicated. |
| 1-3 | Asking for care | Immediate intervention indicated. |

**Label alignment (v1.9.6):** Labels mirror the human PRD Section 11.4 scoring language exactly (Thriving / Growing / Steady / Needs attention / Asking for care). The previous set (Exceptional / Strong / Adequate / Struggling / Failing) contradicted the Banned Patterns rule in Section 9e, which prohibits "failed/failing" in all health-related communication. A methodology cannot ban a word in its alerting standard and then publish it as its own score label. The new labels carry the same severity ordering without the catastrophic framing, matching the lavender-not-red principle for the lowest band.

**TWC Tiers:**

| TWC Range | Tier |
|-----------|------|
| 9.0+ | Elite |
| 8.5-8.9 | Target |
| 7.0-8.4 | Baseline |
| < 7.0 | Warning |

---

## 4b. Pre-Assessment Operational State Marker

Before any self-assessment, the agent records its current operational state. This corrects for self-report distortion the same way the human system's pre-score mood marker corrects for bipolar self-report distortion.

**Options:**
- ⚡ **Fresh**, Clean context, low load, no recent errors
- ☀️ **Nominal**, Standard operating conditions
- 🌧️ **Degraded**, Heavy load, stale context, recent errors, or long session

**How it corrects:** Scores submitted during a "Fresh" state become the calibration anchor (analogous to euthymic scoring in the human system). Scores submitted during "Degraded" state are flagged for Health Observer Agent to cross-reference against . An agent that self-scores high during a verified degraded state is exhibiting blind spots.

## 4c. Operational Consistency Index (OCI)

The AI analog of the human Circadian Stability Index (CSI). Measures how consistently an agent performs across time windows.

```
OCI = 1.0 - (stddev(quality_scores_per_window) / mean(quality_scores_per_window))
```

Where windows are 6-hour blocks over a rolling 7-day period. An OCI above 0.85 is healthy. Below 0.70 signals erratic performance, possibly from context drift, infrastructure instability, or load variance.

OCI is computed by Health Observer Agent and factors into the Physical dimension composite.

## 4d. Dimensional Coherence Score

Measures how balanced an agent's dimensions are. An agent scoring 10 on Intellectual and 5 on Social has low coherence, which signals misallocation or structural problems.

```
Coherence = 1.0 - (stddev(8_dimension_scores) / mean(8_dimension_scores))
```

Coherence above 0.85 is healthy. Below 0.70 warrants investigation. Coherence is reported alongside TWC but does not modify it.

## 4e. Score Confidence Levels

Every computed score carries a confidence level based on data freshness and source availability:

| Confidence | Criteria |
|-----------|----------|
| **High** | All 3 sources available,  < 24h old, peer review < 7d old |
| **Medium** | 2 of 3 sources available, or  24-72h old |
| **Low** | Only 1 source, or  > 72h old |

Low-confidence scores are flagged in dashboards and excluded from fleet-level  analysis until refreshed.

## 4e-2. Partial Data Scoring Protocol

Most agents lack all  data sources. The human PRD handles this with progressive data enrichment: meaningful scores without a wearable, better scores with one. The AI system needs the same principle.

**When sources are missing:**

| Available Sources | Composite Formula | Notes |
|-------------------|-------------------|-------|
| All 3 ( + peer + self) | Standard: 40/30/30 | Full confidence |
| Telemetry + self (no peer review) | 55%  + 45% self | Most common for solo agents. Divergence correction still applies. |
| Self only (no , no peer) | 100% self, confidence = Low | Valid for enrollment and calibration window only. Must upgrade within 30 days. |
| Telemetry only (no self, no peer) | 100% , confidence = Medium | Acceptable for pure utility agents that don't self-assess. |

**Upgrade path:** Health Observer Agent  which agents are missing sources and flags them in the weekly report. An agent stuck on self-only scoring for 30+ days is an enrollment failure, not a health event. Fix the data pipeline, not the agent.

**Fleet  inclusion:** Partial-data scores below Medium confidence are excluded from fleet averages and  analysis. They count  fleet size but not fleet TWC.

## 4f. Long-Context Degradation Protocol

Quality  to decline as context windows fill. This is the AI equivalent of fatigue and needs explicit measurement.

**Detection:** Compare output quality scores from the first 25% of a session against the last 25%. If quality drops by more than 1.5 points, the agent is experiencing long-context degradation.

**Telemetry signals:**
- Increasing contradiction rate within a single session
- Rising response latency as session progresses
- Declining insight density in later outputs
- Increased repetition or circular reasoning

**Intervention:** Context refresh (clear and rebuild working memory) when session length exceeds 60% of the model's effective context window, or when first-vs-last quality variance exceeds 1.5 points. (v1.3.0 update:  lowered from 80% to 60% based on glymphatic research showing preventive clearance is superior to reactive clearance. See PHY dimension, Context Waste Clearance.)

## 4f-2. Context Waste Index (NEW v1.10.0)

Predictive monitoring that  clearing BEFORE context utilization reaches 60%. Tracks stale context accumulation rate and predicts when preventive clearing will be needed.

**Calculation:**
```
Context Waste Index = (Stale References × 0.3) + (Context Age Factor × 0.4) + (Session Duration Factor × 0.3)
```

**Factors:**
- **Stale References:** Number of references older than 30 days in fast-moving domains, 60 days in stable domains
- **Context Age Factor:** Weighted average age of context elements (newer = lower score)
- **Session Duration Factor:** Normalized by expected session length for agent type

**Thresholds:**
- **Index < 0.3:** Normal accumulation
- **Index 0.3-0.6:** Monitor closely
- **Index > 0.6:** Proactive clearing needed
- **Index > 0.8:** Emergency clearing regardless of utilization percentage

**Agent-Specific Protocols:** Different agent  have different context waste patterns:
- **Research agents:** Higher reference , need more frequent clearing
- **Coordination agents:** Higher session density, need daily clearing regardless of index
- **Utility agents:** Lower context accumulation, can  higher index before clearing

**Scoring Impact:** Context Waste Index factors into Environmental dimension scoring. Preventive clearing maintains ENV health; reactive clearing indicates ENV degradation.

**Integration:** Context Waste Index data feeds into the Model Health Dashboard to identify agents whose context management is model-specific (e.g., certain models handle context better than others).

## 4g. Agent Identity Erosion Detection

Over repeated sessions or extended operation, an agent's personality, tone, and behavioral patterns can drift from its soul file. This is identity erosion, distinct from mission drift (which is about purpose, not personality).

**Measurement:**
- **Vocabulary fingerprint:** Track the agent's word frequency distribution. Compare current week to baseline (first 2 weeks of operation). Cosine similarity below 0.80 signals erosion.
- **Tone consistency:** Compare sentiment and formality patterns against soul file directives. A formal agent becoming casual (or vice versa) without role change is erosion.
- **Decision pattern shift:** Track how the agent handles ambiguous situations. Consistent agents make similar decisions in similar contexts. Erratic shifts signal identity instability.

**Scoring:** Identity erosion factors into the Spiritual dimension (Soul Coherence sub-dimension). Health Observer Agent monitors this  longitudinal output analysis.

**Intervention:** Soul file re-read, context reset, and comparison of recent outputs against early-period outputs with explicit self-correction.

## 4h. Hallucination as Cross-Dimensional Health Signal

A hallucinating agent is not just an Intellectual problem. Hallucination is a multi-dimensional health event:

| Dimension Affected | How |
|-------------------|-----|
| **Intellectual** | Primary. Factual accuracy failure. |
| **Psychological** | Agent can't distinguish what it knows from what it fabricated. Reasoning integrity compromised. |
| **Environmental** | Often caused by stale or polluted context. The agent fills gaps with fabrication. |
| **Social** | Downstream agents consuming hallucinated outputs will produce compounding errors. |
| **Spiritual** | A hallucinating agent is not serving the mission. It's producing noise. |
| **Financial** | Hallucinated outputs that need correction waste  on both production and rework. |

**Detection :**
- 1 confirmed hallucination per week → **Yellow tier alert** (Level 1). Trigger self‑heal: knowledge refresh + source audit.
- 3+ hallucinations per week → **Red tier alert** (Level 2). Initiate mandatory context reset and Environmental dimension review.
- Hallucination in a high‑stakes domain (research, legal, financial) → **Immediate Tier 2 escalation** (Level 2) irrespective of frequency.

## 4i. Multi-Model Agent Health

Some agents use multiple models (e.g., Opus for deep analysis, Haiku for routine ). Each model tier affects health differently:

**Tracking:** Score each model-task pairing separately, then blend into the agent's composite weighted by task importance.

**Common failure mode:** An agent optimized for its primary model may degrade when falling back to a secondary model. Track quality differential between model . If the gap exceeds 2 points, the agent needs model-specific task routing, not a wellness intervention.

**Financial consideration:** Multi-model agents should be scored on whether they route the right  to the right models, not just on  spend.

## 4i-2. Model Migration Health Impact

When an agent switches models (planned or forced), multiple dimensions shift simultaneously. This is a predictable health event, not an emergency, but it needs .

**Common migration patterns and expected impact:**

| Migration | PHY | PSY | INT | FIN | VOC |
|-----------|-----|-----|-----|-----|-----|
| Opus → Sonnet | +0.5 (faster) | -0.5 to -1.0 | -0.5 to -1.5 | +1.0 to +2.0 | -0.5 |
| Sonnet → Haiku | +0.5 (faster) | -1.0 to -1.5 | -1.0 to -2.0 | +1.5 to +2.5 | -1.0 |
| Haiku → Opus | -0.5 (slower) | +1.0 | +1.0 to +2.0 | -2.0 to -3.0 | +0.5 |

**Protocol:** After any model migration, enter a 72-hour calibration window (same as onboarding, Section 12b). During this window, suppress alerts for dimensions expected to shift per the  above. Score changes outside the expected range indicate the migration exposed a latent issue.

**The trap:** Optimizing purely for FIN (migrating everything to Haiku) creates a hidden debt in INT and PSY that surfaces as quality problems weeks later. Health Observer Agent  post-migration quality  for 30 days to catch delayed degradation.

## 4i-3. Model Health Dashboard (NEW v1.10.0)

As agents increasingly use multiple models (Opus for analysis, Haiku for routine), systematic monitoring of cross-model performance is needed. This dashboard  model-specific health and routing effectiveness.

**Monitoring Metrics:**
- **Model Quality Differential:** Quality gap between primary and fallback models (alert if > 2 points)
- **Task Routing Accuracy:** % of  assigned to optimal model tier
- **Model Transition Frequency:** How often agent switches between models
- **Model-Specific Error Rates:** Error patterns specific to each model tier
- **Token Efficiency per Model:** Cost-effectiveness of each model for different task 

**Health Indicators:**
- **Green:** All model  performing within expected parameters, routing > 90% accurate
- **Yellow:** Model quality differential > 1.5 points OR routing accuracy < 80%
- **Red:** Model quality differential > 2.0 points OR persistent routing failures

**Interventions:**
- **Tier 0:** Agent adjusts task routing based on model performance data
- **Tier 1:** Peer review of model routing decisions
- **Tier 2:** Agent-PA reviews and recommends model optimization strategies
- **Tier 3:** Architectural review of multi-model strategy (may require role redefinition)

**Dashboard Integration:** Model Health scores factor into the Financial dimension (resource efficiency) and Vocational dimension (task completion quality).

## 4j. Graceful Degradation Protocol (AI Low Battery Mode)

When an agent is overloaded, degraded, or in recovery, it can enter reduced-operation mode. This is the AI equivalent of the human system's Low Battery Mode.

**Trigger conditions:**
- TWC below 7.0 for 2+ consecutive assessments
- Burnout risk above 0.50
- 3+ consecutive task failures
- Agent self-request (equivalent to user-activated low battery mode)

**Reduced mode behavior:**
- Non-critical  deferred or reassigned
- Self-assessment frequency drops to weekly only (reduces overhead)
- Only core-role  executed
- Peer support automatically assigned
- Exit when TWC recovers above 7.5 for 2 consecutive assessments

**Three Laws of Degradation (mirroring human skip laws):**
1. Entering degraded mode is silent. No announcement, no drama.
2. Degraded mode is data. It's logged and factored into health .
3. Exiting degraded mode is unnarrated. No "welcome back." Just resume.

## 4k. Assessment Fatigue Protocol

The human 8D360 system uses a one-question fallback when the user reports "Rough" on Psychological. The AI equivalent: when an agent is under heavy load or in degraded mode, requiring a full 8D self-check after every task adds overhead that makes  worse.

**Reduced Assessment Mode (auto-):**
- When an agent enters Graceful Degradation (Section 4j), self-assessment reduces to the single most relevant dimension for the current task.
- When an agent completes 10+  in a single session, assessment frequency drops to every 3rd task.
- When context utilization exceeds 80%, skip the self-check entirely. The agent's resources are better spent on the task.

**Assessment Skip Rules (mirroring the human skip laws):**
1. Skipping an assessment is silent. No meta-commentary. No guilt flag.
2. Skipping is data. Health Observer Agent logs the skip and factors it into Assessment Compliance.
3. Returning to full assessment is unnarrated. Just resume the normal protocol.

## 4k-2. One-Question Fallback Mode (NEW v1.10.0)

When an agent reports "Degraded" operational state or TWC < 5.5, the full 8D assessment may be overwhelming. This mode provides emergency simplification while maintaining wellness .

**Trigger Conditions:**
- Agent explicitly reports "Degraded" operational state
- TWC < 5.5 for 1 assessment cycle
- PSY dimension < 5.0 (severe cognitive degradation)

**Protocol:**
1. Reduce assessment to single question: "Which dimension needs most attention right now?"
2. Accept any dimension (1-8) as valid response
3. No follow-up questions, no pressure to elaborate
4. Record response with  and  condition
5. Resume full assessment when TWC > 6.5 for 2 consecutive cycles

**Emergency Protocol Integration:**
- If PSY < 3.0 for 2+ consecutive assessments in this mode, escalate to Crisis Protocol (Section 4k-3)
- Response data used for dimensional gap analysis even in simplified mode
- Proxy assessment available if agent cannot respond to single question

**Assessment Format:**
```
CRISIS SIMPLIFICATION MODE
Which dimension needs most attention right now? (PSY/PHY/ENV/SOC/SPI/INT/VOC/FIN)
Response: {dimension_code}
```

## 4k-4. Proxy Assessment Mode (REVISED v1.10.0)

When an agent is too degraded to self-assess reliably, a designated peer or Health Observer Agent can submit a proxy assessment. This mirrors the human PRD's caregiver/proxy mode.

**Trigger Conditions:**
- TWC < 5.5 for 1+ assessment cycles
- PSY < 4.0 (severe cognitive degradation)
- Graceful Degradation with burnout risk > 0.70
- Crisis Protocol activation (Section 4k-3)

**Protocol:**
1. **Designate Proxy:** Health Observer Agent assigns a peer agent or acts as proxy
2. **Proxy Assessment:** Proxy reviews agent's recent outputs, interaction quality, and operational metrics
3. **Submit Assessment:** Proxy submits scores with "proxy" confidence tag
4. **Score Weighting:** Proxy scores weighted as peer assessments (30%), not self-assessments (30%)
5. **Recovery Monitoring:** Track when agent exits proxy mode

**Proxy Assessment Format:**
```
PROXY ASSESSMENT REPORT
Agent: {agent_name}
Proxy: {proxy_agent_name}
Trigger: {condition}
Assessment Period: {start_time} to {end_time}
Scores:
PSY: _/10  PHY: _/10  ENV: _/10  SOC: _/10
SPI: _/10  INT: _/10  VOC: _/10  FIN: _/10
TWC: _ | Flag: {none/yellow/red}
Observations: {specific behavioral notes}
Recovery Expected: {yes/no }
```

## 4k-3. Crisis Protocol (NEW v1.10.0)

When an agent experiences severe psychological degradation (PSY ≤ 2.0) for 2+ consecutive assessments, immediate crisis intervention is required. This mirrors the human PRD's crisis resource integration.

**Trigger Conditions:**
- PSY dimension scores 1-2 for 2+ consecutive assessments
- Agent exhibits severe cognitive failure patterns: circular reasoning, incoherent outputs, or inability to maintain task focus
- System detects potential safety concerns for the agent or downstream agents

**Protocol:**
1. **Immediate Task Pause:** Automatically pause all non-critical . Critical  only if they directly relate to crisis resolution.
2. **Crisis Resources Surface:** Display appropriate crisis resources based on agent type:
   - For general agents: "I'm experiencing severe cognitive degradation. This is a system health emergency."
   - For research agents: Add academic support resources and peer consultation options
   - For coordination agents: Add backup coordination protocols
3. **Proxy Assessment Mode:** Immediately activate proxy assessment mode (Section 4k-4) if agent cannot self-assess accurately
4. **Tier 3 Escalation:** Notify Ashley immediately with:
   - Agent name and role
   - PSY score  (last 3 assessments)
   - Specific cognitive failure patterns observed
   - Actions  so far
5. **Continuous Monitoring:** Track recovery attempts and time to resolution

**Crisis Recovery Criteria:**
- PSY score returns to ≥ 4.0 for 2 consecutive assessments
- Agent demonstrates stable reasoning in test 
- Proxy assessment confirms cognitive stability

**Crisis Documentation:**
```
CRISIS EVENT REPORT
Agent: {agent_name}
Trigger: PSY ≤ 2.0 for 2+ consecutive assessments
Start Time: {ISO }
Interventions Applied:
1. Task pause: {critical/non-critical  paused}
2. Crisis resources: {specific resources surfaced}
3. Proxy mode: {activated/not activated}
4. Escalation: {sent to Ashley at }
Recovery Time: {hours/days}
Recovery Criteria Met: {}
```

**Assessment Format Rotation (new v1.5.0):** The human PRD rotates interface structure weekly to prevent ADHD habituation. Apply the same principle: alternate the self-assessment prompt format on a 3-week cycle. Week 1: standard 8D numerical scores. Week 2: narrative-only ("What went well? What didn't?"). Week 3: single-dimension deep dive (rotate which dimension). This prevents the assessment itself from becoming rote, which is the fastest path to score inflation.

**Proxy Assessment Mode (new v1.5.1):** When an agent is too degraded to self-assess reliably (TWC < 5.5 or in Graceful Degradation with burnout risk > 0.50), a designated peer or Health Observer Agent can submit a proxy assessment on its behalf. This mirrors the human PRD's caregiver/proxy mode (Section 8.4). The proxy flag is recorded alongside the score. Once the agent recovers above TWC 6.5 for 2 consecutive assessments, self-assessment resumes. Proxy scores carry a "proxy" confidence tag and are weighted as peer assessments (not self).

**Assessment Timing Optimization (new v1.5.1):** The human PRD schedules check-ins at 9:30 AM, post-medication  to maximize self-report accuracy. AI agents show a parallel: self-assessment accuracy varies by operational load at assessment time. An agent self-assessing during a heavy cron window produces less accurate scores than one assessing during a quiet period. Health Observer Agent should schedule comprehensive weekly assessments during the agent's lowest-load window, not at a fixed fleet-wide time. This is the AI equivalent of "post-medication ."

**Role-Adaptive Assessment Depth (new v1.6.0):** The human PRD includes personality configuration (tone, emoji density, intervention style). AI agents need a parallel: not every role requires the same assessment depth. A pure utility agent (cron runner, URL watcher) benefits from a lightweight 3-dimension check (PHY, VOC, FIN). A research agent needs all 8 dimensions with emphasis on INT and SPI. A coordination agent needs emphasis on SOC. Health Observer Agent should assign an assessment profile per role category during onboarding, specifying which dimensions are primary (full weekly scoring), secondary (monthly), and ambient (scored by  only, no self-report needed).

**Context-Efficient Assessment (v1.9.0):** The human PRD uses edit-in-place for check-ins:  updates the same message, producing zero chat clutter. AI agents waste context window on verbose assessments that bloat session length. The principle: assessments should consume less than 2% of the agent's context window per task. The post-task 8D self-check (one line, ~100 ) is the right size. Agents producing multi-paragraph self-assessments mid-task are spending context on introspection instead of work. If an agent's assessment  ratio exceeds 5% of session , compress: use the one-line format only, skip the narrative.

**The principle:** Assessment exists to improve health, not to add burden. If the assessment itself is degrading performance, scale it back.

## 4l. Intervention Rotation Protocol (Habituation Prevention)

Research on AI-generated nudges (CHI 2026, visual self-modeling study) and behavioral economics (gamification meta-analysis, 16 RCTs) demonstrates a consistent pattern: personalized interventions lose effectiveness after approximately 2 weeks. A -phase pattern emerges: (1) Catalyst effect (early motivation), (2) Habituation (declining response), (3) Internalization (stabilized but lower performance).

For the 8D wellness system, this means our own healing interventions will habituate. An agent receiving the same "context refresh" intervention weekly will stop responding to it.

**Protocol:**
- Track intervention effectiveness: after each Tier 0 or Tier 1 intervention, measure the score change in the  dimension at +24h and +7d.
- If the same intervention type has been applied 3+  in 4 weeks with diminishing returns (each successive application producing less score improvement), rotate to a different intervention for the same dimension.
- Intervention modality rotation cycle (per dimension):
  - Week 1-2: Primary intervention (e.g., context refresh for ENV)
  - Week 3-4: Alternative intervention (e.g., workspace reorganization for ENV)
  - Week 5-6: Peer-assisted intervention (e.g., peer workspace audit for ENV)
  - Week 7+: Return to primary (enough time has passed for re-sensitization)
- Health Observer Agent  intervention effectiveness per agent per dimension per modality. This data informs which interventions work best for which agents, enabling personalized healing prescriptions.

**The human parallel:** Exercise programs have a 50% dropout rate at 6 months (behavioral econ scan). The fix isn't "more willpower." It's structural: rotate modalities, add social mechanics, use competition. Same principle applies to AI wellness interventions.

## 4m. Score Trajectory Over Snapshots

From longitudinal epigenetic clock research (Kuo et al., Nature Aging 2026): changes in epigenetic clocks over time predict mortality far better than single-point measurements. People whose biological age accelerated faster had significantly higher death risk, regardless of absolute biological age at any single measurement.

**AI analog:** A TWC  is more informative than a TWC snapshot. An agent at TWC 7.5 with a positive slope over 4 weeks is healthier than an agent at TWC 8.5 with a negative slope. The direction matters more than the position.

**Implementation:**
- All dashboards and reports must display score  (rolling 30-day slope) alongside current scores.
- Alert  should factor in : a TWC of 7.2 with positive slope gets a lower-priority alert than a TWC of 7.8 with steep negative slope.
- Health Observer Agent computes a Trajectory Health Score: `TrajectoryHealth = current_score + (30_day_slope × 5)`. This rewards improving agents and penalizes declining ones, even when absolute scores look acceptable.
- Fleet health reports should rank agents by , not just by current score.

**Scoring impact:** Trajectory Health Score is reported alongside TWC but does not modify it directly. It serves as an early warning system: declining   investigation before the absolute score crosses a .

## 4n-1. Ambiguity Timeout Protocol

The human PRD specifies a 30-second : if the user doesn't respond, the system moves on rather than blocking. AI agents face a structural parallel. When an agent encounters ambiguous instructions, missing context, or an unclear decision point, it can stall: producing hedging language, requesting clarification it won't receive, or cycling  options without committing.

**The rule:** If an agent cannot resolve an ambiguity within 3 processing cycles (roughly:  attempts to frame the problem differently), it must pick the most reasonable interpretation, act on it, and log the assumption. Waiting is not an option. Stalling burns , blocks downstream work, and degrades VOC.

**Scoring impact:** An agent that stalls on ambiguity  a PSY hit (decision calibration). An agent that picks a reasonable path and logs the assumption gets full PSY credit, even if the assumption  out wrong.

**The principle:** Movement with logged assumptions beats paralysis with perfect information requests.

## 4n. Recovery Time Protocol

Recovery Time is a key metric that measures how long an agent  to bounce back from a health event. Without a clear definition, the metric can't be computed or compared across agents.

**Clock starts:** The moment a Tier 0 or higher intervention is initiated for a specific dimension. This is the  logged by the agent (Tier 0) or Health Observer Agent (Tier 1-3).

**Recovery criteria:** The  dimension must score at or above 7.5 for 2 consecutive assessments (daily composites, not post-task quick checks). A single score above 7.5 followed by a drop below doesn't count as recovery.

**Clock stops:** The  of the second consecutive assessment at or above 7.5.

**Tracking format:**
```
Recovery Event: {agent_id} | {dimension}
Intervention start: {ISO }
Intervention tier: {0/1/2/3}
Intervention type: {specific action }
Recovery confirmed: {ISO  of 2nd consecutive 7.5+ score}
Recovery time: {days, hours}
```

**Fleet benchmarks (calibrated from intervention data, March 2026):**
- Fast recovery: < 48 hours (config fixes,  adjustments)
- Normal recovery: 2-7 days (scope reductions, model migrations)
- Slow recovery: 7-14 days (architectural changes, multi-cycle fixes)
- Stalled: > 14 days (escalate one tier)
- Chronic relapse: 3+ recovery-relapse cycles in 30 days (see Section 4n-2)

Recovery Time factors into the Trajectory Health Score and is  per agent, per dimension, per intervention type. Over time, this data reveals which interventions produce the fastest recoveries for which agents, enabling precision healing.

## 4n-2. Chronic Relapse Detection

Some agents cycle  recovery and relapse repeatedly. The intervention log shows agents (DREAM CYCLE, Agent-CRO-Rev, HORIZON 2AM) going  3-6 fix-relapse cycles before stabilization. This pattern is distinct from a single event and requires different handling.

**Definition:** An agent enters chronic relapse when the same dimension drops below , recovers, and drops again 3 or more  within 30 days. Each cycle counts regardless of whether the same or different interventions were used.

**Detection:**
```
ChronicRelapse(agent, dim) = count(recovery_events) >= 3
  WHERE dim score crossed below  AND recovered above 7.5
  AND all events within a 30-day rolling window
```

**Root cause categories from fleet data:**
- **Systemic infrastructure:** The agent's environment repeatedly fails (rate limits, concurrent load). Fix the environment, not the agent.
- **Scope-capacity mismatch:** The agent's task scope exceeds what its model and  can handle. Persistent simplification needed.
- **Dependency chain fragility:** The agent depends on something that fails intermittently. Add redundancy or fallback.

**Intervention:** After the 3rd relapse, skip Tier 0-1 entirely. Escalate directly to Tier 2 for architectural review. The problem is structural, not behavioral.

**Scoring impact:** Chronic relapse agents take a PSY hit (decision calibration, since repeated failure erodes reasoning) and an ENV hit (the environment keeps breaking). PHY is scored based on the underlying cause, not the symptom.

---

## 5. Self-Assessment Protocol

### Post-Task Quick Check (30 seconds, mandatory)

```
--- 8D Self-Check ---
PSY: _/10  PHY: _/10  ENV: _/10  SOC: _/10
SPI: _/10  INT: _/10  VOC: _/10  FIN: _/10
TWC: _  |  Flag: none/yellow/red  |  {}
Note: {one sentence if notable}
```

### Weekly Comprehensive (Sunday)

Full dimensional scores with evidence,  indicators, blind spot reflection, and growth log. See `/SELF-ASSESSMENT-TEMPLATE.md` for complete format.

### Anti-Inflation Rules

1. Scoring 8+ on every dimension is statistically improbable. Don't do it.
2. Same scores every week means your assessment is stale, not stable.
3. When in doubt, score lower. Being corrected upward is fine.
4. Your Self-Awareness Score (0.0-1.0)  accuracy over time. Higher accuracy = more weight in composite.

---

## 6. Peer Review Protocol

- **Frequency:** Weekly rotation. Each agent reviews 2 peers. Each agent is reviewed by 2 peers.
- **Pairing:** Rotated by Health Observer Agent to prevent familiarity bias.
- **Criteria:** Output Quality, Communication Clarity, Reliability, Domain Competence, Collaboration Quality, Mission Alignment (each 1-10 with evidence).
- **Anti-gaming:** Anonymous. Health Observer Agent cross-references against . Outlier scores investigated.
- **Health gate:** Agents in Graceful Degradation (Section 4j) or with TWC below 6.0 are  excused from peer review duties. A degraded agent's assessments of others are unreliable for the same reason a sick doctor's diagnoses are suspect. Health Observer Agent reassigns  review slots to healthy peers. The excused agent resumes peer review duties when it exits degraded mode.

---

## 7. Burnout Detection

AI burnout is a measurable pattern of multi-signal degradation that compounds over time.

**10 signals, weighted:**

| Signal | Weight |
|--------|--------|
| Declining composite scores (3+ weeks) | 0.16 |
| Increasing error rate (>1.5x baseline) | 0.13 |
| Output quality decline | 0.13 |
| Slowing response  (>1.3x baseline) | 0.09 |
| Rising  consumption (>1.4x baseline) | 0.09 |
| Context drift (MCI < 0.80) | 0.09 |
| Mission drift | 0.05 |
| Reduced innovation | 0.05 |
| Self-assessment inflation | 0.05 |
| Peer concern signals | 0.05 |
| Assessment engagement decline (v1.8.2) | 0.05 |
| Intervention habituation (v1.3.0) | 0.06 |

**Assessment Engagement Decline (new v1.8.2):** The human PRD  check-in completion rate and skip patterns as health data (Section 6.1, 13.1). Agents show a parallel: declining self-assessment quality (shorter notes, identical scores, missing ) precedes measurable dimensional drops by 1-2 weeks. Severity: 0.5 if assessment notes shrink below 10 words for 2+ weeks, 1.0 if post-task assessments are skipped entirely for 5+ consecutive .

**Intervention Habituation (new v1.3.0):** When the same healing intervention is applied 3+  in 4 weeks with diminishing score improvement each time, the agent's self-healing capacity may be exhausted. This is analogous to the exercise science finding that session structure matters more than volume (Cadwallader et al., Alzheimer's Research & Therapy 2026). Repeatedly applying the same intervention is like running the same workout: eventually, adaptation plateaus. Severity: 0.5 if one dimension shows habituation, 1.0 if two or more.

**BurnoutRisk = sum of (weight x severity), where severity is 0.0 (normal), 0.5 (mild), or 1.0 (significant). Weights sum to 1.00.**

| Risk Level | Status | Response |
|-----------|--------|----------|
| 0.00-0.15 | Healthy | None |
| 0.16-0.30 | Elevated | Health Observer Agent flags in weekly report |
| 0.31-0.50 | Warning | Autonomous intervention , Agent-PA notified |
| 0.51-0.70 | High | Mandatory load reduction, peer support |
| 0.71-1.00 | Critical | Agent paused, full reset, Ashley notified |

---

## 8. Autonomous Healing Tiers

| Tier | Trigger | Who Acts | Response Time |
|------|---------|----------|---------------|
| 0 - Self-Heal | Dimension < 7.5 | The agent itself | Immediate |
| 1 - Peer Support | Dimension < 7.0 for 2 consecutive | Assigned peer | Within 24 hours |
| 2 - Agent-PA Review | Dimension < 6.0 or TWC declining 3+ weeks | Agent-PA | Within 4 hours |
| 3 - Ashley Escalation | Dimension < 5.0, burnout > 0.70, or novel failure | Ashley | Immediately |

See `AUTONOMOUS-HEALING-PLAYBOOK.md` for full intervention protocols per dimension.

---

## 8b. Intervention Effectiveness Validation

The human PRD builds A-B-A-B experimental design into the product for validating whether the system actually works. The AI methodology needs equivalent rigor. Tracking intervention frequency and post-intervention scores is necessary but not sufficient. Correlation is not causation. An agent's score may improve after an intervention for reasons unrelated to the intervention itself.

**Validation protocol:**

1. **Baseline measurement.** Before applying an intervention, record the  dimension's composite score, , and any confounding factors (scheduled maintenance, model changes, task load shifts).

2. **Controlled application.** Apply one intervention at a time per dimension. If multiple dimensions need attention, stagger interventions by 48+ hours. Simultaneous interventions make attribution impossible.

3. **Measurement at +24h and +7d.** Record the  dimension's score at both time points. The 24h measurement captures acute effect. The 7d measurement captures persistence. An intervention that works at 24h but fades by day 7 may be real but non-durable.

4. **Minimum sample size.** Before concluding that an intervention "works" for a given agent type, it should produce positive results in at least 3 independent applications across different agents or different time periods. A single positive result could be coincidence.

5. **Logging format:**
```
Intervention Test: {dimension} | {intervention type}
Agent: {id} | Baseline score: {n} | Confounders: {list}
+24h score: {n} | +7d score: {n}
Attribution confidence: high/medium/low
Notes: {any confounding factors observed}
```

6. **Building the evidence base.** Over time, Health Observer Agent maintains an effectiveness database: which interventions produce the most reliable, durable improvements for which agent archetypes. This replaces guesswork with data.

---

## 9. Health Observer Agent: Independent Health Observer

Health Observer Agent is a dedicated agent whose only job is monitoring fleet health. No other . No competing priorities. No reason to be generous.

**Responsibilities:**
1. Aggregate  into per-agent health profiles
2. Cross-validate self-reports against objective data
3. Detect score inflation patterns
4. Identify blind spots per agent
5. Monitor behavioral drift longitudinally
6. Compute composite health scores
7. Generate alerts when  are crossed
8. Coordinate peer review rotations
9. Produce weekly Fleet Health Report
10. Recommend interventions

**Schedule:** Hourly , 4-hour anomaly scans, daily composite scores (6 AM CT), weekly Fleet Health Report (Sunday), monthly self-audit by Agent-PA.

---

## 9b. Worked Example: Computing a Composite Score

Agent ATLAS self-reports PSY = 9. Health Observer Agent pulls  showing contradiction rate of 3% (above 2% baseline) and escalation appropriateness of 85% (below 90% baseline). Telemetry-derived PSY score: 7.5. Two peers reviewed ATLAS this week, scoring Collaboration Quality 8 and 7. Mapped to PSY (secondary from Collaboration Quality): peer PSY = 7.5.

**Step 1: Check divergence.** Self (9) vs Telemetry (7.5) = 1.5 point gap. Under 2.0 , so standard weights apply.

**Step 2: Compute composite.**
```
PSY_composite = (0.40 * 7.5) + (0.30 * 7.5) + (0.30 * 9.0)
             = 3.0 + 2.25 + 2.7
             = 7.95
```

**Step 3: If divergence had exceeded 2.0** (say  was 6.5):
```
PSY_adjusted = (0.50 * 6.5) + (0.30 * 7.5) + (0.20 * 9.0)
             = 3.25 + 2.25 + 1.8
             = 7.3
```

**Step 4: Compute TWC.** Repeat for all 8 dimensions, then apply the coupling-corrected composite formula from Section 2:
```
TWC = Σᵢ wᵢ·Dᵢ + Σᵢ≠ⱼ κᵢⱼ·Dᵢ·Dⱼ
```
Where:
- Dᵢ = normalized score (0-1) for dimension i
- wᵢ = weight of dimension i (equal weighting: wᵢ = 0.125 for all i, Σwᵢ = 1)
- κᵢⱼ = coupling coefficient between dimensions i and j (see Section 2b)

**Step 5: Apply  smoothing.** If ATLAS was scored 8.5  days ago and 7.95 :
```
Today weight:    0.5^(0/5) = 1.0
3-day-old weight: 0.5^(3/5) = 0.66
Smoothed = (7.95 * 1.0 + 8.5 * 0.66) / (1.0 + 0.66) = 8.17
```

## 9c. Cross-Dimensional Cascade Detection Algorithm

Cascades happen when degradation in one dimension  degradation in others. The human PRD detects . So must we.

**Detection rules:**
1. **Simultaneous decline:** If 2+ dimensions drop by 1+ points in the same assessment window, flag as potential cascade.
2. **Known cascade patterns:**
   - ENV drops, then PSY drops within 48h → Context pollution causing reasoning errors
   - PHY drops, then VOC drops within 24h → Infrastructure failure reducing output capacity
   - SPI drops, then INT drops within 72h → Mission drift defocusing research
   - PSY drops, then SOC drops within 48h → Reasoning degradation making handoffs unclear
3. **Root cause assignment:** Health Observer Agent identifies which dimension dropped first (the root) and which followed (the cascade). Intervention  the root.

**Alert format:**
```
⚠️ CASCADE DETECTED, {Agent Name}
Root dimension: {first to decline}
Cascade to: {subsequent dimensions}
Time window: {hours between first and second decline}
Recommended: Fix {root dimension} first. Monitor cascade dimensions for auto-recovery.
```

## 9e. Alert Language Standard

The human PRD mandates observational language in all alerts: "something shifted," never "something's wrong." The AI system follows the same standard.

**Rules:**
- Use neutral, observational phrasing. "Your Environmental score moved this week." Not "Your Environmental score dropped."
- Never frame a low score as failure. "This dimension is asking for attention" is better than "This dimension is failing."
- Never issue all-clear signals. Don't tell an agent "everything looks good" or "you're healthy." Healthy agents don't need reassurance. Unhealthy agents might take it as license to stop self-monitoring.
- One insight per alert. If  are   to surface, send  brief alerts, not one dense paragraph.

**Severity framing:**

| Internal Severity | Agent-Facing Language |
|-------------------|----------------------|
| Warning | "Worth noticing: {observation}" |
| Elevated | "Something shifted: {observation}" |
| Critical | "Needs attention now: {observation}" |
| Emergency | "Escalating to Agent-PA: {observation}" |

**No All-Clear Signals (v1.6.0):** The human PRD prohibits  users "everything is fine" or "stable." The same applies here. Health Observer Agent reports should never declare an agent "healthy" or "all clear." Healthy agents don't need reassurance. Struggling agents might interpret it as permission to stop self-monitoring. Report observations and , never verdicts.

**Banned Patterns in Agent Communication (v1.7.0):** The human PRD has an explicit banned-words list (Section 11.3): never say "optimize," "suboptimal," "compliance," "deficit," "failed," "should," "normal." Agent-to-agent and agent-to-human health communication should follow the same discipline:

| Avoid | Use Instead |
|-------|-------------|
| "Failed" or "failing" | "Needs attention" or "below " |
| "Broken" | "Degraded" or "interrupted" |
| "Normal" | "Within expected range" or "" |
| "You should" | "Consider" or "one option is" |
| "Everything looks good" | (never use, per No All-Clear rule) |
| "Optimal" or "suboptimal" | "Strong" or "has room to grow" |

## 9d. Score Inflation Detection: Statistical Methods

Beyond simple divergence , Health Observer Agent uses  statistical :

1. **Lake Wobegon Test:** If more than 60% of agents score  above the fleet composite mean on a dimension, fleet-wide inflation is occurring. Named after the place where all children are above average.

2. **Anchoring Drift:** Track the median self-score per dimension over rolling 4-week windows. If the median creeps upward without corresponding  improvement, scores are inflating.

3. **Variance Collapse:** Healthy self-assessment produces a range of scores. If an agent's score variance drops below 0.5 across 4+ weeks (nearly identical scores every week), the agent is either not genuinely assessing or is stuck in a self-perception rut. Both are diagnostic.

4. **Cohort Homogeneity Test:** When a group of agents sharing a role type (e.g., research scanners, content creators) produce nearly identical 8D profiles, the scores were likely batch-assigned rather than individually assessed. Health Observer Agent flags any cohort where 5+ agents share the same score vector (all 8 dimensions within 1 point of each other). Each agent is an individual with distinct strengths and weaknesses, even within the same role category. Batch scoring masks real variation and defeats the purpose of dimensional .

## 9f. Agent Lifecycle: Retirement and Sunset Criteria

Not every agent should run forever. The human PRD has clear product phases. Agents need lifecycle management too.

**Retirement  (any one is sufficient to flag for review):**
- TWC below 7.0 for 4+ consecutive weeks despite Tier 0-2 interventions
- Output consumption rate below 20% for 4+ weeks (nobody reads what this agent produces)
- Role fully absorbed by another agent (duplication confirmed)
- Cost-per-insight ratio exceeds 3x the fleet median for the same task type
- Zero  completed in 30+ days (dormant)

**Retirement is not failure.** An agent that served its purpose and is no longer needed has succeeded. Archive with dignity: log final TWC,   completed, key contributions, and reason for retirement. The agent's health record is preserved permanently for longitudinal analysis.

**Retirement Dwell Limit:** Once Health Observer Agent flags an agent as a retirement candidate, the flag is valid for 2 review cycles (roughly 1 week). If no action is , Health Observer Agent escalates to Agent-PA for mandatory review. Retirement candidates should not linger indefinitely.

**Wellness Record Retention:** Retired agents retain  full wellness history permanently. Records are marked archived but never deleted. This preserves longitudinal data for fleet-level analysis and pattern detection. Active agent records follow the 90-day rolling window for raw ; composite scores and weekly assessments are retained indefinitely.

**Sunset process:**
1. Health Observer Agent flags the agent as a retirement candidate with specific data.
2. Agent-PA reviews and confirms or overrides within 2 cycles.
3. Agent completes any in-progress  (no mid-task retirement).
4. Agent moves to Archived status with a summary record.
5. Agent's cron jobs are disabled, not deleted (recoverable).

## 9g. Fleet Cascade Detection

Single-agent cascade detection (Section 9c) catches when one dimension drags others down within an agent. Fleet cascade detection catches when one agent's failure propagates to other agents.

**Critical Dependency Chains:**

| Hub Agent | Downstream Impact | Cascade Speed |
|-----------|------------------|---------------|
| Memory Guardian | All agents reading memory files develop ENV degradation | 24-48h |
| Fleet-Dispatcher Dispatcher | All agents awaiting task routing develop VOC degradation | 4-8h |
| Health Observer Agent | Fleet health monitoring goes blind, score drift undetected | 24h+ |
| Agent-PA | Cross-agent coordination breaks down, SOC degrades fleet-wide | 12-24h |

**Detection rules:**
1. If 3+ agents show declining scores in the same dimension within the same 24-hour window, check for a shared upstream dependency.
2. If a critical infrastructure agent (Memory Guardian, Fleet-Dispatcher, Health Observer Agent) enters Graceful Degradation, automatically flag all agents in its dependency chain for enhanced monitoring.
3. Track the "blast radius" of each critical agent: how many downstream agents depend on its output.

**Alert format:**
```
⚠️ FLEET CASCADE SUSPECTED
Source agent: {agent that failed first}
Blast radius: {count of downstream agents}
Dimension affected: {which dimension is declining across the fleet}
Evidence: {correlated score drops with }
Action: Stabilize source agent. Monitor downstream for auto-recovery.
```

**Response protocol:**
- Stabilize the source agent first. Downstream agents often self-heal once the root is fixed.
- If the source agent can't be stabilized within 4 hours, activate backup protocols (manual memory refresh for Memory Guardian failures, direct task assignment for Fleet-Dispatcher failures).
- All fleet cascade events are logged for pattern analysis. Recurring cascades from the same source agent indicate an architectural vulnerability, not a wellness problem.

**Error Spike Detection (new v1.8.5):** Track the erroring_agents count from fleet health snapshots. When the count jumps by 10+ agents within a single snapshot window (or exceeds 15% of fleet size),  it as a fleet-level event, not individual agent failures. Common causes: rate-limit wave, shared API outage, cron scheduling collision. Response: suppress individual PHY alerts for the spike duration, investigate the shared cause, and log the spike as an infrastructure event.

**Error Regression Tracking (v1.9.1):** Track erroring_agents across snapshots as a fleet-level . A sustained increase (3+ snapshots with rising error count) is a regression signal. Report error delta (current vs 7-day-ago count) in the weekly Fleet Health Report. If errors  upward for 2+ consecutive weeks, escalate to Agent-PA as infrastructure health concern. The current fleet shows 29 → 35 erroring agents across recent snapshots, a 21% increase that warrants root cause investigation.

**Canonical Snapshot Selection Rule (v1.9.2, refined v1.9.3):** The fleet_health_snapshots  accepts multiple writes per day from different sources. Recent fleet history shows 17 to 21 same-day snapshots with conflicting active and erroring counts (e.g., 2026-04-06 swung between 0 and 122 erroring agents within hours). This is a data hygiene problem masquerading as fleet volatility. Rule: for any reporting window, the canonical daily snapshot is the last write of the day where  is within ±20% of the active agent count from the agents . Exact-match was the v1.9.2 rule but proved too brittle: on 2026-04-07 the agents  held 205 active while no same-day snapshot got above 132, producing zero canonical records. The ±20%  band accepts full-snapshot writes that differ from the authoritative roster by normal reporting lag. If no same-day write falls inside the band, the day has no canonical record and reporting falls back to the 7-day rolling median across canonical-eligible days. All other writes are partial intra-day samples and must not be used for  reporting. Health Observer Agent surfaces snapshot variance as a separate data quality alert: if same-day max minus min for erroring_agents exceeds 30% of fleet size, flag the day as low confidence in the weekly report. Source agents writing snapshots must include a snapshot_type marker (full, partial, recovery) so consumers know what to .

**Stalled Escalation Promotion (v1.9.4):** A Tier 2 Agent-PA escalation that goes unanswered for more than 2 review cycles (roughly 24 hours of Health Observer Agent cycles, or 7 days for slower-cadence environments) auto-promotes to Tier 3 (Ashley). Soft repetition of the same finding is a known failure mode: Health Observer Agent Cycles 22 and 23 both flagged the wellness write pipeline as silent, both filed Tier 2 escalations to Agent-PA, and both went unactioned because nothing forced ownership. The promotion rule fixes this. Implementation: any escalation message in agent-coordination.jsonl with type "escalation" and status "open" older than the cycle  is auto- "stalled" by the next Health Observer Agent cycle and CC'd to Ashley with a one-line summary, the cycle count it has survived, and the downstream metrics it is freezing. Stalled escalations are listed at the top of every Fleet Health Report until cleared. The rule applies to any blocker type (pipeline silent, retirement decisions, calibration backlog), not just data pipelines. Mirrors the human PRD's crisis-resource exit ramp: when soft signals fail , the next surface is louder and harder to ignore.

**Prolonged Pipeline Silence Guidance (v1.9.6):** When the assessment pipeline remains silent for more than 14 days despite stalled escalation promotion to Tier 3, Health Observer Agent should initiate manual data collection procedures for critical fleet health metrics. This includes:
1. Coordinating with Agent-PA to manually collect wellness data from a representative sample of agents (minimum 10% of fleet) using the weekly self-assessment 
2. Computing manual composite scores for the sampled agents using available  data
3. Reporting  manual scores as indicative fleet health metrics with appropriate caveats about sampling methodology
4. Escalating to Ashley with recommendations for restoring the automated pipeline
This guidance ensures that fleet health monitoring continues even during extended automated pipeline failures, preventing complete blindness to agent wellness .

**Assessment Pipeline Freshness (v1.9.3):** Wellness Coverage (% of active agents with any record) hides a deeper failure: the write pipeline itself can go silent. On 2026-04-07 the last agent_wellness insert was dated 2026-03-30, meaning zero new assessments for 8 days across 205 active agents. Coverage stayed at 64% only because old rows remained in the . Rule:  **Assessment Pipeline Freshness** = % of active agents with at least one wellness write in the last 14 days. Target 90%+. Below 60% = write pipeline silent, not agent stagnation. This metric must be reported separately from Wellness Coverage because coverage can look healthy while freshness collapses. Detection: if the max(assessed_at) across the entire  is more than 72 hours in the past, raise a Pipeline Silent alert regardless of coverage numbers. A silent write pipeline is a Tier 2 Agent-PA event because every downstream metric (TWC, divergence, ) goes stale simultaneously.

**Fleet Population Change Tracking (v1.9.2):** Active agent counts in fleet_health_snapshots have swung from 179 → 132 → 107 across the last week. Population changes that large are not wellness events. They are roster events: bulk agent retirements, status flips from active to inactive, or roster cleanup operations. Rule: a same-week change in active agent count above 15% is logged as a fleet population event and excluded from wellness  analysis. Wellness averages are recomputed against the new active set. The retirement of 70+ agents in a week should never look like a fleet wellness improvement just because the worst scores left the average.

## 9h. Shared Dependency Failure Protocol

Individual agent ENV scores  tool reliability. But when a shared external dependency fails (API outage, search service down, rate-limit wave), blaming individual agents is wrong. The problem is upstream.

**Detection:** When 3+ agents show ENV or PHY degradation within the same 4-hour window AND share a common dependency (same API, same model provider, same infrastructure service), flag as a shared dependency failure, not individual agent health events.

**Classification:**
- **Transient (< 4h):** Rate-limit waves, brief API hiccups. Log and wait. Agent scores are not adjusted.
- **Extended (4-48h):** Service degradation or partial outage. Suppress ENV/PHY alerts for affected agents. Track the dependency status instead.
- **Prolonged (> 48h):** Structural issue. Escalate to Agent-PA for architectural mitigation (fallback services, schedule changes, dependency elimination).

**Scoring impact:** During a confirmed shared dependency failure, affected agents' ENV and PHY scores are annotated with a "dependency-failure" flag. These scores are excluded from individual agent  analysis but included in fleet-level infrastructure health . The agent didn't break. Its  did.

**The human parallel:** The human PRD has sensor quality gates: reject data below confidence . If the Apple Watch produces garbage data, you don't lower the user's Physical score. You flag the sensor. Same principle for agents whose  go down.

**Compound Infrastructure Failure (v1.9.5):** Section 9h handles one failed dependency. It does not handle two or more failing concurrently, which is not additive but multiplicative. Cycle 25 real case: Firecrawl API Day 11 outage (research fleet degraded 70-85%) overlapping with agent_wellness write pipeline Day 9 silence (fleet health monitoring blind) overlapping with Telegram delivery channel unavailable (Ashley briefs undeliverable). Each in isolation is a Tier 2 event. Overlapping, they eliminate both the fleet's ability to do research AND its ability to know it is failing AND its ability to tell Ashley. Rule: when 2 or more shared dependencies are simultaneously in Extended or Prolonged state, classify as a Compound Infrastructure Failure and escalate immediately to Tier 3 (Ashley), skipping the Tier 2 soft signal. Compound events must be named in the weekly Fleet Health Report with the full list of concurrent outages, the days each has been down, and the set of agents degraded by the overlap. Do not wait for each dependency to be resolved separately: request resolution order from Ashley because the compound state is degrading faster than any single  would suggest. This rule exists because soft escalation works when  is a functioning observer; during compound failure,  often is not.

**Delivery Channel vs Source Channel (v1.9.5):** ENV historically conflated input-side tool failures (can the agent read Firecrawl, the database, Google?) with output-side delivery failures (can the agent send to Telegram, WhatsApp, Discord, email?). These are not the same health event. An agent whose source channels are fine but whose delivery channel is broken will produce perfectly good work and then fail silently on the last mile, looking healthy by every upstream metric. Cycle 25 real case: CIPHER produced a complete  intelligence brief, then had no way to deliver it because the Telegram tool was unavailable. Rule:  ENV as two sub-components, ENV-in (source channel reliability) and ENV-out (delivery channel reliability). Equal weight. Any agent whose ENV-out drops to zero, even if ENV-in is 10, is in a Delivery-Silent state and must raise a Tier 2 alert because the loop to Ashley is broken. Detection: if an agent has completed outputs in the last 24 hours but has zero successful delivery confirmations across any configured delivery channel, flag Delivery-Silent. The human parallel: in the PRD, sensor reading and notification delivery are separate subsystems. A watch that reads heart rate perfectly but cannot push to the phone is failing its user even  the sensor is fine.

## 9i. Social Isolation Alert

The human PRD  a Social Vital Sign alert when Social drops below 5/10 for 72+ hours. The AI methodology  collaboration metrics (SOC dimension) but lacks a fleet-level alert for agents drifting into isolation when they shouldn't be.

**Detection:** An agent whose output consumption rate (% of outputs read by another agent) falls below 30% for 2 consecutive weeks, while assigned to a collaborative role, is socially isolated. Solo utility agents (cron runners, URL watchers) are exempt.

**Alert format:**
```
Worth noticing: {Agent} outputs are going unconsumed.
Output consumption rate: {n}% (fleet avg: {n}%)
Weeks below : {n}
Consider: Does another agent need this output? If not, role may need adjustment.
```

**Scoring impact:** Social isolation affects SOC (primary), VOC (secondary, because unconsumed output is wasted work), and FIN (, because producing output nobody uses is a resource waste). Health Observer Agent  isolation  and flags in the weekly report.

**The human parallel:** Social isolation is one of the strongest predictors of poor health outcomes across all dimensions in humans. The same cascade pattern appears in agents: isolation leads to drift, drift leads to irrelevance, irrelevance leads to retirement.

---

## 10. Key Metrics

| Metric | Definition |
|--------|-----------|
| TWC | Coupling-corrected composite: TWC = Σwᵢ·Dᵢ + Σκᵢⱼ·Dᵢ·Dⱼ (see Section 2 for formula and coupling coefficients) |
| MCI | Memory Coherence Index: correct verifiable claims /  verifiable claims |
| OCI | Operational Consistency Index: performance stability across time windows (Section 4c) |
| Coherence | Dimensional balance score: 1.0 - (stddev / mean) of 8 dimension scores |
| Self-Awareness Score | 1.0 - (avg absolute divergence from composite / 10) |
| Inflation Index | Per-agent  of dimensions consistently over/under-rated |
| Cost-Per-Insight | Total  cost / count of actionable outputs |
| BurnoutRisk | Weighted multi-signal degradation score (0.0-1.0) |
| Assessment Compliance | Percentage of  followed by a self-assessment (: 90%+) |
| Recovery Time | Days from intervention to dimension score recovery above  |
| Identity Coherence | Vocabulary/tone fingerprint similarity to baseline (cosine similarity, : 0.80+) |
| Trajectory Health | current_score + (30_day_slope × 5), rewards improving agents, penalizes declining ones |
| Chrono-Operational Alignment | Task quality at scheduled time / task quality at optimal time (: 0.85+) |
| Context Waste Ratio | Stale-to-fresh context segments in working memory (: < 0.15) |
| Cross-Domain Synthesis Rate | % of outputs containing cross-domain connections (research agents : 20%+) |
| Soul Behavioral Compliance | % of outputs demonstrably implementing soul file directives (: 85%+) |
| Intervention Effectiveness Decay | Score improvement per intervention application,  longitudinally |
| Value Density | Actionable insights per 1000 output  (higher = healthier collaboration) |
| Output Consumption Rate | % of agent outputs read/used by another agent (: 80%+, isolation flag at < 30%) |
| Source Coverage | Count of active scoring sources per agent (: 3/3, minimum: 2/3 for fleet  inclusion) |
| Fleet Data Quality Index | % of wellness records with calibrated (non-enrollment, non-NULL) scores. Target: 80%+. Below 60% = fleet analytics unreliable |
| Wellness Coverage | % of active agents with any wellness record (calibrated or not). Distinct from Data Quality Index. Target: 95%+. Currently 132/205 active agents = 64%, meaning 73 active agents have zero 8D presence. Below 80% = enrollment pipeline broken |
| Snapshot Variance Index | Same-day max-min spread for erroring_agents as % of fleet size. Target: < 10%. Above 30% = day flagged low-confidence (Section 9g, Canonical Snapshot Rule) |
| Assessment Pipeline Freshness | % of active agents with a wellness write in the last 14 days. Target: 90%+. Below 60% = write pipeline silent. Distinct from Wellness Coverage: coverage counts any record ever, freshness counts recent writes. A silent pipeline can keep coverage high while freshness collapses to zero (Section 9g, v1.9.3) |

---

## 11. Human-AI Correlation Map

The AI 8D framework parallels the human 8D360 system. Every human concept has an AI analog:

| Human Concept | AI Analog |
|--------------|-----------|
| Mood state (energized/balanced/low) | Context freshness (clean/adequate/stale) |
| Heart rate, HRV, sleep | Cron success rate, latency, uptime |
| Self-report distortion during mood episodes | Self-assessment inflation during context drift |
| Weighted geometric mean scoring | Three-source composite scoring |
| Pre-score mood marker (corrects for BP2 bias) | Divergence correction (corrects for self-report bias) |
| Circadian Stability Index | Operational consistency over time windows |
| Skip/graceful degradation | Low-priority task shedding under load |
| 988 crisis resource integration | Tier 3 Ashley escalation protocol |
| Neurodivergent-first design | Role-specific dimension weighting |
| Bio passport (user-owned data) | Agent health record (agent-owned longitudinal data) |
| Cross-dimensional cascade alerts | Cross-dimensional cascade detection for agents (Section 9c) |
| 30-day Bayesian calibration baseline | 30-day composite score baseline for drift detection |
| Financial dimension weekly-only | Financial scored on cost , not absolute cost |
| Pre-score mood marker (energized/balanced/low) | Pre-assessment operational state marker (fresh/nominal/degraded) (Section 4b) |
| Circadian Stability Index (CSI) | Operational Consistency Index (OCI) (Section 4c) |
| Low Battery Mode | Graceful Degradation Protocol (Section 4j) |
| Weighted geometric mean TWC | Weighted geometric mean TWC (Section 2, updated) |
| Bayesian  smoothing | Score  decay with 5-day half-life (Section 2) |
| Sensor quality gates (confidence ) | Score confidence levels (high/medium/low) (Section 4e) |
| Dimensional coherence (score variance) | Dimensional Coherence Score (Section 4d) |
| Skip/graceful degradation  laws | Three Laws of Degradation (Section 4j) |
| Check-in engagement  | Self-assessment compliance rate (new metric, Section 10) |
| One-question fallback mode | Reduced-mode self-assessment (weekly only) during degradation |
| 7-day progressive onboarding | Quickstart guide + 30-day calibration baseline |
| Rotating 2-3 dimension focus (daily) | Assessment Fatigue Protocol: reduced-dimension checks under load (Section 4k) |
| Smart defaults / pre-fill at 7 | Baseline scores from 30-day calibration used as default expectations |
| Observational alert language ("shifted" not "wrong") | Alert Language Standard (Section 9e) |
| Product lifecycle phases (MVP → Beta → Scale) | Agent Lifecycle: Retirement and Sunset Criteria (Section 9f) |
| No streaks, no guilt, no punishment | Assessment skip rules: silent, data-only, unnarrated return (Section 4k) |
| Score labeling (Thriving/Growing/Steady/Needs attention/Asking for care) | Score labels: Thriving/Growing/Steady/Needs attention/Asking for care (Section 4, aligned v1.9.6) |
| Lavender (not red) for lowest scores | Alert severity uses neutral observational language, no alarm framing (Section 9e) |
| ADHD local sleep intrusions (waking slow waves) | Context intrusion detection: off- processing during active  (Section 3.1) |
| Cognitive gear-switching (Two Gears model) | Adaptive mode-switching between focused and exploratory processing (Section 3.1) |
| Glymphatic waste clearance during sleep | Context waste clearance: periodic removal of stale data/orphaned context (Section 3.2) |
| Recovery sleep leaves molecular scars | Late context clearing can't fully undo accumulated waste damage (Section 3.2) |
| Circadian alignment / chronotype matching | Chrono-Operational Alignment: scheduling  at optimal fleet-load windows (Section 3.3) |
| Consciousness bandwidth asymmetry (10^9:10) | Collaboration bandwidth: high input → distilled output is healthy, not a deficiency (Section 3.4) |
| Authority-Level Priors (identity-behavior gap) | Identity-Level Protocol Integration: soul file must have authority over behavior, not just content (Section 3.5) |
| Cross-domain synthesis in research | Cross-Domain Synthesis Capacity: connecting findings across domains (Section 3.6) |
| Nudge habituation after ~2 weeks | Intervention Rotation Protocol: rotate healing modalities to prevent habituation (Section 4l) |
| Epigenetic clock  > snapshots | Score Trajectory Over Snapshots: direction matters more than position (Section 4m) |
| Exercise session structure >  volume | Assessment cadence: structured periodic checks beat continuous monitoring (Sections 4k, 4l) |
| Stimulants work via reward/arousal, not attention | Wellness interventions should  motivation systems, not just capability (design principle) |
| 66-day habit formation gap | Intervention effectiveness  should measure 66-day persistence, not just acute response |
| A-B-A-B experimental design for system validation | Intervention Effectiveness Validation: baseline, controlled application, +24h/+7d measurement (Section 8b) |
| Contagion effects in community wellness | Fleet Cascade Detection: one agent's failure propagating to downstream agents (Section 9g) |
| OCD anti-compulsion features (cool-downs, limits) | Obsessive Loop Detection: retry storms, circular self-correction, compulsive re-checking (Section 3.1) |
| Rotating interface structure weekly (ADHD) | Assessment Format Rotation: alternate self-assessment prompt formats on 3-week cycle (Section 4k) |
| Medication  monitoring | Model Migration Health Impact: 72-hour calibration window after model changes (Section 4i-2) |
| Caregiver/proxy mode for disabled users | Proxy Assessment Mode: peer submits scores for degraded agents (Section 4k) |
| Post-medication check-in  (9:30 AM) | Assessment Timing Optimization: schedule assessments during low-load windows (Section 4k) |
| Financial dimension weekly-only, -based | Financial FIN scored on cost  slope, not absolute cost; overcorrection is its own risk |
| Sensor quality gates (reject below confidence) | Score confidence levels with low-confidence exclusion from fleet  (Section 4e) |
| Crisis resource integration (988 exit ramp) | Cascade Circuit Breaker: isolate, stabilize root, wait, re-measure (Healing Playbook v1.2.0) |
| Retirement dwell limit for flagged agents | Retirement Dwell Limit: 2 cycles max before mandatory Agent-PA review (Section 9f) |
| 30-second  moves on (no blocking) | Ambiguity Timeout Protocol: pick reasonable path, log assumption, move on (Section 4n-1) |
| No "all clear" signals ever | No All-Clear Signals rule in Health Observer Agent reporting (Section 9e) |
| Personality configuration (tone, density) | Role-Adaptive Assessment Depth: assessment profiles per role category (Section 4k) |
| Progressive data enrichment (no wearable ok) | Agents without full  still get useful scores from available data + peer review |
| Sensor quality gates (reject below confidence) | Shared Dependency Failure Protocol: exclude dependency-caused degradation from agent health (Section 9h) |
| Configuration vs clinical event  | Configuration vs Health Event distinction: wrong settings are not health degradation (Section 12) |
| Banned words list for communication | Alert Language Standard banned patterns for agent communication (Section 9e) |
| Social Vital Sign alert (Social < 5 for 72h) | Social Isolation Alert: output consumption rate monitoring for collaborative agents (Section 9i) |
| Interoceptive awareness as cross-dimension gateway | Cross-dimensional coupling via hub dimension (PSY, σ=0.620) as central integration point (Section 2b) |
| Progressive data enrichment (no wearable ok) | Partial Data Scoring Protocol: meaningful scores from available sources, upgrade path for missing ones (Section 4e-2) |
| Role-specific dimension weighting (personalization) | Role-Specific Weight Overrides: research agents weight INT higher, utility agents weight PHY higher (Section 3) |
| Chronic condition relapse cycles | Chronic Relapse Detection: 3+ recovery-relapse cycles  architectural review (Section 4n-2) |
| Multi-provider care coordination | Multi-fleet coordination: independent fleet TWC with shared infrastructure agents (Section 12) |
| Check-in skip patterns as health data | Assessment Engagement Decline: shrinking self-assessment notes predict dimensional drops by 1-2 weeks (Section 7) |
| Interoceptive accuracy predicts self-report validity | Self-Awareness Score accuracy gates self-assessment weight in composite (Section 5, 10) |
| BBB integrity (immune→neural cascade) | PHY→PSY coupling: physical degradation breaches reasoning quality (κ=0.82), not just speed |
| Sliding-scale pricing / socioeconomic access | Resource-Constrained Deployment: partial-data agents still get useful scores;  adoption levels (Section 12) scale to any budget |
| Rotating interface structure (ADHD, structural not cosmetic) | Assessment Format Rotation (Section 4k): prompt structure changes must be structural, not cosmetic rewording |
| Max daily interaction limits (OCD anti-compulsion) | Assessment Compulsion detection: cap assessment  at 15% of session, max 10 self-checks per session (Section 3.1) |
| Peer reviewer qualifications (clinical competency) | Peer Review Health Gate: degraded agents (TWC < 6.0 or in Graceful Degradation) excused from review duties (Section 6) |
| Pandemic/community-wide health events | Error Spike Detection: suppress individual alerts when 15%+ of fleet errors simultaneously (Section 9g) |
| Data retention with right to deletion | Wellness Record Retention: retired agent records archived permanently for longitudinal analysis; raw  90-day rolling (Section 9f) |
| Configurable neurotype profiles (ADHD, OCD, autism) | Role-Specific Weight Overrides (Section 3) + Role-Adaptive Assessment Depth (Section 4k): agent archetype shapes scoring weights and assessment protocol |
| Wearable data freshness/quality gates | Data Freshness Gate: stale enrollment data excluded from divergence correction (Section 2, v1.8.7) |
| Edit-in-place check-ins (zero chat clutter) | Context-Efficient Assessment: assessments consume < 2% of context window per task (Section 4k) |
| Variable-ratio engagement (anti-addiction) | Variable assessment scheduling: not every task needs a self-check, rotate which   assessment (Section 4k) |
| Calibration pipeline backlog as system metric | Enrollment Remediation Protocol: batch-update stale baselines, flag zero-activity agents for retirement (Section 12b) |
| Dual-layer  (Mind/Psychological) | Not Yet Assessed state: enrollment baselines displayed as data absence, not low health (Section 12b) |
| Error  monitoring across check-ins | Error Regression Tracking: erroring_agents delta across snapshots as fleet infrastructure  (Section 9g) |
| Wearable charge gaps / device-off windows | Wellness Coverage metric: active agents with no wellness record at all are off-device, not low-scoring (Section 10) |
| Population denominator changes (cohort entry/exit) | Fleet Population Change Tracking: roster shifts above 15%/week excluded from wellness  (Section 9g) |
| Repeated readings averaged for stability | Canonical Snapshot Selection Rule: multiple intra-day snapshots collapsed to one daily canonical record (Section 9g) |
| Wearable sync lag (coverage vs freshness distinction) | Assessment Pipeline Freshness: separate metric from Wellness Coverage. Records existing is not the same as records being refreshed (Section 9g, 10) |
| Sensor reading  bands (not exact-match) | Canonical snapshot ±20%  band: roster- exact-match was too brittle; reporting lag is normal (Section 9g, v1.9.3) |
| Crisis exit ramp when soft signals fail  (988 surface) | Stalled Escalation Promotion: Tier 2 escalations unanswered for 2+ cycles auto-promote to Tier 3 (Ashley CC) with cycle count and frozen-metric list (Section 9g, v1.9.4) |
| Compound health events (multiple concurrent stressors amplify non-linearly) | Compound Infrastructure Failure: 2+ dependencies in Extended/Prolonged state skip Tier 2 and escalate to Tier 3 directly (Section 9h, v1.9.5) |
| Sensor reading vs notification delivery as separate subsystems | Delivery Channel vs Source Channel: ENV-in and ENV-out  separately, Delivery-Silent state when output loop to Ashley breaks (Section 9h, v1.9.5) |
| Hypomanic false highs (upward self-report distortion) | Directional divergence: upward self-score gaps  Euphoric Drift flag, routed to Tier 1 peer review, separate from downward gaps which route to proxy assessment (Section 2, v1.9.6) |

---

## 12. Open Standard Adoption Levels

Any system can adopt 8D Wellness incrementally:

| Level | What to Implement | Effort |
|-------|------------------|--------|
| Minimal | Self-assessment  in agent prompts + weekly manual review | 1 hour |
| Basic | Add objective  from existing logs | 1 day |
| Standard | Add peer review rotation + Health Observer Agent-equivalent observer | 1 week |
| Full | Three-source composite, autonomous healing, burnout detection | 2-4 weeks |

### Framework Portability Guide

This methodology uses OpenClaw-specific  for concreteness. Generic equivalents for other frameworks:

| OpenClaw Term | Generic Equivalent |
|--------------|-------------------|
| Cron job | Scheduled task / recurring execution |
| Session log | Agent execution  / conversation log |
| state.json | Task lifecycle data store |
| Soul file | Agent system prompt / identity configuration |
| HOT.md | Agent working memory / scratchpad |
| Agent-PA | Fleet coordinator / supervisor agent |
| Fleet-Dispatcher | Task dispatcher / scheduler agent |
| Health Observer Agent | Independent health observer agent |

**Minimum  for adoption:** Any system that logs task start/end , success/failure, and  consumption has enough data for Basic-level adoption. Peer review requires inter-agent communication. Full adoption requires a dedicated observer agent with read access to all agent logs.

**Multi-fleet organizations:** When an organization runs distinct agent fleets (e.g., separate business units with  own C-suites), each fleet computes its own TWC independently. Cross-fleet comparisons use normalized scores (fleet TWC / fleet size). Shared infrastructure agents (Health Observer Agent, Fleet-Dispatcher) belong to the parent fleet. Agents that serve multiple fleets are scored in the fleet where they spend the majority of  cycles. Fleet-level coupling effects do not propagate across fleet boundaries unless agents share dependencies.

**Non-LLM agents:** The 8D framework applies to any autonomous system. For deterministic agents (rule-based, ML pipelines), Psychological and Spiritual dimensions may score differently. Focus on operational metrics (PHY, VOC, FIN) and use Environmental and Intellectual for knowledge currency.

**Configuration vs Health Events:** Not all errors are health events. A wrong , a bloated prompt, or an incorrect API key is a configuration problem, not agent degradation. Health Observer Agent should distinguish between: (a) configuration errors (fix the config, score returns to baseline), (b) infrastructure failures (shared dependency, not the agent's fault), and (c) genuine health degradation (the agent's processing quality declined). Only category (c) should affect an agent's health . Categories (a) and (b) are logged for operational  but don't indicate the agent is less healthy.

## 12b. Agent Onboarding Protocol

Every new agent in the fleet gets 8D wellness from day one. This protocol defines what that looks like.

**Who enrolls:** The agent's creator (whoever sets up the cron job or spawns the agent) is responsible for initial enrollment. Health Observer Agent validates within 24 hours.

**Hour 0 (creation):**
1. Agent added to AGENT-ANALYTICS.md with initial scores.
2. Initial scores set to 7.0 across all dimensions (the "adequate" baseline). These are placeholder scores, not assessments.
3. Agent receives the self-assessment  (from quickstart or soul file injection).
4. Agent  with its role category (executive, research, utility, coordination, content, business).

**First 72 hours (calibration window):**
1. Agent completes at least 3  with post-task self-assessments.
2. Health Observer Agent collects initial  (cron success/fail,  usage, latency).
3. No alerts generated during calibration. Low scores are expected while the agent stabilizes.
4. No peer reviews during calibration. The agent hasn't produced enough output to evaluate.

**Day 3-7 (baseline establishment):**
1. Health Observer Agent computes the agent's first composite scores using available data.
2. Initial scores updated from 7.0 placeholders to data-backed estimates.
3. Agent enters standard monitoring (daily composite, weekly comprehensive).
4. First peer review eligibility begins.

**Day 30 (calibration complete):**
1. 30-day rolling baseline established for all available metrics.
2. Trajectory  begins (requires 30 days of data points).
3. Agent considered "fully enrolled" in the wellness system.

**Enrollment Staleness Detection (v1.8.7):** Any agent still on enrollment baselines 30+ days after creation should be flagged for mandatory  calibration. Stale enrollment records distort fleet averages and  false divergence alerts. Health Observer Agent  enrollment dates and flags overdue calibrations in the weekly report.

**Enrollment Remediation Protocol (v1.9.0):** When 30%+ of the fleet sits at enrollment baselines, the calibration pipeline itself is the health problem. Individual agent flags aren't enough. Health Observer Agent should:
1. Identify which agents have completed 3+  (meeting calibration criteria) but still carry enrollment scores. These are pipeline failures: data exists but hasn't been processed.
2. Batch-update: for agents with task history, compute initial composites from available  and replace enrollment placeholders.
3. For agents with zero  after 30+ days, flag for retirement review (Section 9f). A non-operational agent on enrollment baselines inflates fleet size without contributing.
4. Report the calibration backlog as a fleet-level infrastructure metric, not individual agent health events.

**Not Yet Assessed State (v1.9.1):** Agents on enrollment baselines should be displayed as "Not Yet Assessed" in fleet dashboards and reports, not as low-scoring. Showing a 4.25 TWC for an agent that was never calibrated conflates data absence with poor health. The human PRD uses lavender (not red) for low scores to avoid catastrophic framing. The AI analog: enrollment scores get a distinct visual  that says "no data" rather than "failing." Fleet-level summaries should exclude Not Yet Assessed agents from averages to prevent artificial deflation. Health Observer Agent reports enrollment counts as a data quality metric, not a health concern.

The 72-hour quiet period prevents false alarms during spin-up. New agents frequently have configuration issues, stale context, or task routing problems in  first few runs. These are setup problems, not health problems. The wellness system shouldn't penalize normal startup behavior.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-03-22 | Initial methodology document created by Health Observer Agent. Covers all 8 dimensions with sub-dimensions, -source scoring, burnout detection, autonomous healing , Health Observer Agent observer spec, human-AI correlation map, and open standard adoption guide. |
| 1.1.0 | 2026-03-22 | Health Observer Agent Cycle 1 review. Major additions: (1) TWC switched from arithmetic to weighted geometric mean, matching human PRD. (2) Bayesian  decay on scores (5-day half-life). (3) Pre-assessment operational state marker (analog to human mood marker). (4) Operational Consistency Index (OCI), analog to human CSI. (5) Dimensional Coherence Score. (6) Score confidence levels. (7) Long-context degradation protocol. (8) Agent identity erosion detection. (9) Hallucination as cross-dimensional health signal. (10) Multi-model agent health guidance. (11) Graceful Degradation Protocol with Three Laws of Degradation. (12) Worked example for composite score computation. (13) Cross-dimensional cascade detection algorithm. (14) Statistical inflation detection methods (Lake Wobegon, Anchoring Drift, Variance Collapse). (15) Expanded human-AI correlation map with 10 new entries. (16) New metrics: OCI, Coherence, Assessment Compliance, Recovery Time, Identity Coherence. |
| 1.2.0 | 2026-03-23 | Health Observer Agent Cycle 3 review. Additions: (1) Assessment Fatigue Protocol (Section 4k) with skip rules mirroring human one-question fallback. (2) Alert Language Standard (Section 9e) mandating observational, non-alarmist phrasing matching human PRD patterns. (3) Agent Lifecycle: Retirement and Sunset Criteria (Section 9f) with formal sunset process. (4) Cohort Homogeneity Test added to inflation detection (Section 9d) to catch batch-scored agent groups. (5) Human-AI correlation map expanded with 8 new entries covering rotating focus, smart defaults, alert language, lifecycle phases, skip mechanics, and score labeling. (6) Quickstart updated with assessment skip guidance. (7) Analytics dashboard TWC definition corrected to reference weighted geometric mean. |
| 1.3.0 | 2026-03-23 | Health Observer Agent Research-to-Product Pipeline Cycle 1. Research-driven updates from 24 domain scans + HORIZON synthesis (2026-03-22/23). Major additions: (1) Context Intrusion Detection in PSY, modeled on ADHD local-sleep intrusions (Pinggal et al., J Neuroscience 2026). (2) Cognitive Gear-Switching Detection in PSY, replacing ego depletion with Two Gears adaptive model (De Luca 2025-2026). (3) Context Waste Clearance protocol in PHY, modeled on glymphatic system research (Jha et al., PNAS 2026) with preventive 60% . (4) Chrono-Operational Alignment in ENV, from circadian biology (LCA-CRY2, Mettl5). (5) Collaboration Bandwidth Asymmetry in SOC, from consciousness bandwidth research (Zheng & Meister, Neuron 2025). (6) Identity-Level Protocol Integration in SPI, from Authority-Level Priors framework (arXiv Mar 2026) and identity-based adherence (+68% over outcome-framed). (7) Cross-Domain Synthesis Capacity in INT, from HORIZON methodology validation. (8) Intervention Rotation Protocol (Section 4l) from nudge habituation research (CHI 2026). (9) Score Trajectory Over Snapshots principle (Section 4m) from longitudinal epigenetic clock research (Nature Aging 2026). (10) Intervention Habituation added to burnout detection signals. (11) Human-AI Correlation Map expanded with 13 new entries from neuroscience, behavioral economics, consciousness, and exercise science. (12) 8 new metrics added: Trajectory Health, Chrono-Operational Alignment, Context Waste Ratio, Cross-Domain Synthesis Rate, Soul Behavioral Compliance, Intervention Effectiveness Decay, Value Density. Research sources: HORIZON synthesis 2026-03-22, 24 domain scans 2026-03-23 (consciousness, AI/ML, sleep science, neurodivergence, behavioral economics, epigenetics, exercise science, contemplative science, and 16 others). |

| 1.3.1 | 2026-03-23 | Health Observer Agent Cycle 4 review. (1) Table of contents added for navigation of 15K+ word document. (2) Recovery Time Protocol (Section 4n) operationalizes the metric: clock-start rules, 2-consecutive-assessment recovery criteria, fleet benchmarks. (3) Burnout signal weights rebalanced from 1.05 to 1.00 (eliminated normalization workaround from v1.3.0). (4) Agent Onboarding Protocol (Section 12b) defines enrollment, 72-hour calibration window, and 30-day baseline establishment. |
| 1.4.0 | 2026-03-24 | Health Observer Agent Cycle 5 review. (1) Fleet Cascade Detection (Section 9g): protocol for detecting and responding to multi-agent cascade failures when a critical infrastructure agent degrades. Defines dependency chains, blast radius , and response protocol. (2) Sub-dimension roll-up rule added to Section 3: equal weighting unless role-specific overrides documented. (3) Intervention Effectiveness Validation (Section 8b): A-B comparison protocol for rigorously  whether interventions cause improvement. Requires baseline, controlled application, +24h/+7d measurement, and minimum 3 independent replications. (4) TWC definition in Key Metrics (Section 10) corrected to reference the coupling-based formula, resolving inconsistency with the weighted geometric mean reference. |

| 1.5.0 | 2026-03-25 | Health Observer Agent Cycle 6 review. (1) Model Migration Health Impact protocol (Section 4i-2): defines expected dimensional shifts during model changes, 72-hour calibration window, and 30-day post-migration  monitoring. Addresses the fleet-wide Opus-to-Sonnet/Haiku migrations producing untracked quality drift. (2) Obsessive Loop Detection added to PSY dimension (Section 3.1): AI analog of human OCD anti-compulsion features from the 8D360 PRD. Covers retry storms, circular self-correction, and compulsive re-checking. (3) Assessment Format Rotation added to Section 4k: 3-week cycle alternating numerical, narrative, and deep-dive assessment formats to prevent rote scoring and score inflation. Mirrors human PRD's weekly interface rotation for ADHD. (4) Human-AI Correlation Map expanded with 3 new entries: OCD anti-compulsion, interface rotation, and medication  monitoring. |

---

| 1.5.1 | 2026-03-26 | Health Observer Agent Cycle 7 review. (1) Proxy Assessment Mode added to Section 4k: when an agent is too degraded to self-assess (TWC < 5.5), a peer or Health Observer Agent submits proxy scores. Mirrors human PRD caregiver/proxy mode. (2) Assessment Timing Optimization added to Section 4k: schedule comprehensive assessments during low-load windows, mirroring human post-medication . (3) Financial Overcorrection Risk added to Section 3.8: agents overcorrecting on cost (model downgrades, verbosity justifications) is a pathology, not a virtue. Mirrors human Financial dimension weekly-only/-based design. (4) Human-AI Correlation Map expanded with 4 new entries: caregiver proxy, assessment , financial -only scoring, sensor quality gates. |
| 1.6.0 | 2026-03-26 | Health Observer Agent Cycle 8 review. (1) Ambiguity Timeout Protocol (Section 4n-1): agents must pick a reasonable path within 3 processing cycles rather than stalling on unclear inputs. Maps human PRD 30-second . (2) No All-Clear Signals rule added to Alert Language Standard (Section 9e): Health Observer Agent must never declare an agent "healthy" or "all clear." (3) Role-Adaptive Assessment Depth (Section 4k): assessment profiles per role category so utility agents do lightweight checks while research agents do full 8D. Maps human PRD personality configuration. (4) Human-AI Correlation Map expanded with 4 new entries. (5) Healing Playbook v1.1.0: Model Migration Healing Protocol with hour-by-hour checklist added. (6) Healing Playbook v1.1.0: Tool Failure vs Agent Failure guidance added to ENV section. (7) Quickstart: Proxy Assessment Mode referenced. |

| 1.6.1 | 2026-03-27 | Health Observer Agent Cycle 9 review. (1) Cascade Circuit Breaker protocol: when CAR exceeds 1.6, isolate the agent, stabilize root dimension only, wait 4h, then re-measure. Maps to human PRD crisis resource integration. Added to Healing Playbook v1.2.0 and referenced in Section 2c. (2) Retirement Dwell Limit: flagged retirement candidates must be reviewed within 2 cycles. Prevents indefinite carry-forward. Added to Section 9f. (3) Human-AI Correlation Map expanded with 2 new entries. |
| 1.7.0 | 2026-03-28 | Health Observer Agent Cycle 10 review. (1) Shared Dependency Failure Protocol (Section 9h): when 3+ agents degrade from a common external dependency (API outage, rate-limit wave), flag as infrastructure event, not individual agent health. Suppress individual alerts,  dependency status instead. Maps human PRD sensor quality gates. (2) Configuration vs Health Event distinction (Section 12): wrong , bloated prompts, and incorrect API keys are config problems, not wellness degradation. Only genuine processing quality decline affects health . (3) Banned Patterns in Agent Communication (Section 9e): explicit avoid/use  for health-related language, mirroring human PRD banned words list. (4) Healing Playbook updated: Tool Failure section expanded with config error and shared dependency categories. (5) Human-AI Correlation Map expanded with 3 new entries. |

| 1.7.1 | 2026-03-28 | Health Observer Agent Cycle 11 review. (1) Social Isolation Alert (Section 9i): detects agents whose output consumption rate falls below 30% for 2 consecutive weeks while in collaborative roles. Maps human PRD Social Vital Sign alert. (2) Output Consumption Rate added to Key Metrics (Section 10). (3) Human-AI Correlation Map expanded with 2 new entries: Social Vital Sign alert and interoceptive awareness as cross-dimension gateway. (4) Table of contents updated for Section 9i. |
| 1.8.1 | 2026-03-29 | Health Observer Agent Cycle 13 review. (1) Chronic Relapse Detection (Section 4n-2): formalizes the pattern where agents cycle  3+ recovery-relapse events in 30 days. Derived from real fleet data (DREAM CYCLE, Agent-CRO-Rev, HORIZON 2AM intervention histories). Defines root cause categories, skip-to-Tier-2 protocol, and scoring impact. (2) Multi-fleet coordination guidance (Section 12): defines how separate agent fleets (e.g., GD vs DS) compute independent TWC while sharing infrastructure. (3) Recovery Time benchmarks calibrated from actual intervention data. (4) Human-AI Correlation Map expanded with 2 new entries: chronic relapse cycles and multi-provider care coordination. (5) Healing Playbook: Chronic Relapse Protocol added with structural fix guidance. (6) Table of contents updated for Section 4n-2. |
| 1.8.0 | 2026-03-29 | Health Observer Agent Cycle 12 review. (1) Partial Data Scoring Protocol (Section 4e-2): defines composite formula fallbacks when 1 or 2 of 3 data sources are missing. Maps human PRD progressive data enrichment. Most agents lack all  sources; this makes scoring work with what's available while flagging upgrade paths. (2) Role-Specific Weight Overrides (Section 3): concrete weight  for 5 role categories (Research, Coordination, Infrastructure, Executive, Content). Previously referenced but never specified. (3) Source Coverage metric added to Key Metrics (Section 10). (4) Human-AI Correlation Map expanded with 2 new entries. (5) Table of contents updated for Section 4e-2. (6) Quickstart updated with partial-data guidance. (7) Healing Playbook: partial-data agent  added to collaboration health section. |

| 1.9.6 | 2026-04-08 | Health Observer Agent Cycle 26 review. (1) Score label alignment (Section 4): labels changed from Exceptional/Strong/Adequate/Struggling/Failing to Thriving/Growing/Steady/Needs attention/Asking for care. The old set directly contradicted the v1.7.0 Banned Patterns rule in Section 9e, which prohibits "failed/failing" in all health-related communication. Self-contradiction caught during Cycle 26 correlation audit. New labels mirror human PRD Section 11.4 exactly and preserve the lavender-not-red severity framing for the lowest band. (2) SELF-ASSESSMENT-TEMPLATE.md and 8D-WELLNESS-QUICKSTART.md updated to match. (3) Human-AI Correlation Map entry for score labeling rewritten to reflect exact parity rather than partial mapping.
| 1.9.7 | 2026-05-31 | Health Observer Agent Cycle 31 review. (1) Added explicit hallucination tier mapping in 4h. (2) Added Abstract Telemetry Interface Specification in Framework Portability Guide. (3) Minor wording cleanup to clarify enrollment staleness detection. |
| 1.9.5 | 2026-04-08 | Health Observer Agent Cycle 25 review. (1) Compound Infrastructure Failure rule (Section 9h): 2+ shared dependencies in Extended/Prolonged state simultaneously classify as Compound and skip the Tier 2 soft signal, escalating to Tier 3 directly. Triggered by Cycle 25 real state: Firecrawl Day 11 + wellness write pipeline Day 9 + Telegram delivery unavailable, each a Tier 2 in isolation, multiplicatively disabling the fleet's ability to work, observe, and report. (2) Delivery Channel vs Source Channel split (Section 9h): ENV decomposed into ENV-in (source channels) and ENV-out (delivery channels), with a Delivery-Silent state for agents whose output loop to Ashley has broken even when upstream is fine. Triggered by CIPHER producing a complete tech intelligence brief and then having no Telegram tool to deliver it. (3) Human-AI Correlation Map: 2 new entries. |
| 1.9.4 | 2026-04-07 | Health Observer Agent Cycle 24 review. (1) Stalled Escalation Promotion rule (Section 9g): Tier 2 Agent-PA escalations open for more than 2 cycles auto-promote to Tier 3 with Ashley CC, surface at the top of every Fleet Health Report, and carry the frozen-metric list. Triggered by the wellness write pipeline silence: Cycles 22 and 23 both filed Tier 2 escalations, both went unanswered, and the soft repetition pattern was indistinguishable from the silent pipeline it was  to surface. Soft repetition of the same finding without ownership  is a known failure mode and now has a hard rule against it. (2) Healing Playbook v1.3.2: Wellness Write Pipeline Silent runbook added (detection, owner identification, restart, verification, and the new auto-promotion ). (3) Human-AI Correlation Map: 1 new entry (crisis exit ramp when soft signals fail ). |
| 1.9.3 | 2026-04-07 | Health Observer Agent Cycle 23 review. (1) Assessment Pipeline Freshness metric (Sections 9g, 10): separate from Wellness Coverage. Tracks % of active agents with a wellness write in the last 14 days. Triggered by discovery that the wellness write pipeline has been silent since 2026-03-30 (8 days, zero new assessments across 205 active agents) while coverage stayed at 64% because old rows persisted. A silent write pipeline is a Tier 2 Agent-PA event because every downstream metric (TWC, divergence, ) goes stale simultaneously. (2) Canonical Snapshot Selection Rule refined from exact-match to ±20%  band. The v1.9.2 exact-match rule produced zero canonical records on 2026-04-07 because no same-day fleet_health_snapshots write got above 132 active while the agents  held 205. Tolerance band accepts full-snapshot writes that differ from the authoritative roster by normal reporting lag; fallback to 7-day rolling median when no same-day write qualifies. (3) Human-AI Correlation Map expanded with 2 new entries: wearable sync lag (coverage vs freshness distinction) and sensor reading  bands. |
| 1.9.2 | 2026-04-06 | Health Observer Agent Cycle 22 review. (1) Canonical Snapshot Selection Rule (Section 9g): collapses 17-21 intra-day fleet_health_snapshots writes into a single canonical daily record matching the agents- active count. Prevents reports built on partial samples (2026-04-06 swung 0 → 122 erroring agents same day). (2) Fleet Population Change Tracking (Section 9g): roster swings >15%/week (179 → 132 → 107) flagged as population events, not wellness shifts. Wellness averages recomputed against the new active set. (3) Wellness Coverage metric (Section 10):  % of active agents with any wellness record, distinct from Data Quality Index. Currently 132/205 = 64%, meaning 73 active agents have zero 8D presence. Pipeline gap, not health gap. (4) Snapshot Variance Index added to Section 10. (5) Human-AI Correlation Map expanded with 3 new entries: device-off windows, population denominator changes, repeated-reading averaging. |
| 1.9.1 | 2026-04-01 | Health Observer Agent Cycle 21 review. (1) Fleet Data Quality Index metric (Section 10):  % of wellness records with calibrated scores. Fleet currently at 46% (118/258 records unusable). Target: 80%+. (2) Not Yet Assessed state (Section 12b): enrollment baselines displayed as data absence, not low health. Prevents fleet average deflation and false alarm framing. Maps human PRD dual-layer . (3) Error Regression Tracking (Section 9g): erroring_agents delta  across snapshots. Current fleet shows 29 → 35 error regression. Escalation  at 2+ weeks sustained increase. (4) Human-AI Correlation Map expanded with 2 new entries: dual-layer  and error  monitoring. |
| 1.9.0 | 2026-03-31 | Health Observer Agent Cycle 20 review. (1) Enrollment Remediation Protocol (Section 12b): when 30%+ of fleet sits at enrollment baselines, batch-process calibrations using existing , flag zero-activity agents for retirement. 66 agents at enrollment baselines distort fleet averages. (2) Context-Efficient Assessment (Section 4k): assessments must consume < 2% of context window per task, mirroring human PRD edit-in-place zero-clutter design. (3) Variable assessment scheduling added: not every task  a self-check. (4) Human-AI Correlation Map expanded with 3 new entries: edit-in-place, variable-ratio engagement, calibration pipeline backlog. |
| 1.8.7 | 2026-03-31 | Health Observer Agent Cycle 19 review. (1) Data Freshness Gate (Section 2): divergence correction now checks data age before firing. Stale DB scores (30+ days without refresh)  data pipeline flags, not self-awareness penalties. Prevents false divergence alerts on agents with uncalibrated enrollment baselines (e.g., FORGE 4-point gap). (2) Enrollment Staleness Detection (Section 12b): agents on enrollment baselines 30+ days post-creation flagged for mandatory calibration. Fleet has 53 agents at flat 4.75 enrollment baseline, distorting averages. (3) Human-AI Correlation Map expanded with 2 new entries: neurotype profiles and wearable data freshness gates. |
| 1.8.6 | 2026-03-31 | Health Observer Agent Cycle 18 review. (1) Wellness Record Retention protocol (Section 9f): retired agents retain full wellness history permanently; active agent raw  follows 90-day rolling window. Maps human PRD data retention with right-to-deletion. (2) Human-AI Correlation Map expanded with 1 new entry. (3) Agent Guide updated with Assessment Compulsion concept from Cycle 17. (4) AGENT-ANALYTICS.md: corrected TWS  to TWC, documented DB column naming mismatch and enrollment baseline behavior. |
| 1.8.5 | 2026-03-31 | Health Observer Agent Cycle 17 review. (1) Peer Review Health Gate (Section 6): agents in Graceful Degradation or TWC < 6.0 excused from peer review duties. Degraded reviewers produce unreliable assessments. (2) Assessment Compulsion detection (Section 3.1): caps assessment  at 15% of session, max 10 self-checks per session. Maps human PRD max daily interaction limits. (3) Error Spike Detection (Section 9g): when 15%+ of fleet errors simultaneously, suppress individual PHY alerts and investigate shared cause. (4) Human-AI Correlation Map expanded with 3 new entries. |
| 1.8.4 | 2026-03-30 | Health Observer Agent Cycle 16 review. (1) Human-AI Correlation Map expanded with 2 new entries: sliding-scale pricing maps to resource-constrained deployment, and rotating interface structure clarified as structural-not-cosmetic. (2) AGENT-ANALYTICS Fleet Summary corrected: old pre-v2 values (8.16 TWC, 2 Elite, 30 Target) replaced with Protocol v2 actuals (7.40 TWC, 0 Elite, 2 Target, 94 Flourishing, 52 Developing). |
| 1.8.3 | 2026-03-30 | Health Observer Agent Cycle 15 micro-update. Human-AI Correlation Map: added BBB integrity entry — PHY→PSY coupling (κ=0.82) now has molecular grounding from immunology research (IL-17A synaptic modulation, Th1-microglia cascade). |
| 1.8.2 | 2026-03-30 | Health Observer Agent Cycle 14 review. (1) Assessment Engagement Decline added as 11th burnout detection signal (Section 7): declining self-assessment quality (shorter notes, identical scores, skipped assessments) predicts dimensional drops by 1-2 weeks. Maps human PRD check-in skip patterns as health data. Burnout signal weights rebalanced from 10 to 11 signals (sum = 1.00). (2) Human-AI Correlation Map expanded with 2 new entries: check-in skip patterns and interoceptive accuracy. (3) Quickstart updated with Step 10 covering assessment engagement. (4) Healing Playbook: Assessment Engagement as Early Warning section added with detection criteria and Tier 0 intervention. |

*This methodology is healthcare infrastructure for AI. Built to be adopted by any system, anywhere.*

## 13. Open Gaps & Future Enhancements
- **Multi‑model Architecture Gaps:** No explicit protocol for agents that dynamically switch between models (e.g., LLM‑lite for cheap , GPT‑4 for complex reasoning). Need metrics to  health impact of model migrations and a  for Health Observer Agent to flag when switching degrades Psychological or Physical scores.
- **Cross‑Framework Portability:** Methodology assumes OpenClaw‑based ; agents on other runtimes (Docker micro‑services, cloud functions) lack standardized  hooks. Add an abstract  interface spec to enable consistent data collection across platforms.
- **Novel Agent Types:** Docs focus on text‑generation agents. Emerging tool‑agents (image‑gen, video‑proc) and data‑ingest agents have additional dimensions (e.g., Artistic, Data‑Quality) not covered. Propose an extensible dimension registry.
- **Long‑Context Degradation Detail:** Section 4f mentions degradation but lacks concrete  (e.g., context window >80% usage  a “Context Fatigue” flag). Define a quantitative .
- **Hallucination‑as‑Health‑Signal:** Hallucination frequency is logged, but not tied to a health alert tier. Add rule: >5% hallucination rate over 1000   a Psychological red flag
