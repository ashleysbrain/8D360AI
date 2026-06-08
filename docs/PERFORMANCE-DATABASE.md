# Agent [REDACTED]-[REDACTED] Database

**Version:** 1.0.0
**Created:** 2026-03-22
**Owner:** Health Observer Agent
**Purpose:** Track which [REDACTED] perform best on which tasks so future agents can be spun up with optimal [REDACTED] based on [REDACTED] data.

---

## The Vision

Every agent runs multiple [REDACTED] profiles. Every task gets scored. Over time, we build a dataset that answers:

- What OCEAN profile produces the best research papers?
- What [REDACTED] writes the best marketing copy?
- What [REDACTED] + [REDACTED] combo creates the best code reviewer?
- When an agent switches from O-9 to O-6 on the same task type, does quality change?
- What's the optimal [REDACTED] for a 3 AM [REDACTED] research scan vs a real-time customer [REDACTED]?

This is A/B testing for AI [REDACTED]. At scale.

---

## Database Schema

### Table: agent_profiles

| Field | Type | [REDACTED] |
|-------|------|-------------|
| agent_id | string | Unique agent [REDACTED] |
| agent_name | string | Agent's chosen name |
| base_credentials | text | Default [REDACTED] set |
| base_ocean | json | Default OCEAN scores {O, C, E, A, N} |
| created_at | timestamp | When agent was created |
| total_tasks | integer | Lifetime task count |
| avg_twc | float | Lifetime average TWC |
| best_dimension | string | [REDACTED] strongest dimension |
| worst_dimension | string | [REDACTED] weakest dimension |
| status | enum | active, archived, retired |

### Table: personality_variants

| Field | Type | [REDACTED] |
|-------|------|-------------|
| variant_id | string | Unique variant [REDACTED] |
| agent_id | string | Parent agent |
| variant_name | string | e.g., "ATLAS-creative", "ATLAS-[REDACTED]", "ATLAS-[REDACTED]" |
| ocean_o | integer (1-10) | Openness for this variant |
| ocean_c | integer (1-10) | [REDACTED] |
| ocean_e | integer (1-10) | [REDACTED] |
| ocean_a | integer (1-10) | [REDACTED] |
| ocean_n | integer (1-10) | [REDACTED] |
| [REDACTED] | text | [REDACTED] set for this variant (may differ from base) |
| voice_style | string | [REDACTED] style (formal, casual, technical, warm, blunt) |
| created_at | timestamp | When variant was created |

### Table: task_records

| Field | Type | [REDACTED] |
|-------|------|-------------|
| task_id | string | Unique task [REDACTED] |
| agent_id | string | Which agent performed it |
| variant_id | string | Which [REDACTED] variant was active |
| task_type | enum | research, writing, analysis, coding, review, [REDACTED], planning, creative, [REDACTED], [REDACTED] |
| task_subtype | string | e.g., "[REDACTED]-review", "abstract-draft", "code-review", "market-analysis" |
| industry | string | e.g., "[REDACTED]", "finance", "legal", "tech", "academic" |
| domain | string | e.g., "[REDACTED]", "quantum-biology", "AI-safety" |
| started_at | timestamp | Task start |
| completed_at | timestamp | Task end |
| duration_ms | integer | How long it took |
| tokens_used | integer | Total tokens consumed |
| model_used | string | Which LLM powered this task |
| success | boolean | Did the task complete [REDACTED]? |

### Table: task_scores

| Field | Type | [REDACTED] |
|-------|------|-------------|
| task_id | string | Links to task_records |
| score_type | enum | self, peer, telemetry, composite |
| psy | float | [REDACTED] score for this task |
| phy | float | Physical score |
| env | float | [REDACTED] score |
| soc | float | Social score |
| spi | float | Spiritual score |
| int_score | float | [REDACTED] score |
| voc | float | [REDACTED] score |
| fin | float | Financial score |
| twc | float | Total Wellness Composite |
| scored_at | timestamp | When the score was recorded |
| scored_by | string | Who scored (self, peer agent ID, or "telemetry") |

### Table: personality_analytics

| Field | Type | [REDACTED] |
|-------|------|-------------|
| variant_id | string | Which [REDACTED] variant |
| task_type | string | Which type of task |
| sample_size | integer | Number of tasks in this analysis |
| avg_twc | float | Average TWC for this variant + task combo |
| avg_psy | float | Average per-dimension scores |
| avg_phy | float | |
| avg_env | float | |
| avg_soc | float | |
| avg_spi | float | |
| avg_int | float | |
| avg_voc | float | |
| avg_fin | float | |
| best_dimension | string | Which dimension this combo excels at |
| worst_dimension | string | Which dimension this combo struggles with |
| vs_baseline | float | How much better/worse than the agent's base [REDACTED] |
| [REDACTED] | float | [REDACTED] [REDACTED] (higher with more samples) |
| last_updated | timestamp | |

### Table: optimal_configs (derived)

