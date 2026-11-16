# RP Character Application Review — architecture notes

> This is a **suggested technical boundary for a private-source module**, not a claim that all components are implemented or active in a particular deployment.

## Objective

Roleplay communities may use multiple character application types with different fields, reviewer roles and downstream permissions. A consistent approval workflow must preserve the submitted data and avoid granting role benefits before the reviewer decision is committed.

## Conceptual responsibilities

**1. Application type.** Select an application type and the corresponding schema.

**2. Dynamic form.** Collect the character submission through a form.

**3. Pending review.** Persist a pending application and notify the correct reviewers.

**4. Staff decision.** Record an authorized approve/reject decision.

**5. Role / status outcome.** Apply any configured role outcome and communicate final status.

## Review risks and recommended tests

| Concern | Failure mode | Verification to add |
|---|---|---|
| Schema evolution | Application fields may change while cases are pending | Version submissions or preserve original field names |
| Role delivery | Approval can persist while Discord role granting fails | Track decision and delivery separately |
| Reviewer isolation | Different applications may need different staff groups | Check permissions per application category |
| Replay safety | Repeated button clicks must not grant twice | Use idempotent decisions and audit history |

## Integration and permissions

The Discord interaction layer should treat its inputs as untrusted. A server-side handler must establish the principal, check authorization for the concrete operation and return user-safe errors. The persistence or external API adapter is separately responsible for safe updates, retries and recovery. The public `src/public_interface.py` is only a surface sketch; **none of these safeguards can be confirmed by running it**.

## Production/public boundary

No real member IDs, credentials, channel IDs, private schemas, moderation rules or live logs should appear in this repository. The architectural context belongs to the wider [DeadCity platform case study](https://github.com/Scumbagsss/BOT). For a separately developed runnable example, see the [ticket workflow backend](https://github.com/Scumbagsss/advanced-discord-ticket-bot).
