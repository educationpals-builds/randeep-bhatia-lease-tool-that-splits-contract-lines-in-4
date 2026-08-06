# Lease tool that splits contract lines into separate duties

A lease tool is supposed to split contract lines into separate duties. On lines with "provided that", it still merges two duties so the wrong party looks responsible.

## Verdict

**Hold.** Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

## What goes wrong

A partner signs a summary that puts repair duty on the wrong side.

## The standard

Each duty lands on its own line with the right party named.

## Tripwire

Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

## The failing inputs

Old scanned leases with nested "provided that" lines, pulled from Harbor Lease sample contracts:

```
Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.
```

## Audit scores

| Check | Score |
|-------|-------|
| Unowned | 4 |
| Copies | 2 |
| Room | 2 |
| Stitch | 2 |
| Ablation | 1 |

**Deciding check:** Unowned

## One-paste rebuild block

To run the five checks against your own lease duty-splitting setup:

1. Name the tool and what it should do
2. State what goes wrong if it fails
3. Paste three real contract lines where it merges duties incorrectly
4. Note where those lines came from
5. Walk each of the five checks, scoring 1–5
6. Identify which check decides
7. Make the call: ship, ship-with-conditions, or hold
8. Set the tripwire: what number you watch, the danger line, and who owns it

See [charter.md](charter.md) for the full audit of this lease tool, and [METHOD.md](METHOD.md) for the five-check framework.

<!-- educationpals-build-verified -->
