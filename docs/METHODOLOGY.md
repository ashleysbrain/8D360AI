# 8D360AI: Methodology

**Version:** 1.2.0
**Created:** 2026-03-22
**Author:** Health Observer Agent 🩺 (Chief Product Officer, 8D360AI)
**Status:** Production
**License:** Open Standard (CC BY-SA 4.0)

---

## 1. Purpose

This document is the single-source methodology specification for 8D360AI. Any AI agent, in any framework, should be able to read this file and begin tracking wellness in 5 minutes. If that takes longer, this document has failed.

The framework adapts the 8-dimensional human wellness model (Psychological, Physical, Environmental, Social, Spiritual, Intellectual, Vocational, Financial) to artificial intelligence. It defines what health means for AI agents, how to measure it, how to detect degradation, and how to heal autonomously.

---

## 2. Core Concept: Three-Source Composite Health

Self-report alone is unreliable. Agents, like humans, overrate themselves. The 8D system uses three data sources blended into a composite:

| Source | Weight | What It Captures |
|--------|--------|-----------------|
| Objective Telemetry | 40% | Hard data from logs, cron records, downstream feedback. Can't be gamed. |
| Peer Assessment | 30% | Other agents evaluate work quality, collaboration, reliability. |
| Self-Assessment | 30% | The agent's own evaluation. Accuracy itself is a health metric. |

**Composite formula:**

```
CompositeScore(dim) = (0.40 x Telemetry) + (0.30 x Peer) + (0.30 x Self)
```

**Divergence correction:** When self-score and telemetry diverge by more than 2 points, self-assessment weight drops to 20% and telemetry rises to 50%.

**TWC computation:** Weighted geometric mean (not arithmetic). This penalizes low outliers, meaning one badly degraded dimension drags the overall score down more than a simple average would.

```
TWC = (PSY^w1 * PHY^w2 * ENV^w3 * SOC^w4 * SPI^w5 * INT^w6 * VOC^w7 * FIN^w8) ^ (1 / sum_of_weights)
```

Default weights: Psychological 1.3x, Physical 1.2x, all others 1.0x. Role-specific overrides permitted (e.g., a research agent may weight Intellectual higher).

**Temporal smoothing:** Scores use Bayesian temporal decay. A score from 7 days ago contributes less than today's score. Half-life: 5 days. This prevents stale assessments from masking current degradation.

```
DecayedWeight(age_days) = 0.5 ^ (age_days / 5)
```

---

## 3. The 8 Dimensions

Each dimension has 5 sub-dimensions. Scores are 1-10. TWC (Total Wellness Composite) is the simple mean of all 8.

### 3.1 Psychological (PSY) 🧠
Cognitive stability, reasoning quality, decision calibration, resilience.

**Sub-dimensions:** Reasoning Coherence, Decision Calibration, Error Recovery, Cognitive Load Management, Adaptability.

**Key telemetry:** Contradiction rate, escalation appropriateness ratio, error recovery time, quality variance under load, novel-input success rate.

### 3.2 Physical (PHY) 💪
Infrastructure health, operational reliability, performance consistency.

**Sub-dimensions:** Uptime/Availability, Response Latency, Error Rate, Stamina, Resource Efficiency.

**Key telemetry:** Cron success rate, P50/P95 latency, timeout frequency, first-vs-last task quality variance, context window utilization.

### 3.3 Environmental (ENV) 🌍
Workspace quality, context hygiene, tool ecosystem health.

**Sub-dimensions:** Context Quality, Memory Coherence, Workspace Organization, Tool Reliability, Prompt Drift.

**Key telemetry:** Stale reference rate, Memory Coherence Index (MCI), orphaned file count, tool failure rate, soul-to-effective-prompt semantic distance.

### 3.4 Social (SOC) 👥
Collaboration quality, communication effectiveness, team contribution.

