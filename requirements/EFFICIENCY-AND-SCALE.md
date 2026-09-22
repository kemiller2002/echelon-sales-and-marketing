# Efficiency and Scale Requirements

Efficiency means reducing unnecessary human work, repeated research, duplicate external actions, and model/API spend without weakening evidence or control.

## 1. Projections

The system SHOULD maintain purpose-specific projections for:
- NeedsMyAttention;
- NextBestWork;
- CampaignHealth;
- OpportunityBlockers;
- EvidenceFreshness;
- FollowUpsDue;
- PendingApprovals;
- IntegrationHealth;
- ResearchQueue;
- CostAndBudget;
- SignalsToInvestigate;
- ExperimentsAwaitingInterpretation.

Projections are derived and rebuildable. They MUST NOT become a second source of truth.

## 2. Incremental computation

New observations SHOULD update only affected projections/hypotheses where practical. The system SHOULD avoid repeatedly asking an agent to re-read the entire repository.

## 3. Evidence reuse

Research artifacts and accepted evidence SHOULD be reusable across relevant accounts/hypotheses with explicit scope. Reuse MUST preserve provenance and MUST NOT broaden the evidence's population beyond what it supports.

## 4. Work deduplication

Before expensive research or external action, the system SHOULD detect:
- identical work already completed;
- semantically equivalent open work;
- prior failed experiment;
- cached provider result still fresh;
- another agent currently holding a work claim.

## 5. Progressive enrichment

The system SHOULD collect the minimum information necessary for the next legal decision and enrich only as an entity advances. Deep research on every discovered organization is inefficient.

## 6. Batch ingestion, individual decisions

External observations MAY be ingested/batched efficiently, but consequential commercial decisions MUST remain traceable to the individual target/evidence context.

## 7. Cost budgets

Budgets SHOULD exist at task, agent, workflow, experiment, campaign, and time-period levels. Thresholds MAY warn, pause, or require approval.

## 8. Model routing

Agent implementation MAY select different models/tools according to task complexity, cost, latency, and evidence requirements. Model choice MUST NOT change domain authorization.

## 9. Human attention budget

The system SHOULD treat human review time as scarce. It SHOULD group similar approvals, highlight material differences, prioritize high-value/high-risk decisions, and avoid requesting approval for unchanged material.

## 10. Search and command surface

Users SHOULD be able to find organizations, people, campaigns, evidence, hypotheses, conversations, obligations, and opportunities through one consistent search/command surface.

## 11. Saved views

Users SHOULD be able to define reusable views from domain projections without changing canonical state.

## 12. Templates without hidden logic

Templates MAY accelerate campaigns, experiments, messages, research plans, and decisions, but template defaults MUST be visible and versioned. Templates MUST NOT bypass transition rules.

## 13. Automation levels

Each workflow SHOULD declare an automation posture such as Manual, Assistive, ApprovalGated, or PolicyAutonomous. The posture is policy, not hard-coded agent behavior.

## 14. Event-driven work

Where practical, new evidence/events SHOULD create targeted obligations/signals instead of relying on repeated full scans.

## 15. Scheduling

Time-based work SHOULD be represented as domain obligations/schedules with explicit due windows and cancellation conditions. Scheduling MUST not bypass current-state eligibility when it fires.

## 16. Bulk operations

Bulk operations MAY be supported for low-risk state changes, tagging, assignment, triage, and review. Bulk external communication requires stronger policy and per-target eligibility evaluation.

## 17. Simulation

The system SHOULD support dry-run/simulation of campaigns, provider effects, state transitions, and agent plans before consequential execution.

## 18. Replay

Domain events/effects SHOULD permit reconstruction sufficient for audit, debugging, and rebuilding projections. Replay MUST NOT repeat external side effects.

## 19. Operational telemetry

Track transition failures, conflicts, stale evidence, queue latency, provider errors, reconciliation backlog, agent cost, human approval latency, duplicate work prevented, and projection freshness.

## 20. Graceful degradation

Loss of an external provider, analytics source, or optional agent SHOULD degrade the relevant capability rather than make unrelated commercial state unusable.
