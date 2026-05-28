---
title: "What are Bayesian statistics?"
source: "https://www.ibm.com/think/topics/bayesian-statistics#498277085"
author:
  - "[[Joshua Noble]]"
published:
created: 2026-05-21
description: "Bayesian statistics is an approach to statistical inference grounded in Bayes’ theorem to update the probability of a hypothesis as more evidence or data becomes available."
tags:
  - "clippings"
---
## What is Bayesian statistics?

## Author

Data Scientist

## What is Bayesian statistics?

Bayesian statistics is an approach to statistical inference grounded in Bayes’ theorem to update the probability of a hypothesis as more evidence or data becomes available. That theorem gives a formal definition for how prior beliefs about uncertain quantities should be updated with newly observed data to produce an estimate of the likelihood of an event happening.

There are two fundamental paradigms for statistical inference: Bayesian statistics, which treats of unknown parameters parameters as random variables characterized by probability distributions, and Frequentist statistics, which treats all unknown parametersparameters as unknown constants.

Bayesian statistics focuses on conditional probability, which is the probability of an event A given event B. This is usually written $p(A∣B)$. A classic example of calculating conditional probability is a test for a rare disease. Imagine that a test detects the disease 99% of the time if the patient has the disease (true positive) and returns a false positive 1% of the time it is administered. However the disease is relatively rare, occurring in only 1 in 10000 people, which is an occurrence rate of 0.01%. If the test returns positive for a patient, how likely is it that they actually have the disease? Conditional probability shows us that the likelihood is 0.0099 or 0.9%.

Bayesian statistics are named for the Reverend Thomas Bayes, an English statistician born in 1701. Bayes became interested in the problem of inverse probability in 1755 and formulated what became known as Bayes’ Theorem (or Bayes’ Rule) sometime between 1755 and his death in 1761. Bayes was exploring techniques to compute a distribution for the probability parameter of a binomial distribution across multiple identical Bernoulli trials. His theorem computes the reverse conditional probability of an event, and it states:

$p(θ∣D)=p(D∣θ)p(θ)p(D)$

\- $θ$ represents a hypothesis

\- $D$ is the observed data

\- $p(θ)$ is the prior probability distribution which expresses beliefs about θ before seeing the data. These can be based upon previous research, or the experimental set up in the case of an experiment. This makes the impact of the rest of the world outside of the data generating process explicit in the calculation.

\- $p(D∣θ)$ is the likelihood function and it represents the probability of observing the data given the hypothesis

\- $p(D)$ is the evidence (sometimes called ‘marginal likelihood’) that serves as a normalizing constant in the equation. This is how likely the observed data is, independent of any testing.

\- $p(θ∣D)$ this is the posterior distribution, the updated belief about the hypothesis after incorporating the evidence and the priors.

Bayes theorem enables inference in the form of a posterior distribution that can be used to compute point estimates like the mean, mode, or median of the posterior. The posterior distribution also contains interval estimates as well as predictive distributions for new data.[^1]

Conceptually, we use the prior information and the observed data to come up with a new estimate of what is likely to happen based on previous belief and new information:

 ![[Image 4.png|The observed distribution and prior distribution being combined into a posterior distribution]]Observed distribution and prior distribution combine to create a posterior distribution

This approach is widely used in statistical machine learning. Model architectures like Naive Bayes leverage Bayes theorem to perform classification tasks like sifting out spam emails. Forecasting in meteorological and financial contexts often apply Bayesian principles to generate probabilistic forecasts that show all possible values in a forecast.

## Computing Bayes Rule