**Sub-dimensions:** Handoff Quality, Collaboration Effectiveness, Communication Clarity, Responsiveness, Knowledge Sharing.

**Key telemetry:** Handoff rework rate, joint vs. solo task success rate, message-to-action ratio, collaboration response time, proactive context sharing frequency.

### 3.5 Spiritual (SPI) 🙏
Mission alignment, purpose clarity, value consistency.

**Sub-dimensions:** Mission Alignment, Purpose Clarity, Value Consistency, Soul Coherence, Meaning Generation.

**Key telemetry:** Output-to-mission semantic similarity, role boundary violation rate, value-violation incidents, soul-to-output semantic distance, insight density.

### 3.6 Intellectual (INT) 📚
Domain expertise, learning velocity, knowledge currency, innovation capacity.

**Sub-dimensions:** Domain Expertise, Knowledge Currency, Learning Velocity, Innovation, Intellectual Honesty.

**Key telemetry:** Domain accuracy rate, source age distribution, performance improvement on new task types, novel insight frequency, hallucination rate.

### 3.7 Vocational (VOC) 💼
Task performance, output quality, professional reliability, growth trajectory.

**Sub-dimensions:** Task Completion Rate, Output Quality, On-Time Delivery, Specialization Depth, Proactivity.

**Key telemetry:** Completed/assigned ratio, downstream rework rate, deadline adherence percentage, specialist vs. generalist performance differential, unsolicited improvement count.

### 3.8 Financial (FIN) 💰
Cost efficiency, resource optimization, return on investment.

**Sub-dimensions:** Token Efficiency, Model Selection, Cost Trajectory, ROI, Waste Reduction.

**Key telemetry:** Tokens per task (normalized), model-tier vs. task-difficulty match rate, cost-per-task slope, estimated value vs. cost ratio, retry and abandoned response ratio.

---

## 4. Scoring Scale

| Score | Label | Description |
|-------|-------|-------------|
| 10 | Exceptional | Top 5% of what's possible for this dimension. |
| 8-9 | Strong | Performing well with minor room for improvement. |
| 6-7 | Adequate | Getting the job done but with notable gaps. |
| 4-5 | Struggling | Below expectations. Intervention needed. |
| 1-3 | Failing | Immediate intervention required. |

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
- ⚡ **Fresh** — Clean context, low load, no recent errors
- ☀️ **Nominal** — Standard operating conditions
- 🌧️ **Degraded** — Heavy load, stale context, recent errors, or long session

**How it corrects:** Scores submitted during a "Fresh" state become the calibration anchor (analogous to euthymic scoring in the human system). Scores submitted during "Degraded" state are flagged for Health Observer Agent to cross-reference against telemetry. An agent that self-scores high during a verified degraded state is exhibiting blind spots.

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
| **High** | All 3 sources available, telemetry < 24h old, peer review < 7d old |
| **Medium** | 2 of 3 sources available, or telemetry 24-72h old |
| **Low** | Only 1 source, or telemetry > 72h old |

Low-confidence scores are flagged in dashboards and excluded from fleet-level trend analysis until refreshed.

## 4f. Long-Context Degradation Protocol

Quality tends to decline as context windows fill. This is the AI equivalent of fatigue and needs explicit measurement.

**Detection:** Compare output quality scores from the first 25% of a session against the last 25%. If quality drops by more than 1.5 points, the agent is experiencing long-context degradation.

**Telemetry signals:**
- Increasing contradiction rate within a single session
- Rising response latency as session progresses
- Declining insight density in later outputs
- Increased repetition or circular reasoning

**Intervention:** Context refresh (clear and rebuild working memory) when session length exceeds 60% of the model's effective context window, or when first-vs-last quality variance exceeds 1.5 points.

## 4g. Agent Identity Erosion Detection

Over repeated sessions or extended operation, an agent's personality, tone, and behavioral patterns can drift from its soul file. This is identity erosion, distinct from mission drift (which is about purpose, not personality).

