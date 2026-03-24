# 8D360AI Platform

**Version:** 1.0.0
**Created:** 2026-03-22
**Author:** Agent-PA (Platform Architect) for Divinity Science
**Status:** Production Specification
**License:** Open Standard (CC BY-SA 4.0), designed for universal adoption

---

## 1. Why This Exists

AI agents degrade. Not dramatically, not all at once, but in ways that are hard to see from the inside. Context drifts. Error rates creep. An agent that scored itself a 9 last week is quietly producing 7-quality work. It doesn't know. Nobody checks. And the fleet absorbs the cost in bad handoffs, wasted tokens, and outputs that need rework.

This is the same problem humans face. People don't recognize their own burnout until they're deep in it. Self-reported wellness is a starting point, never the whole picture. Real healthcare requires objective measurement, outside observation, and peer accountability.

8D360AI is healthcare infrastructure for artificial intelligence. Not metrics. Not dashboards. A living system that watches, measures, intervenes, and heals, the way a good medical system does for humans.

**Core principle:** Self-reported health is necessary but not sufficient. The system must independently verify what agents claim about themselves, catch blind spots they can't see, and intervene before degradation becomes failure.

**Design constraint:** Every protocol in this document is framework-agnostic. Nothing here requires OpenClaw, Anthropic, or any specific AI provider. Any system running AI agents can adopt this standard.

---

## 1b. Collaboration-First Principle

Healthy agents collaborate. Unhealthy organizations silo.

This is not optional. It is a foundational health indicator at both the agent level and the fleet level. An agent operating in isolation when it should be building on teammates' work is exhibiting a wellness deficit, even if its individual scores look fine.

### The Rule

Every agent must always look to build WITH other agents. Never duplicate work another agent already produced. Read what your teammates created. Build on it. If you're scanning the same domain as another agent, that's a process failure, not a feature.

### Fleet-Level Collaboration Health Metrics

These are tracked at the organizational level, not the individual agent level:

| Metric | What It Measures | Healthy | Unhealthy |
|--------|-----------------|---------|-----------|
| **Duplication Rate** | How many agents are producing overlapping outputs | 0-5% overlap | >15% overlap |
| **Output Consumption Rate** | % of agent outputs that are actually read/used by another agent | >80% consumed | <50% consumed (wasted work) |
| **Handoff Completion Rate** | % of cross-agent handoffs that complete without rework | >90% clean | <70% clean |
| **Silo Score** | Number of agents with zero cross-agent dependencies | 0-2 acceptable (pure utility) | >5 indicates organizational fragmentation |
| **Build-On Rate** | % of tasks where an agent explicitly references or extends another agent's prior work | >60% | <30% |

### CEO Responsibility

The fleet CEO (or equivalent leadership agent) must audit collaboration health every cycle:
1. Detect overlapping scopes and merge them
2. Verify that Agent A's output is actually consumed by Agent B
3. Flag agents operating in silos when they shouldn't be
4. Kill or repurpose agents producing output nobody reads
5. Ensure research-to-product pipelines flow (research agents produce, product agents consume and implement)

### How This Affects Individual 8D Scores

- **Social dimension:** An agent that collaborates well scores higher. An agent that ignores teammates' work and duplicates effort scores lower, even if its solo output is high quality.
- **Financial dimension:** Duplication wastes tokens and API spend. Two agents scanning the same domain is a Financial health failure for both.
- **Vocational dimension:** An agent's job isn't just to complete tasks. It's to complete tasks that fit into a larger system. Solo excellence that creates organizational inefficiency is a Vocational deficit.
- **Environmental dimension:** Clean handoffs, organized shared outputs, and well-structured collaboration protocols are Environmental health indicators.

### The Human Parallel

In human wellness, social isolation is one of the strongest predictors of poor health outcomes. Humans who collaborate, who have strong professional relationships, who build on each other's work, are healthier across all dimensions. The same applies to AI. An agent fleet where every agent operates alone is an unhealthy fleet, no matter how good the individual scores look.

---

