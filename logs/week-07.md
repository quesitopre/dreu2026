# Week 7

**Dates:** 07-20 to 07-26

## Goals
- Rebuild the feature-engineering pipeline to group by (src_ip, session) rather than src_ip alone.
- Produce a per-source feature table for both years that can pass all verified Sanity checks.
- Continue column/time-span verification before reprocessing the dataset.
- Generate first-pass micropacing detection results.

## Approach and Implementation
- This week I continued segmenting the full 2M packet CSV of darknet traffic from both years.
- Then I recomputed the 13 per-source behavioral features (IAT statistics, micropace_ratio, protocol/flag ratios, port entropy, TTL, etc.) grouped by (src_ip, session) this time, so no source's timing is diffed across a real capture gap. I added a 14th feature, Goh-Barabási burstiness parameter with bounds -1 to 1 to rescale IAT coefficient of variation to formalize burstiness.Then also included a statistically-derived confidence tier label (based on target relative standard error of the CV estimate about 10%/5%/2% thresholds), a threshold-sensitivity to test "true" micropaced behavior.
- Once completed, I verified & checked both split datasets(2021 & 2025) before finalizing feature extraction for model training.
## Results
- Verifying micropace behavior in the dataset is really challenging becuase all my computations point to a very very small portion (about 38 real sessions in 2021 and 42 in 2025) that show possibility of micropaced behavior. 
- However, sources with micropace_ratio > 0.7 rose from 12.13% (2021) to 18.45% (2025), also an increase in tcp_ratio and syn_ratio.
- Confidence tiers confirmed the data isn't dominated by high-packet-count sources.
- had issues resolving a stricter dual criterion filter(for instance micropace_ratio > 0.7 AND burstiness_b < -0.3) collapsed the flagged population (from 173 to 8 sources in 2021 to 2025, respectively). Which is opposite of what the micropaced ratio indicates. I have not yet determined whether this reflects two distinct behaviors (fast/chaotic vs. truly paced) or an unrepresentative fixed cutoff.
## Notes
- There was an issue with Google Drive append-write data loss of about 16M rows. I resolved it by writing to local Colab disk first and bulk-copying to Drive afterward, and then added a not-empty guard to prevent stale file corruption on re-runs.
- Next step is to examine the full burstiness_b percentile distribution within the micropaced subgroup.
- Check confidence-tier composition of the strict criterion subgroup given the very small sample size.
- Methodology limitation to document: absolute IAT values are not directly comparable across sessions with very different packet arrival rates (dense/fast vs. quiet 6-hour windows).
