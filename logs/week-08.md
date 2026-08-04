# Week 8

**Dates:** 07-27 to 0802

## Goals
- Resolve the IAT cross-capture contamination bug and re-verify all downstream statistics on the corrected pipeline.
- Determine whether a genuine micro-pacing signature exists once fully corrected, and if not, identify a defensible alternative research question with Dr. Asma.
- Build a rigorous, non-circular way to test whether timing features distinguish 2021 from 2025.

## Approach and Implementation
- Diagnosed the root cause of the capture-boundary defect (non-monotonic timestamp ordering in source files, invisible to gap-based detection) and replaced gap-inference with deterministic capture-window assignment from the known 00/06/12/18 UTC schedule. Then I re-ran Phase 2 feature extraction on both years.
- I corrected a separate periodicity_score bias (small sample autocorrelation inflation) via a significance bound subtraction.
- Re verified iat_cv existence test thresholds and the "packet_count vs micropace_ratio" confound (Spearman) against collaborator's independently-computed values.
- After talking to Dr. Asma about the findings, we pivoted the research question, given the extreme rarity of micro pacing in Merit's passive network telescope dataset(2021 & 2025) to: Can behavioral timing features distinguish 2025 reconnaissance from 2021 baseline even though micro-pacing is rare?
- I created histograms/CDFs of iat_cv and micropace_ratio, confound scatter plots for visuals of findings, and then worked on building/testing machine learning models to distinguishing 2025 from 2021 reconnaissance with timing features.
- I began drafting Methodology, Results, and Related Work sections incorporating all corrected findings.

## Results
- Existence test (corrected data): genuinely-paced population remains negligible and shrinks from 2021 to 2025 (0.137% to 0.009% at iat_cv<0.2), this was also independently replicated by collaborator.
- Confound test(w/ correct data), packet_count vs micropace_ratio, correlation ρ=0.748/0.769, confirmed the rate effect but no pacing conclusion still holds post-fix.
- Detection task of timing features alone distinguish 2025 from 2021 at AUC=0.770 (Random Forest), moderate guess. Not perfect in distinguishing but confirms the discrimination isn't rate driven or a leakage artifact, and isn't explained by deliberate pacing because periodicity_score, meant to catch deliberate rhythmic pacing, contributed the least of all features.
- Although the original micro-pacing claim doesn't hold up under corrected, independently replicated testing the timing behavior has shifted between years becoming faster and trending towards randomness.

## Notes
- I started a known-signature (Mirai/ICS port) cross-reference and MITRE ATT&CK heuristic tagging as a follow-on to the detection task. It's still in progress, not yet finalized.