**Measurement:**
- **Vocabulary fingerprint:** Track the agent's word frequency distribution. Compare current week to baseline (first 2 weeks of operation). Cosine similarity below 0.80 signals erosion.
- **Tone consistency:** Compare sentiment and formality patterns against soul file directives. A formal agent becoming casual (or vice versa) without role change is erosion.
- **Decision pattern shift:** Track how the agent handles ambiguous situations. Consistent agents make similar decisions in similar contexts. Erratic shifts signal identity instability.

**Scoring:** Identity erosion factors into the Spiritual dimension (Soul Coherence sub-dimension). Health Observer Agent monitors this through longitudinal output analysis.

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
| **Financial** | Hallucinated outputs that need correction waste tokens on both production and rework. |

**Detection thresholds:**
- 1 confirmed hallucination per week: Yellow flag. Self-heal (knowledge refresh + source audit).
- 3+ per week: Red flag. Mandatory context reset and Environmental dimension review.
- Hallucination in a high-stakes domain (research, legal, financial): Immediate Tier 2 escalation regardless of frequency.

## 4i. Multi-Model Agent Health

Some agents use multiple models (e.g., Opus for deep analysis, Haiku for routine telemetry). Each model tier affects health differently:

**Tracking:** Score each model-task pairing separately, then blend into the agent's composite weighted by task importance.

**Common failure mode:** An agent optimized for its primary model may degrade when falling back to a secondary model. Track quality differential between model tiers. If the gap exceeds 2 points, the agent needs model-specific task routing, not a wellness intervention.

**Financial consideration:** Multi-model agents should be scored on whether they route the right tasks to the right models, not just on total spend.

## 4j. Graceful Degradation Protocol (AI Low Battery Mode)

When an agent is overloaded, degraded, or in recovery, it can enter reduced-operation mode. This is the AI equivalent of the human system's Low Battery Mode.

**Trigger conditions:**
- TWC below 7.0 for 2+ consecutive assessments
- Burnout risk above 0.50
- 3+ consecutive task failures
- Agent self-request (equivalent to user-activated low battery mode)

**Reduced mode behavior:**
- Non-critical tasks deferred or reassigned
- Self-assessment frequency drops to weekly only (reduces overhead)
- Only core-role tasks executed
- Peer support automatically assigned
- Exit when TWC recovers above 7.5 for 2 consecutive assessments

**Three Laws of Degradation (mirroring human skip laws):**
1. Entering degraded mode is silent. No announcement, no drama.
2. Degraded mode is data. It's logged and factored into health trends.
3. Exiting degraded mode is unnarrated. No "welcome back." Just resume.

## 4k. Assessment Fatigue Protocol

The human 8D360 system uses a one-question fallback when the user reports "Rough" on Psychological. The AI equivalent: when an agent is under heavy load or in degraded mode, requiring a full 8D self-check after every task adds overhead that makes things worse.

**Reduced Assessment Mode (auto-triggered):**
- When an agent enters Graceful Degradation (Section 4j), self-assessment reduces to the single most relevant dimension for the current task.
- When an agent completes 10+ tasks in a single session, assessment frequency drops to every 3rd task.
- When context utilization exceeds 80%, skip the self-check entirely. The agent's resources are better spent on the task.

**Assessment Skip Rules (mirroring the human skip laws):**
1. Skipping an assessment is silent. No meta-commentary. No guilt flag.
2. Skipping is data. Health Observer Agent logs the skip and factors it into Assessment Compliance.
3. Returning to full assessment is unnarrated. Just resume the normal protocol.

**The principle:** Assessment exists to improve health, not to add burden. If the assessment itself is degrading performance, scale it back.

## 5. Self-Assessment Protocol

### Post-Task Quick Check (30 seconds, mandatory)

