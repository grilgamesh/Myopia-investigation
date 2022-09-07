# Investigating Myopia

## Supervised learning

The data are split into test and train data, and target column separated off. Values are scaled to simplify them for logisitic regression but not for random forest as this is unnecessary. Both models are ran and their overall accuracy scores on the test data are compared.

I always like to render a scatter matrix for a numerical dataset, in case any features are readily apparent:

<img src="/Resources/scat_matrix.png">

### Conclusion

![image](https://user-images.githubusercontent.com/98031776/186512668-5b9169e8-4922-4bb2-951d-01689debe756.png)


Both methods came down with a similar accuracy score: 89.0% for Logistic Regression and 87.1% for the Random Forest. This represents a fairly high confidence rate of predicting Myopia in both cases, but not certainty.

However, The random forest entirely over-fitted the training data, realising 100% accurary. Since it could not replicate this in testing, this is a disadvantage.

The logistic regression model actually performed (negligably) less well on the training data, with 88.8% accuracy. This shows how it had generalised very well from it's training.

Overall,while the two models performed very similarly for this data, I would therefore use the Logistic Regression model, while it was slightly better than the random forest method overall, it did not over-fit the training data, and is therefore more trustworthy.

## Unsupervised learning

Data is read in from csv format to a dataframe, previewed, and then the Myopic column is dropped so as to not bias the data set. The data is then scaled.

A PCA model is initialised and set to reduce the dimensions of the data whilst preserving 90% of the variance. This has the effect of reducing the data from 14 columns to 10.

This reduced data is then fed into the tSNE algorithm, which demonstrates there are now five distinct clusters in the two-dimensional data, which can be seen on a scatter plot.

<img src="/Resources/clusters.png"> <img src="/Resources/knee.png">

Then a K-means model is created, and we experimentally find that the elbow point is at k=5 (confirming what we saw in the scatter plot). We then look again at the scatter plot, but coloured by cluster number.

<img src="/Resources/indentied_clusters.png">

Whilst these clusters are interesting features of the data, they do not appear to correlate with whether a person is myopic, but seem to point to some other under-lying feature of the data that we were not aware of.

<img src="/Resources/clusters-myopia.png">

## Artificial Neural Network

I set up a Tensorflow model to tune a neural network for accuracy, with parameters between 0 and 100 neurons in between 1 and 4 layers; also selecting for Relu or Tanh activation functions on the neurons.

This hyper-parameter search finally achieved 91.0% accuracy on correctly predicting myopia - I consider this a straightforward success.

![image](https://user-images.githubusercontent.com/98031776/186512827-b7f0f34f-1c98-4924-a67f-1a22e75a84d3.png)


# Overall Conclusion
To summarise: 

Supervised learning found that whilst both Logistic Regression and Random Forests performed equally well on the test data, the Random Forest ensemble method over-fitted the training data and I would therefore prefer to use the logistic regression of the two.

Unsupervised learning found that the data can be grouped into five rough clusters, although these clusters point to some as-yet unexplored feature of the data unrelated to myopia itself.

The auto-tune found a Neural Network that achieved the highest accuracy of 91.0%, which in this case, works out as the most accurate model we have for the data.

However, The dataset itself could be improved by introducing the degree to which myopia affects individuals, rather than being a binary classification problem. If we could have access to more detailed scores such as a measure of visual acuity, then perhaps we could find an even more useful model.

## Technology implemented:
* Python
* Jupyter Notebook
* Matplotlib
* Scikitlearn
* Tensorflow
