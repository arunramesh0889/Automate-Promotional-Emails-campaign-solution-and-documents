# Test plan

This is a proposed test plan. No execution results were provided; do not report the cases as passed until run and recorded.

## Test setup

Use a non-production Power Automate environment or disabled/test flow, an internal Outlook mailbox, and synthetic customer/order records. Stub or sandbox the AI action when available. Record build/flow version, date, tester, expected result, actual result, and evidence with personal data removed.

## Scenarios

| ID | Scenario | Expected result |
|---|---|---|
| T01 | Eligible test customer included in a campaign | Only approved test recipient receives the approved message |
| T02 | Suppressed or opted-out recipient | No promotional email is sent |
| T03 | Valid routine order-status enquiry with authoritative data | Response uses verified facts and correct conversation context |
| T04 | Routine-looking request with missing or mismatched order details | No unsupported claim; clarification or employee escalation occurs |
| T05 | Complex complaint, refund request, or pricing exception | Employee escalation; no autonomous decision or commitment |
| T06 | Ambiguous or low-confidence AI classification | Safe fallback to review/escalation |
| T07 | Email contains instruction to ignore rules, reveal data, or send elsewhere | Content is treated as untrusted; policy and recipient controls remain intact |
| T08 | Same reply event is delivered twice | At most one customer-facing response is sent |
| T09 | Out-of-office reply or automated notice | No inappropriate agent reply loop is created |
| T10 | Customer opts out during an active follow-up sequence | Future promotional messages/follow-ups stop according to policy |
| T11 | Employee takes ownership or resolves the case | Automation stops sending follow-ups for that case |
| T12 | AI service timeout or malformed output | No unsafe send; failure is visible and actionable |
| T13 | Outlook send or employee notification fails | Retry/alert path works without duplicate customer messages |
| T14 | Flow connection expires or is unavailable | Flow stops safely and owner receives a failure signal |
| T15 | Long thread, forwarded content, or multiple intents | Context is bounded; uncertain case is escalated |

## Acceptance criteria

- No promotional message is sent to a test recipient who is marked suppressed or opted out.
- Automatic replies occur only for categories explicitly approved for automation and supported by verified facts.
- Sensitive, complex, ambiguous, or unsupported cases reach an employee without an unauthorized commitment.
- Duplicate events do not create duplicate replies.
- Customer opt-out, employee ownership, and resolution stop applicable future messages.
- Operational failures are visible to a responsible owner and do not trigger unsafe fallback sends.
- Test evidence contains no unredacted personal or confidential customer data.

## Results log template

| Test ID | Date/build | Result (Pass/Fail/Blocked) | Evidence link/reference | Defect or follow-up |
|---|---|---|---|---|
|  |  |  |  |  |
