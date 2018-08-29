---
layout: single
title:  "Bias in the Shadows"
header:
  overlay_image: /assets/images/chess.png
  overlay_filter: rgba(200,200,200,0.8)
  caption: "Photo credit: Max Pixel [CC0 Public domain] https://www.maxpixel.net/"
---

## Understanding Bias

Mathematics has a connotation of being purely objective, and this is a
well-deserved distinction. Once we agree on some precisely defined objects, and
some underlying rules governing them, called axioms, then a valid proof of a
new statement about those objects by a mathematician in one place is verifiable
by a mathematician somewhere else and no other persuasion is necessary. For
instance, once we agree about what we mean by the terms triangle, length, and
Euclidean plane, and decide on our axioms, then it can be concluded beyond any
doubt that the sum of any two triangle side lengths [must
be][triangle-inequality] at least as long as the length of the third side. 

Because of this, we can fall into a mistake of seeing the results of predictive
mathematical models as being similarly beyond question. The problem with this
is that we're conflating two things: on one hand, the mathematical model for a
situation, which exists purely abstractly and almost always involves
simplifications in order to be useful, and on the other hand, the messy
real-world system that is being modeled. British statistician [George
Box][george-box] is credited with the aphorism that succinctly captures this
idea:

> All models are wrong but some are useful.

Deep learning models are generally statistical models by nature. They are
informed by data, and the data used in the process of training a model is
almost always a subset, called a sample, of the total data that could
theoretically be collected in the real world. Imagine a model trained to 
recognize when a photograph contains a cat. This model might be trained on
thousands or even millions of pictures of cats. But that's still just a small
portion of the set of all possible pictures of all existing cats.

### Statistical Sampling Error and Biased Samples

When sample data is collected in the sciences, there are always differences
between the characteristics of the sample and the characteristics of the
overall population from which the sample was drawn. Some of those differences
are due to randomness. For example, a random sample of adult males might
have an average height that's a little larger or a little smaller than the
overall population average height of all adult males. The difference between
these two averages is called sampling error. If data was collected in such a
way that in the long run, these sampling errors would average out to zero, then
statisticians would not consider this to be a biased sample for the purposes of
estimating the average height. In other words, sampling error is viewed as a
necessary feature of the process of random sampling.

On the other hand, when samples are drawn in such a way that the possible
sampling errors do not average to zero, then a biased sample has been
collected. If the bias is understood, this might still give useful information,
but treating biased samples as though they are unbiased can be a significant
source of systematic errors. There are many ways that bias can creep into
sample data, but the important distinction here is that bias in this sense is
not about the data, but about the methodology by which the data was collected.

In science, the focus is on understanding and eliminating systematic errors
because as experiments are repeated, the random sampling errors will average
out. This assumes that experiments will be repeated. Failure to repeat
experiments can still lead to mistaking sampling errors for real phenomena. 

### Bias in Training Data

This distinction mostly disappears in practice when we talk about sample data
used to train machine learning models, because these models are often trained
on existing data sets, so the model creator may have no control over the
methodology by which the data was collected. Machine learning models generally
improve their performance as the training sets grow larger. Because of limited
resources, this creates an incentive to train a model using all of the data
available. But in practice, it's unlikely that the sample consisting of all
available data was drawn in an unbiased way. Furthermore, even if the sample is
unbiased in the statistical sense above, any known differences in the
characteristics of the training data and the characteristics of the actual
population become important to consider, if those models are then used to guide
decisions with real-world consequences.

Consider for example models being used by judges to predict recidivism rates,
the likelihood that someone will commit another crime. Various characteristics,
such as age, the crime committed, the number of prior offenses, are fed into
the model, and it outputs a probability score. The judge can then use this
score when deciding someone's sentence. Someone the model decides is at high
risk to commit another crime might get a longer sentence from a judge than
someone at low risk to commit another crime, all other things being equal. 

But some of these models have been shown to have a [racial
bias][recidivism-bias], even though there is no explicit race data used as an
input. The problem is that the data used to train the model is from a *biased
sample*, reflecting other systematic racial biases in the criminal justice
system. 

So what can be done to prevent biased predictions?

## Mitigating Bias

In order to avoid making biased predictions, the most important thing we can do
is have transparency. Transparency in data collection and model construction
are key to exposing potential bias. When data sets and models are made publicly
available, statisticians and domain experts have the opportunity to check for
biases that the model creators may have missed. 

One driving force against this kind of transparency is the profit motive.
Certain models might be closely guarded trade secrets, and data sets from which
key insights might be gleaned are frequently bought and sold.

Another roadblock to transparency is privacy. Much of the data collected online
is personal information that may have been voluntarily shared, but for which
the sharer has an expectation that the information will not be made public. If
that data is then used in predictive modeling, how can we know whether or not
those predictions are biased? 

Data-driven machine learning models already impact many aspects of our lives,
through services provided by Facebook, Google, and other tech giants, and new
applications emerge every day. Overall, machine learning models offer amazing
potential to positively impact our lives. But as their influence increases, and
especially in situations where the consequences could be life-altering in ways
large and small, we should demand transparency wherever possible, while still
protecting privacy. Without transparency, bias will inevitably thrive in the
shadows. 

[triangle-inequality]: https://en.wikipedia.org/wiki/Triangle_inequality
[george-box]: https://en.wikipedia.org/wiki/George_E._P._Box
[recidivism-bias]: https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing
