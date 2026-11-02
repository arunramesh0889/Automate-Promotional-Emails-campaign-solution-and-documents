# Setup and configuration guide

This guide is a practical deployment checklist for Microsoft Power Automate, Outlook, and an AI agent. Because no exported flow or screenshots were available, it deliberately does not prescribe exact connector action names or claim that any step is already configured.

## Before setup

- Identify the Power Automate environment, flow owners, Outlook mailbox, AI service/agent, and required licenses.
- Obtain approval from the organization’s email, privacy, security, and marketing owners.
- Define the intended audience, permissible campaign purpose, opt-out handling, approved offer facts, and escalation categories.
- Create a test mailbox and synthetic customer/order data. Do not begin validation on a live customer audience.

## Recommended configuration sequence

1. **Audience source:** document where recipients come from, who can update it, and how consent, suppression, bounce, and unsubscribe status are checked immediately before sending.
2. **Campaign flow:** configure a controlled trigger or manual approval step, recipient eligibility checks, send limits, and a test/dry-run mode. Use an approved template or AI-generated draft bounded by verified offer details.
3. **Reply flow:** configure the Outlook event trigger and filters for the relevant mailbox/folder. Capture a stable message identifier and conversation/thread reference if available. Confirm how automated messages and out-of-office replies are excluded.
4. **AI action:** provide a narrow task, relevant message context, approved policies, and a structured result such as intent, risk flags, confidence, draft reply, and escalation reason. Validate the output before using it in later actions.
5. **Decision gate:** route only explicitly allowed categories to automatic send. Send uncertain, sensitive, or unsupported requests to the employee path.
6. **Employee notification:** include the message reference, concise summary, draft if useful, reason for escalation, and an explicit next action. Avoid including unnecessary personal data.
7. **Follow-up logic:** define the timing, maximum number, eligible statuses, and stop conditions. Verify that an employee reply or customer opt-out cancels scheduled follow-ups.
8. **Operational controls:** configure retries only for transient failures, alert an owner on terminal failures, and keep run-history access limited.
9. **Connection ownership:** use organization-approved connections and service ownership practices. Review connector permissions and reauthentication/owner-change procedures.

## Configuration record

Keep a non-secret configuration reference in the repository or internal runbook:

| Setting | Record |
|---|---|
| Environment and flow names | Fill in after verification |
| Trigger and mailbox/folder | Fill in after verification |
| AI service/action and version | Fill in after verification |
| Audience source and opt-out source | Fill in after verification |
| Allowed auto-response categories | Fill in after policy approval |
| Escalation channel and owner | Fill in after verification |
| Follow-up delay, cap, and cancellation rules | Fill in after verification |
| Retry policy and failure notification | Fill in after verification |
| Data retention and run-history access | Fill in after verification |

Do not commit connection references, access tokens, API keys, real customer emails, exported run histories, or unredacted flow definitions. If flow exports are later added, inspect them for embedded identifiers and secrets first.

## First-run checklist

- Run with internal/test recipients only.
- Confirm the exact content, recipient list, and sender identity before enabling sends.
- Verify a customer reply is associated with the right conversation.
- Verify the AI response is bounded to the approved information and the correct branch executes.
- Verify escalation reaches a named employee and includes enough context to act.
- Verify duplicate events do not send duplicate replies.
- Verify opt-out, employee takeover, and resolution stop future messages.
- Confirm failures are visible to an owner and can be safely retried.
- Record the test date, environment, cases executed, and known gaps.