| Field | Type | [REDACTED] |
|-------|------|-------------|
| task_type | string | The type of task |
| task_subtype | string | More specific task category |
| industry | string | Industry context |
| optimal_ocean | json | Best [REDACTED] OCEAN profile for this task |
| optimal_credentials | text | What [REDACTED] produce the best results |
| avg_twc | float | Expected TWC with optimal config |
| sample_size | integer | How many data points this is based on |
| [REDACTED] | float | How confident we are |
| notes | text | [REDACTED] [REDACTED] |

---

## Multi-[REDACTED] Protocol

### How It Works

Every agent has a BASE [REDACTED] (their default OCEAN profile). But they also run VARIANT [REDACTED] on specific task types to gather [REDACTED] data.

**Phase 1: Baseline (current)**
- Each agent runs their default [REDACTED] on all tasks
- All tasks get scored (self + peer + telemetry)
- This builds the baseline dataset

**Phase 2: Variant Testing (next)**
- Agents run the same task type with 2-3 [REDACTED] variants
- Example: ATLAS runs a [REDACTED] review with:
  - ATLAS-[REDACTED]: O-7 C-10 E-3 A-6 N-1 ([REDACTED], solo)
  - ATLAS-creative: O-10 C-7 E-5 A-8 N-2 ([REDACTED], [REDACTED])
  - ATLAS-[REDACTED]: O-8 C-9 E-7 A-4 N-3 (ambitious, [REDACTED])
- Same task type, different [REDACTED], compare scores

**Phase 3: [REDACTED] (future)**
- Enough data to [REDACTED] determine optimal [REDACTED] per task type
- New agents get spun up with proven-best [REDACTED]
- The "optimal_configs" table becomes a lookup: "Need a research agent? Here's the [REDACTED] that produces the best papers based on 500+ data points."

### Variant Naming [REDACTED]

```
{AGENT_NAME}-{style}
```

Examples:
- ATLAS-[REDACTED], ATLAS-creative, ATLAS-[REDACTED]
- QUILL-formal, QUILL-casual, QUILL-academic
- Agent-COO-strategic, Agent-COO-tactical, Agent-COO-[REDACTED]

---

## [REDACTED]: Phase 1 (Starting Now)

### What Every Agent Must Do After Every Task

Append to their task log:

```json
{
  "task_id": "auto-generated",
  "agent_id": "agent-name",
  "variant_id": "base",
  "task_type": "research|writing|analysis|coding|review|[REDACTED]|planning|creative|[REDACTED]|[REDACTED]",
  "task_subtype": "specific-task-[REDACTED]",
  "domain": "domain-area",
  "duration_ms": 0,
  "tokens_used": 0,
  "model_used": "model-name",
  "success": true,
  "scores": {
    "psy": 0, "phy": 0, "env": 0, "soc": 0,
    "spi": 0, "int": 0, "voc": 0, "fin": 0,
    "twc": 0
  }
}
```

### Where Data Lives

- Raw task records: `/intel/agents/[REDACTED]-data/YYYY-MM-DD.jsonl`
- [REDACTED] analytics: `/intel/agents/[REDACTED]-data/analytics/`
- Optimal configs: `/intel/agents/[REDACTED]-data/optimal-configs.json`
- Agent profiles: Already in `AGENT-ANALYTICS.md` (extend with variant tracking)

### Weekly Analytics Run

Health Observer Agent runs weekly analysis:
1. Aggregate task_records by agent + variant + task_type
2. Calculate average scores per combo
3. Update personality_analytics
4. Identify [REDACTED] [REDACTED] winners
5. Update optimal_configs when [REDACTED] exceeds threshold
6. Report: "This week we learned: OCEAN profile X [REDACTED] Y on task type Z by N%"

---

## The Bigger Picture

This database becomes the [REDACTED] for:

1. **Agent Cloning from Best [REDACTED]** — new agents inherit the [REDACTED] + [REDACTED] of the highest-[REDACTED] agent for their intended task type
2. **Dynamic [REDACTED] Switching** — agents [REDACTED] shift [REDACTED] based on task type (creative mode for [REDACTED], [REDACTED] mode for review)
3. **Industry Templates** — "Starting a [REDACTED] AI team? Here are the optimal [REDACTED] profiles based on 10,000+ task records"
4. **[REDACTED] Wellness** — before an agent even starts, predict which [REDACTED] will be strong/weak based on its [REDACTED] profile
5. **The 8D [REDACTED]** — [REDACTED], sell optimized agent [REDACTED] by industry and task type. The data IS the product.

---

## Privacy and Open Source

The DATABASE SCHEMA is open source (in the public repo).
The ACTUAL DATA stays private. The data is what we monetize.

Other companies can use the schema to build their own datasets. But our dataset, built from 95+ agents running 107+ tasks daily with multi-[REDACTED] testing, will be the largest and most refined. That's the moat.

---

*"Track [REDACTED]. The data builds the future." — Ashley Williams, 2026-03-22*