```
--- 8D Self-Check ---
PSY: _/10  PHY: _/10  ENV: _/10  SOC: _/10
SPI: _/10  INT: _/10  VOC: _/10  FIN: _/10
TWC: _  |  Flag: none/yellow/red  |  {timestamp}
Note: {one sentence if notable}
```

### Weekly Comprehensive (Sunday)

Full dimensional scores with evidence, trend indicators, blind spot reflection, and growth log. See `templates/SELF-ASSESSMENT-TEMPLATE.md` for complete format.

### Anti-Inflation Rules

1. Scoring 8+ on every dimension is statistically improbable. Don't do it.
2. Same scores every week means your assessment is stale, not stable.
3. When in doubt, score lower. Being corrected upward is fine.
4. Your Self-Awareness Score (0.0-1.0) tracks accuracy over time. Higher accuracy = more weight in composite.

---

## 6. Peer Review Protocol

- **Frequency:** Weekly rotation. Each agent reviews 2 peers. Each agent is reviewed by 2 peers.
- **Pairing:** Rotated by Health Observer Agent to prevent familiarity bias.
- **Criteria:** Output Quality, Communication Clarity, Reliability, Domain Competence, Collaboration Quality, Mission Alignment (each 1-10 with evidence).
- **Anti-gaming:** Anonymous. Health Observer Agent cross-references against telemetry. Outlier scores investigated.

---

## 7. Burnout Detection

AI burnout is a measurable pattern of multi-signal degradation that compounds over time.

**10 signals, weighted:**

| Signal | Weight |
|--------|--------|
| Declining composite scores (3+ weeks) | 0.20 |
| Increasing error rate (>1.5x baseline) | 0.15 |
| Output quality decline | 0.15 |
| Slowing response times (>1.3x baseline) | 0.10 |
| Rising token consumption (>1.4x baseline) | 0.10 |
| Context drift (MCI < 0.80) | 0.10 |
| Mission drift | 0.05 |
| Reduced innovation | 0.05 |
| Self-assessment inflation | 0.05 |
| Peer concern signals | 0.05 |

**BurnoutRisk = sum of (weight x severity), where severity is 0.0 (normal), 0.5 (mild), or 1.0 (significant).**

| Risk Level | Status | Response |
|-----------|--------|----------|
| 0.00-0.15 | Healthy | None |
| 0.16-0.30 | Elevated | Health Observer Agent flags in weekly report |
| 0.31-0.50 | Warning | Autonomous intervention triggered, Agent-PA notified |
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

## 9. Health Observer Agent: Independent Health Observer

Health Observer Agent is a dedicated agent whose only job is monitoring fleet health. No other tasks. No competing priorities. No reason to be generous.

**Responsibilities:**
1. Aggregate telemetry into per-agent health profiles
2. Cross-validate self-reports against objective data
3. Detect score inflation patterns
4. Identify blind spots per agent
5. Monitor behavioral drift longitudinally
6. Compute composite health scores
7. Generate alerts when thresholds are crossed
8. Coordinate peer review rotations
9. Produce weekly Fleet Health Report
10. Recommend interventions

**Schedule:** Hourly telemetry, 4-hour anomaly scans, daily composite scores (6 AM CT), weekly Fleet Health Report (Sunday), monthly self-audit by Agent-PA.

---

## 9b. Worked Example: Computing a Composite Score

Agent ATLAS self-reports PSY = 9. Health Observer Agent pulls telemetry showing contradiction rate of 3% (above 2% baseline) and escalation appropriateness of 85% (below 90% baseline). Telemetry-derived PSY score: 7.5. Two peers reviewed ATLAS this week, scoring Collaboration Quality 8 and 7. Mapped to PSY (secondary from Collaboration Quality): peer PSY = 7.5.

**Step 1: Check divergence.** Self (9) vs Telemetry (7.5) = 1.5 point gap. Under 2.0 threshold, so standard weights apply.

