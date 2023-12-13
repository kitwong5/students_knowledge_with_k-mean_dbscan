# Analysis on Students’ Knowledge with Cluster Modeling

The goal of this project is to perform classification on developing students’ knowledge domain through data modeling. This project will employ K-mean and DBSCAN approach in clustering modeling. The dataset used in this project was collected by H. T. Kahraman, Sagiroglu, S., Colak, I. (2013) on knowledge based systems study on developing intuitive knowledge classifier and modeling of users’ domain dependent data in web. It contains real data about student’s knowledge status about the subject of Electrical DC Machine.[1] The dataset contained a sample size of 403 records with 5 attributes and 1 target value from student’s responses, details of attributes as below. The 5 
attributes are different contributing factors that lead to achieving the knowledge level on the subject of Electrical DC Machine. 

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/81ae8531-6cd6-477c-a539-91c9e62b9fb1)

# Methodology
The dataset was maintained in two separate worksheets, in order to perform data cleaning and data exploratory. Data from the two worksheets were merged for further processing. The dataset was found to be in good data quality condition that no missing data, no invalid data, and no outliner data was found. Only on the target value field ‘UNS’ inconsistent data value ‘Very Low’ vs ‘very_low’ was found. Action has been performed to align the inconsistent values in filed ‘UNS’. To perform data exploration, graphs and statistics of the 5 attributes against the user’s knowledge level (UNS) were reviewed. On user’s knowledge level, the dataset contained 4 categories that the ‘High’ and ‘Very Low’ knowledge users consist of 25% and 12% accordingly, ‘Middle‘ and ‘Low’ categories split the remaining shares to represent 30% and 32% of users. In terms of user’s knowledge level distribution, we
know that most students in this research is having a ‘Low’ to ‘Middle‘ level of knowledge. How can students improve their knowledge level to reach the ‘High’ category and avoid falling into the ‘Very Low’ category? Let us further look into the 5 attribute factors that lead to the user’s knowledge level.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/ab6eea4b-895d-4d5c-bc09-e48647986bfa)

The below table shows the means of 5 attributes by user’s level of knowledge. In the mean statistic, no direct relationship can be found between the attributes and the user’s knowledge level, except for PEG 
attributes. In PEG attributes, the mean value was in line with the user’s knowledge level. When the user’s knowledge level is low, the PEG mean value figure is found to be low (e.g. PEG mean value is 
0.0958 for user’s knowledge ‘very low’ group). In contrast, when the user’s knowledge level is high, the PEG mean value figure is found to be high (e.g. PEG mean value is 0.799804 for user’s knowledge ‘high’
group). According to the mean statistic value, there seems to be a positive relationship between PEG and the user’s knowledge level. This finding can be further illustrated in the ‘PEG distribution chart – by 
UNS’.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/e2e4c103-dc94-48a2-b38b-a910adc8b1f2)

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/aa47dc92-8a44-48eb-86ea-22e305e4adbb)

Looking into the correlation statistic of the 5 attributes, no clear positive or negative correlation was found between the 5 attributes. The highest correlated attribute is between PEG vs STG and PEG vs SCG. 
Cluster data modeling will perform for these 2 sets of attributes in order to explore any new data pattern. 

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/194cf8bc-7a00-4553-aa95-0f0fc8979637)

# Result
K Means clustering was performed on attributes PEG and STG. To select the best value of K for K Means clustering, a calculation of the average distance between data points and centroids has been performed. 
Below graph is the calculation result, it shows K=3 is the optimal K value to be used for K Means clustering on PEG and STG.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/0feb253a-0460-4a94-8c24-e36f58f8cd53)

Next K Means clustering was performed with K = 3 to try to identify 3 clusters for the data points between PEG and STG, below chart is the K Means cluster result.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/1362e0ed-934b-4605-9ea1-9b6c4c1b02cd)

From the K =3 K Means cluster result, the purple cluster is with users spending a low degree of study time (low STG) but having high exam performance (high PEG). The yellow cluster is with users spending 
a high degree of study time (high STG) and having high exam performance (high PEG). Since PEG and UNS is positively related, users in both purple and yellow clusters are likely to have a high level of 
knowledge (high UNS). The green cluster is with user spending low to the middle degree of study time (low to middle STG) and having low exam performance (low PEG) and low level of knowledge (low UNS). 
If the purple cluster was taken out, the degree that users spend on study time (STG) is positively related to exam performance (PEG).

To evaluate the K Means clustering model, K value was adjusted to 4 to align with the 4 dedicated target values from the User Knowledge dataset. Below is the K Means cluster model result with K = 4. In the 
result, the purple cluster is having a low degree of study time and low exam results (low STG and PEG), this sector was assumed to have a low level of knowledge (low UNS). The blue cluster sector is having
users with a low degree of study time and high exam result (low STG and high PEG), this sector was assumed to have a very low level of knowledge (very low UNS). The yellow cluster is having users with a 
high degree of study time and exam results (high STG and PEG), this sector was assumed to have a high level of knowledge (high UNS). The green cluster is having users with mid degree of study time and low 
exam results (mid STG and low PEG), this sector was assumed to have middle level of knowledge (middle UNS).

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/3b4b63b6-4d48-497c-8107-5e78be964335)

Below confusion matrix illustrated the mapping of the predicted result and the actual UNS values. It shows variance was found in the ‘Very Low’ and ‘Middle’ clusters.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/3d2651e7-2abf-4b62-b92b-d4fa1e3ed820)

