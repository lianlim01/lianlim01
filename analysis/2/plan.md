# Plan: CLEAR: an auditable foundation model for radiology grounded in clinical concepts

- Issue: https://github.com/lianlim01/lianlim01/issues/2
- Paper: `recommended/2026-08-19/clear-radiology-foundation-model/paper.json`
- DOI: https://doi.org/10.1038/s41551-026-01741-4
- Physician's focus: general request ("잘 분석해줘" — no narrower constraint given),
  so the deep dive should follow the paper's own stated relevance axis: whether
  a multi-institution, externally-validated model like CLEAR is a useful
  reference for our cohort's long tail of low-frequency chest findings
  (Nodule, Fibrosis, Pneumothorax, etc.) that sit behind a 53% No-Finding
  majority.

## Proposed presentation

Dashboard entry for this paper, four sections in reading order:

1. **What we asked (text)** — one paragraph restating the physician's focus
   and the paper's relevance/caveat/check fields from `paper.json`, so the
   reader knows the question before seeing any numbers.

2. **Label distribution — bar chart (not pie)** — x-axis: `findings_label`
   categories (No Finding vs. the ~7 single-label conditions with n≥5:
   Infiltration, Atelectasis, Nodule, Effusion, Fibrosis, Cardiomegaly,
   Pneumothorax), y-axis: record count. A bar chart is chosen over a pie
   because the point is the *long tail* — a pie would compress low-count bars
   into indistinguishable slivers, while a bar chart preserves the visual gap
   between the 145-record majority class and the single-digit minority
   classes, which is exactly the generalization problem CLEAR is being
   considered for.

3. **Institution / view-position split — small table, not a chart** — counts
   by `institution_code` (5 sites, 48–62 each) and `view_position` (PA 184 /
   AP 88). A table suits this better than a chart because the reader needs
   exact denominators to judge whether any one subgroup (e.g., minority
   finding × AP view) is large enough to analyze at all — that's a lookup,
   not a trend.

4. **Differences vs. CLEAR's evaluation setup — comparison table** — scale
   (0.87M image-report pairs / 239,391 patients vs. our 272 records / 153
   patients), supervision (paired free-text reports vs. our label-only
   `findings_label` field, no report text available for concept grounding),
   and validation scope (4 physician-annotated external datasets vs. our
   single synthetic in-house cohort). This table carries the "can we even
   reproduce this" answer faster than prose.

Layout order: question → distribution (the problem) → table (the exact
denominators) → differences (why direct reproduction isn't possible) — moving
from framing to evidence to caveats.

## Open questions

- Does "잘 분석해줘" mean the physician wants the deep dive scoped narrowly to
  the Nodule subgroup (n=7 single-label, n=12 including combinations), or a
  broader look across all low-frequency labels? The proposed plan defaults to
  the broader long-tail framing since no specific finding was named.
- CLEAR's concept-bottleneck / zero-shot interpretability claims cannot be
  verified against our data because we have no `report_text` populated for
  concept extraction (the paper's caveat already flags this) — confirm the
  physician is fine with the deep dive being limited to distributional
  comparison, not a reproduction of CLEAR's method.
- Should the deep dive attempt to call CLEAR's public weights/API (as
  suggested in `paper.json`'s "check" field) or stay purely descriptive/
  comparative? This affects scope and feasibility significantly.
