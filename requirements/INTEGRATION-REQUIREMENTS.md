# Integration Requirements

## Architecture

The system MUST establish a provider-neutral canonical integration boundary before provider-specific implementations.

Suggested assemblies:
- Echelon.SalesMarketing.Integration
- Echelon.SalesMarketing.Integration.Contracts
- Echelon.SalesMarketing.Integration.Proton
- Echelon.SalesMarketing.Integration.Reddit
- Echelon.SalesMarketing.Integration.Meta
- Echelon.SalesMarketing.Integration.X
- Echelon.SalesMarketing.Integration.LinkedIn

Provider API types MUST NOT leak into the core domain.

## Capabilities

Providers MUST declare verified capabilities rather than implement a false common interface.

Potential capabilities:
Discovery, Search, Listening, Publishing, Conversation, Engagement, DirectMessaging, Identity, Analytics, Mentions, Reactions, Threading, Media, DeliveryStatus.

Unsupported actions MUST be unrepresentable or rejected by SDE capability checks.

## Canonical external types

Canonical contracts SHOULD include:
ExternalIdentity, ExternalOrganization, ExternalConversation, ExternalMessage, ExternalPost, ExternalComment, ExternalReaction, ExternalAudience, ExternalThread, ExternalMetric, ExternalAttachment, ExternalReference, ExternalEvidence.

Imported objects SHOULD preserve provider, provider object ID, canonical URL, observed/published timestamps, author, source/raw reference, content hash, and synchronization metadata where available.

## Observation pipeline

External material MUST remain distinct from interpretation:

External source -> Observation -> Evidence extraction -> Interpretation -> Hypothesis support/contradiction.

Observation SHOULD be first-class and reusable.

## Listening

Listening and publishing MUST be separate pipelines.

Listening SHOULD support problem discovery, customer language, objections, competitors/alternatives, market signals, implementation failures, dissatisfaction, triggers, and technology/industry shifts.

## Reddit

Reddit SHOULD initially be used primarily for research/listening rather than promotion.

Initial capabilities SHOULD prioritize discovery, search, post/comment observation, thread context, provenance, evidence creation, and customer-language extraction.

## Meta/Facebook

Meta SHOULD be evaluated by market/audience rather than assumed universally useful. Potential relevance includes restaurant, foodservice, small-business, local-business, accessibility, and other community-driven markets.

## X

X SHOULD initially be evaluated for technology/industry discussion, executive commentary, announcements, complaints, AI discourse, conferences, and emerging signals. Listening precedes autonomous publishing.

## Proton

Proton Mail SHOULD be the first outbound communication adapter because it exercises the complete outreach loop.

Domain commands SHOULD remain provider-neutral, such as SendOutreachMessage, SendFollowUp, RecordInboundMessage, RecordDeliveryFailure, RecordDeliverySuccess, and RecordReply.

Proton-specific identifiers, auth, threading, translation, delivery mechanics, and errors belong in the adapter.

## Campaign targets and outreach

CampaignTarget MUST be an explicit entity.

Suggested lifecycle:
Identified -> Researched -> QualifiedForOutreach -> MessagePrepared -> ApprovedToSend -> Sent -> Responded -> FollowUpDue -> Converted/Closed.

Outreach eligibility SHOULD derive from market/problem/ICP fit, organization/contact evidence, campaign strategy, channel policy, and communication eligibility.

First contact requires human approval.

## Communication eligibility

The system SHOULD support states/attributes such as DoNotContact, Unsubscribed, InvalidAddress, RelationshipOnly, MarketingAllowed, DirectOutreachAllowed, ExistingCustomer.

Capabilities MAY include CanSendMarketingEmail, CanSendDirectPersonalEmail, and CanSendTransactionalEmail.

Agents MUST NOT independently override eligibility.

## Sequences

Sequences SHOULD respond to state, evidence, policy, response, obligations, time, and campaign status rather than blindly execute elapsed-time drip rules.

Stop conditions include response, decline, unsubscribe, invalid address, pause/completion, no longer fitting ICP, invalidated hypothesis, excessive negative/bounce signals, policy violation, human stop, and budget thresholds.

## External effects

Every consequential provider action SHOULD create an ExternalEffect with effect ID, provider, operation, domain entity, requester, approver where needed, timestamps, result, provider ID, idempotency key, error/retry state.

The system MUST distinguish intent, attempt, confirmed external effect, and persisted internal state.

Unknown external effects MUST remain unknown until reconciled rather than being collapsed into failure.

## Integration inbox

Inbound flow:
Provider -> Adapter -> Canonical inbound event -> Integration Inbox -> Domain processor.

Events MAY include MessageReceived, CommentReceived, MentionReceived, ReplyReceived, ReactionObserved, PostObserved, MetricObserved, DeliverySucceeded, DeliveryFailed, IdentityObserved, ThreadUpdated.

Adapters SHOULD remain thin. Business interpretation belongs to the domain.

## Channel policy

ChannelPolicy SHOULD define allowed/prohibited operations, approvals, automation level, content/outreach restrictions, account restrictions, rate controls, and escalation conditions.

Agents MUST request domain transitions such as RequestPublication or RequestOutreach rather than call provider APIs directly.

## Publishing

Publishing flow:
Content strategy -> Canonical asset -> Channel variant -> Review -> Approval -> Scheduled publication -> External effect -> Metrics -> Learning.

The same copy SHOULD NOT automatically be sprayed across every channel.

## Reputation and anti-spam

The system SHOULD optimize for high-quality conversations rather than volume.

Controls SHOULD include daily/campaign limits, duplicate prevention, rate/domain throttling where relevant, bounce/rejection monitoring, immediate unsubscribe enforcement, review of new campaigns, and stop thresholds.

## Reliability

Integrations MUST account for idempotency, retries, provider outages, rate limits, duplicate inbound events, partial completion, stale state, authorization expiration, revoked credentials, send-succeeded/state-update-failed, and state-updated/send-failed scenarios.

## Security

Credentials MUST NOT live in normal GitHub domain data. Least privilege applies separately to observation, drafting, requesting, approving, publishing, and direct messaging.

## Provider verification

Capabilities MUST be verified against current provider documentation and actual account/API access. Consumer-app functionality MUST NOT be assumed to exist in an API.

## Implementation order

1. Canonical integration contracts
2. Provider simulator/test harness
3. Proton adapter
4. Observation + Evidence
5. Reddit listener
6. CustomerLanguage pipeline
7. Campaign state machine
8. ChannelPolicy
9. ExternalEffect journal
10. Integration Inbox
11. Limen campaign/research UI
12. Opportunity bridge
13. Content asset system
14. Metrics/learning
15. Meta/X integrations
16. LinkedIn integration when feasible
17. Publishing workflows
18. Multi-channel orchestration
19. Cross-provider analytics and learning