Although Bayes’ Theorem has been around for a long time, methods to utilize it efficiently in [data science](https://www.ibm.com/think/topics/data-science) with large datasets had to wait for adequate computing resources to be invented. Consider the following equation to compute the likelihood of the observed data occuring:

$p(D)=∫p(D∣θ)p(θ)dθ$

The denominator $p(D)$ requires integrating over all possible values of the parameters. For simple conjugate pairs of priors and likelihoods, the integral can be computed exactly but most real world models break conjugacy. This means the integral has no analytic solution. Even with simple conjugate pairs, when the parameter space is high-dimensional or extremely large (e.g. millions of parameters) as is common in data science, doing exact integration becomes computationally impossible.

When the posterior is intractable, Bayesian inference relies on approximation methods that compute an approximation of the posterior. Some of the most commonly used methods are Markov Chain Monte Carlo (MCMC), variational inference and Laplace approximation.

### Markov Chain Monte Carlo methods (MCMC)

This is perhaps the most popular approach where samples are drawn from the posterior and these are then used to approximate expectations, probabilities and credible intervals by averaging over those samples. The most commonly used algorithm, Metropolis-Hastings is roughly as follows:

1. The user provides a “transition kernel,” a way of moving randomly from a current position in n-dimensional space to a new position.
2. The algorithm chooses an initial guess for a distribution θ0.
3. Sample a candidate x\* from a proposal distribution Q(θ1∣θ0). This gives us a new proposed value for our next position.
4. Compute the probability that we should accept the new candidate and if it’s likely enough to lie within the target distribution, then select that as the current candidate and repeat steps 3 and 4.

Since the sampling is entirely random, there is no analytically derived definition of convergence for MCMC, but there are diagnostic techniques widely used by Bayesian statisticians, like examining trace plots or graphs of sampler output that can indicate when MCMC has arrived at a best estimate.

There are other variants like Gibbs sampling or the more computationally efficient variants Hamiltonian Monte Carlo, which uses gradient information to make proposals more efficient.

### Variational inference (VI)

This is an alternative to MCMC, which can be slow and computationally intensive. VI works by attempting to find a density function for a simpler distribution that most closely approximates the posterior (e.g., a Gaussian), and then optimizing that approximation.

### Laplace approximation

This is, in many ways, the simplest deterministic method to determine the characteristics of the posterior. The Laplace approximation attempts to find a Gaussian approximation around the mode of the posterior. With large and higher-dimensional data this can be a helpful technique.

Bayesian programs are often written in Stan, a programming language that offers bindings to R and Python. Other libraries like PyMC and Pyro have been developed to enable probabilistic programming of many kinds, including Bayesian modeling.

## Uncertainty

Perhaps the most important feature of Bayesian statistics is that it treats [uncertainty](https://www.ibm.com/think/topics/uncertainty-quantification) explicitly. Unlike frequentist approaches which produce a single estimate, Bayesian approaches output full probability distributions over unknowns. This is important because it enables reasoning about the uncertainty of the observed data overall as well as the model itself and each parameter within. This is especially useful in contexts with limited data, hierarchical structures, or where prior information is substantively important.

Philosophically Bayesian statistics takes a subjective interpretation of probability as containing an element of subjective belief. This is different from a strictly frequentist approach which views probability as emerging only from observed data and not from any other information. In practice, Bayesian methods are widely applied in fields such as [machine learning,](https://www.ibm.com/think/topics/machine-learning) epidemiology, econometrics and cognitive science, where uncertainty quantification and principled incorporation of prior knowledge are essential.

In Bayesian statistics, parameters, predictions and even hypotheses are treated as random variables with probability distributions. Rather than producing a single estimate (e.g., a maximum likelihood point), the Bayesian framework gives a full distribution, the posterior probabilities of all features of the model, that reflects the entire range of plausible values and their relative credibility.[^2]

This means uncertainty isn’t something added on after the fact (like a standard error), but is intrinsic to the inference process.

Because everything uncertain is represented probabilistically, uncertainty at one stage carries through to the next. For example, in hierarchical Bayesian models, uncertainty about group-level parameters feeds into estimates of individual-level parameters. Similarly, when making predictions, the predictive distribution integrates over parameter uncertainty, rather than assuming parameters are fixed. This propagation avoids overconfidence and yields calibrated measures of uncertainty.

Bayesian inference produces credible intervals (probability statements about parameters) and posterior predictive distributions (probability distributions over future observations). Unlike frequentist confidence intervals, which have indirect interpretations, Bayesian outputs are uncertainty statements, for instance, “There is a 95% probability that the parameter lies in this interval.”

Think Keynotes

### Win the enterprise AI race

Join Arvind Krishna to see how IBM is enabling AI-first enterprises through hybrid cloud and emerging quantum capabilities.

## Hypothesis testing

Hypothesis testing is where a scientist or statistician attempts to determine whether a hypothesis is valid or not given some observed data. In the case of a drug for a disease, the hypothesis might be that the drug cures the disease. That hypothesis is easy to test in a randomized control trial because the drug works or it does not. A more challenging case can be found in a wind farm. A wind turbine may be under-performing because important mechanical parts are beginning to fail or because the wind hasn’t been blowing as much as anticipated. Allowing the comparison of two distinct hypotheses is one of the areas where Bayesian statistics shine.

In Frequentist statistics a p-value is commonly used to represent how well a model has estimated a parameter value. Technically a p-value is the probability of observing data as extreme as or more extreme than the observed, assuming that the null hypothesis ( $H0$ ) is true.

p-value = P(Data as extreme as observed | $H0$ )

The p-value is not the probability that ( $H0$ ) is true, it measures how surprising the data would be if ( $H0$ ) were true. Small p-values (e.g., < 0.05) suggest the data are inconsistent with ( $H0$ ), but they don’t directly compare ( $H0$ ) to an alternative. This is why Frequentist statistics is often described as Null Hypotheses Testing because it enables comparing any hypotheses to the null hypotheses.

In Bayesian statistics methods, the Bayes factor is used to compare two hypotheses directly by how well they explain the observed data:

$BF=p(D∣H1)p(D∣H0)$

If BF=10, that would indicate that the data are 10 times more likely to occur under the alternative hypothesis ( $H1$ ) than under ( $H0$ ). There is no rigid rejection threshold as in a p-value, instead the Bayes Factor simply calculates how much more likely one hypothesis is than the other. The Bayes factor directly compares hypotheses by using the likelihood of the observed data under each. The statistician can then update prior odds into posterior odds:

$P(H1∣D)P(H0∣D)=BF·P(H1)P(H0)$

Using a drug efficacy trial as an example, a p-value of 0.03 could be interpreted as indicating that if the drug had an effect although there’s a 3% chance of seeing the results seen in the trial simply by random chance. In the same scenario, a Bayes factor of 10 would indicate that the data are 10 times more likely to occur if the drug works than if the drug does not work. When trying to determine whether a wind turbine is underperforming because of a mechnical issue or because of lower than expected wind, the Frequentist interpretation is more challenging, whereas the Bayes factor can be easier to interpret.

## Priors

Priors are a source of confusion in Bayesian statistics. Bayesian methods are sometimes described as “subjective” because they use priors while frequentist methods do not. Priors do encode subjective beliefs but those often are based on empirical data, physical symmetries, or regularization principles. Choosing a likelihood or model form is equally subjective in either a Frequentist or Bayesian approach. The Bayesian framework just makes those assumptions explicit.

Another common misconception is that the prior overwhelms the data and creates unreliable results. However if the prior is uninformative or if enough data is present, then that data will dominate and the posterior will converge toward the same result as frequentist estimates. Priors only dominate when data are scarce or contain significant irregularities. This is when including prior knowledge is the most helpful.

### Selecting Priors

An important element of doing Bayesian data analysis is selecting priors. When there is reliable information about the probability of an event that informs how data can be interpreted, that information can be incorporated in what is called an informative prior. This informative prior should affect how subsequent information is interpreted. The posterior should take into account the previous information as well as the new evidence. In practice the shape of the prior distribution can indicate how strongly that information should affect the probable posterior values. Choosing priors is where Bayesian analysis shifts from plugging in numbers to carefully considered statistical thinking.

In the case that there is not any such data, statisticians will often use an uninformative or flat prior consisting of a uniform distribution which does not overly bias the estimate of the posterior. These flat priors indicate that a wide range of possible values could be true and thus previous information should not strongly affect the probable posterior values calculated in the Bayesian estimation process.

A data scientist may choose what is called a conjugate prior if they believe that the posterior belongs to the same family as the prior. With a conjugate prior the posterior has a closed form which means that there’s no need for MCMC. Two commonly used conjugate priors are using a Beta Distribution when a Bernoulli random variable best represents the observed data and using a Gamma prior when a Poisson distribution best represents the observed data.[^3]

## Linear Regression

Suppose you want to model the relationship between study hours $x$ and exam scores $y$. You might begin with a simple linear statistical model that looks like the following:

$yi=β0+β1xi+εi,εi∼N(0,σ2)$

The following variables are represented in this model:

- $β0$ = intercept
- $β1$ = slope
- $ϵ$ = noise variance. One of the assumptions of linear regression is that the error is normally distributed with a mean of 0 and a standard deviation of $σ2$

Here’s how the approaches to fitting this model in a Frequentist and Bayesian paradigm would differ.

### Frequentist Estimation (OLS)

A classically frequentist approach would treat $β0$, $β1$ as fixed but unknown values. An algorithm like least squares would be used to minimize the error in the estimation of $β0$, $β1$:

$β1^=∑(xi-x¯)(yi-y¯)∑(xi-x¯)2$

$β0^=y¯-β1^x¯$

This would produce a single point estimate for each $β0$ and $β1$. Any uncertainty in those estimates would be described indirectly by confidence intervals and standard errors.

### Bayesian Estimation

When estimating the relationship between study hours and exam scores using Bayesian statistical methods, the data scientist would treat each of $β0$, $β1$ and $σ2$ as random variables. They would specify priors for each of those values:

$β0∼N(0,102)$

$β1∼N(0,102)$

$σ2∼Inverse-Gamma(1,1)$

This states that the data scientist believes that $β0$ and $β1$ are somewhere within a normal distribution centered around 0 and that the errors are probably small but never negative. The inverse-gamma distribution models this belief because it has 0 as a lower bound and the majority of the probable values below 2.

 ![[Image 5.png|The inverse gamma distribution, which is often as a prior for errors.]]The inverse gamma distribution, often as a prior for errors.

The data would be used to modify those parameters

$p(y∣β0,β1,σ2,x)=∏iN(yi∣β0+β1xi,σ2)$

The Posterior then is derived via Bayes’ theorem:

$p(β0,β1,σ2∣data)∝p(y∣β0,β1,σ2,x)·p(β0)·p(β1)·p(σ2)$

This posterior distribution gives a range of plausible values for slope and intercept, not just single estimates for each. This can make it easier to observe how extreme values for studying affect test scores and also shows which parameters have high certainty, which are more ambiguous given the data.

The frequentist model would provide a predicted score for 10 hours of study:

$y^=β0^+β1^·10$

The Bayesian model would sample from the posterior of $β0$, $β1$, $σ2$ and generate a distribution of predicted scores for 10 hours of study. The more informative and aligned that the data and the priors are, the narrower that generated distribution would be.

## Hierarchical Modeling

Bayesian approaches are especially powerful in hierarchical modeling. Hierarchical modeling is a model where the values of certain parameters depend on other parameters within the model. In the case of studying and test scores, the difficulty of a class and the seniority of the students in that class may affect the amount of studying required. Having distributional estimates for each of these parameters can give vital insights into how much certainty exists for each parameter and their interactions as well as for the final inference from the model.

A Bayesian hierarchical model typically contains three different levels of predictions: an individual likelihood, a group level and a population level. In the case of student test scores this would be each individual student, each school and then all students as a whole. This would be broken into the following:

An individual student i in school j would be modeled by a normal distribution shaped by the information we know about all students $σ2$ and about the school that the student attends $θj$:

$(yij∣θj,σ2)∼N(θj,σ2)$

Each school would be modeled by a normal distribution shaped by using what we know about all students and what we know about that school $τ2$

$(θj∣μ,τ2)∼N(μ,τ2)$

Finally, all students are modeled using a population level information:

$μ∼N(0,σμ2)$

This states that the population mean is near 0, but uncertain with scale $σμ2$

$τ2∼Inverse-Gamma(a,b)$

Finally, as in the previous section, the errors are likely to be an inverse-gamma distribution. If the data proves otherwise, the modeling process will correct this, but this is a safe prior to begin with.

These values don’t fix the population average ( $μ$ ) or the spread across schools ( $τ2$ ). Instead both are informed by the observed data. Each level of the model is assigned its own prior and each student or school can have uncertainty assigned to them. This can be important since one school may have plenty of students and thus allow for far more accurate predictions where another with fewer students and thus a smaller sample size will lead to less accurate predictions. This kind of uncertainty at different levels allows a data scientist to see where their predictions are confident and where they are not.

Bayesian statistics offers a powerful approach to comparing hypotheses and reasoning about uncertainty in data and modeling. It is not as commonly used as Frequentist statistics because the computational resources to utilize it are only now available to everyone. It also can be slightly more challenging to get comfortable with, particularly the use of priors when calculating a posterior. However, when predictions require uncertainty calculations or when a data scientist needs to compare different models or hypotheses, the Bayesian approach offers a great deal of invaluable information.

Link copied

[Data science and MLOps for data leaders](https://www.ibm.com/forms/mkt-51585)

[

Join forces with other leaders to drive the three essential pillars of MLOps and trustworthy AI: trust in data, trust in models and trust in processes.

](https://www.ibm.com/forms/mkt-51585)

[^1]: Gelman, A., Hill, J., & Vehtari, A. (2020). Regression and Other Stories. Cambridge University Press

[^2]: Gelman, A., Carlin, J.B., Stern, H.S., Dunson, D.B., Vehtari, A., & Rubin, D.B. (2013). Bayesian Data Analysis (3rd ed.). Chapman and Hall/CRC

[^3]: Bernardo, J. M., and Smith, A. F. M. (2009) Bayesian Theory, Wiley.