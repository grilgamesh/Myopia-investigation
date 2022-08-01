# Unsupervised
Week 20: Unsupervised machine learning homework

This code provides the solution to the week 20 homework illustrating unsupervised learning.

Data is read in from csv format to a dataframe, previewed, and then the Myopic column is dropped so as to not bias the data set. The data is then scaled.

A PCA model is initialised and set to reduce the dimensions of the data whilst preserving 90% of the variance. This has the effect of reducing the data from 14 columns to 10.

This reduced data is then fed into the tSNE algorithm, which demonstrates there are now five distinct clusters in the two-dimensional data, which can be seen on a scatter plot.

Then a K-means model is created, and we experimentally find that the elbow point is at k=5 (confirming what we saw in the scatter plot). We then look again at the scatter plot, but coloured by cluster number.

Whilst these clusters are interesting features of the data, they do not appear to correlate with whether a person is myopic, but seem to point to some other under-lying feature of the data that we were not aware of.

