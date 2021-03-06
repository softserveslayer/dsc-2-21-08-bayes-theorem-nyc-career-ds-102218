
# Bayes' Theorem 

## Introduction

Before introducing Parametric inference, it is necessary to understand Bayes’ theorem (Bayes' Law) and its different components. What makes Bayes' theorem useful is that it allows incorporation of some knowledge or belief that we already have (commonly known as the prior) to help us calculate the probability of a related event. Looking back at our initial example, we identified the need for having some ability to incorporate our prior beliefs or understanding in order to figure out if our mood has any impact on the weather. 

This lesson will explain how we can consider doing this. 

## Objectives
* Understand and describe the Bayesian theorem from conditional probabilities
* Describe the roles of Prior, Likehood and Posterior components of Bayes Theorem 
* Understand and perform simple applications of Bayes Theorem for sensitivity and specificity

## Mathematical definition
Bayes theorem is a special case of conditional probabilities and mathematically this theorem is defined as below.

You will usually see Bayes Theorem displayed in one of two ways:

$$ P(A|B) = \frac{P(B|A)P(A)}{P(B)} $$

$$ P(A|B) = \frac{P(B|A)P(A)}{P(B|A)P(A) + P(B|not A)P(not A)}$$

Here P(A|B) stands for the Probability that A happened given B has occured. These are both the same, in the second case, you would use this form if you don't directly have the Probability of B occuring on its own. (not A is same as A complement)


Here is how you would derive this equation from what we know already from previous lessons:
<img src="bayes3.png" width=600>

To re-iterate, A and B are random events, $P(A|B)$ is the conditional probability that event A occurs given that event B has already occurred. $P(B|A)$ has the same meaning but with the roles of A and B reversed.  P(A) and P(B) are the called marginal probabilities of event A and event B occurring respectively.

> **Marginal Probability**: Probability of any single event occurring unconditioned on any other events. Whenever someone asks you whether the weather is going to be rainy or sunny today, you are computing a marginal probability.

### Example 1

In a medical context, we might be interested in finding out a patient’s probability of having liver disease if they are an alcoholic. “Being an alcoholic” is the key test for liver disease.

* A could be the event “Patient has liver disease.” Past data tells us that 10% of patients entering your clinic have liver disease. 

$$P(A) = 0.10$$

* B could be the event that “Patient is an alcoholic.” Five percent of the clinic’s patients are alcoholics. 

$$P(B) = 0.05$$

We also know that among those patients diagnosed with liver disease, 7% are alcoholics. This is our P(B|A) i.e. the probability that a patient is alcoholic, **given** that they have liver disease.

### Bring in the Bayes’ theorem 

$$P(A|B) = (0.07 * 0.1)/0.05 = 0.14$$

In other words, if the patient is an alcoholic, their chances of having liver disease is 0.14 (14%). This is a large increase from the 10% suggested by past data. But it is still unlikely that any particular patient has liver disease.

## The PRIOR Probability

This is calculated as $P(A)$ on the right hand side is the expression that is known as the **prior**. $P(A)$ is the marginal probability of patient having liver disease, regardless of their alcohol consumption. i.e. no conditioning taking place here. This is called the "prior" as it reflects the prior probability of the disease. 

So we effectively have this prior knowledge before deciding anything on the effect of alcohol on liver disease. This is a fundamental step that allows incorporation of what we already know before we solve a new problem.  

In some cases we may not have any prior information in terms of frequencies to calculate the marginal prior probability. In such cases we can create a subjective prior where using our experience of selling ice cream (or some domain knowledge to make informed guesses).So it is possible to have a P(A) probability that is not based on any real data. As we shall see later, Bayesian inference allows us to improve our priors if they do not match with incoming data. 

## The LIKELIHOOD

$P(B|A)$ in our bayesian equation is the likelihood. it shows the probability of a patient being alcoholic , GIVEN that he has a liver disease. It’s not a probability, but it is **proportional** to a probability. The likelihood of a hypothesis (B) given some data (A) is proportional to the probability of obtaining B given that A is true. Since a likelihood isn’t actually a probability it doesn’t obey various rules of probability. For example, likelihood need not sum to 1.

A critical difference between probability and likelihood is in the interpretation of what is fixed and what can vary. In the case of a conditional probability, P(A|B), the hypothesis is fixed and the data are free to vary. Likelihood, however, is the opposite. The likelihood of a hypothesis, $L(Hypothesis|Data)$, conditions on the data as if they are fixed while allowing the hypotheses to vary.

The distinction is hard to grasp at first,.

>For conditional probability, the hypothesis is treated as a given and the data are free to vary. For likelihood, the data are a given and the hypotheses vary.

## The Posterior Probability 

$P(A|B)$ is known as the posterior probability and is the revised probability of an event occurring after taking into consideration new information. Posterior probability is calculated by updating the prior probability by using Bayes' theorem. In statistical terms, the posterior probability is the probability of event A occurring given that event B has occurred.

Prior probability represents what is originally believed before new evidence is introduced, and posterior probability takes this new information into account. For our example above, this reflects th probability of having a liver disease, given that the patient is an alcoholic. 

## Bayes Theorem with Sensitivity and Specificity 

Bayes' theorem elegantly demonstrates the effect of false positives and false negatives in medical tests.

> **Sensitivity** is the true positive rate. It is a measure of the proportion of correctly identified positives. 

For example, in a pregnancy test, it would be the percentage of women with a positive pregnancy test who were pregnant. A sensitive test rarely misses a "positive."

> **Specificity** is the true negative rate. It measures the proportion of correctly identified negatives. 

For example, in a pregnancy test, it would be the percent of women with a negative pregnancy test who were not pregnant. A specific test rarely registers a false positive.

**A perfect test would be 100 percent sensitive and specific**. In reality, tests have a minimum error called the Bayes error rate. Let's see this in another example. 

### Example 2

This is a classic example of Bayes Theorem and the approach is used in medical diagnostics:

We have a test to screen for breast cancer, with the following conditions:

- 1% of women have breast cancer 
- 80% of mammograms detect breast cancer when it is there
- 9.6 % of mammograms detect breast cancer when it is *not* there. (False Positive)

We could assign the probabilities to the  sample space by using a table:
<table>
  <tr>
    
    <td></td>
    <td>Cancer (1%)</td>
    <td>No Cancer (99%)</td> 
    
  </tr>
  <tr>
    
    <td>Tested Positive</td>
    <td>80%</td>
    <td>9.6%</td> 
    
  </tr>
  <tr>
    
    <td>Tested Negative</td>
    <td>20%</td>
    <td>90.4%</td> 
    
  </tr>
</table>


Now let's say you wanted to know how accurate this test is. If someone went to go get the test and had a positive result, what is the probability that they have breast cancer?

We can first visualize Bayes Theorem by filling out the table above:

<table>
  <tr>
    
    <td></td>
    <td>Cancer (1%)</td>
    <td>No Cancer (99%)</td> 
    
  </tr>
  <tr>
    
    <td>Tested Positive</td>
    <td>True Positive: 1%  × 80%</td>
    <td>False Positive: 99%  ×  9.6%</td> 
    
  </tr>
  <tr>
    
    <td>Tested Negative</td>
    <td>False Negative: 1%  × 20%</td>
    <td>True Negative: 99%  × 90.4%</td> 
    
  </tr>
</table>



Remember that the proabbility of an event occuring is the number of ways it could happen given all possible outcomes:

$$ Probability = \frac{Desired \ event} { All \ possibilities}$$

Then the probability of getting a real, positive result is .01 × .8 = .008. 

The chance of getting any type of positive result is the chance of a *true positive* plus the chance of a *false positive* 
which is (.008 + 0.09504 = .10304).

So, our chance of cancer is .008/.10304 = 0.0776, or about 7.8%.

This means that a positive mammogram results in only a 7.8% chance of cancer, rather than 80% (the supposed accuracy of the test). 

This might seem counter intuitive at first but it makes sense: the test gives a false positive 10% of the time, so there will be a ton of false positives in any given population. There will be so many false positives, in fact, that most of the positive test results will be wrong.

Now we can turn the above process into the Bayes Theorem Equation:

Let's go ahead and plug in the information we do know into the second equation.

$$ P(A|B) = \frac{P(B|A)P(A)}{P(B|A)P(A) + P(B|not A)P(not A)}$$

Looking back on the information we were given:


* Pr(A|B) = Chance of having cancer (A) given a positive test (B). This is the desired information: How likely is it to have cancer with a positive result? We've already solved it using the table, so let's see if the equation agrees with our results: 7.8%.


* Pr(B|A) = Chance of a positive test (B) given that you had cancer (A). This is the chance of a true positive, 80% in this case.


* Pr(A) = Chance of having cancer (1%).


* Pr(not A) = Chance of not having cancer (99%).


* Pr(B|not A) = Chance of a positive test (B) given that you didn’t have cancer ( Not A). This is a false positive, 9.6% in our case.

Plugging in these numbers, we arrive at the same answer as our table method: 7.76%

>Note: In above example we have used baysian theorem in terms of odds/ratios, hence a slightly more complex denominator. [Visit this link](https://stats.stackexchange.com/questions/250522/difference-between-conditional-probability-and-bayes-rule) and additional resources to get an insight into this. 

## Additional Resources
Bayesian Theorem and understanding of involved conditional probabilities need a lot of practice. You are advised to visit following links for detailed examples highlighting the mechanics of Bayesian theorem and and deeper understanding of involved mathematical concepts. 

[Anatomy of Bayes Theorem](https://www.probabilisticworld.com/anatomy-bayes-theorem/) - A great article explaining all the points from this lesson in more detail

[Bayes theorem dot net](https://www.bayestheorem.net/) - A Whole site dedicated to Bayesian logic and intuitive examples

[The Bayes Equation denominator](https://www.academia.edu/14173151/The_Role_of_the_Denominator_in_Bayes_Theorem) - To get indepth understanding of how a bayes denominator i.e. P(Data) works. 

## Summary 

In this lesson we looked at the Bayes theorem in detail and looked at different components. We saw how BAyes theorem allows us to incorporate prior beliefs into the model as probabilities. We looked at a few simple problems where bayesian approach can be used to used to update our beliefs about a certain event, based on prior knowledge and incoming data. NExt , we shall look at the likelihood component and will see how to estimate this.
