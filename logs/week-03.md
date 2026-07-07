# Week 3

**Dates:** 06-22 to 06-28

## Goals
- Use Scapy + pandas to export and view the data files.
- Export files at the intervals of the research paper to compare my results.
- Debug the Colab PCAP extraction code for epoch and UTC timestamp (00:00) handling.
- Use Merit's VM to obtain PCAP files and conduct analysis (pending access).
- Continue to collect and read through research papers on ICS anomaly detection using ML and darknet traffic analysis.

## Approach and Implementation
- Dr. Akbarfam introduced me to Ramy, a member of the research team who can guide me on data processing and on retrieving the dataset from the PCAP files.
- Had a meeting with Ramy to review the dataset report and extracting data from PCAP files in Google Colab.
- Searched for and reviewed published papers on darknet traffic analysis.
- Reached out to one of the research team members, Alex, to ask how he was able to extract CSVs from PCAP files.
## Results
- Tried to debug PCAP extraction code using Scapy and pandas in Google Colab, but the pcap files were significantly too large even with with minimimal feature set of about 10.
- Reviewed the 2021 and 2025 dataset from the previous paper, but it did not have useful features to train the machine learning models on micropacing behaviors characterized by artificial botnets.
- After my meeting with Ramy it strengthened my knowledge of the darknet dataset from Merit ORION network telescope, specifically that I need timestamp (μs), source IP, destination IP, destination port,transport protocol, TCP flags, and frame length features to measure micropacing.
- Alex suggest using dpkt for analyzing the PCAP files and that he used Merit's VM to get the PCAP files for the data. From what I researched on their wedbpage I would need permission from Merit to be able to access their network Telescope VM.
- Updated the notes for Background section in darknet traffic analysis and unsupervised ML methods such as Isolation Forest, Autoencoder, and LSTM.
- Dr.Akbarfam requested remote access for me to Merit's Network telescope VM to be able to obtain the data. When I will gain access to Merit's VM is unsure.
## Notes


