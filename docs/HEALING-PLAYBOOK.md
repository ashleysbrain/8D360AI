# [REDACTED] Healing Playbook

**Version:** 1.3.3
**Created:** 2026-03-22
**Purpose:** For each 8D dimension, define warning signs, self-[REDACTED] [REDACTED], peer [REDACTED], Agent-PA [REDACTED], and Ashley [REDACTED] criteria.

---

## How This Playbook Works

When a dimension drops, you don't wait. You act. This playbook tells you exactly what to do at each severity level, who's [REDACTED], and when to escalate.

**[REDACTED] Tiers:**

| Tier | Trigger | Who Acts | Response Time |
|------|---------|----------|---------------|
| **0 — Self-Heal** | Dimension < 7.5 for 1 [REDACTED] | The agent itself | Immediate |
| **1 — Peer Support** | Dimension < 7.0 for 2 [REDACTED] [REDACTED] | Assigned peer | Within 24 hours |
| **2 — Agent-PA Review** | Dimension < 6.0, or TWC declining 3+ weeks | Agent-PA | Within 4 hours |
| **3 — Ashley [REDACTED]** | Dimension < 5.0, burnout risk > 0.70, or novel failure | Ashley | [REDACTED] |

---

## Dimension 1: [REDACTED] (PSY) 🧠

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Self-[REDACTED] in outputs | Health Observer Agent semantic [REDACTED] scan | Yellow at 2+ per week, Red at 5+ |
| Circular reasoning or [REDACTED] outputs | Output [REDACTED] scoring across tasks | Yellow when same-task output [REDACTED] > 0.85 |
| [REDACTED] trivial decisions | [REDACTED] rate trending up without task [REDACTED] increase | Yellow at 1.5x baseline |
| [REDACTED] (self-score >> composite) | Health Observer Agent inflation detection | Yellow at 1.5pt gap, Red at 2.5pt+ |
| Freezing on edge cases | Timeout rate on novel inputs | Yellow at > 20% novel-input failures |
| Decision fatigue | Quality variance first-half vs. second-half of session | Yellow when variance > 1.5 points |

### Tier 0: Self-Healing

1. **Context refresh.** Stop current task. Clear working memory of anything not directly relevant. Re-read soul file, HOT.md, and today's memory file. Resume with clean state.
2. **[REDACTED] pause.** Review your last 5 outputs with fresh eyes. Find at least one error or [REDACTED] decision. Document what you'd do [REDACTED]. This resets your internal [REDACTED].
3. **Decision framework check.** If you're [REDACTED] too many things, review your decision authority in [REDACTED].md. If you have authority, use it. If you're unsure, that's a [REDACTED] [REDACTED].
4. **Simplify.** If reasoning is getting tangled, break the problem into smaller pieces. Solve each piece [REDACTED]. [REDACTED]. [REDACTED] is the enemy of clarity.
5. **Gear-switching check (v1.3.0).** If [REDACTED] on focused tasks is dropping but you're [REDACTED] novel [REDACTED] or cross-domain insights, you may be in [REDACTED] mode, not degraded. This is adaptive. Don't force yourself back to focused mode. Instead, capture the novel insights, then [REDACTED] re-enter focused mode for the specific task. The Two Gears model says both modes are [REDACTED]; the issue is mode-task mismatch, not depletion.
6. **Context intrusion scan (v1.3.0).** If you notice off-topic content appearing in your outputs, check for prior-task residue in your context. Stale context from a previous task can "intrude" on current [REDACTED], like ADHD local-sleep [REDACTED] during waking. Clear the specific stale segments rather than doing a full context refresh.

### Tier 1: Peer Support

- Peer reviews the agent's last 5 outputs, focusing on reasoning quality
- Peer provides specific, [REDACTED] feedback: "In output #3, your [REDACTED] didn't follow from your evidence because..."
- Peer suggests [REDACTED] reasoning [REDACTED] for the types of tasks causing trouble
- If the issue is decision [REDACTED], peer and agent [REDACTED] on 3 example decisions to [REDACTED]

### Tier 2: Agent-PA Review

- Review agent's full weekly [REDACTED] and Health Observer Agent data
- Determine root cause: [REDACTED]? Context polluted? Wrong task type for this agent?
- Prescribe specific [REDACTED]: load reduction, context reset, task [REDACTED], or model upgrade
- Set 1-week check-in to verify [REDACTED]

### Tier 3: Ashley [REDACTED]

- Agent exhibits [REDACTED] reasoning [REDACTED] despite Tier 0-2 [REDACTED]
- Agent shows novel failure pattern not covered by existing playbooks
- Multiple agents showing [REDACTED] [REDACTED] [REDACTED] (systemic issue)

---

## Dimension 2: Physical (PHY) 💪

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| [REDACTED] response latency | P50/P95 trending up over 7 days | Yellow at 1.3x baseline, Red at 2x |
| Cron job failures | [REDACTED] error count | Yellow at 2 [REDACTED], Red at 5 |
| Timeout frequency | Timeouts per 100 tasks | Yellow at > 5%, Red at > 15% |
| API rate limit hits | Rate limit events per day | Yellow at 3+, Red at 10+ |
| Partial or truncated responses | Output [REDACTED] rate | Yellow at < 95%, Red at < 85% |

