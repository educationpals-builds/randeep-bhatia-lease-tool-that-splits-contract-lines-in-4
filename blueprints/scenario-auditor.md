# Lease tool that splits contract lines into separate duties

## What this auditor does

A conversational auditor that walks five checks against any lease-duty-splitting tool. A stranger pastes their failing setup and sample lease lines; the auditor scores each check, names the deciding crack, and returns a call with an owner and a tripwire.

---

## The specimen under audit

**Tool:** Lease tool that splits contract lines into separate duties

**What goes wrong if this never gets fixed:** A partner signs a summary that puts repair duty on the wrong side

**Pass criterion:** Each duty lands on its own line with the right party named

**Real inputs:** Old scanned leases with nested "provided that" lines

**Source:** Harbor Lease sample contracts

---

## Failing sentences (verbatim from Harbor Lease samples)

```
Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.
```

---

## The five checks

| Check | What it asks | Rating (1–5) |
|-------|--------------|--------------|
| Unowned | Is there an owner accountable for this check passing? | 4 |
| Copies | Does the tool produce consistent output across duplicate runs? | 2 |
| Room | Is there headroom for edge cases and new templates? | 2 |
| Stitch | Do the split duties reconnect correctly in downstream summaries? | 2 |
| Ablation | If you remove one component, does the failure surface clearly? | 1 |

**Deciding check:** unowned

---

## Audit result

### Call

Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

### Tripwire

Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

---

## How a stranger uses this auditor

1. **Paste your specimen:** Describe the lease-splitting tool you rely on—what it's supposed to do, who gets hurt when it fails.
2. **Paste three failing lease lines:** Real lines where the tool merges duties or assigns the wrong party.
3. **Walk the five checks:** The auditor asks about unowned, copies, room, stitch, and ablation for your setup.
4. **Receive your audit:** A scored table, the deciding crack, a ship/hold call with an owner on any condition, and a tripwire with a number, a danger line, and a watcher.

---

## Sample asks

A stranger with a similar lease-splitting problem might paste:

> "Our contract parser is supposed to separate maintenance obligations from payment terms. On clauses with 'subject to' or 'notwithstanding', it lumps both into one line and the landlord's duty disappears. Here are three lines from our Riverside portfolio leases where it fails..."

> "We have a duty-extraction tool for commercial leases. When a sentence has 'provided, however' it assigns both duties to the tenant. Three examples from our Q2 renewals..."

The auditor walks the same five checks, scores each, identifies the deciding crack, and returns a call and tripwire grounded in their specimen.

---

## Acceptance criteria

- Auditor walks all five checks for a stranger's lease-splitting tool
- Every finding names the measurement that would confirm it
- Each result includes a call with an owner on any condition, and an alarm with a number, a danger line, and a watcher
- The Harbor Lease audit above is visible as the worked example