To compare the overall prediction result again the actual UNS values, the accuracy of prediction was found to be around 45%.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/99b432c0-ebf5-46ef-af2a-1e38b989027d)

From the evaluated outcome, it concluded attributes exam result (PEG) and the degrees of study time (STG) were not able to accurately predict the level of knowledge (UNS). Maybe other attributes from the 
User Knowledge dataset need to be added to the analysis in order to improve the prediction accuracy on the user’s level of knowledge. 

Other than K Means cluster modeling, DBSCAN cluster model has also been performed for attributes PEG and STG. DBSCAN requires two parameters that they are the maximum distance between two samples to be considered in the same neighborhood (Eps) and the minimum number of points (minPTS). Since no domain knowledge was obtained to specify these two parameters, a k-distance graph was employed in determining the Eps parameter value, and small value approach was used in determining the minPTS parameter. By running the k-distance graph, the optimal k-distance of 0.075 was identified for Eps parameter. For minPTS parameter, it was decided to use 3 as the minPTS parameter because the points distribution between PEG and STG are not tightly packed thus small minPTS was employed.

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/76e9dc40-614f-4dce-a4fc-9c8a2d1695c6)

After the parameter was set up, DBSCAN modeling was executed, and follows result was obtained. In the DBSCAN modeling result, it identified 1 big cluster, 1 small cluster, and 4 tiny clusters. For the big 
cluster that is in purple color, it covered all ranges of PEG and STG points with values from low to high. Except for the section that both PEG and STG values are high, a small cluster in greed was identified. For 
the 4 tiny clusters, it can be considered as noisy data from the dataset. The result implied that there is only a small correlation between STG and PEG. Except the small number of users who spend a high 
degree of study time and achieved high exam performance and high knowledge (the small green cluster), the rest of the users are having no direct relationship between study time and exam performance or level of knowledge (the big purple cluster).

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/6ab35504-607e-4db8-acd9-3f9d57752610)

In order to identify more clusters from the DBSCAN model, the Eps parameter was adjusted down to 0.06. In this result, more clusters were identified. The result identified a big cluster (in purple color)
with low STG value and all range of PEG value, and 2 smaller clusters (in dark blue and light blue color)with high STG value. The rest of the tiny clusters can consider noisy from the dataset. In this run, more 
clusters have been identified, however, most of the clusters are small in size making it difficult to illustrate any findings. Further downward adjustment in the Eps parameter has been tried; however, the 
DBSCAN model results remain in similar cluster splitting as of Eps parameter equal to 0.06. Thus, it wasconcluded the no direct relationship between study time and exam performance when users have a low 
degree of input on study time (the big purple cluster).

![image](https://github.com/kitwong5/students_knowledge_with_k-mean_dbscan/assets/142315009/b3231eed-d354-4e76-9149-e836d6a72e0f)

# Discussion

To compare the cluster model results between K means and DBSCAN, K means is found to be more suitable for the usage of this User Knowledge dataset. This dataset is having 4 target values (very low, 
low, middle, high), and the ideal number of cluster splits will be close to the target number values. Since K means allow a pre-defined number of splits beforehand, the result from K means is more applicable to 
this dataset. Other than that, K mean model is good in capture data patterns that have a spherical-like shape. As seems in the K mean model results, it always tries to construct a spherical-like shape around 
the centroid. This makes it good to cluster this 2D User Knowledge dataset. In DBSCAN result, no matter how the input parameter be adjusted, it also ends up with one big cluster with many small to tiny 
clusters around. Those small and tiny clusters are consisted with too less data points making it difficult to represent any findings. One of DBSCAN nature is it cannot cluster data sets well with dataset having 
large differences in densities because the minPts-ε combination cannot be chosen appropriately for all clusters. [2] In this User Knowledge dataset, the data densities are with large differences that data points 
are highly packed in the low STG section and quite loose for other sections. The data point density differences might cause DBSCAN not able to perform as well in K means cluster model. Other than that, 
since there is no domain subject expert who can contribute to the DBSCAN parameters setting, it makesDBSCAN result less reliable when compared to the K means model. The other drawback point on 
DBSCAN is it’s difficult to evaluate its result. In the User knowledge dataset, data points are split across 4 target sectors. However, in our run of the DBSCAN result, only 1 large cluster was obtained. It’s different 
to map and evaluate DBSCAN results again the target values.

# Conclusion
In conclusion, K means and DBSCAN are an efficient data modeling tools for identifying data patterns. However, in the User Knowledge dataset, it is found K means result outperforms DBSCAN in data 
clustering. Although prediction accuracy in K means model on attribute PEG and STG from the K means model was found not with high accuracy, it still performed better when compared to the DBSCAN model 
result for the User Knowledge dataset. The reason for K means outperforming DBSCAN in clustering the User Knowledge dataset might be due to the pre-defined number of cluster capabilities available in the K 
means model, spherical-like data pattern, and the data points density.

# References
[1] H. T. Kahraman, Sagiroglu, S., Colak, I., Developing intuitive knowledge classifier and modeling of 
users' domain dependent data in web, Knowledge Based Systems, vol. 37, page 283-295, 2013.
[2] Kriegel, Hans-Peter; Kröger, Peer; Sander, Jörg; Zimek, Arthur (2011). "Density-based Clustering". WIREs Data Mining and Knowledge Discovery. 1 (3): 231–240. doi:10.1002/widm.30. S2CID 36920706. Archived from the original on 2016-11-17. Retrieved 2011-12-12.







