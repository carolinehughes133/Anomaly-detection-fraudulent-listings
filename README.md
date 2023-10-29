# Anomaly-detection-fraudulent-listings
Flagging suspicious secondhand fashion seller listings<br />

Anomaly/outlier = a data point in the data set that differs significantly from the other data or observations.

# Files:
**anomaly_detection_for_fraudulent_listings.ipynb**: jupyter notebook with project code <br /><br />
**seller listings.csv**: list of product listings posted by sellers on a secondhand fashion app. The file contains the seller's overall return rate for products they have sold in the past on a scale of 0-1, the seller's overall app rating on a scale of 0-1, number of units sold and returned on the app, the brand of the product listed, product type of product listed, and the listing price for the product listed. <br /><br />
**brand, product retail prices.csv**: list of retail prices for brand/product type combinations (i.e. brand= gucci;  product type= shoes). This will be used to define the average 
retail selling price for the anomaly detection to determine if the seller's listing is significantly different.

# Project Description:
This notebook uses two anomaly detection methods to flag outliers in the seller listings dataset. <br /><br />
1. **Isolation forest:** An Isolation Forest introduces (an ensemble of) binary trees that recursively generate partitions by randomly selecting a feature and then randomly selecting a split value for the feature. The partitioning process will continue until it separates all the data points from the rest of the samples. To detect an anomaly the Isolation Forest calculates the average path length (the number of splits required to isolate a sample) of all the trees for a given instance and uses this to determine if it is an anomaly (shorter average path lengths indicate anomalies)<br /><br />
2. **Zscore**: The Z-score tells us how many standard deviations away a given observation is from the mean.  <br /><br />

The notebook flags anomalous values in the seller return rate, seller rating, and the listing price of the product.<br /><br />

# Recommendations:
The output file 'joined_df' could be used to flag suspicious listings in the app. I recommend investigating/flagging the listings flagged as outliers by the isolation forest method (anomaly_IF = TRUE) where the seller has either a significantly higher return rate than avg listings (anomaly_rr_zscore = TRUE) OR a significantly lower seller rating than the avg seller (anomaly_rating_zscore = TRUE). Consider prioritizing investigation on listings with significantly higher listing prices than the avg retail listing price for that brand/product combination (sig_high_list_price = TRUE)


