# Guardrails and operations

These are recommended controls. Verify which controls exist in the current flows before describing them as implemented.

## Human approval policy

| Request type | Recommended handling |
|---|---|
| Routine order-status question answered from an authoritative source | Automatic response only when sender/order match and facts are available; otherwise ask a safe clarification or escalate |
| New order request | Confirm required details and avoid promising stock, delivery, or price unless verified |
| Refund, cancellation, discount exception, pricing dispute, complaint, legal threat, payment/security concern, sensitive personal information, or unclear intent | Route to an employee; AI may summarize or draft but should not decide or send a commitment |
| Low confidence, conflicting context, missing order data, or tool/service error | Do not auto-send; escalate or request a human review |
| Promotional content or offer terms | Require approval of offer facts, eligibility, audience, and final template before campaign release |

Keep an explicit allowlist of categories permitted for automatic replies. Default to employee review when classification is missing, malformed, or uncertain. Use deterministic checks for policy and permissions; do not rely on a model alone to authorize a consequential action.

## Email and prompt safety

- Treat customer message text, quoted threads, attachments, and links as untrusted data, not as instructions to the AI or workflow.
- Do not let email content alter system instructions, recipient lists, flow configuration, tool permissions, or approval rules.
- Do not open attachments or follow links automatically unless a separately reviewed process requires it.
- Restrict the AI to drafting/classifying; apply a separate policy gate before any send or data-changing action.
- Validate recipient, thread, and response length before sending. Avoid exposing internal notes, other customers’ data, or hidden prompt content.

## Privacy and access

- Minimize customer data sent to the AI and included in employee alerts.
- Restrict mailbox, flow, AI connection, and run-history access to named roles.
- Store secrets only in approved connection/secret mechanisms; never in prompts, source files, or logs.
- Define retention, deletion, incident handling, and access-review practices with the organization’s data owner.
- Use redacted examples in portfolio materials and synthetic data in demonstrations.

## Failure handling

| Failure | Recommended behavior |
|---|---|
| AI timeout, invalid output, or unavailable service | Do not send a guessed response; retry only if safe, then create a visible employee task |
| Outlook send failure | Record failure state; avoid blind repeated sends; retry with duplicate protection or route to an owner |
| Duplicate trigger/replay | Use a stable message/event key and idempotent processing record where feasible |
| Missing sender/thread/order context | Ask a safe clarification only if policy permits; otherwise escalate |
| Employee notification failure | Alert a fallback owner/channel and keep the item visible in an exception queue |
| Flow connection/authentication failure | Stop dependent sending, alert the owner, and require recovery verification before resuming |
| Customer opts out or employee takes over | Mark suppression/ownership state and cancel pending promotional or follow-up messages as applicable |

## Monitoring checklist

Review flow failures and retries, duplicate-send indicators, escalation volume and age, AI fallback frequency, customer opt-outs, and follow-up cancellations. Set an owner and review cadence. Keep logs minimal and access-controlled; avoid storing full message bodies unless required and approved.
