![unsw_0](https://user-images.githubusercontent.com/7439960/197022279-cfdf58ea-01ca-4c1e-854e-99776012a0bd.png) 
# IoT_cybersecurity_prediction

**Authors**  
  Carlos A. Rivera A.(1), Arash Shaghaghi1(1), Gustavo Batista(1), David D. Nguyen(1), and Salil S. Kanhere(1)  
   1. The University of New South Wales (UNSW) Sydney Australia.  
  
**Abstract**  
In our IoT-based research projects, we have developed and implemented three different machine-learning architectures with the sole purpose of helping the ITC administrator of any enterprise to manage (install, grand or deny access, and remove) IoT devices. Our approach utilises the cybersecurity characteristics of the devices as a pinpoint to carry-out different analyses and predictions. The output of this project is two-fold. First, the resolution of whether grant or deny access to the requested device and Second, a set of recommended remediation actions that the ITC administrators must follow if they want to implement the analysed IoT device. When fully enforced, these remediation actions will give the organisation's stockholders the certainty that all the installed IoT devices have been subject to rigorous security analyses.

**Keywords**  
IoT CyberSecurity Prediction | National Vulnerability Database (NVD) | Common Weaknesses Enumeration (CWE) | IoT security | Machine learning

**Link**  
Publisher:  
Link to the paper: https://www.paper.com
DOI: https://doi.org


**The Datasets**  
To this end, we created three datasets:
- The IoT & CWEs dataset.
- The All-Systems & CWEs dataset.
- The IoT & CAPECs dataset.


Table 1.    

**Table 1. Dataset features.**  
| Feature Name | Data Type | Unique Values | Details |  
| --- | --- | --- | --- |
|Brand          |Categorical            |129      |Name of the device reported on the CVE.|
|Product Type   |Categorical            | 71      |Phrase describing the product.|
|Category       |Categorical            |  5      |SmartHome, Medical, Wearable, Telecomm, and Other.|
|Price          |Continuous             |Infinite |Reported in US Dollars.|
|Protocols      |Categorical            |8        |Protocols used in Communication Capability.|
|Data Storage   |Binary                 |2        |Location of data Locally or Remotely.|
|Personal Information |Binary           |2        |Personal information data used: Yes or No.|
|Location Track |Binary                 |2        |Tracks physical location: Yes or No.|
|Communication Capability |Categorical  |31       |Communication technology.|
|Authorisation Encryption |Categorical  |4        |Encryption used: Symmetric, Asymmetric, None, or Both.|
|Risk Score    |Categorical             |4        |From CVSS V3: Low, Medium, High, or  Critical.|
 

The records added from the NVD range from the year 2013 to the year 2021. And, to keep the dataset updated with the latest records, carried a sweep to the NVD over the year 2021 up to June. Noteworthy to mention that as a part of our measurement mechanism on the behaviour of the models in the different classes, we added eight synthetic records, one record per classification belonging to two specific products (A smart speaker and a smart camera). We report 1,153 as the final number of records collected, in the Table 2 we disclose the distribution among classes.  

**Table 2. Distribution of Dataset classes.**  
|Classification| Counts | Distribution %|
| --- | --- | --- |
|Low      |176        |15%|
|Medium   |138        |12%|
|High     |183        |16%|
|Critical |656        |57%|

The dataset can be found in the following [link](https://github.com/criveraalvarez/IsThisIoTDeviceLikelyToBeSecure-/blob/main/Dataset_IsThisIoTDeviceLikelytoBeSecure.csv).  
  
**Cite our data**  
Rivera A, Carlos A., Arash Shaghaghi, David D. Nguyen, and Salil S. Kanhere. "Is This IoT Device Likely to Be Secure? Risk Score Prediction for IoT Devices Using Gradient Boosting Machines." In International Conference on Mobile and Ubiquitous Systems: Computing, Networking, and Services, pp. 115-127. Springer, Cham, 2021.  
