### Assignment description

I use [KMeans](http://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) to cluster data on 6,104 food recalls. I used the elbow analysis to arrive at an initial cluster of 300.

### Clustering Result

My final solution is to cluster at a more granular level - "packaged lettuced", "peanut butter", "cherry ice cream" etc. By examing the elbow and sampling the clustered item descriptions, I think the 300 is a good start.

### Further Improvement

Some clusters get a bit mixed up and upon inspection, it seems that the poorer clusters all have Formula labels which might have an outsized influence. I may consider adding Formula to the stop words. It is also challenging to review 300 clusters all at once. I wonder how I can further evaluate the quality of the clusters.
