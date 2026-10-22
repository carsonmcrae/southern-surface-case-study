# Product and architectural decisions

These summaries are original public explanations based on private architecture records and implementation reviewed October 22, 2026. They are not copies of those records. “Documented” identifies a written decision and its rationale; “inferred” identifies my interpretation of implementation behavior. Neither label proves current production performance.

## 1. Keep external discovery candidate-first

**Evidence: documented decision and implementation.**

**Problem:** Automatically discovered records can be incomplete, duplicated, or unsuitable. Putting them straight into the working pipeline would imply a level of review they had not received.

**Choice:** Persist discovered opportunities as candidates, with approval and rejection handled by a person. Approval creates or updates the working lead; rejection does not.

**Rationale:** The architecture record explicitly separates raw discovery from verified work. It replaces an earlier flow in which curated collector inputs could enter the verified pipeline directly.

**Tradeoff:** Review takes time, and candidates may remain waiting. Discovery volume alone cannot show that the business has more usable opportunities.

**Result and limit:** Collection can evolve while preserving the review boundary. Human approval remains necessary; it is not a guarantee that an opportunity will become a customer.

## 2. Retrieve current public evidence within clear bounds

**Evidence: documented decision, later amendments, and implementation.**

**Problem:** Scheduled processing repeatedly encountered a fixed list of reference businesses. Deduplication prevented repeats, but the input did not produce fresh opportunities.

**Choice:** Retrieve current structured public records, applying source permission checks, bounded retrieval, service-area scope, and source-specific relevance rules.

**Rationale:** The records explicitly favor current evidence and lawful, repeatable sources over a larger static list or volume for its own sake. A source can be disabled when commercial-use permission is unavailable.

**Tradeoff:** Source availability, terms, incomplete records, and duplicate input can reduce yield. Some runs may produce no usable candidates.

**Result and limit:** The design addresses the repeated-static-input problem without bypassing review. No claim of a stable daily yield or continuously verified source availability is made here.

## 3. Treat scheduled discovery as recoverable work

**Evidence: documented reliability correction and implementation.**

**Problem:** Earlier run coordination could drift, leave stale work behind, or record an unhelpful empty intake. One invocation failing did not necessarily leave a useful recovery path.

**Choice:** Use fixed run windows, owned leases and heartbeats, bounded retries, isolated partial failures, and recorded run diagnostics. Preserve candidates if optional enrichment fails and expose the degraded state.

**Rationale:** The decision explicitly addresses stale-worker ownership, retry safety, and the difference between an executed request and useful intake. A worker that has lost ownership must not overwrite the recovered run.

**Tradeoff:** Coordination and failure states add complexity. Operators still need to interpret diagnostics and decide when recovery is appropriate.

**Result and limit:** The implementation makes failures and partial results visible and constrains overlap. It is not evidence of a published uptime measure or of fault-free historical operation.

A clean empty or duplicate-only run can be healthy in the current implementation. A zero-new count alone is not an error; source failures, invalid results, and degraded states supply the context needed to interpret it.

## 4. Check opportunity identity before enrichment

**Evidence: implementation and adjacent operational documentation; efficiency rationale inferred.**

**Problem:** A retry or another source record can refer to an opportunity already known to the business. Repeating enrichment on that input can add work without adding an opportunity.

**Choice:** Check known candidate opportunities before optional enrichment, then revalidate and save candidates. Approval uses the existing lead workflow to resolve lead records. Opportunity identity is broader than a display name alone.

**Rationale:** Retry safety is documented in the operational design. Reducing repeated enrichment is a reasonable interpretation of the ordering, rather than a separately documented evaluation of alternative algorithms.

**Tradeoff:** Matching must balance missed duplicates against incorrectly treating distinct opportunities as one. No matching scheme can prove that all real-world duplicates have been removed.

**Result and limit:** Repeated input can be skipped without claiming a new lead. The public simulation illustrates this behavior with intentionally fictional duplicates; it does not expose the private matching contract.

## 5. Give first-party inquiries their own intake path

**Evidence: documented decision and implementation.**

**Problem:** The external-candidate review queue could obscure an incoming customer's quote request and did not represent the request's different origin.

**Choice:** Save a valid website request as an active inquiry for follow-up, preserving separate requests and leaving contact verification false.

**Rationale:** A person expressing interest through the company's own form needs prompt visibility. Syntax checks are still not proof that the person owns the supplied contact details.

**Tradeoff:** The public form needs abuse controls and validation, and people still need to assess the inquiry. Active status does not mean verified identity.

**Result and limit:** Inbound requests use the working activity and status workflow without being presented as reviewed external discoveries. This exception does not apply to collector-produced prospects.

## 6. Assist outreach while keeping communication human

**Evidence: documented decision and implementation.**

**Problem:** Operators need context and useful wording when deciding how to approach a potential customer, followed by a record of what happened.

**Choice:** Provide manually selected, generated text for review and copying, plus manual activity, follow-up, and outcome tracking. The documented provider can use deterministic assistance; this case study does not claim a deployed live generative-AI provider.

**Rationale:** The written decision explicitly avoids becoming an automated outreach system. Suggested text must not invent prior work, customer interest, guarantees, or pricing promises.

**Tradeoff:** People perform the communication and record the outcome. The software cannot promise that a follow-up date leads to a conversation or that a conversation produces a job.

**Result and limit:** Discovery and recordkeeping support an operator's work. They do not send messages, make calls, or establish independently audited attribution for the owner's reported results.