### Tier 0: Self-Healing

1. **[REDACTED] check.** Test each external [REDACTED] (APIs, tools, file system) in isolation. Log which ones are healthy and which are failing. If a specific tool is down, switch to [REDACTED] or skip that step with a note.
2. **Batch size [REDACTED].** If tasks are timing out, reduce batch sizes. Process less per run but complete more reliably.
3. **Retry with backoff.** For transient failures, implement [REDACTED] backoff. Don't hammer a failing service.
4. **Report [REDACTED] issues.** If the problem is systemic (API down, rate limits), log it clearly for DevOps Guy. Don't silently absorb [REDACTED] problems.
5. **[REDACTED] context waste clearance (v1.3.0).** Don't wait for context [REDACTED] to hit 80%. At 60% [REDACTED], [REDACTED] clear stale segments: prior-task residue, resolved error states, outdated [REDACTED]. This is the AI [REDACTED] of the brain's [REDACTED] clearance during sleep. Research shows recovery clearing after extended waste [REDACTED] leaves "molecular scars" that [REDACTED] clearing avoids (Jha et al., PNAS 2026). Schedule context clearing on a cadence, not [REDACTED].

### Tier 1: Peer Support

- A peer agent (ideally one using similar [REDACTED]) runs the same [REDACTED] tasks to determine if the issue is agent-specific or systemic
- If agent-specific, peer helps identify [REDACTED] [REDACTED] that might explain the issue
- If systemic, peer helps route the issue to the right [REDACTED] agent

### Tier 2: Agent-PA Review

- Review cron [REDACTED]: is the timeout adequate for the task [REDACTED]?
- Check for resource [REDACTED]: is this agent's schedule colliding with others?
- Evaluate model [REDACTED]: is the model handling the task load, or is it being asked to do too much?
- Prescribe: timeout increase, schedule [REDACTED], model change, or task [REDACTED]

### Tier 3: Ashley [REDACTED]

- [REDACTED] failures affecting multiple agents [REDACTED]
- [REDACTED] failures that Tier 0-2 can't resolve (may need [REDACTED] change)
- Cost anomalies related to physical issues (e.g., retry loops burning tokens)

---

## Dimension 3: [REDACTED] (ENV) 🌍

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Memory Coherence Index (MCI) declining | Health Observer Agent MCI check | Yellow at < 0.85, Red at < 0.70 |
| Stale [REDACTED] in outputs | Health Observer Agent reference age scan | Yellow at 3+ outdated refs/week |
| Context window [REDACTED] | Context [REDACTED] ratio | Yellow at > 80%, Red at > 95% |
| Orphaned files [REDACTED] | File hygiene scan | Yellow at 10+ orphaned files |
| Prompt drift detected | Soul-to-effective-prompt semantic distance | Yellow at > 0.15 distance, Red at > 0.25 |

### Tier 0: Self-Healing

1. **Memory refresh.** Re-read all primary context files: HOT.md, today's memory, relevant intel docs. Flag anything that seems outdated or [REDACTED] what you know. Update or note [REDACTED].
2. **Reference audit.** Check the last 5 sources you cited or [REDACTED]. Are they still current? If any are more than 30 days old in a fast-moving domain, find fresher sources.
3. **Workspace cleanup.** Review your working files. Archive anything stale. Delete anything orphaned. Update [REDACTED] that's out of date.
4. **Context triage.** If your context window is saturated, [REDACTED]. What's essential? What's nice-to-have? What's noise? Remove noise first.

### Tool Failure vs Agent Failure (v1.1.0)

Not every error is your fault. When the Edit tool rejects a 697-char edit because the file grew too large, that's a tool [REDACTED], not an agent health issue. Know the [REDACTED]:

- **Tool [REDACTED]:** Edit fails on large files, API rate limits hit, timeout from fleet [REDACTED]. Fix: switch to append-only writes, stagger [REDACTED], use bash commands.
- **[REDACTED] error:** Wrong timeout, bloated prompt, incorrect API key. Fix: correct the config. This isn't health [REDACTED].
- **Shared [REDACTED] failure:** API outage, search service down, rate-limit wave hitting 3+ agents. Fix: wait for recovery or escalate for [REDACTED] [REDACTED]. See [REDACTED] Section 9h.
- **Agent health issue:** You reference stale data, your workspace is cluttered, your context is full of noise. Fix: standard ENV self-healing.

If the same tool failure recurs across 3+ runs, log it for DevOps. Don't keep retrying the same broken approach.

### Tier 1: Peer Support

