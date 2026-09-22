# Echelon Sales and Marketing

Echelon Sales and Marketing is an evidence-driven commercial intelligence and execution system.

It is not intended to be a conventional CRM, autonomous spam system, social-content factory, or collection of disconnected agents. The system treats sales and marketing as explicit state, evidence, hypotheses, controlled transitions, obligations, experiments, external effects, outcomes, and learning.

## Governing capabilities

This repository is governed by:

- State-Directed Engineering / Ordo
- Repository Operating System (ROS)
- Visual Engineering
- Communication Engineering
- Limen for browser application architecture

See `requirements/` for the canonical product requirements.

## Core loop

Market hypothesis -> problem hypothesis -> evidence -> ICP -> experiment -> campaign -> execution -> result -> learning -> revised belief.

Agents do not turn assumptions into truth. Evidence and interpretation remain distinct, contradictory evidence is retained, and consequential external actions require explicit capability and policy checks.

## Architecture direction

The browser application will use Limen. GitHub is the initial durable backing store. Provider-specific integrations are isolated behind canonical integration contracts. Proton Mail is the initial email integration. Reddit is initially prioritized for listening and market intelligence. Meta, X, LinkedIn, and future providers plug into the same capability-based integration boundary.

## Requirements index

- `requirements/PRODUCT-REQUIREMENTS.md` - canonical product requirements
- `requirements/INTEGRATION-REQUIREMENTS.md` - provider-neutral integration architecture
- `requirements/LEGACY-MARKETING-OS.md` - requirements retained from the predecessor Marketing OS repository
- `requirements/OPPORTUNITY-DISCOVERY.md` - diversification and market exploration requirements
- `requirements/IMPLEMENTATION-PLAN.md` - recommended build order and parallel workstreams

The older `kemiller2002/sales-and-marketing` repository is treated as predecessor research. Relevant concepts have been carried forward here rather than making the new system depend on the old repository.
