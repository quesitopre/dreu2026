# Week 5

**Dates:** 07-06 to 07-12

## Goals
 - Extract source IPS, destination port, Transport protocol, timestamp into a CSV to understand micro pacing behaviors for ml model.
-Compute inter-arrival-time(IAT)
- Compute statistical analysis to understand micropaced behavior.
- Chose ~ 13 features that will evaluate the timing, volume, and targeting of each unique source IPs.

## Approach and Implementation
- This week I focused on data preprocess for features that I believe are valuable to train the ml methods in detecting micropaced botnets.
- I wanted to go with a statisical approach for network traffic analysis to understand the patterns of automated botnets sending them.
- To compute IAT of packets I calculated the mean, median, and coefficient of variation of gaps between packets. If it has a shorter arrival time then packet rate is high, versus higher arrival time means that the packets are arriving at a later pace.
- The next thing I focused on was the volumetrics of the source's traffic and targeting of the source IP by getting how many different ports and the Shannon entropy of the destination ports.
## Results
- Practice using statistical approaches to gain insight on the results and behavior of the dataset.
- Shared my preliminary results with Dr.Akbarfam, and encountered some issues with the statistical values falling oustide of range or returning unexpected values. I will need to investigate why that is.
- During my meeting I raised concerns about the dataset being purely unlabeled suspicious traffic. Dr.Akbarfam suggested I also try the dataset she sent me that has labeled attack to compare behaviors.
## Notes


