## Welcome to the FakeNews Detector App 
<div style="text-align:center"><img src="https://github.com/balee555/FakeNewsDetector/blob/master/src/logo.png" /></div>

In today's political climate, biased and untrustworthy news articles are everywhere. One news site may claim the Democrats are trying to monitor the enitre American populace with Big Government, while another says that the Republicans are busy trying to deport everyone who doesn't agree with their tax agenda. 

While it is obvious to most people that neither of these two examples are true, it becomes more difficult to distinguish the role of bias in more subtle articles. Most people don't have the time, or sometimes the training to sift through dense political articles to determine what is actually true and what is a product of a manipulative news site. Our app simplifies this problem by doing the work for you. 

## A Demonstration

### Step 1:
First, we extract named entities. By this we mean the names of organizations and polititians, for example, Hillary CLinton, Donald Trump, or the NRA. For a more specific demonstration, we will use the headline of this article:

***Trump Presidency Is Taking The Luster Off Trump Tower***

Firstly, the algorithm breaks down the headline into the entity and adjective phrases. In this case the subject is the ***Trump Presidency*** and the phrase is ***Taking The Luster Off***.

### Step 2:
It then uses sentiment analysis to determine if there is a positive or negative feeling about the entity. In this case, the phrase ***Taking the Luster Off*** is a negative phrase. It conducts Sentiment Analysis for each sentence that an entity appears in and captures its polarity score from (-1,1) as approving or disapproving. Then it applies the polarity score to the entity and calculates the bias metric using scaled sums per named entity in order to see in which ideological direction, Conservative (R) or Liberal (R) the article's bias tends to lean.

### Step 3:
Thus it concludes that there is a negative sentiment to this statement, and outputs the following:

***[L,.96]***

The L denotes that the headline is biased towards the Left/Liberal side, while the .1234 denotes the degree of bias. In this case it is xyz percent liberally leaning...

Can you guess who might have published this article? 

The answer is: ***Huffington Post**. Huffington Post is a well known liberal news outlet, and the output of our program aligns with the their  historically demonstrated ideological bias, heavily left leaning. 


## What We Used
  - NLTK: Natural Language Toolkit
  - Textblob: Wrappers for NLTK
  - Sci-Kit Learn: Machine Learning
  - SVM: Support Vector Machine 

#### Sci-Kit Learn	(Machine Learning)
A SVM with Radial Kernel:
We used a radial kernel for our SVM classifier from Sci-Kit to derive and plot features of our corpus. We tested linear and polynomial kernels, however the radial kernel outperformed both. We hypothesize that journalists and writers may use quotations or sarcasm when writing, which creates 'pockets' of left and right leaning cluster in k-space. The kernel makes hyperplanes around the bounds for the different groups, with a tune-able tolerance metric for flexiblity. The distance from the hyperplane to the article's k-dimensional datapoint is used to create a metric for measuring bias. The closer to -1 the more liberal an article is, and the closer to 1, the more conservative. Our SVM classifies our articles similar to the picture below:

![RadialKernel](http://scikit-learn.org/stable/_images/sphx_glr_plot_svm_kernels_003.png)


