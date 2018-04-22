## Welcome to the FakeNews Detector App ![Logo](https://github.com/balee555/FakeNewsDetector/blob/master/src/logo.png)

In today's political climate, biased and untrustworthy news articles are everywhere. One news site may claim the Democrats are trying to monitor the enitre American populace with Big Government, while another says that the Republicans are busy trying to deport everyone who doesn't agree with their tax agenda. 

While it is obvious to most people that neither of these two examples are true, it becomes more difficult to distinguish the role of bias in more subtle articles. Most people don't have the time, or sometimes the training to sift through dense political articles to determine what is actually true and what is a product of a manipulative news site. Our app simplifies this problem by doing the work for you. 

## A Demonstration

### Step 1:
First, we extract named entities. By this we mean the names of organizations and polititians, for example, Hillary CLinton, Donald Trump, or the NRA. For a more specific demonstration, we will use the headline of this article:

Trump Presidency Is Taking The Luster Off Trump Tower

Firstly, the algorithm breaks down the headline into the entity and adjective phrases. In this case the subject is the ***Trump Presidency*** and the phrase is ***Taking The Luster Off***.

### Step 2:
It then uses sentiment analysis to determine if there is a positive or negative feeling about the entity. In this case, the phrase ***Taking the Luster Off*** is a negative phrase. It conducts Sentiment Analysis for each sentence that an entity appears in and captures its polarity score from (-1,1) as approving or disapproving. Then it applies the polarity score to the entity and calculates the bias metric using scaled sums per named entity in order to see in which ideological direction, Conservative (R) or Liberal (R) the article's bias tends to lean.

### Step 3:
Thus it concludes that there is a negative sentiment to this statement, and outputs the following:

***[L,.1234]***

The L denotes that the headline is biased towards the Left/Liberal side, while the .1234 denotes the degree of bias. In this case it is xyz percent liberally leaning...

Can you guess who might have published this article? 

The answer is: ***Huffington Post**. Huffington Post is a well known liberal news outlet, and the output of our program aligns with the their  historically demonstrated ideological bias, heavily left leaning. 



## What We Used

#### SVM: Support Vector Machine 
#### NLTK: Natural Language Toolkit
#### Textblob: (Wrappers for NLTK)

#### Sci-Kit Learn	(Machine Learning)
Radial Kernel:
We used the Radial Kernel tool of Sci-Kit to plot the data points we derived from the articles that our program analyzed. The kernel makes hyperplane that is within the bounds that we set for the different groups, in this case [-1,1] The closer to -1 the more liberal an article is, and the closer to 1, the more conservative. The result would look something like the image below:

![RadialKernel](http://scikit-learn.org/stable/_images/sphx_glr_plot_svm_kernels_003.png)