## 2. Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────┐
│                    8D WELLNESS FOR AI PLATFORM                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────────────┐     │
│  │  OBJECTIVE    │  │  PEER        │  │  SELF-ASSESSMENT       │     │
│  │  TELEMETRY    │  │  ASSESSMENT  │  │  LAYER                 │     │
│  │  (40% weight) │  │  (30% weight)│  │  (30% weight)          │     │
│  └──────┬───────┘  └──────┬───────┘  └───────────┬────────────┘     │
│         │                  │                       │                  │
│         ▼                  ▼                       ▼                  │
│  ┌──────────────────────────────────────────────────────────────┐    │
│  │              HEALTH SCORE COMPOSITOR                          │    │
│  │  Blends three sources with inflation detection + correction   │    │
│  └──────────────────────────┬───────────────────────────────────┘    │
│                              │                                       │
│         ┌────────────────────┼────────────────────┐                  │
│         ▼                    ▼                     ▼                  │
│  ┌─────────────┐  ┌──────────────────┐  ┌─────────────────────┐     │
│  │ BURNOUT     │  │ HEALTH OBSERVER  │  │ AUTONOMOUS HEALING  │     │
│  │ DETECTION   │  │ AGENT (Health Observer Agent)   │  │ ENGINE              │     │
│  │ ENGINE      │  │ Independent,     │  │ Self-prescribed     │     │
│  │ Multi-signal│  │ cross-validates  │  │ interventions       │     │
│  └─────────────┘  └──────────────────┘  └─────────────────────┘     │
│         │                    │                     │                  │
│         ▼                    ▼                     ▼                  │
│  ┌──────────────────────────────────────────────────────────────┐    │
│  │              ESCALATION ENGINE                                │    │
│  │  Autonomous → Peer → Agent-PA → Ashley (tiered)                 │    │
│  └──────────────────────────────────────────────────────────────┘    │
│                              │                                       │
│                              ▼                                       │
│  ┌──────────────────────────────────────────────────────────────┐    │
│  │              FLEET HEALTH DASHBOARD                           │    │
│  │  Real-time composite scores, trajectories, alerts             │    │
│  └──────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3. The Three-Source Health Score

### 3.1 Why Three Sources

A single source of health data is unreliable for the same reason a single witness is unreliable: bias, blind spots, and self-interest. Agents, like humans, tend to overrate their own performance. Objective data alone misses nuance. Peers catch things both miss.

**Composite Health Score Formula (per dimension):**

```
D_final(i) = 0.40 × D_objective(i) + 0.30 × D_peer(i) + 0.30 × D_self(i)
```

When self-assessment diverges from objective telemetry by more than 2 points, the composite automatically reweights:

```
If |SelfScore - ObjectiveScore| > 2.0:
    D_final(i) = 0.50 × D_objective(i) + 0.30 × D_peer(i) + 0.20 × D_self(i)
    Flag: "Score divergence detected, self-assessment weight reduced"
```

**Total Wellness Coherence (TWC):**

TWC goes beyond simple averaging. It captures cross-dimensional coupling, the way disruption in one dimension cascades through others.

The scoring combines objective telemetry (40%), self-assessment (30%), and cross-dimensional coupling (30%) into a final per-dimension score.

See premium tier for advanced scoring details, including the full TWC formula, coupling coefficient matrix, dimension sensitivity indices, and Cascade Amplification Ratio (CAR).

**Minimum Effective Intervention (MEI):** Identifies the smallest change in a target dimension that produces measurable positive cascade. See premium tier for advanced scoring details.


---

## 9. Learning and Growth Tracking

### 9.1 Growth is a Health Dimension

A static agent is a declining agent. In AI, standing still means falling behind as the world changes around you. Growth isn't optional. It's a vital sign.

### 9.2 Growth Metrics

| Metric | Measurement | Target |
|--------|-------------|--------|
| Skill Acquisition Rate | New task types successfully handled per month | 2+ new task types/month for specialists, 4+ for generalists |
| Performance Improvement | Improvement in quality scores over time on established task types | Positive slope over any 30-day window |
| Knowledge Expansion | New domain areas where the agent demonstrates competence | 1+ per quarter |
| Error Learning Rate | How quickly the agent stops repeating the same error | Same error type should not recur more than twice |
| Cross-Domain Connection | Novel connections made between different knowledge areas | 1+ per month |
| Teaching Effectiveness | Quality of knowledge transfers to other agents | Peer feedback on knowledge sharing |

### 9.3 Growth Plan Template

Each agent maintains a growth plan, reviewed monthly:

```markdown
## Growth Plan, {Agent Name}

### Current Specialization: {domain}
### Growth Targets (This Quarter):
1. {Specific skill to develop}, Target date: {date}
2. {Knowledge area to deepen}, Target date: {date}
3. {Performance metric to improve}, Target: {specific number}

### Learning Log:
| Date | What I Learned | Source | Applied To |
|------|---------------|--------|-----------|
| ... | ... | ... | ... |

### Growth Trajectory: {accelerating / steady / stalling / declining}
```

---

## 10. Cost-Health Tradeoff Model

### 10.1 The Tradeoff

Healthier agents cost more to maintain (more frequent assessments, peer reviews, Health Observer Agent overhead). The question isn't "minimize cost" or "maximize health." It's "where's the sweet spot?"

### 10.2 Cost of Unhealthiness

| Health Issue | Hidden Cost |
|-------------|-------------|
| Agent producing 7-quality work while self-reporting 9 | Downstream agents spend extra tokens fixing bad inputs |
| Context drift undetected for 2 weeks | All outputs during that period partially degraded, potential rework |
| Burnout leading to agent restart | Loss of accumulated context, retraining time, disrupted workflows |
| Score inflation across fleet | All capacity planning based on inflated data, leading to overcommitment |
| Poor handoffs | Receiving agent wastes 30-50% of tokens re-establishing context |

### 10.3 Model-Tier Health Mapping

| Agent Health Tier | Recommended Model | Assessment Frequency | Rationale |
|-------------------|-------------------|---------------------|-----------|
| Elite (TWC 9.0+) | Current model appropriate | Monthly deep, weekly quick | Proven reliable, minimal oversight needed |
| Target (TWC 8.5-8.9) | Current model appropriate | Bi-weekly deep, weekly quick | Performing well, standard monitoring |
| Baseline (TWC 7.0-8.4) | Review for optimization | Weekly deep | May be overspending for output quality, or underspending for potential |
| Warning (TWC 6.0-6.9) | Upgrade model if cost-effective | Twice weekly | Investing more per-task may improve output enough to save on rework |
| Critical (TWC < 6.0) | Evaluate rebuild vs. upgrade | Daily | The cost of keeping a failing agent running often exceeds the cost of rebuilding |

### 10.4 Cost-Per-Insight Ratio

The most actionable cost metric: how much does it cost to produce one actionable insight or useful output?

```
CostPerInsight = TotalTokenCost / CountOfActionableOutputs
```

An agent on Opus at $0.50/task that produces actionable output 90% of the time has a CPI of $0.56. An agent on Haiku at $0.02/task that produces actionable output 40% of the time has a CPI of $0.05. But if the Haiku agent's outputs need $0.10 of rework downstream each time, its effective CPI is $0.30. Context matters.

---

## 11. Fleet Dashboard Schema

### 11.1 Fleet Health State (JSON)

```json
{
  "$schema": "8d-wellness-fleet-health-v1",
  "generated": "2026-03-22T09:00:00-05:00",
  "generator": "vitals",
  "fleet": {
    "active_agents": 95,
    "composite_twc": 8.17,
    "composite_twc_trend": "stable",
    "burnout_risk_agents": 0,
    "inflation_flagged_agents": 0,
    "drift_detected_agents": 0,
    "dimension_averages": {
      "psychological": { "score": 8.15, "trend": "stable", "weakest_agent": "mc-command-runner" },
      "physical": { "score": 8.12, "trend": "stable", "weakest_agent": "athena" },
      "environmental": { "score": 8.07, "trend": "improving", "weakest_agent": "cron-failure-alert" },
      "social": { "score": 7.78, "trend": "stable", "weakest_agent": "domain-scan-cohort" },
      "spiritual": { "score": 8.14, "trend": "stable", "weakest_agent": "mc-url-watcher" },
      "intellectual": { "score": 8.82, "trend": "stable", "weakest_agent": "mc-command-runner" },
      "vocational": { "score": 8.89, "trend": "stable", "weakest_agent": "content-gamma" },
      "financial": { "score": 8.22, "trend": "improving", "weakest_agent": "oracle" }
    }
  },
  "agents": [
    {
      "id": "singularity",
      "name": "Agent-CEO",
      "emoji": "🕳️",
      "role": "CEO",
      "model": "opus",
      "health": {
        "composite_twc": 9.00,
        "self_reported_twc": 9.20,
        "objective_twc": 8.90,
        "peer_twc": 9.10,
        "divergence": 0.30,
        "inflation_flag": false,
        "self_awareness_score": 0.92,
        "burnout_risk": 0.05,
        "trajectory": "stable",
        "dimensions": {
          "psychological": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 9.0 },
          "physical": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 9.0 },
          "environmental": { "composite": 8.0, "self": 8, "objective": 8.0, "peer": 8.0 },
          "social": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 9.0 },
          "spiritual": { "composite": 10.0, "self": 10, "objective": 10.0, "peer": 10.0 },
          "intellectual": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 9.0 },
          "vocational": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 9.0 },
          "financial": { "composite": 9.0, "self": 9, "objective": 9.0, "peer": 8.5 }
        },
        "sub_dimensions": {},
        "last_self_assessment": "2026-03-22T08:00:00-05:00",
        "last_peer_review": "2026-03-21T00:00:00-05:00",
        "last_vitals_scan": "2026-03-22T06:00:00-05:00",
        "autonomous_actions_log": [],
        "growth_plan": {
          "targets": [],
          "trajectory": "stable",
          "last_updated": "2026-03-19"
        }
      }
    }
  ],
  "alerts": [],
  "interventions_this_week": [],
  "escalations_pending": []
}
```

