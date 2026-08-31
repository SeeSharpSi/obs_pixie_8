---
title: What is model risk management?
source: https://www.ibm.com/think/topics/model-risk-management
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2024-08-14
created: 2026-08-31
description: "Model risk management is the process of identifying, gauging and controlling model risk. Model risk occurs when a model is used to measure and predict quantitative information but the model performs inadequately."
---

## What is model risk management?

Model [risk management](https://www.ibm.com/topics/risk-management) is the process of identifying, gauging and controlling model risk. Model risk occurs when a model is used to measure and predict quantitative information but the model performs inadequately. Poor model performance can result in detrimental consequences, including significant financial losses.

A model is any quantitative approach, method or system that processes input data and produces quantitative estimates.<sup>1</sup> Models are typically applied when [making business decisions](https://www.ibm.com/think/topics/data-driven-decision-making), determining business opportunities and risks, devising business strategies and managing business operations.

Financial institutions, for instance, rely on a range of models for pricing, valuation and detecting and preventing fraud and money laundering, among other financial services. The use of models often poses risk, which makes model risk management (MRM) a crucial consideration for enterprises.

The 2007 to 2008 global financial crisis, for instance, was partially blamed on flawed value at risk (VaR) models, which estimated future losses that investments might incur.<sup>2</sup> In 2012, the JPMorgan Chase “London Whale” trading debacle resulted in USD 6 billion in losses and nearly USD 1 billion in fines.<sup>3</sup> This was partly due to a spreadsheet error in model calculations, understating risk.<sup>4</sup>

In 2021, real estate marketplace company Zillow took a USD 304 million inventory write-down and planned to slash a quarter of its workforce following its failed home-buying venture, which was partly caused by the inability of its housing price valuation model to accurately predict home prices.<sup>5</sup>

## Sources of model risk

Model risk can stem from various causes:

A model’s input data might be erroneous, incomplete, outdated or [biased](https://www.ibm.com/think/topics/ai-bias). If outdated data is used for a market model, for instance, then it might project skewed trends regarding market performance or market prices.

Also, if training data sets for [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) models aren’t evaluated for the presence of bias, these [AI models](https://www.ibm.com/think/topics/ai-model) can produce results that reflect and perpetuate the intrinsic bias in the data. For example, job applicant screening systems might favor male or younger applicants, while healthcare prediction software might exhibit racial bias when prioritizing patients in need of immediate care.

Assumptions might be flawed or unrealistic. Irrelevant, wrong, missed or omitted variables or incorrect variable calibrations can affect model output.

For instance, a pricing model that doesn’t factor in market volatility might produce inaccurate estimates, while product demand forecasting models that fail to consider seasonal purchasing behaviors or current economic conditions, such as shipping delays or decreased spending, might lead to poorly managed inventory levels.

Meanwhile, a patient care prediction model that puts a greater weight on a variable such as healthcare spending might result in the model discriminating against those who have lower incomes and thus spend less on healthcare but have a greater need to access it.

The chosen methodology might have inherent errors, so model developers need to be knowledgeable about the model and aware of its limitations. For example, statistical methods such as [regression](https://www.ibm.com/think/topics/linear-regression) modeling can have sampling and standard errors.

This is also where selecting the right model comes in. For instance, even though [generative AI](https://www.ibm.com/think/topics/generative-ai) is the latest technology, it might not be a strong fit for financial [forecasting](https://www.ibm.com/think/topics/forecasting), where other well-established models can do it for less work and lower cost.

Incomplete or incorrect model development can lead to inaccurate results or model errors. The same is true for programming errors, mistakes in approximations or calculations and other technical errors. Applying any shortcuts or simplifications as a result of model uncertainty and complexity might also affect the outcome.

For example, tight timelines to deploy a [predictive analytics](https://www.ibm.com/think/topics/predictive-analytics) model for sales performance might lead to using real-time data feeds of sales numbers. However, because of this decision, the model might fail frequently or be slow to run. In this case, switching to a daily or weekly data snapshot might improve the model’s speed and stability.

Rigorous testing can also help detect errors during implementation, such as accidentally using a different date format for an insurance claims assessment model or another unit of measurement for a healthcare diagnostics model, or inadvertently modifying the currency for a pricing model.

Misinterpreting the output of a model can lead to misinformed decision-making and taking the wrong course of action. This is where expert analysis is needed, with subject matter experts evaluating the soundness of a model’s results. [Explainability](https://www.ibm.com/think/topics/explainable-ai) and transparency are also crucial in determining how a model arrived at its conclusions.

Models might be misused or the wrong model might be applied to a certain scenario. A model’s design and specifications might also be unfit for a particular business case.

For instance, a model that helps hospitals triage patients faster in a particular state or region might not be suitable for a neighboring state or region due to varying demographics. Meanwhile, models that identify a lung condition in children from their chest scans might not be able to detect the same condition in adults.

## Managing model risk

If left unmanaged, model risk can wreak havoc on an organization’s finances, operations and reputation. Effective model risk management requires a framework that considers risk at every stage of a model’s lifecycle.

Management of model risk also entails following regulatory guidelines. In the US, for instance, the Federal Reserve and Office of the Comptroller of the Currency (OCC) released a [supervisory guidance on model risk management](https://www.federalreserve.gov/supervisionreg/srletters/sr1107a1.pdf), which serves as a benchmark for an MRM framework.

Here are six common steps toward an effective model risk management framework:

### 1. Model risk identification

Identifying risks is the first step in model risk management. This involves conducting a model inventory and defining the risks associated with each model.

### 2. Model risk assessment

The next step is to measure and evaluate model risk. Enterprises can come up with a rating system that ranks model risks according to priority, probability of occurrence and the gravity of their effects, among other metrics.

In addition to individual model risk measurement, companies can consider aggregate model risk as well. Aggregate model risk refers to the risks posed by the dependencies and interactions among different types of models. For instance, the results of a healthcare diagnostics model might feed into a patient care prediction model. If the diagnostics model exhibits bias, then that bias might carry over to the prediction model, affecting who might get urgent care.

### 3. Model risk mitigation

Mitigating risk requires addressing its sources and causes. Here are a few [risk mitigation](https://www.ibm.com/think/topics/risk-mitigation) strategies that can be integrated into a model risk management framework:

- Audits and reviews: Companies can conduct their own internal audits of their models or employ third-party experts to carry out independent reviews.

- Standards: Creating standards for the modeling process can help minimize risk. Standards can be crafted for data collection, the model design and development process, testing, documentation and model use.

Not all risks can be mitigated, so enterprises might still be subject to a certain amount of risk exposure. Therefore, organizations might find it helpful to set their risk appetite. This is the level of risk a company is willing and prepared to tolerate and can assume when it comes to its use of models.

### 4. Model validation

The validation process acts as an effective challenge of a model to check its quality and verify its results. Model validation is done after implementation and before release to model users. It encompasses both quantitative and qualitative approaches.

Quantitative model validation includes these strategies:

- Backtesting is a form of outcomes analysis that uses real-world historical data to test a model, thus assessing its accuracy and effectiveness.

- Challenger models are alternative models developed to challenge a “champion” model. Both champion and challenger models use the same data, and their results are compared to reveal any potential or hidden risks.

- Sensitivity analysis examines how altering a specific variable under certain conditions affects other variables.

- Stress testing applies simulations based on speculative or theoretical scenarios to see how a model responds.

Meanwhile, qualitative model validation considers factors such as a model’s suitability for its purpose and whether a model conforms to standards or complies with regulations.

### 5. Model monitoring

Model [monitoring](https://www.ibm.com/think/topics/compliance-monitoring) continually scrutinizes models to check whether they’re still functioning as intended and continue to perform as expected. It pinpoints any additional risks that might arise or updates needed as a result of changes to data, processes and regulations.

Model validation is typically part of the ongoing monitoring process. At this stage, monitoring and validation reports are produced and reviewed by the relevant stakeholders to recommend any necessary course of action.

### 6. Model governance

Model [governance](https://www.ibm.com/think/topics/grc) offers oversight of the entire modeling process. It establishes a system of ownership and control through policies and procedures. Sound model risk governance needs a varied team of decision-makers and stakeholders—from the board of directors and senior management to model owners, model developers and model users.

## AI for model risk management

Many of today’s models employ AI and [machine learning](https://www.ibm.com/think/topics/machine-learning) in some form, particularly when generating and testing models.

For instance, [AI is commonly applied in the financial industry](https://www.ibm.com/think/topics/artificial-intelligence-finance) to model credit risk, market risk and [operational risk](https://www.ibm.com/think/topics/operational-risk). The technology can help assess credit and lending risk, create market models and aid in detecting financial fraud and money laundering.

AI and machine learning can also be applied to model risk management, especially during model validation (such as stress testing market models) and real-time model monitoring. Here are some common machine learning algorithms and methods used in model risk management:

- [Clustering](https://www.ibm.com/think/topics/clustering) can be implemented for sensitivity analysis to uncover anomalies that might indicate risk when variables are changed or when simulating specific scenarios.

- [Decision trees](https://www.ibm.com/think/topics/decision-trees) can be combined with neural networks to monitor trading models, for instance, alerting traders of changes to underlying patterns during trading.

- Both [deep learning](https://www.ibm.com/think/topics/deep-learning) and [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) can be used for real-time model monitoring, detecting issues and automatically recommending resolutions.

- [Neural networks](https://www.ibm.com/think/topics/neural-networks) can aid with stress testing, helping banks model their liquidity under challenging economic conditions, such as a recession.

## Model risk management software

Model risk management software can help organizations manage model risk more effectively. It provides advanced features, such as model inventory and tracking and mapping metrics, models and policies to multiple regulatory requirements. Other model risk management tools also allow for [AI and machine learning model management](https://www.ibm.com/think/insights/ai-risk-management), with capabilities that include automation of model monitoring and model validation.

## Footnotes

<sup>1</sup> “[SR 11-7: Guidance on Model Risk Management](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm)”, Federal Reserve, 4 April 2011.

<sup>2</sup> “[Structural causes of the global financial crisis: a critical assessment of the ‘new financial architecture’](https://academic.oup.com/cje/article/33/4/563/1730705)”, Cambridge Journal of Economics, 1 July 2009.

<sup>3</sup> “[JPMorgan fined USD 920 million in ‘London Whale’ trading loss](https://www.bbc.com/news/business-24159801)”, BBC, 19 September 2013.

<sup>4</sup> “[Model risk – daring to open up the black box](https://www.actuaries.org.uk/system/files/field/document/Model%20risk%20%E2%80%93%20daring%20to%20open%20up%20the%20black%20box.pdf)”, British Actuarial Journal, December 2015.

<sup>5</sup> “[Zillow’s home-buying debacle shows how hard it is to use AI to value real estate](https://edition.cnn.com/2021/11/09/tech/zillow-ibuying-home-zestimate/index.html)”, CNN, 9 November 2021.
