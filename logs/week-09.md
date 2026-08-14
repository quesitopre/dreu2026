# Week 9

**Dates:** 08-03 to 08-09

## Goals
- Finalize the known-signature cross-reference analysis.
- Diagnose and resolve the port-0 artifact and source-grouped train/test leakage.
- Condense the full paper per mentor's comment while preserving technical results and methodology for last.
## Approach and Implementation
- This week I continued the Known Signature cross-reference by expanding the KNOWN_SIGNATURES table (Satori/ADB port 5555, common brute-force ports, DVR/NVR exploitation, VPN gateway scanning, IoT UPnP). And then verified each addition against real sources rather than assumptions.
- I identified the port-0 anomaly with two independent tests (protocol-level check to confirm ICMP and a source-level check ruling out as an artifact in the "dominant port" computation). Then I recategorized these sources as ICMP Host Discovery rather than leaving them unclassified.
- Verified the supervised detection task's train/test split for source-identity leakage (grouped by src_ip instead of random) per collaborator feedback. The results confirmed the AUC=0.770 result was unchanged. 
- Condensed the Abstract, Introduction, and background and rewrote them to accurately reflect the change in supervised classifiers for machine learning model.
- Restructured the Conclusion into a single contributions-only paragraph per faculty guidance; relocated Limitations and Implications content rather than deleting it.
- Made revisions to technical sections to reduce redundancy and strengthen paper.
## Results
- Signature cross-reference finalized: 60.71%/71.52% of source-captures match a known signature, 58.64%/66.46% dominant-match, expanding the Known Signature table led Mirai/Telnet matches to grow from 29.03% to 44.44%, while Unclassified fell from 39.29% to 28.48%. Reinforcing the paper's core claim that 2025 traffic reflects more classic scanning, not more sophisticated evasion.
- Both data-quality checks came back clean, port-0 is nearly 100% ICMP (not real port targeting), and the leakage corrected AUC was unchanged from the original (0.770), confirming the detection result isn't an artifact.
- Paper restructured into a coherent draft with an updated Abstract, condensed Background/Related Work, and Conclusion.

## Notes


