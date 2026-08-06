# Lease Duty-Splitting Tool — Five-Check Audit Prompts

Use these five prompts to audit any lease-line-splitting tool that should separate contract duties into distinct lines with the correct party named. Each prompt walks one check and ends with the measurement that confirms the finding.

---

## Check 1: Unowned

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to audit whether the hinge logic—the part that decides where one duty ends and another begins—has a named owner who is accountable when it fails.
>
> Here is a failing input from my tool:
>
> "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
>
> The tool merged both duties onto one line, making Tenant look responsible for the whole obligation.
>
> Walk me through: Who owns the splitting logic? If no one is named, what happens when a new lease template breaks it? Is there a test suite someone runs, or does failure surface only when a partner catches a bad summary?
>
> **Measurement:** Name the person accountable for the hinge check, or confirm no owner exists. If unowned, state how many days/weeks a silent failure could persist before anyone notices.

---

## Check 2: Copies

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to audit whether the splitting logic is duplicated in multiple places—code paths, prompt variants, or config files—so that a fix in one place leaves the bug alive elsewhere.
>
> Here are three failing inputs from Harbor Lease sample contracts:
>
> 1. "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
> 2. "Fees accrue daily; provided, however, that the cap in §4.2 still applies."
> 3. "Notice is deemed given when posted, unless the parties agree otherwise in writing."
>
> Walk me through: Is the "provided that" / "provided, however" / "unless" splitting rule defined once, or does it appear in multiple places? If I fix the rule in one location, will the other two inputs still fail?
>
> **Measurement:** Count the distinct locations where the conditional-splitting rule is defined. If more than one, list each location and confirm whether a single-point fix would cover all three failing inputs.

---

## Check 3: Room

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to audit whether the tool has room to handle the variation in real lease language—nested conditionals, semicolon-separated clauses, and legacy scan artifacts.
>
> Here is what real inputs look like: Old scanned leases with nested "provided that" lines.
>
> And here are three real failing sentences:
>
> 1. "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
> 2. "Fees accrue daily; provided, however, that the cap in §4.2 still applies."
> 3. "Notice is deemed given when posted, unless the parties agree otherwise in writing."
>
> Walk me through: Does the tool's splitting logic have headroom for these variations, or is it tuned to a narrower pattern? If I add a fourth variant—say, "provided always that"—would it require a code change or just a config update?
>
> **Measurement:** State how many of the three sentence patterns the current logic covers without modification. For any uncovered pattern, estimate the effort (config change vs. code change) to add support.

---

## Check 4: Stitch

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to audit whether the split outputs stitch back together correctly—each duty on its own line, with the right party named, and no orphaned fragments.
>
> The standard for "fixed" is: Each duty lands on its own line with the right party named.
>
> Here is a failing input:
>
> "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
>
> The tool currently outputs a single merged line that makes Tenant look responsible for both the repair and the funding condition.
>
> Walk me through: After splitting, does each output line name exactly one duty and exactly one responsible party? Are there orphaned clauses (e.g., "within 10 days") that lost their party reference?
>
> **Measurement:** For the failing input above, show the expected split output (two lines, each with one duty and one party). Then confirm whether the tool's current output matches, or list the specific mismatches.

---

## Check 5: Ablation

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to audit whether removing or disabling part of the splitting logic would surface the failure faster—or whether the current setup hides failures until a partner catches a bad summary.
>
> Here is what goes wrong if this never gets fixed: A partner signs a summary that puts repair duty on the wrong side.
>
> And here is the tripwire I'm watching: Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.
>
> Walk me through: If I disabled the "provided that" splitting rule entirely, would the failure surface immediately in a test, or would it only appear when a partner reviews a summary days later? Is there a pre-signature check that would catch fused duties before they reach a partner?
>
> **Measurement:** State the current time-to-notice (how long between a fused duty being generated and a human catching it). Identify whether a pre-signature automated check exists, and if not, estimate how many summaries could ship with fused duties before detection.

---

## Sample Asks

A stranger auditing their own lease-splitting tool can paste inputs like these:

1. "Lessee shall maintain insurance coverage, provided that Lessor approves the carrier within 30 days of policy inception."

2. "Rent increases annually; provided, however, that increases shall not exceed 3% without mutual written consent."

3. "Subtenant may assign this lease unless Landlord objects in writing within 14 business days."

For each, run the five checks above to surface unowned logic, duplicated rules, variation gaps, stitching errors, and hidden failure paths.

---

## Worked Example: Harbor Lease Audit Results

**Specimen:** Lease tool that splits contract lines into separate duties

**Failing inputs (from Harbor Lease sample contracts):**

1. Tenant shall repair the roof provided that Landlord funds materials within 10 days.
2. Fees accrue daily; provided, however, that the cap in §4.2 still applies.
3. Notice is deemed given when posted, unless the parties agree otherwise in writing.

**Check ratings:**
- Unowned: 4 (critical gap)
- Copies: 2
- Room: 2
- Stitch: 2
- Ablation: 1

**Top crack:** Unowned

**Ship call:** Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

**Tripwire:** Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.
