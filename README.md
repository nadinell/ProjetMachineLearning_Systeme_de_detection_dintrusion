# Machine Learning Project: Intrusion detection system using supervised learning
## IDS System :

![NIDS](https://github.com/YASMINE12AMOR/IDS-system/assets/115255200/f910178c-8d56-411f-bcab-3c167eb99a49)
**Definition**: An Intrusion Detection System (IDS) is a security technology that monitors computer networks or systems for signs of unauthorized or malicious activity and alerts administrators or takes action to protect against potential threats.

## Description 
With the pervasive use of network technology and the internet, cyberattacks and network protocol corruption have become inevitable threats. To counter these threats, an efficient Intrusion Detection System (IDS) is imperative. This project focuses on implementing two machine learning techniques, Decision Tree and K-Nearest Neighbors (KNN), for IDS and evaluates their performance based on accuracy metrics. The evaluation employs Univariate feature selection with Analysis of Variance (ANOVA) on the NSL-KDD dataset.
## Two Main Types of IDS :
![Picture1](https://github.com/user-attachments/assets/78e8dcab-b142-4d72-b19d-2268d6c2189e)

## Types of IDS Based on Detection Method

 - **Signature-based IDS:** This type identifies malicious patterns or signatures. It is effective against known attacks but has no false alarm tolerance.
 - **Anomaly-based IDS:** Utilizing machine learning techniques, it compares current traffic to previously recorded benign traffic. While effective against unknown attacks, it may produce higher false negatives.

## Dataset
For this project, we utilized the NSL-KDD Dataset, a well-known benchmark for evaluating intrusion detection systems (IDS). The NSL-KDD dataset contains labeled records that categorize network connections as either normal or one of four types of attacks: DoS (Denial of Service), Probe, R2L (Remote-to-Local), and U2R (User-to-Root).
 
## 4 basic type of attack class:

|   Class           |  Description                                                       |
| ----------------- | ------------------------------------------------------------------ |
| DoS| A harmful attack where the attacker overloads the system or keeps resources busy, preventing users from accessing services. |
| U2R | An attack where the attacker gains root user access, obtaining control over the entire system and its data. |
| R2L | The attacker gains access to a system by sending messages to the server, often through methods like password guessing. |
| Probe attacks | An attack aimed at analyzing the network to gather information for future attacks. |

## Data Preprocessing
The dataset is preprocessed to handle outliers, apply transformations, and perform dimensionality reduction (PCA).
## Model Evaluation and comparison

![model compare](https://github.com/user-attachments/assets/f45a8e14-09e9-4c28-aee9-81ad776e869f)
Comaparison metrics are : Recall , Precision and F1 Score
=> best model is Random Forest 

# Intrusion detection system using unsupervised learning 
## Data Preprocessing
The `protocol`, `service`, and `flag` variables were deleted due to interdependencies, with experiments focusing solely on `tcp` records. Additionally, content-related features were also removed, as they are inaccessible to a network router. Furthermore, To construct normal behavior models we used only the samples labeled as normal in the training set.
## Models
- **GMM model:** The GMM approach models the normal behavior of network traffic by assuming that each feature follows a Gaussian mixture distribution. The model identifies latent components (mean and variance) for each feature, based on the normal data only. By using these latent components, the model calculates the probability of occurrence for each traffic vector under the assumption that it belongs to normal traffic. If a feature’s observed value deviates significantly from its Gaussian distribution, it is more likely to be considered anomalous.
- **KMEANS(squared euclidean distances method):** The K-Means algorithm, used for clustering, was adapted to work as an anomaly detector by first clustering normal traffic data only. This process created clusters that represent normal traffic patterns. When classifying new data, the distance of both normal and attack traces to these clusters' centroids was measured. Since the clusters were based on normal traffic, attack traces would ideally show larger distances from the centroids, thereby signaling potential anomalies. This method provides a reactive model for anomaly detection based solely on normal data.