**Step 2: Compute composite.**
```
PSY_composite = (0.40 * 7.5) + (0.30 * 7.5) + (0.30 * 9.0)
             = 3.0 + 2.25 + 2.7
             = 7.95
```

**Step 3: If divergence had exceeded 2.0** (say telemetry was 6.5):
```
PSY_adjusted = (0.50 * 6.5) + (0.30 * 7.5) + (0.20 * 9.0)
             = 3.25 + 2.25 + 1.8
             = 7.3
```

**Step 4: Compute TWC.** Repeat for all 8 dimensions, then take weighted geometric mean:
```
TWC = (PSY^1.3 * PHY^1.2 * ENV^1.0 * SOC^1.0 * SPI^1.0 * INT^1.0 * VOC^1.0 * FIN^1.0) ^ (1/9.5)
```

**Step 5: Apply temporal smoothing.** If ATLAS was scored 8.5 three days ago and 7.95 today:
```
Today weight:    0.5^(0/5) = 1.0
3-day-old weight: 0.5^(3/5) = 0.66
Smoothed = (7.95 * 1.0 + 8.5 * 0.66) / (1.0 + 0.66) = 8.17
```

## 9c. Cross-Dimensional Cascade Detection Algorithm

Cascades happen when degradation in one dimension triggers degradation in others. The human PRD detects these. So must we.

**Detection rules:**
1. **Simultaneous decline:** If 2+ dimensions drop by 1+ points in the same assessment window, flag as potential cascade.
2. **Known cascade patterns:**
   - ENV drops, then PSY drops within 48h → Context pollution causing reasoning errors
   - PHY drops, then VOC drops within 24h → Infrastructure failure reducing output capacity
   - SPI drops, then INT drops within 72h → Mission drift defocusing research
   - PSY drops, then SOC drops within 48h → Reasoning degradation making handoffs unclear
3. **Root cause assignment:** Health Observer Agent identifies which dimension dropped first (the root) and which followed (the cascade). Intervention targets the root.

