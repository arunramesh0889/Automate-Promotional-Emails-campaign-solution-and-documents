# Prioritized improvement roadmap

Priorities are recommendations based on the project description and should be adjusted after reviewing the actual flows.

## P0 — Establish safe operating boundaries

- Inventory existing flows, triggers, connectors, AI actions, owners, and current send behavior.
- Confirm campaign audience source and opt-out/suppression enforcement.
- Define the allowed automatic-reply category list and mandatory escalation topics.
- Add a human approval gate for promotional content and risky customer commitments if missing.
- Validate email/thread identity and add duplicate protection before automatic sends.
- Run the test plan with synthetic data before enabling broader sending.

## P1 — Improve reliability and supportability

- Add explicit failure states, transient retry rules, and owner alerts.
- Add an employee exception queue with ownership, age, and resolution status.
- Make follow-up limits and cancellation rules explicit and test them.
- Keep structured, minimal audit events for classification, decision path, send result, and escalation outcome.
- Document connection ownership, permissions, and recovery steps.

## P2 — Improve answer quality

- Use an approved knowledge source for order facts and offer details rather than model memory.
- Separate intent classification, policy checks, and response drafting.
- Require structured AI output and validate schema, confidence, and prohibited content before use.
- Review a sample of human-reviewed drafts and automation outcomes to refine prompts and category boundaries.
- Track safe-response rate, escalation rate, duplicate rate, failure rate, and customer correction/complaint signals.

## P3 — Portfolio polish and scale

- Add redacted architecture/flow screenshots, a sample synthetic run, and a completed test-results summary.
- Add versioning/change notes, deployment checklist, and rollback instructions.
- Establish periodic access, prompt, offer, and policy reviews.
- Consider controlled rollout by internal recipients, then a small eligible cohort, with clear disable/rollback criteria.

## Suggested measures

Use measures that can be calculated from approved operational data: eligible campaign delivery count, reply-processing latency, automatic-response rate, escalation rate and age, duplicate-send count, flow failure rate, opt-out processing time, and sampled response quality. Define measurement windows and privacy limits before collecting them.