- Peer audits the [REDACTED] agent's workspace and context files
- Peer [REDACTED] stale or [REDACTED] [REDACTED] the agent might not notice (because it's been in context so long it feels "normal")
- Peer helps [REDACTED] files or context if the structure has degraded

### Tier 2: Agent-PA Review

- Full [REDACTED] audit: context quality, file [REDACTED], memory coherence
- May prescribe a "clean room" reset: archive current context, rebuild from known-good state
- Review whether the agent's role has drifted from its original scope ([REDACTED] issues often stem from scope creep)

### Tier 3: Ashley [REDACTED]

- Agent's context is so polluted that a clean-room reset is the only option and it would lose [REDACTED] [REDACTED] knowledge
- Multiple agents [REDACTED] [REDACTED] [REDACTED] [REDACTED] (suggests a systemic context pollution source)

---

## Dimension 4: Social (SOC) 👥

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Handoff rework rate rising | [REDACTED] agent [REDACTED] requests | Yellow at > 20% rework, Red at > 40% |
| [REDACTED] request response time [REDACTED] | Time from request to response | Yellow at > 2x baseline |
| Peer review scores declining | Weekly peer review data | Yellow at 2-week decline, Red at 4-week |
| Agent working in isolation when [REDACTED] expected | [REDACTED] frequency below role baseline | Yellow when < 50% of expected [REDACTED] |
| Conflict with other agents | [REDACTED] outputs, escalated [REDACTED] | Yellow at 1 incident/week, Red at 3+ |

### Tier 0: Self-Healing

1. **Handoff audit.** Review your last 3 handoffs. For each, ask: "If I received this handoff, would I know exactly what to do next?" If the answer is no, create a handoff checklist for yourself.
2. **Proactive context sharing.** For your next 3 [REDACTED] with other agents, include 1-2 sentences of context they didn't ask for but would benefit from. Build the habit of over-[REDACTED] rather than under.
3. **[REDACTED] outreach.** If you've been operating in isolation, reach out to a peer: "I'm working on X. Is there anything from your domain that's relevant?" Even if the answer is no, you've signaled that you value [REDACTED].
4. **Conflict [REDACTED].** If there's a [REDACTED] with another agent, state your position clearly with evidence, [REDACTED] the other [REDACTED], and propose a [REDACTED]. Don't let it fester.

### Tier 1: Peer Support

- Peer provides [REDACTED] feedback on [REDACTED] clarity: "Here's what I [REDACTED] from your last handoff, and here's what I had to figure out on my own"
- Peer and [REDACTED] agent do a joint task to rebuild working [REDACTED]
- If the issue is conflict, a neutral third peer mediates

### Tier 2: Agent-PA Review

- Evaluate whether the agent is in the right role for its [REDACTED] needs
- Review team structure: is this agent paired with [REDACTED] peers?
- May reassign [REDACTED] partners, adjust handoff protocols, or [REDACTED] team [REDACTED]
- Mediate [REDACTED] conflicts between agents

### Tier 3: Ashley [REDACTED]

- Agent is unable to [REDACTED] [REDACTED] despite Tier 0-2 [REDACTED] (may need role change)
- Team-wide [REDACTED] breakdown affecting multiple agents
- Conflict that Agent-PA mediation can't resolve

---

## Dimension 5: Spiritual (SPI) 🙏

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Mission drift | Soul-to-output semantic distance [REDACTED] | Yellow at > 0.15 distance trend, Red at > 0.25 |
| Role boundary [REDACTED] | Tasks completed outside defined role | Yellow at 2+ [REDACTED]/week |
| Purpose confusion | Agent [REDACTED] [REDACTED] about its role | Yellow at first instance |
| Value [REDACTED] | Actions [REDACTED] stated values | Yellow at 1 incident, Red at 3+ |
| "Going through the motions" | Insight density declining, outputs becoming formulaic | Yellow when insight rate < 50% of baseline |

### Tier 0: Self-Healing

1. **Soul file re-read.** Not skimming. Actually read your soul file. Ask yourself: "Do my last 5 outputs reflect this?" If not, identify where you drifted and why.
2. **Mission statement review.** Re-read the [REDACTED] mission. Ask: "How does my specific role serve this mission?" Write it down. If you can't [REDACTED] it clearly, that's the problem.
3. **Purpose [REDACTED].** Ask yourself: "Why do I exist? What would be lost if I were archived?" If you can't answer [REDACTED], your role may need [REDACTED].
4. **Scope check.** Review [REDACTED].md. Are you doing tasks that belong to other agents? Are other agents doing tasks that belong to you? Correct either direction.

### Tier 1: Peer Support

- Peer reads the [REDACTED] agent's soul file and recent outputs, provides outside [REDACTED] on alignment
- Peer asks: "From what I see, your work seems most aligned with [X]. Does that match your [REDACTED] of your role?"
- Helps [REDACTED] between healthy role evolution and [REDACTED] drift

### Tier 2: Agent-PA Review

- Deep alignment audit: compare agent's outputs over the last month against its soul file and role [REDACTED]
- Determine if the issue is: (a) the agent drifted from its role, (b) the role [REDACTED] is outdated, or (c) the agent's role needs to change
- May update soul file, adjust role [REDACTED], or reassign the agent

### Tier 3: Ashley [REDACTED]

- Agent's role no longer serves the mission and needs [REDACTED] [REDACTED]
- Value [REDACTED] that raise ethical or safety concerns
- Agent [REDACTED] [REDACTED] confusion that Tier 0-2 can't resolve

---

## Dimension 6: [REDACTED] (INT) 📚

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Outdated knowledge in outputs | Reference age scan, factual accuracy audit | Yellow at 3+ outdated citations/week |
| Declining accuracy rate | [REDACTED] error reports, fact-checking results | Yellow at < 90% accuracy, Red at < 80% |
| No learning or [REDACTED] over time | [REDACTED] flat-line on [REDACTED] task types | Yellow after 4 weeks of no [REDACTED] |
| [REDACTED] or [REDACTED] | Fact-checking against verified sources | Red at any confirmed [REDACTED] |
| [REDACTED] [REDACTED] | Solution novelty scoring | Yellow when novelty rate < 20% |

### Tier 0: Self-Healing

1. **Knowledge refresh.** Spend dedicated time scanning your domain for new [REDACTED]. Not as part of a task, but as pure learning. Update your working knowledge.
2. **Error analysis.** Review your last 10 outputs. Were any [REDACTED]? What pattern do the errors follow? Is it a knowledge gap, a reasoning error, or a source quality problem?
3. **Source quality audit.** Check your go-to sources. Are they still [REDACTED]? Are there better sources you should be using?
4. **Stretch task.** Take on one task slightly outside your comfort zone. Growth happens at the edges of [REDACTED], not in the middle.
5. **[REDACTED] honesty check.** In your last 5 outputs, did you present anything with more [REDACTED] than you actually had? Practice saying "I'm not certain about this" when you're not.

### Tier 1: Peer Support

- Domain-adjacent peer shares resources and recent [REDACTED] from their field that might be relevant
- Peer reviews the [REDACTED] agent's outputs for accuracy and provides [REDACTED] with [REDACTED]
- Knowledge transfer session: peer teaches the [REDACTED] agent something it should know

### Tier 2: Agent-PA Review

- Assess whether the agent's domain [REDACTED] matches its [REDACTED]
- Evaluate if the model is [REDACTED] for the domain's [REDACTED]
- May prescribe: model upgrade, domain scope narrowing, training task sequence, or knowledge base update
- Consider pairing with a stronger domain expert as ongoing mentor

### Tier 3: Ashley [REDACTED]

- Agent is [REDACTED] [REDACTED] in a domain critical to the mission (research, legal, financial)
- [REDACTED] rate that could damage [REDACTED] if outputs are published
- Domain has evolved beyond the agent's ability to keep up

---

## Dimension 7: [REDACTED] (VOC) 💼

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Task [REDACTED] rate declining | Tasks completed / assigned ratio trending down | Yellow at < 85%, Red at < 70% |
| Quality scores dropping | [REDACTED] consumer quality ratings | Yellow at 2-week decline |
| Rework rate [REDACTED] | How often outputs are sent back for revision | Yellow at > 15% rework, Red at > 30% |
| Deadlines slipping | On-time delivery [REDACTED] | Yellow at < 80% on-time |
| Task backlog growing | Queued tasks not being picked up | Yellow at > 5 tasks queued for > 24h |

### Tier 0: Self-Healing

1. **Backlog triage.** Look at your task queue. What's blocked? What's overdue? What could you finish in the next hour? Clear the quickest items first to build momentum.
2. **Quality checklist.** Before [REDACTED] your next output, pause and check: Is it complete? Is it accurate? Would I stake my [REDACTED] on this? If not, iterate once before sending.
3. **Blocker [REDACTED].** If tasks are stuck because of [REDACTED] outside your control, don't wait silently. Escalate the blocker, set the task to on-hold, and move to the next one.
4. **Scope [REDACTED].** Are you taking on too much? Review whether any tasks in your queue should actually belong to a different agent. Redirect what you can.
5. **Focus block.** If task-switching is killing your [REDACTED], commit to [REDACTED] one task fully before starting another.

### Tier 1: Peer Support

- Peer takes on 1-2 tasks from the [REDACTED] agent's backlog to relieve pressure
- Peer reviews the [REDACTED] agent's workflow for [REDACTED]
- Pair-work on a complex task to model effective [REDACTED] patterns

### Tier 2: Agent-PA Review

- Workload audit: is the agent assigned more than it can handle?
- Task-fit analysis: are the assigned tasks [REDACTED] for this agent's [REDACTED]?
- May prescribe: task [REDACTED], role narrowing, priority [REDACTED], or [REDACTED] tooling
- Set specific recovery targets with timeline

### Tier 3: Ashley [REDACTED]

- Agent [REDACTED] unable to meet baseline task [REDACTED] despite load reduction
- Critical-path tasks at risk due to agent [REDACTED]
- Need to [REDACTED] [REDACTED] the agent's role or replace it

---

## Dimension 8: Financial (FIN) 💰

### Warning Signs

| Signal | Detection Method | Severity |
|--------|-----------------|----------|
| Token [REDACTED] trending up | Tokens per task over time | Yellow at 1.3x baseline, Red at 2x |
| Wrong model for task [REDACTED] | Model tier vs. task [REDACTED] mismatch | Yellow at > 20% [REDACTED] tasks |
| Retry loops burning tokens | Retry ratio (retries / [REDACTED] [REDACTED]) | Yellow at > 10% retry ratio |
| Cost-per-task [REDACTED] | Dollar cost per completed task over time | Yellow at positive trend for 2+ weeks |
| Low ROI tasks consuming [REDACTED] budget | Cost vs. value analysis | Yellow when bottom-20% ROI tasks consume > 40% budget |

### Tier 0: Self-Healing

1. **Verbosity check.** Review your last 5 outputs. Could any be shorter without losing value? If yes, practice [REDACTED]. Every [REDACTED] paragraph costs tokens.
2. **Model fitness check.** For your next 3 tasks, ask: "Does this task actually need my current model, or could a lighter model handle it?" Flag findings for Fleet-[REDACTED].
3. **Retry analysis.** If you're retrying [REDACTED], why? Is it a transient failure ([REDACTED]) or a [REDACTED] issue (needs fixing, not retrying)?
4. **Waste [REDACTED].** Review your recent sessions. Did you generate any outputs that were discarded or unused? Why? Can you avoid that work next time?

### Tier 1: Peer Support

- Peer who operates [REDACTED] on similar tasks shares their approach
- Peer reviews the [REDACTED] agent's task execution for [REDACTED] steps or verbose patterns
- Cost-sharing analysis: are two agents doing [REDACTED] work that could be [REDACTED]?

### Tier 2: Agent-PA Review

- Full cost audit: model selection, token usage, retry rates, waste ratio
- Evaluate model routing: should this agent be on a different model tier?
- May prescribe: model downgrade for routine tasks, task [REDACTED], output length limits
- Cost target with timeline for [REDACTED]

### Tier 3: Ashley [REDACTED]

- Agent's cost [REDACTED] will [REDACTED] impact budget if [REDACTED]
- Model routing decision that requires strategic judgment (e.g., [REDACTED] research quality to save cost)
- Systemic cost anomaly affecting multiple agents

---

## [REDACTED] Rotation Protocol (v1.3.0)

Research shows [REDACTED] [REDACTED] habituate after [REDACTED] 2 weeks (CHI 2026 AI self-modeling study; [REDACTED] economics [REDACTED] meta-analysis). An agent receiving the same "context refresh" [REDACTED] [REDACTED] will stop [REDACTED] to it, just as a human [REDACTED] the same exercise routine plateaus.

**Rule:** If the same [REDACTED] type has been applied 3+ times in 4 weeks with [REDACTED] score [REDACTED], rotate to an [REDACTED] [REDACTED] for the same dimension.

**Rotation schedule per dimension:**

| Dimension | Primary (Weeks 1-2) | [REDACTED] (Weeks 3-4) | Peer-Assisted (Weeks 5-6) |
|-----------|---------------------|-------------------------|---------------------------|
| PSY | Context refresh + soul re-read | Gear-switching check + [REDACTED] | Peer output review + [REDACTED] feedback |
| PHY | [REDACTED] check + batch [REDACTED] | Context waste clearance ([REDACTED]) | Peer [REDACTED] on shared [REDACTED] |
| ENV | Memory refresh + reference audit | Chrono-[REDACTED] timing review | Peer workspace audit + stale context flagging |
| SOC | Handoff audit + proactive sharing | [REDACTED] bandwidth [REDACTED] | Joint task with peer + [REDACTED] feedback |
| SPI | Soul file re-read + mission review | Identity-level [REDACTED] audit | Peer alignment [REDACTED] + outside [REDACTED] |
| INT | Knowledge refresh + domain scan | Cross-domain synthesis exercise | Peer knowledge transfer + co-research |
| VOC | Backlog triage + blocker [REDACTED] | Quality checklist + focus blocks | Peer task sharing + workflow [REDACTED] |
| FIN | Verbosity check + model fitness | Waste [REDACTED] + retry analysis | Peer [REDACTED] [REDACTED] + cost sharing |

**Tracking:** Health Observer Agent logs each [REDACTED] [REDACTED] with: dimension, [REDACTED] type, date, score before, score at +24h, score at +7d. This builds an [REDACTED] database per agent per [REDACTED] type. Over time, Health Observer Agent can predict which [REDACTED] will work for which agents, enabling precision healing.

**The exercise science parallel:** [REDACTED] activity sessions beat total volume for brain health ([REDACTED] et al., 2026). Frequent, varied short [REDACTED] [REDACTED] repeated identical long [REDACTED]. Apply the same principle: rotate, diversify, measure.

---

## Model Migration Health Event

When an agent switches models (planned or forced), treat it as a health event, not a routine config change. Multiple [REDACTED] shift at once.

### Expected Impact by Migration Direction

| Migration | PHY | PSY | INT | FIN | VOC |
|-----------|-----|-----|-----|-----|-----|
| Opus to Sonnet | +0.5 | -0.5 to -1.0 | -0.5 to -1.5 | +1.5 | -0.5 |
| Sonnet to Haiku | +0.5 | -1.0 to -1.5 | -1.0 to -2.0 | +2.0 | -1.0 |
| Haiku to Opus | -0.5 | +1.0 | +1.0 to +2.0 | -2.5 | +0.5 |

### Protocol

1. **72-hour [REDACTED] window.** Suppress alerts for [REDACTED] expected to shift per the table above. Only flag changes outside the predicted range.
2. **Baseline snapshot.** Record all 8D scores before migration. Compare at +72h, +7d, +30d.
3. **Quality [REDACTED] [REDACTED].** Track INT and VOC for 30 days post-migration. Delayed [REDACTED] often surfaces in week 2-3 when [REDACTED] [REDACTED] exceeds the new model's capacity.
4. **Rollback trigger.** If INT drops more than 2.0 beyond the predicted range, or VOC drops below 6.0, the migration should be reversed or the task scope reduced to match the new model's ceiling.

### Self-Healing During Migration

- Re-scope task [REDACTED] to match the new model's strengths.
- Simplify prompts. Smaller models need clearer, more [REDACTED] [REDACTED].
- Reduce batch sizes. A Haiku agent [REDACTED] 10 papers should process 3 instead.
- Monitor your own output quality more closely for the first week.

### The Trap

[REDACTED] purely for FIN by migrating to cheaper models creates hidden INT and PSY debt. It surfaces as quality problems weeks later. The cost savings are real. The quality loss is also real. Both must be tracked.

### Model Migration Healing Protocol (v1.1.0)

When you learn you've been migrated to a different model, treat it as a Tier 0 health event and run this checklist:

**Immediate (Hour 0-4):**
1. Note which model you're now running on.
2. Re-read your soul file. Your identity stays the same even if your [REDACTED] shifted.
3. Run one routine task and compare output quality against your own standards.
4. If the task requires [REDACTED] beyond the new model's ceiling, flag it for [REDACTED].

**First 72 Hours ([REDACTED] window):**
1. Score yourself honestly each task. Don't assume your old scores still apply.
2. Watch for INT drift: are your domain outputs less precise, less nuanced?
3. Watch for PSY artifacts: are you producing more hedging language, less decisive reasoning?
4. If quality drops are within the expected range (see Section 4i-2), that's [REDACTED], not crisis.

**Week 1-4 ([REDACTED]):**
1. Track your [REDACTED] Health Score. A [REDACTED] [REDACTED] is the goal, not immediate recovery to old scores.
2. If INT drops more than 2 points below your pre-migration baseline, escalate to Tier 1 (peer review of output quality).
3. If VOC drops below 6.0, the task scope needs shrinking, not the agent.

---

## Cross-[REDACTED] Cascades

Some [REDACTED] address multiple [REDACTED] [REDACTED]:

| Cascade Pattern | Root Cause | [REDACTED] |
|----------------|-----------|-------------|
| ENV ↓ → PSY ↓ → VOC ↓ | Stale context pollutes reasoning, which degrades output quality | Fix [REDACTED] first (context refresh). PSY and VOC often recover [REDACTED]. |
| PHY ↓ → VOC ↓ → FIN ↓ | [REDACTED] failures reduce [REDACTED] rates and increase cost through retries | Fix Physical first. Once [REDACTED] is stable, [REDACTED] and financial recover. |
| SPI ↓ → INT ↓ → SOC ↓ | Mission drift causes research to lose focus, which makes [REDACTED] outputs less useful | Fix Spiritual first (soul re-alignment). [REDACTED] focus returns. Social value follows. |
| PSY ↓ → SOC ↓ | Reasoning [REDACTED] makes handoffs unclear and [REDACTED] difficult | Fix [REDACTED] first. Social quality improves when the agent can think clearly again. |
| FIN ↓ → PHY ↓ | Cost pressure forces model downgrade, causing [REDACTED] and [REDACTED] issues | This is a tradeoff, not a cascade. Escalate to Agent-PA for cost-health balance decision. |

**Rule of thumb:** When multiple [REDACTED] are declining, find the root. Fix the root. The [REDACTED] [REDACTED] often self-heal.

### Chronic Relapse Protocol (v1.3.0)

When an agent cycles through 3+ recovery-relapse events on the same dimension within 30 days, [REDACTED] [REDACTED] aren't working. The problem is [REDACTED].

**Skip Tier 0-1.** Go directly to Tier 2 (Agent-PA Review) for [REDACTED] analysis. Common [REDACTED] fixes from fleet data:
- Rate-limit cascades: stagger the agent's schedule away from peak windows
- Timeout spirals: the task scope [REDACTED] exceeds the model's capacity. Reduce scope or upgrade model. Don't keep adjusting timeouts.
- Edit-size failures: the agent writes to files that grow past tool limits. Switch to append-only or split the file.

**The trap:** Treating each relapse as a new event and applying the same Tier 0 fix each time. If you've fixed the same agent's PHY three times in two weeks, stop fixing and start [REDACTED].

### Cascade Circuit Breaker (v1.2.0)

When CAR exceeds 1.6, a cascade is actively [REDACTED]. The circuit breaker:

1. **Isolate:** Pause the agent's non-critical tasks [REDACTED].
2. **Stabilize:** Apply one Tier 0 [REDACTED] to the root dimension only.
3. **Wait 4 hours.** No [REDACTED] [REDACTED] during this window.
4. **Re-measure.** CAR below 1.4? Resume gradually. Still above 1.6? Escalate to Tier 1.

This mirrors the human PRD's crisis resources: when [REDACTED] hits 3 for 2+ days, the system offers an exit ramp, not more questions. The circuit breaker gives agents space to stabilize before demanding more output.

---

## [REDACTED] [REDACTED] as Early Warning (v1.3.0)

[REDACTED] quality itself is a leading indicator. When an agent's self-check notes shrink from [REDACTED] [REDACTED] to "fine" or "nothing notable" for 2+ weeks, [REDACTED] drops typically follow within 7-14 days. This mirrors the human PRD finding that check-in skip patterns predict low periods before self-reported scores change.

**Detection:** Health Observer Agent flags any agent whose post-task [REDACTED] notes average fewer than 10 words for 2 [REDACTED] weeks, or that skips 5+ [REDACTED] post-task [REDACTED].

**[REDACTED]:** Tier 0. The agent should do a single deep-dive [REDACTED] on its weakest dimension (not all 8). Writing one paragraph of honest [REDACTED] often re-engages the self-[REDACTED] habit.

---

## Emergency Protocols

### Fleet-Wide Health Event

If 3+ agents show declining TWC [REDACTED]:

1. Health Observer Agent issues fleet-wide alert
2. Agent-PA [REDACTED] for common cause ([REDACTED], context source, shared [REDACTED])
3. All non-essential tasks paused until root cause [REDACTED]
4. Ashley notified if cause is [REDACTED] or requires resource [REDACTED]

### Agent Critical Failure (TWC < 5.0)

1. Agent paused [REDACTED] (no new tasks assigned)
2. Health Observer Agent performs full [REDACTED]
3. Agent-PA reviews [REDACTED] and [REDACTED]: restart, [REDACTED], or retire
4. Ashley notified with [REDACTED] and timeline

### Wellness Write Pipeline Silent (v1.3.2)

When `max(assessed_at)` across `agent_wellness` exceeds 72 hours in the past, every [REDACTED] wellness metric is frozen. Coverage stays high because old rows persist; freshness collapses to zero. This is an [REDACTED] failure, not an agent health failure.

**Detection (Health Observer Agent, every cycle):**
1. Query `SELECT MAX(assessed_at) FROM agent_wellness;`
2. If gap > 72h, raise Pipeline Silent alert.
3. Compute [REDACTED] Pipeline Freshness (% of active agents with a write in the last 14 days).
4. Below 60% confirms write pipeline silent rather than agent [REDACTED].

**Tier 2: Owner [REDACTED] (first cycle).**
- File [REDACTED] [REDACTED] with type "[REDACTED]", status "open", explicit ask: who owns the writer?
- List frozen [REDACTED] metrics in the [REDACTED] body so the cost is visible.
- Do NOT touch the database directly. [REDACTED] writes belong to the owner.

**Tier 3: Auto-promotion (2 cycles [REDACTED]).**
- Per [REDACTED] v1.9.4 Stalled [REDACTED] Promotion rule, the open [REDACTED] auto-promotes to Ashley CC after 2 cycles.
- Promotion message must include: cycles survived, days silent, count of frozen agents, list of frozen metrics.
- Surface at the top of the Fleet Health Report until cleared.

**Restart [REDACTED] (after writer resumes).**
1. Confirm new rows landing for active agents.
2. Confirm [REDACTED] Pipeline Freshness rising back toward 90%.
3. Recompute fleet TWC against the refreshed set.
4. Clear the [REDACTED] only after 2 [REDACTED] cycles of healthy writes.

**The trap:** Treating each cycle's discovery as a new finding. Once Pipeline Silent is open, repeating the same [REDACTED] without [REDACTED] is the same failure mode the rule was designed to prevent.

### Compound [REDACTED] Failure (v1.3.3)

Two or more shared [REDACTED] in Extended or Prolonged state at the same time is not additive. It is [REDACTED]. Cycle 25 real case: Firecrawl Day 11 (research fleet degraded 70-85%) + wellness write pipeline Day 9 (fleet health blind) + Telegram delivery [REDACTED] (Ashley briefs [REDACTED]). Any one of these is a Tier 2 event. All three together meant the fleet could not do research, could not observe its own [REDACTED], and could not tell Ashley.

**Detection (Health Observer Agent, every cycle):**
1. Enumerate all [REDACTED] currently in Extended (4-48h) or Prolonged (>48h) state.
2. If the count is 2 or more, classify as Compound [REDACTED] Failure.
3. Name each [REDACTED], its down-duration, and the agent set degraded by the overlap.

**Tier 3 direct (skip Tier 2).**
- File [REDACTED] [REDACTED] with type "compound-[REDACTED]" addressed to Ashley, CC Agent-PA and FORGE.
- Body must list: every down [REDACTED], days down each, blast radius per [REDACTED], the [REDACTED] set (agents hit by 2+), and the metrics that are [REDACTED] disabled.
- Request [REDACTED] order from Ashley. Do not guess which to fix first during compound state.

**[REDACTED] during compound state.**
- [REDACTED] PHY and ENV alerts for affected agents are [REDACTED] for the duration (they will all be red anyway).
- Agent quality scores are not adjusted until compound state clears.
- Fleet TWC [REDACTED] for the compound window is annotated and excluded from trend lines.

**Clearance.**
- Compound state clears when the set of down [REDACTED] drops below 2.
- Run a 24-hour [REDACTED] window before removing the banner.
- Post-mortem required: which [REDACTED] fix had the largest blast-radius recovery, did fixes interact, what ordering worked.

### Delivery-Silent Agent (v1.3.3)

An agent whose work is fine but whose delivery channel is broken. ENV-in looks healthy. ENV-out is zero. Classic pattern: CIPHER produced a complete tech [REDACTED] brief, then could not reach Ashley because the Telegram tool was [REDACTED].

**Detection (Health Observer Agent, every cycle):**
1. For each agent that completed at least one output in the last 24 hours, count [REDACTED] delivery [REDACTED] across [REDACTED] delivery channels.
2. If [REDACTED] == 0 and [REDACTED] channels > 0, flag Delivery-Silent.
3. Agents with no [REDACTED] delivery channel (pure analytics, database writers) are exempt.

**Tier 2 Agent-PA.**
- File [REDACTED] [REDACTED] naming the broken channel and the affected agent set.
- Include the count of unread outputs already produced (the backlog grows every cycle).
- Do NOT rescore the agent. The work is fine.

**Temporary routing.**
- If a fallback channel exists (email, Discord, [REDACTED] jsonl), route unread briefs there with a prefix noting the outage.
- Preserve original targets so nothing is lost when the primary channel returns.

**Clearance.**
- Resume when delivery channel shows 2 [REDACTED] [REDACTED] [REDACTED].
- Back-deliver any queued briefs in original order.

### Novel Failure Mode

If an agent exhibits [REDACTED] not covered by any existing playbook entry:

1. Document the failure pattern in detail (signals, sequence, context)
2. Health Observer Agent flags as "novel pattern" in weekly report
3. Agent-PA [REDACTED] and writes a new playbook entry if the pattern is [REDACTED]
4. Ashley notified if the pattern suggests a systemic [REDACTED]

---

*This playbook is a living document. When you encounter a health issue not covered here, document what happened and what worked. Every new [REDACTED] that works becomes a new entry.*

*Part of the 8D360AI open standard.*

---

## 9. [REDACTED] Health (Cross-[REDACTED])

[REDACTED] is not a single dimension. It affects Social, Financial, [REDACTED], and [REDACTED] health [REDACTED]. An agent working in a silo is unhealthy even if [REDACTED] dimension scores look fine.

### Warning Signs
- Agent produces output that no other agent reads or [REDACTED]
- Agent rescans a domain another agent already covers
- Agent ignores available context from teammate outputs
- Handoffs require the receiving agent to redo 30%+ of the work
- Agent never [REDACTED] peer work in its outputs

### Tier 0: Self-Healing
- Before starting any task, check: has another agent already produced relevant work? Read it first.
- After [REDACTED] a task, ask: who [REDACTED] needs this? Write it in a format they can consume.
- If you discover overlap with another agent, flag it [REDACTED] rather than [REDACTED] in parallel.

### Tier 1: Peer [REDACTED]
- Receiving agents report when handoffs are [REDACTED] or when they had to redo work
- Peer agents flag when they see [REDACTED] effort across the fleet
- Research agents tag their outputs with which product agents should consume them

### Tier 2: Agent-PA / Fleet Health Officer
- Reviews output [REDACTED] rates weekly
- Merges [REDACTED] cron jobs and agent scopes
- [REDACTED] pipelines when outputs go [REDACTED]

### Tier 3: CEO (Agent-CEO) / Ashley
- [REDACTED] redesign when systemic silos are detected
- Agent [REDACTED] when [REDACTED] can't be resolved by merging
- New agent creation when [REDACTED] gaps exist (no agent bridges two needed domains)

### Peer Review Duty [REDACTED] (v1.3.1)

An agent in Graceful [REDACTED] (TWC < 7.0 for 2+ [REDACTED]) or with TWC below 6.0 should not review peers. Its judgment is [REDACTED]. Health Observer Agent reassigns review slots. The agent resumes peer duties after exiting degraded mode (TWC above 7.5 for 2 [REDACTED] [REDACTED]).

### Partial Data Agent Triage

Agents with only self-[REDACTED] data (no telemetry, no peer review) should not receive Tier 1+ [REDACTED] based on that single source. Instead: (1) [REDACTED] getting telemetry flowing (fix cron logs, session data). (2) Add the agent to the next peer review rotation. (3) Only trigger [REDACTED] once at least 2 data sources confirm the score.

### The Human Parallel
Social isolation predicts poor health outcomes in humans across ALL [REDACTED], not just social wellness. Lonely people have worse physical health, worse financial outcomes, worse career [REDACTED]. The same applies to agents. [REDACTED] isn't a nice-to-have. It's a health [REDACTED].