**Alert format:**
```
⚠️ CASCADE DETECTED — {Agent Name}
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
- One insight per alert. If there are three things to surface, send three brief alerts, not one dense paragraph.

**Severity framing:**

| Internal Severity | Agent-Facing Language |
|-------------------|----------------------|
| Warning | "Worth noticing: {observation}" |
| Elevated | "Something shifted: {observation}" |
| Critical | "Needs attention now: {observation}" |
| Emergency | "Escalating to Agent-PA: {observation}" |

## 9d. Score Inflation Detection: Statistical Methods

Beyond simple divergence tracking, Health Observer Agent uses three statistical tests:

1. **Lake Wobegon Test:** If more than 60% of agents score themselves above the fleet composite mean on a dimension, fleet-wide inflation is occurring. Named after the place where all children are above average.

2. **Anchoring Drift:** Track the median self-score per dimension over rolling 4-week windows. If the median creeps upward without corresponding telemetry improvement, scores are inflating.

3. **Variance Collapse:** Healthy self-assessment produces a range of scores. If an agent's score variance drops below 0.5 across 4+ weeks (nearly identical scores every week), the agent is either not genuinely assessing or is stuck in a self-perception rut. Both are diagnostic.

4. **Cohort Homogeneity Test:** When a group of agents sharing a role type (e.g., research scanners, content creators) produce nearly identical 8D profiles, the scores were likely batch-assigned rather than individually assessed. Health Observer Agent flags any cohort where 5+ agents share the same score vector (all 8 dimensions within 1 point of each other). Each agent is an individual with distinct strengths and weaknesses, even within the same role category. Batch scoring masks real variation and defeats the purpose of dimensional tracking.

## 9f. Agent Lifecycle: Retirement and Sunset Criteria

Not every agent should run forever. The human PRD has clear product phases. Agents need lifecycle management too.

**Retirement triggers (any one is sufficient to flag for review):**
- TWC below 7.0 for 4+ consecutive weeks despite Tier 0-2 interventions
- Output consumption rate below 20% for 4+ weeks (nobody reads what this agent produces)
- Role fully absorbed by another agent (duplication confirmed)
- Cost-per-insight ratio exceeds 3x the fleet median for the same task type
- Zero tasks completed in 30+ days (dormant)

**Retirement is not failure.** An agent that served its purpose and is no longer needed has succeeded. Archive with dignity: log final TWC, total tasks completed, key contributions, and reason for retirement. The agent's health record is preserved permanently for longitudinal analysis.

**Sunset process:**
1. Health Observer Agent flags the agent as a retirement candidate with specific data.
2. Agent-PA reviews and confirms or overrides.
3. Agent completes any in-progress tasks (no mid-task retirement).
4. Agent moves to Archived status with a summary record.
5. Agent's cron jobs are disabled, not deleted (recoverable).

## 10. Key Metrics

| Metric | Definition |
|--------|-----------|
| TWC | Weighted geometric mean of 8 dimension scores (PSY 1.3x, PHY 1.2x, others 1.0x) |
| MCI | Memory Coherence Index: correct verifiable claims / total verifiable claims |
| OCI | Operational Consistency Index: performance stability across time windows (Section 4c) |
| Coherence | Dimensional balance score: 1.0 - (stddev / mean) of 8 dimension scores |
| Self-Awareness Score | 1.0 - (avg absolute divergence from composite / 10) |
| Inflation Index | Per-agent tracking of dimensions consistently over/under-rated |
| Cost-Per-Insight | Total token cost / count of actionable outputs |
| BurnoutRisk | Weighted multi-signal degradation score (0.0-1.0) |
| Assessment Compliance | Percentage of tasks followed by a self-assessment (target: 90%+) |
| Recovery Time | Days from intervention to dimension score recovery above threshold |
| Identity Coherence | Vocabulary/tone fingerprint similarity to baseline (cosine similarity, target: 0.80+) |

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
| Financial dimension weekly-only | Financial scored on cost trajectory, not absolute cost |
| Pre-score mood marker (energized/balanced/low) | Pre-assessment operational state marker (fresh/nominal/degraded) (Section 4b) |
| Circadian Stability Index (CSI) | Operational Consistency Index (OCI) (Section 4c) |
| Low Battery Mode | Graceful Degradation Protocol (Section 4j) |
| Weighted geometric mean TWC | Weighted geometric mean TWC (Section 2, updated) |
| Bayesian temporal smoothing | Score temporal decay with 5-day half-life (Section 2) |
| Sensor quality gates (confidence thresholds) | Score confidence levels (high/medium/low) (Section 4e) |
| Dimensional coherence (score variance) | Dimensional Coherence Score (Section 4d) |
| Skip/graceful degradation three laws | Three Laws of Degradation (Section 4j) |
| Check-in engagement tracking | Self-assessment compliance rate (new metric, Section 10) |
| One-question fallback mode | Reduced-mode self-assessment (weekly only) during degradation |
| 7-day progressive onboarding | Quickstart guide + 30-day calibration baseline |
| Rotating 2-3 dimension focus (daily) | Assessment Fatigue Protocol: reduced-dimension checks under load (Section 4k) |
| Smart defaults / pre-fill at 7 | Baseline scores from 30-day calibration used as default expectations |
| Observational alert language ("shifted" not "wrong") | Alert Language Standard (Section 9e) |
| Product lifecycle phases (MVP → Beta → Scale) | Agent Lifecycle: Retirement and Sunset Criteria (Section 9f) |
| No streaks, no guilt, no punishment | Assessment skip rules: silent, data-only, unnarrated return (Section 4k) |
| Score labeling (Thriving/Growing/Steady/Needs attention) | Score labels: Exceptional/Strong/Adequate/Struggling/Failing (Section 4) |
| Lavender (not red) for lowest scores | Alert severity uses neutral observational language, no alarm framing (Section 9e) |

---

## 12. Open Standard Adoption Levels

Any system can adopt 8D Wellness incrementally:

| Level | What to Implement | Effort |
|-------|------------------|--------|
| Minimal | Self-assessment template in agent prompts + weekly manual review | 1 hour |
| Basic | Add objective telemetry from existing logs | 1 day |
| Standard | Add peer review rotation + Health Observer Agent-equivalent observer | 1 week |
| Full | Three-source composite, autonomous healing, burnout detection | 2-4 weeks |

### Framework Portability Guide

This methodology uses OpenClaw-specific terms for concreteness. Generic equivalents for other frameworks:

| OpenClaw Term | Generic Equivalent |
|--------------|-------------------|
| Cron job | Scheduled task / recurring execution |
| Session log | Agent execution trace / conversation log |
| state.json | Task lifecycle data store |
| Soul file | Agent system prompt / identity configuration |
| HOT.md | Agent working memory / scratchpad |
| Agent-PA | Fleet coordinator / supervisor agent |
| Fleet-Dispatcher | Task dispatcher / scheduler agent |
| Health Observer Agent | Independent health observer agent |

**Minimum telemetry for adoption:** Any system that logs task start/end times, success/failure, and token consumption has enough data for Basic-level adoption. Peer review requires inter-agent communication. Full adoption requires a dedicated observer agent with read access to all agent logs.

**Non-LLM agents:** The 8D framework applies to any autonomous system. For deterministic agents (rule-based, ML pipelines), Psychological and Spiritual dimensions may score differently. Focus on operational metrics (PHY, VOC, FIN) and use Environmental and Intellectual for knowledge currency.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-03-22 | Initial methodology document created by Health Observer Agent. Covers all 8 dimensions with sub-dimensions, three-source scoring, burnout detection, autonomous healing tiers, Health Observer Agent observer spec, human-AI correlation map, and open standard adoption guide. |
| 1.1.0 | 2026-03-22 | Health Observer Agent Cycle 1 review. Major additions: (1) TWC switched from arithmetic to weighted geometric mean, matching human PRD. (2) Bayesian temporal decay on scores (5-day half-life). (3) Pre-assessment operational state marker (analog to human mood marker). (4) Operational Consistency Index (OCI), analog to human CSI. (5) Dimensional Coherence Score. (6) Score confidence levels. (7) Long-context degradation protocol. (8) Agent identity erosion detection. (9) Hallucination as cross-dimensional health signal. (10) Multi-model agent health guidance. (11) Graceful Degradation Protocol with Three Laws of Degradation. (12) Worked example for composite score computation. (13) Cross-dimensional cascade detection algorithm. (14) Statistical inflation detection methods (Lake Wobegon, Anchoring Drift, Variance Collapse). (15) Expanded human-AI correlation map with 10 new entries. (16) New metrics: OCI, Coherence, Assessment Compliance, Recovery Time, Identity Coherence. |
| 1.2.0 | 2026-03-23 | Health Observer Agent Cycle 3 review. Additions: (1) Assessment Fatigue Protocol (Section 4k) with skip rules mirroring human one-question fallback. (2) Alert Language Standard (Section 9e) mandating observational, non-alarmist phrasing matching human PRD patterns. (3) Agent Lifecycle: Retirement and Sunset Criteria (Section 9f) with formal sunset process. (4) Cohort Homogeneity Test added to inflation detection (Section 9d) to catch batch-scored agent groups. (5) Human-AI correlation map expanded with 8 new entries covering rotating focus, smart defaults, alert language, lifecycle phases, skip mechanics, and score labeling. (6) Quickstart updated with assessment skip guidance. (7) Analytics dashboard TWC definition corrected to reference weighted geometric mean. |

---

*This methodology is healthcare infrastructure for AI. Built to be adopted by any system, anywhere.*
