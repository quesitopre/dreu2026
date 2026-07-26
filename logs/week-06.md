# Week 6

**Dates:** 07-13 to 07-20

## Goals
- Make Revisions to the Intro and Background section of paper.
- Get access & familarize myself to OSG computing resources.
- Validate the feature-engineering pipeline and correct anomalies in the extracted micropacing features.

## Approach and Implementation
- Meeting with OSG facilitator that specializes in High-Throughput computing(HTC) to discuss computing needs for research project and go over how to use OSG resource. This will be especially helpful for processing large amounts of data using batch processing and building the ml model.
- Built and ran the per-packet/per-source transformation in Google Colab, aggregating packets by source IP into 13 behavioral features (timing, volume, targeting, protocol/flag statistics) centered on inter-arrival time (IAT) and micropacing ratio.
- Ran summary-statistics and distribution checks as a sanity gate on each feature.
## Results
- Characterized the dataset as heavy-tailed approx. 65% of sources sent a single packet whereas only about 4% sent ≥ 20 packets, confirming the need for a minimum-packet threshold.
- Found outliers in the dataset that skews the IAT values, like iat_mean and iat_cv.These outliers came from single sources recorded across very large time gaps. Handling them was challenging because I had to dig deeper to understand nonsensical or contraditory values' cause and do additional data cleaning to improve the reliability of the statistical analysis.
- Grouping by src_ip alone injected multi-week gaps into any source reappearing in a later window. Ramy,the other collaborator, also found this issue and suggested we group by src_ip and the window to see the true cadence of artificially micropaced of botnets. 
- Discovered a more fundamental sampling limitation with Ramy that about 100K packets/window only gave about 2.5 sec to measure micropacing behaviors. Therefore I requested the paper's full size window from Alex of about 2 million packets that gives us about 50 seconds to measure the micropacing of botnets.
- Once I got the 2M packet CSVs for both 2021 & 2025 I verified the columns and time-span and moved on to segmenting the CSVs to smaller chunks. This takes a while so I will have to continue this next week.
- Made progress to the developing research paper for this research project by adding more details, omitting, and proofreading the paper.
## Notes
- Continue column/time-span verification before reprocessing the dataset.
- Decided that I'm sticking to Google Colab for feature extraction and OSG to build and train the ML.
- After meeting with an OSG facilitator about my computing needs for this research project.
- Dr. Asma was super helpful in onboarding me to OSG resources, she shared alot of materials, tutorial links, and documentation throughout the week. 

