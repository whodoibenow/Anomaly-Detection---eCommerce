# Anomaly Detection eCommerce - Superstore

### What is an Anomaly?

Anomaly detection (or outlier detection) is the identification of rare items, events or observations which raise suspicions by differing significantly from the majority of the data. Typically, anomalous data can be connected to some kind of problem or rare event such as e.g. bank fraud, medical problems, structural defects, malfunctioning equipment etc. This connection makes it very interesting to be able to pick out which data points can be considered anomalies, as identifying these events are typically very interesting from a business perspective.
This brings us to one of the key objectives: How do we identify whether data points are normal or anomalous? In some simple cases, as in the example figure below, data visualization can give us important information.

### The Approach

A sudden spike or dip in a metric is an anomalous behavior and both the cases needs attention. Detection of anomaly can be solved by supervised learning algorithms if we have information on anomalous behavior before modeling, but initially without feedback its difficult to identify that points. So we model this as an unsupervised problem using algorithms like Isolation Forest, Local Outlier Factor (LOFs) etc. Here we are identifying anomalies using Isolation Forest as well as LOF and K-Nearest Neighbours (KNN).

### Objective

Our primary objective was to train a anomaly detection model that would help us detect anomalies in SuperStore sales.

So, in a superstore, anomalies can be a sudden upsurge in sales or a negetive profit. Any amount of negetive profit is an anomaly.

### Isolation Forest

Isolation Forests(IF), similar to Random Forests, are build based on decision trees. And since there are no pre-defined labels here, it is an unsupervised model.

IsolationForests were built based on the fact that anomalies are the data points that are “few and different”.

In an Isolation Forest, randomly sub-sampled data is processed in a tree structure based on randomly selected features. The samples that travel deeper into the tree are less likely to be anomalies as they required more cuts to isolate them. Similarly, the samples which end up in shorter branches indicate anomalies as it was easier for the tree to separate them from other observations.

### The Flow

The flow of the code started with essential data visualisation and understanding the dataset. The dataset comprises of 21 features and 9994 rows. Followed by basic preprocessing and data visualisation to get an knowhow of the distribution of data to better under the anomaly.

![MyImage](https://raw.githubusercontent.com/whodoibenow/Anomaly-Detection---eCommerce/main/Screenshot%202022-09-05%20at%203.43.39%20PM.png)
![Plot](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.43.49%20PM.png)

Further, we inspected few random points to know the format of data input. We found out there were few data points with negetive profit, which is an anomaly. And found some extremely large sales, which can also be an anomaly. 

![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.45.20%20PM.png)

After all the exploratory analysis, we moved forward to transform the data in the form of Min-Max Scaler.

Next, we ran outlier detection using Cluster Based Local Outlier Factor (CBLOF), Histogram Based Outlier Detetion (HBOS), K-Nearest Neighbours (KNN), and Isolation Forest (IF). We cannot just settle with one algorithm without testing others.

### Cluster Based Local Outlier Factor (CBLOF)

With Cluster Based Local Outlier Factor (CBLOF), we were able to detect 100 Outliers and 9894 Inliers.

![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.44.15%20PM.png)

### Histogram Based Outlier Detetion (HBOS)

With Histogram Based Outlier Detetion (HBOS), we were able to detect 90 Outliers and 9904 Inliers.

![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.44.26%20PM.png)

### Isolation Forest (IF)

With Isolation Forest (IF), we were able to detect 100 Outliers and 9894 Inliers. 

![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.44.35%20PM.png)

### K-Nearest Neighbours (KNN)

With K-Nearest Neighbours (KNN), we were able to detect 91 Outliers and 9903 Inliers.

![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.44.50%20PM.png)


### Predictions

Isolation Forest was finally decided to use as our model to predict outliers. Hence, we saved the Isolation Forest model in a pickle format to further use for predictions.

We used several arbitrary figures as sales to predict the Anomaly such as follows:


For this, we used 122.184 units of sales to check if its an anomaly. Model predicted : NOT ANOMALY
![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.56.20%20PM.png)


For this, we used 2000.184 units of sales to check if its an anomaly. Model predicted : ANOMALY
![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.56.32%20PM.png)


For this, we used 1000.184 units of sales to check if its an anomaly. Model predicted : ANOMALY
![My Image](https://github.com/whodoibenow/Anomaly-Detection---eCommerce/raw/main/Screenshot%202022-09-05%20at%203.56.49%20PM.png)