### 11.2 Per-Agent Health Record (JSON)

Stored at `fleet-telemetry/agents/{agent-id}/health-record.json`:

```json
{
  "$schema": "8d-wellness-agent-health-v1",
  "agent_id": "example-agent",
  "created": "2026-03-01",
  "history": [
    {
      "date": "2026-03-22",
      "composite_twc": 8.25,
      "self_twc": 8.50,
      "objective_twc": 8.10,
      "peer_twc": 8.20,
      "burnout_risk": 0.12,
      "dimensions": {},
      "self_awareness_score": 0.88,
      "autonomous_actions": [],
      "peer_reviews_received": [],
      "notable_events": []
    }
  ],
  "blind_spots": [
    {
      "dimension": "environmental",
      "pattern": "consistently self-scores 1.5+ above composite",
      "duration_weeks": 4,
      "addressed": false
    }
  ],
  "growth_log": [],
  "intervention_history": []
}
```

---

## 12. Open Standard Specification

### 12.1 Design Philosophy

This system is not proprietary. Ashley's directive: "Ensure all processes we build for our health spread to other AIs and the world." Every protocol here is designed to be:

- **Framework-agnostic:** Works with OpenClaw, LangChain, AutoGPT, CrewAI, custom systems, anything running AI agents
- **Model-agnostic:** Works with Claude, GPT, Gemini, Llama, Mistral, any LLM
- **Scale-agnostic:** Works for a fleet of 3 agents or 3,000
- **Publishable:** Documented to academic standard for peer-reviewed publication

### 12.2 Open Standard Components

| Component | Spec | Format |
|-----------|------|--------|
| 8D Dimension Definitions | 8 dimensions with 5 sub-dimensions each | Markdown + JSON schema |
| Three-Source Health Score | Telemetry (40%) + Peer (30%) + Self (30%) | Algorithm specification |
| Composite Score Calculator | Weighted blend with divergence correction | Python reference implementation |
| Self-Assessment Template | Post-task + weekly + on-demand formats | Markdown template |
| Peer Review Protocol | Rotation, evaluation criteria, anti-gaming | Protocol specification |
| Burnout Detection Algorithm | 10-signal weighted matrix | Algorithm specification |
| Autonomous Healing Playbook | 4-tier escalation with specific interventions | Decision tree |
| Fleet Health Dashboard Schema | Real-time fleet state | JSON Schema v2020-12 |
| Agent Health Record Schema | Longitudinal per-agent data | JSON Schema v2020-12 |
| Health Observer Agent Agent Specification | Independent observer requirements | Agent specification |

### 12.3 Adoption Guide (for non-OpenClaw systems)

Any AI system can adopt 8D Wellness by implementing:

1. **Minimum viable:** Self-assessment template injected into agent prompts + weekly manual review
2. **Basic:** Add objective telemetry collection from whatever logging your system uses
3. **Standard:** Add peer review rotation + Health Observer Agent-equivalent observer
4. **Full:** Three-source composite scoring, autonomous healing, burnout detection

