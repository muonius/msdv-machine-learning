## Image Recognition | Perceptron & Neural Network

In this assignment, I tested out both Perceptron and Neural Network (multi-layer Perceptron) to identify airplanes in images.

### Process

**Iteration 1**: I made three steps of modifications to the starter code - the first two steps on the feature set of the MLPClassifier and the last step on the image processing.

Step 1: Drawing from previous lessons, I know a model sometimes benefits from greater max number of iterations and improved regulations. I increased the hidden_layer_size, max_iter, and tested out a much smaller alpha value: hidden_layer_sizes=(200,100,50) alpha=0.0000001, max_iter=3000. I saw an improvement in MLPClassifier test set performance.

Step 2: Drawing from Skimage documentation, I changed activation to identity which “is useful to implement linear bottleneck” and solver to lbfgs, which is said to converge faster and perform better. I saw an improvement in test set outcome but a true positive rate that is shy of 0.8 indicates further modification is needed.

<img src="./images/Baseline.png" width="800" alt="Baseline ROCs">

Step 3: I then moved onto image processing after examining the false positive and false negative images. It seems that the horizontal line and noises contribute to the mis-categorizations. I researched to find a method to remove noises and adopted Gaussian_blur filter, a rather subtle change to the original image processing method. In the end, I saw the test set outcome was worsen. Further research and testing are needed.

**Step 2**: Next, I passed in a custom text preprocessor to the `CounterVectorizer()` function and I saw a major improvement in the Ridge Regression model.

<img src="./images/Text Preprocessing.png" width="600" alt="Text Preprocessing">

**Step 3**: I began testing `alpha` value for the Ridge Regression model. I tested values using a linear scale from default 1 to 16,000 in increments of 500. The test suggested I achieved the highest TPR and lowest FPR when the `alpha` value is around 16,000.

<img src="./images/Alpha.png" width="800" alt="Alpha">

This is when I submitted my first result ([Jupyter Notebook](https://github.com/muonius/msdv-machine-learning/blob/master/movie-review/moviereviews_yang_v08_submission01.ipynb)). Upon reviewing the [test outcome](https://github.com/visualizedata/ml/blob/master/iterations/ML_1_01_moviereviews.ipynb), I know that my model might have some overfitting issue. In addition, I know I applied a rather small `alpha` value.

**Step 4**: I moved on to experimenting `C value` for the Support Vector Machine Linear model. A smaller `C value` creates soft margin that allows more mistakes but regulates the model while a bigger `C value` creates greater margin but is prone to overfitting. This time, I learned to test my `C value` in logarithmic scale of 1e-06, 1e-05, 1e-04, 1e-03....100, and 1000. The result indicated that I achieved the highest TPR and lowest FPR with a minimum `C value` of 0.001.

<img src="./images/SVM.png" width="800" alt="SVM C value">

**Step 5**: Going back to Ridge Regression, I bumped the `alpha` in logarithmic scale. However, my performance did not improve. I decided to remove my own text preprocessor and again, bring the model to baseline. After clearing up the preprocessor, a larger `alpha` did bring a lot better result, but is it overfitting? I think I will need to submit my second test and find out. ([Jupyter Notebook](https://github.com/muonius/msdv-machine-learning/blob/master/movie-review/moviereviews_yang_v11_submission02.ipynb))

<img src="./images/Submissions.png" width="800" alt="Submissions Comp">

**Step 6**: For my third submission, I added back my own text preprocessor and unfortunately the performance worsened. However, it's still a good learning experience that the simpliest form of Bag of Words is actually the best performing model. ([Jupyter Notebook](https://github.com/muonius/msdv-machine-learning/blob/master/final_assignment_1/moviereviews_yang_v12_submission03.ipynb))
