# Audit: Lease tool that splits contract lines into separate duties

## Specimen under review

**Tool:** Lease tool that splits contract lines into separate duties

**What goes wrong if this never gets fixed:** A partner signs a summary that puts repair duty on the wrong side

## Standard for success

Each duty lands on its own line with the right party named

## Real inputs tested

**Source:** Harbor Lease sample contracts

**Input reality:** Old scanned leases with nested "provided that" lines

### Pasted failure samples

```
Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.
```

---

## Five-check findings

| Check | Score (1–5) | Notes |
|-------|-------------|-------|
| Unowned | 4 | No clear owner for the hinge check that catches fused conditionals |
| Copies | 2 | Duplicate logic paths for "provided that" variants |
| Room | 2 | Insufficient space to handle nested conditional clauses |
| Stitch | 2 | Poor joining of split duties back to correct parties |
| Ablation | 1 | Removing components doesn't isolate the failure source |

## Deciding check

**Top crack:** Unowned

The "unowned" check scores highest (4) because there is no accountable owner for the hinge check that should catch when "provided that" clauses fuse two duties into one line. When the tool silently merges duties, no one is watching for it.

---

## Ship call

**Verdict: Hold**

Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

---

## Tripwire

**Metric:** time-to-notice

**What to watch:** Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

| Element | Value |
|---------|-------|
| Metric | time-to-notice (signed summaries before catch) |
| Danger line | More than zero per month |
| Owner | Priya |

---

## Summary

This audit examined the lease tool's handling of contract lines containing "provided that" clauses. The tool currently merges duties that should be split, causing the wrong party to appear responsible. The deciding gap is the lack of ownership for the check that would catch these fused conditionals. Until Priya assigns ownership and the tool passes against all three Harbor Lease samples, the tool is on hold.
