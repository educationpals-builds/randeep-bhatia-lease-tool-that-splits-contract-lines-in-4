# The Five Checks: PRISM

When auditing whether a setup actually splits work correctly, apply these five principles in sequence.

---

## P — Partition the Space

Before testing anything, define the complete territory the tool must cover. For a lease duty-splitter, this means: every clause structure that assigns responsibility—simple statements, conditional clauses with "provided that," nested exceptions, cross-references to other sections. If you haven't mapped the partition, you can't know what you haven't tested.

---

## R — Run in Parallel

Each check runs independently. Don't let a passing score on one check excuse skipping another. A tool might correctly identify parties (one check passes) while still fusing conditional duties into a single line (another check fails). Run all five before drawing conclusions.

---

## I — Individuate the Pattern

Name the specific failure pattern, not the category. "It doesn't handle conditionals" is a category. "Lines with 'provided that' merge two duties so the wrong party looks responsible" is an individuated pattern. The individuated pattern tells you exactly what to fix.

---

## S — Stitch the Spectra

After scoring each check, stitch the results into a single picture. A tool with scores of 4-2-2-2-1 across five checks isn't "mostly passing"—it has one unowned gap (the 4) that dominates the risk profile. The stitched view reveals which check decides.

---

## M — Map What Each Head Sees

For every finding, name the measurement that would confirm it. "The unowned check is failing" becomes "count how many signed summaries go out before a fused conditional duty is caught." Without a mapped measurement, you can't verify the finding or set a tripwire.

---

## The Anti-Pattern: Collapse to Monochrome

The failure mode is collapsing all five checks into a single pass/fail judgment without examining each one. This is "collapse to monochrome"—you lose the color that shows where the real crack is. A lease tool might pass four checks and catastrophically fail one. Monochrome scoring hides that the unowned check is the one that will cause a partner to sign a summary putting repair duty on the wrong side.

Keep the five checks separate. Score each. Then stitch.