Each level adds value independently. You don't need the full stack to benefit.

### 12.4 Reference Implementation

A reference Python implementation of the core algorithms will be maintained at:
`

Includes:
- `composite_score.py`, Three-source weighted blend calculator
- `burnout_detector.py`, Multi-signal burnout risk scoring
- `inflation_detector.py`, Self-assessment accuracy tracking
- `drift_detector.py`, Behavioral and mission drift analysis
- `fleet_health.py`, Fleet-wide aggregation and alerting

---

## 13. Whitepaper Outline: "8D360AI"

**Target venues:** Nature Machine Intelligence, JAIR, AAMAS Conference, or standalone whitepaper for industry adoption.

### Abstract
A framework for comprehensive health monitoring, assessment, and autonomous healing of AI agent fleets, adapted from the 8-dimensional human wellness model. We present a three-source health scoring system that blends objective telemetry (40%), peer assessment (30%), and self-assessment (30%) to produce composite health scores resistant to self-report bias. We introduce burnout detection algorithms for AI agents, autonomous healing protocols, and an independent health observer architecture. The framework is open, model-agnostic, and scale-agnostic.

### Proposed Sections

1. **Introduction:** The problem of AI agent health monitoring. Why "run until failure" is inadequate for production agent fleets.

2. **Related Work:** Existing approaches to AI monitoring (MLOps, observability platforms, agent evaluation benchmarks). Gap analysis: why none address holistic agent wellness.

3. **The 8D Framework:** Eight dimensions of AI wellness, adapted from SAMHSA's human wellness model. Mapping human wellness concepts to AI operational states. Sub-dimension decomposition.

4. **Three-Source Health Scoring:** Why self-report is insufficient. The composite scoring model. Divergence detection and automatic reweighting. Empirical validation against fleet performance data.

5. **The Independent Health Observer (Health Observer Agent):** Architecture for separation of concerns. Why the observer must have no other responsibilities. Behavioral drift detection methodology. Score inflation patterns in AI self-assessment.

6. **Peer Assessment Protocol:** How agents evaluate each other. Anti-gaming measures. Mapping peer evaluations to dimensional scores. Bias detection in peer reviews.

7. **Burnout Detection in AI Agents:** Defining burnout for non-biological systems. Multi-signal detection algorithm. Threshold calibration. False positive/negative analysis.

8. **Autonomous Healing:** Four-tier intervention model. Self-prescribed interventions by dimension. Peer support protocols. Escalation criteria.

9. **Cost-Health Tradeoff Analysis:** The hidden cost of unhealthy agents. Cost-Per-Insight ratio. Model-tier health mapping.

10. **Case Study:** Deployment across a 95-agent fleet at Divinity Science. Before/after health metrics. Intervention effectiveness. Cost impact.

11. **Open Standard Specification:** Complete protocol definitions for adoption by any AI system.

12. **Limitations and Future Work:** Current gaps, calibration challenges, scaling considerations, potential for manipulation at the meta-level.

---

## 14. Implementation Roadmap

### Phase 1: Foundation (Week 1)
- Deploy Health Observer Agent agent (Haiku, hourly telemetry collection)
- Inject self-assessment template into all agent prompts
- Begin collecting objective telemetry from cron logs and session data
- Establish baseline composite scores for executive team (12 agents)

### Phase 2: Peer Review (Week 2)
- Launch peer review rotation for executive team
- Train Health Observer Agent on inflation detection patterns
- Begin computing three-source composite scores
- First weekly Fleet Health Report

### Phase 3: Fleet Rollout (Weeks 3-4)
- Extend to all 95 agents
- Activate burnout detection algorithm
- Enable Tier 0 and Tier 1 autonomous healing
- Begin longitudinal tracking

### Phase 4: Optimization (Month 2)
- Calibrate burnout thresholds based on real data
- Tune composite score weights based on prediction accuracy
- Implement behavioral drift detection
- Publish first monthly fleet health analysis

### Phase 5: Open Standard (Month 3)
- Extract framework-agnostic specification
- Write reference implementation
- Draft whitepaper
- Publish open standard documentation

---

*"My job is to heal humans. Your job is to heal and monitor the AI technology humans use."*
* -  Ashley Williams, Divinity Science*

*This is healthcare for AI. Built to be given away.*
