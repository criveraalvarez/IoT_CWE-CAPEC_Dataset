![unsw_0](https://user-images.githubusercontent.com/7439960/197022279-cfdf58ea-01ca-4c1e-854e-99776012a0bd.png) 
# IoT CWE & CAPEC Datasets


**Authors**  
  Carlos A. Rivera A.(1), Arash Shaghaghi1(1), Gustavo Batista(1), and Salil S. Kanhere(1)  
   1. The University of New South Wales (UNSW) Sydney, Australia.  
  
  
**Abstract**  
In our IoT-based research projects, we have developed and implemented two different machine-learning architectures with the sole purpose of helping the ITC administrator of any enterprise manage IoT devices. Our approach utilises the devices' cybersecurity characteristics as a pinpoint to carry out different analyses and predictions. The first algorithm is primarily dedicated to predicting vulnerabilities inherent in IoT devices, while the second algorithm is focused on forecasting attack patterns that stem from weaknesses in susceptible IoT devices. The successful utilisation of these algorithms offers invaluable assistance to ICT administrators at the enterprise level, enabling them to effectively manage IoT devices within their organisation by proactively addressing vulnerabilities associated with high-risk weaknesses and high potential of exploiting attack patterns. Our rigorous comparative analysis involved assessing the performance metrics of our implementations against similar policy models, confirming the reliability and trustworthiness of the results for deployment in real-world production environments. We share the two datasets we used in our research.


**Keywords**  
IoT CyberSecurity Prediction | National Vulnerability Database (NVD) | Common Vulnerabilities Enumeration (CVE) | Common Weaknesses Enumeration (CWE) | IoT security | Machine learning


**CWE Datasets**  
We aim to analyse text and, through ML models, predict any IoT device's weakness(es). We define the necessity of a dataset with mostly text as its content and divide it into two parts: the first, a text sequence (the input) and the classes to predict (the output). The output would contain a finite list of weaknesses(CWEs). 
Searching for possible sources, we used the dataset from [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7) and added technical information (from Zoomeye) to form our dataset-0 (Table-1). Analysing this dataset, we found two problems: First, the information is organised in features rather than just text; Secondly, the classes predicted are risk labels(Low, Medium, High, Critical). 

We solved these problems by conducting the following activities:
- Utilise the features that provide mainly textual information (the numeric-based features do not provide information when used as part of a larger text) and combine them. 
- Since the records match the vulnerability codes that the NVD generates, we used a program to query the CVE code and obtained the text of each record's weakness(es). 
- To complement the information of each device, we extracted five technical features through the ZoomEye search engine and pasted them into the corresponding text of each record of the dataset. 
- We searched the NVD for only the CVEs in the IoT devices database, obtained the corresponding vulnerability description, and used it as a new record. We extracted the CVE's weakness(es) and added it to the DS.
- We extracted the weakness(es) of the CVE and added it to the DS.



**Table 1. Dataset-0 features.**
Description of features of dataset from [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7)(SRC-1), ZoomEye (RC-2) and The NVD (SRC-3)
|Source |Feature Name |Data Type |Unique Values|Details|
| --- | --- | --- | --- | --- |
|SRC-1  |Brand        |Categorical|            129     |Name of the device reported on the CVE.
|SRC-1  |Product Type |Categorical|             71     |Phrase describing the product.
|SRC-1  |Category     |Categorical|              5     |SmartHome, Medical, Wearable, Telecomm, and Other.
|SRC-2  |Model        |Categorical|            Infinite |Product model identifier.
|SRC-2  |Operating System|    Categorical|     Infinite |Operating System name identifier.
|SRC-2  |Operating System Version|Categorical| Infinite |Operating System version identifier.
|SRC-2  |Ports       |Categorical|             65535    |Numeric identifier of the port(s) detected open.
|SRC-2  |Services    |Categorical|             [Infinite](https://www.rfc-editor.org/rfc/rfc6335) |Name of service associated to each open port.
|SRC-3  |Vulnerability Description|Categorical|Infinite |Text of each vulnerability description.
|SRC-3  |Weakness Description|Categorical     |926       |Text of each weakness description.
|SRC-3  |Weakness ID   |Categorical           |926       |Identifier code assigned to each weakness. E.g. CWE-001. 



Figure 1 shows an extract of two records from the same device generated from two different sources. We show an extract of records the Only-IoT DS contains; the first record shows an example obtained
from the NVD, and the second shows an example of structured text together using the Vulnerabilities DB and ZoomEye engine

**Figure 1. Extract of records from the Only-IoT Dataset. **

![CWE_DS_Combined](https://user-images.githubusercontent.com/7439960/197088114-8f28bc4b-92f3-435a-a7be-819f75d2a1f2.png)


The first record shows an example from the NVD (the CVE description text as the source and the associated CWEs as the target (classes to predict). The second record shows an example of text (from string-based features) extracted from the structured dataset (Table 1).  

Since this dataset contains information related to only IoT devices, we branded this dataset as Only-IoT DS. We used the whole NVD as a separate dataset
and extracted the text of each vulnerability and the corresponding weakness(es). This dataset contains information about many systems, not just IoT; therefore, we named it
the All-Systems DS.

Table 2 discloses the number of records each DS contains, and Table 3 provides the statistics of each dataset.

**Table 2. Datasets and their respective record counts.**

|Dataset| Records | 
| --- | --- | 
|Only-IoT DS      |4,892        |
|All-Systems DS   |75,559        |


**Table 3. Datasets Statistics. "AS" represents All-Systems DS, and "OI" represents Only-IoT DS.**

|Dataset| Median | Min| Max | Classes|
| --- | --- | --- | --- | --- |
|IO DS |21.5    | 2| 19,273 | 46 |
|AS DS |123.5   |19|  1,110 | 43 |

The CWE datasets can be found in the following links:
[IO_DS](https://github.com/criveraalvarez/IoT_CWE-CAPEC_Dataset/blob/30968d67946d40da633b09028a8d204da4a365e9/Datasets/OI_V1.1_DS.csv).
[AS_DS](https://github.com/criveraalvarez/IoT_CWE-CAPEC_Dataset/blob/30968d67946d40da633b09028a8d204da4a365e9/Datasets/AS_V2.1_DS.csv).


**Notes:**

-	To create the datasets, we used information from the NVD, however, we found numerous records to contain poor or no details related to weaknesses. Thus, the resulting datasets, contain records that we could match with current weaknesses.  
-	The Only-IoT dataset contains records that relate to vulnerabilities reported in most of the known IoT devices' brands. Furthermore, in our analysis of the information we did not consider devices from brands such as Apple or Google. The All-systems has not limitations, hence, it contains these two brands' devices.



**CAPEC Dataset**
We use the CAPEC mapping as labels to predict CAPECs from the dataset of IoT devices with weaknesses. 
We constructed the dataset for our prediction framework from different sources, and we used as the foundation the same dataset we created in [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7). The elements and source of each element are described in Table \ref{table:table1_DS_Sources}. We added to this dataset the weaknesses that are associated with each device. It is important to clarify here that each record of this dataset is coupled with different vulnerabilities (managed by the NVD). Because of this association, we have several repeated records; however, the content will differ in the type and number of weaknesses (CWEs) associated with each vulnerability. For the current prediction, we needed to link the devices and the weaknesses with the CAPECs, a problem we solved using the mapping approach in [Luh et al.](https://doi.org/10.1007/s11416-019-00342-x). The final structure and details of each feature of the dataset we constructed are disclosed in Table 4.


**Table 4. CAPEC Dataset features.**
Description of features we gathered to create the CAPECs dataset we use to predict the CAPECs in IoT devices. We show the details for each feature. The sources labels are: SRC-1 from [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7), RC-2 from NVD, and SRC-3 from [Luh et al.](https://doi.org/10.1007/s11416-019-00342-x). 
|Source |Feature Name |Data Type |Unique Values|Details|
| --- | --- | --- | --- | --- |
|SRC-1 |Brand        |Categorical    |129      |Name of the device reported on the CVE.
|SRC-1 |Product Type |Categorical    | 71      |Phrase describing the product.
|SRC-1 |Category     |Categorical    |  5      |SmartHome, Medical, Wearable, Telecomm, and Other.
|SRC-1 |Price        |Continuous     |Infinite |Reported in US Dollars.
|SRC-1 |Year Difference |Continuous  |Infinite |Difference of Years between a vulnerability was reported and the product release year.
|SRC-1 |Protocols    |Categorical    |  8      |Protocols used in Communication Capability.
|SRC-1 |Data Storage |Binary         |  2      |Location of data Locally or Remotely.
|SRC-1 |Personal Information |Binary |  2      |Tracks physical location: Yes or No.
|SRC-1 |Communication Capability |Categorical  | 31 |Communication technology.
|SRC-1 |Authorisation Encryption |Categorical  |  4 |Encryption used: Symmetric, Asymmetric, None, or Both.
|SRC-2 |Weakness ID-1 |Categorical |  9        |From NVD, identification code of each weakness(CWE) associated per vulnerability.
|SRC-2 |Weakness ID-2 |Categorical |  9        |From NVD, identification code of each weakness(CWE) associated per vulnerability.
|SRC-3 |Associated CAPEC-IDs [8 Class Labels] |Binary |  2  |Mapped APT-CAPEC categories list.


We applied the same data transformation approach as in [Rivera et al.](https://doi.org/10.1007/978-3-030-94822-1\_7), which consisted of Label Encoding for each categorical feature, Text Frequency Normalisation technique to all numeric values, and scaling the data and reducing the sparseness through the Standard function.

The CWEs are associated with one or up to eight CAPECs (Details in Table 5). We found the dataset to be imbalanced from the data distribution analysis.

**Table 5. Dataset Labels Distribution.**
|Associated Labels | Counts  | Distribution |
| --- | --- | --- |
|1 CAPEC  |320      |30%
|2 CAPECs |1        |0.1%
|3 CAPECs |434      |40.7%
|4 CAPECs |0        |0%
|5 CAPECs |226      |21.2%
|6 CAPECs |0        |0%
|7 CAPECs |75       |7%
|8 CAPECs |5        |0.5%

The CAPEC dataset can be found in the following [link](https://github.com/criveraalvarez/IoT_CWE-CAPEC_Dataset/blob/b6bbe4e3103faa70c610eda947a29cba90cad13c/Datasets/DS_V575.5.csv).

**Datasets inquiries**
Please submit any inquiry related to the datasets to:
- [Dr. Carlos Rivera - UNSW](mailto:c.rivera_alvarez@unswalumni.com),
- [Dr. Arash Shaghaghi - UNSW](mailto:a.shaghaghi@unsw.edu.au), 
- [Professor Salil Kanhere - UNSW](mailto:salil.kanhere@unsw.edu.au)
