---
title: What is a feature engineering?
source: https://www.ibm.com/think/topics/feature-engineering#1003835715
author:
- '[[Jacob Murel Ph.D.]]'
- '[[ Eda Kavlakoglu]]'
published: null
created: 2026-05-21
description: What is feature engineering? Learn the methods and processes for transforming
  raw data into machine-readable variables
---
[^1]: Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* \[Feature engineering for machine learning\]. O’Reilly. 2018. Sinan Ozdemir and Divya Susarla. *Feature Engineering Made Easy* \[Feature engineering made easy\]. Packt. 2018.

[^2]: Yoav Goldberg. *Neural Network Methods for Natural Language Processing* \[Neural network methods for natural language processing\]. Springer. 2022.

[^3]: Suhang Wang, Jiliang Tang, and Huan Liu. “Feature Selection” \[Feature selection\]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

[^4]: Sinan Ozdemir. *Feature Engineering Bookcamp* \[Feature engineering bootcamp\]. Manning Publications. 2022. Sinan Ozdemir and Divya Susarla. *Feature Engineering Made Easy* \[Feature engineering made easy\]. Packt. 2018.

[^5]: Max Kuhn and Kjell Johnson. *Applied Predictive Modeling* \[Applied predictive modeling\]. Springer. 2016.

[^6]: Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* \[Feature engineering for machine learning\]. O’Reilly. 2018.

[^7]: Jiawei Han. *Data Mining: Concepts and Techniques* \[Data mining: concepts and techniques\]. 3rd edition. 2012.

[^8]: Kevin Murphy. *Machine Learning: A Probabilistic Perspective* \[Machine learning: a probabilistic perspective\]. MIT Press. 2012. Soledad Galli. *Python Feature Engineering Cookbook* \[Python feature engineering cookbook\]. 2nd edition. Packt. 2022.

[^9]: Max Kuhn and Kjell Johnson. *Applied Predictive Modeling* \[Applied predictive modeling\]. Springer. 2016.

[^10]: I.T. Jolliffe. *Principal Component Analysis* \[Principal component analysis\]. Springer. 2002.

[^11]: Chris Albon. *Machine Learning with Python Cookbook* \[Machine learning with Python cookbook\]. O’Reilly. 2018.

[^12]: Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* \[Feature engineering for machine learning\]. O’Reilly. 2018.

[^13]: Zahraa Abdallah, Lan Du, and Geoffrey Webb. “Data preparation” \[Data preparation\]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

[^14]: Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* \[Feature engineering for machine learning\]. O’Reilly. 2018.

[^15]: Zahraa Abdallah, Lan Du, and Geoffrey Webb. “Data preparation” \[Data preparation\]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017. Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* \[Feature engineering for machine learning\]. O’Reilly. 2018.

[^16]: James Kanter and Kalyan Veeramachaneni. “Deep feature synthesis: Towards automating data science endeavors” \[Deep feature synthesis: toward automating data-science work\]. *IEEE International Conference on Data Science and Advanced Analytics*. 2015. [https://ieeexplore.ieee.org/document/7344858](https://ieeexplore.ieee.org/document/7344858)

[^17]: Udayan Khurana, Deepak Turaga, Horst Samulowitz, and Srinivasan Parthasrathy. “Cognito: Automated Feature Engineering for Supervised Learning” \[Cognito: automated feature engineering for supervised learning\]. *IEEE 16th International Conference on Data Mining Workshops*. 2016. pp. 1304–130. [https://ieeexplore.ieee.org/abstract/document/7836821](https://ieeexplore.ieee.org/abstract/document/7836821). Franziska Horn, Robert Pack, and Michael Rieger. “The autofeat Python Library for Automated Feature Engineering and Selection” \[The autofeat Python library for automated feature engineering and selection\]. *Joint European Conference on Machine Learning and Knowledge Discovery in Databases*. 2019. pp. 111–120. [https://link.springer.com/chapter/10.1007/978-3-030-43823-4\_10](https://link.springer.com/chapter/10.1007/978-3-030-43823-4_10)

[^18]: Ahmad Alsharef, Karan Aggarwal, Sonia, Manoj Kumar, and Ashutosh Mishra. “Review of ML and AutoML Solutions to Forecast Time-Series Data” \[Review of ML and AutoML solutions for forecasting time-series data\]. *Archives of Computational Methods in Engineering*. Vol. 29. 2022. pp. 5297–5311. [https://link.springer.com/article/10.1007/s11831-022-09765-0](https://link.springer.com/article/10.1007/s11831-022-09765-0). Sjoerd Boeschoten, Cagatay Catal, Bedir Tekinerdogan, Arjen Lommen, and Marco Blokland. “The automation of the development of classification models and improvement of model quality using feature engineering techniques” \[Automation of classification-model development and quality improvement using feature-engineering techniques\]. *Expert Systems with Applications*. Vol. 213. 2023. [https://www.sciencedirect.com/science/article/pii/S0957417422019303](https://www.sciencedirect.com/science/article/pii/S0957417422019303). Shubhra Kanti Karmaker, Mahadi Hassan, Micah Smith, Lei Xu, Chengxiang Zhai, and Kalyan Veeramachaneni. “AutoML to Date and Beyond: Challenges and Opportunities” \[AutoML to date and beyond: challenges and opportunities\]. *ACM Computing Surveys*. Vol. 54. No. 8. 2022. pp. 1-36. [https://dl.acm.org/doi/abs/10.1145/3470918](https://dl.acm.org/doi/abs/10.1145/3470918)

[^19]: Yoav Goldberg. *Neural Network Methods for Natural Language Processing* \[Neural network methods for natural language processing\]. Springer. 2022.

[^20]: Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press. 2016. [https://www.deeplearningbook.org/](https://www.deeplearningbook.org/)

[^21]: Xinwei Zhang, Yaoci Han, Wei Xu, and Qili Wang. “HOBA: A novel feature engineering methodology for credit card fraud detection with a deep learning architecture” \[HOBA: a novel feature-engineering methodology for credit-card fraud detection using a deep-learning architecture\]. *Information Sciences*. Vol. 557. 2021. pp. 302–316. [https://www.sciencedirect.com/science/article/abs/pii/S002002551930427X](https://www.sciencedirect.com/science/article/abs/pii/S002002551930427X). Daniel Gibert, Jordi Planes, Carles Mateu, and Quan Le. “Fusing feature engineering and deep learning: A case study for malware classification” \[Fusing feature engineering and deep learning: a case study for malware classification\]. *Expert Systems with Applications*. Vol. 207. 2022. [https://www.sciencedirect.com/science/article/pii/S0957417422011927](https://www.sciencedirect.com/science/article/pii/S0957417422011927). Ebenezerm Esenogho, Ibomoiye Domor Mienye, Theo Swart, Kehinde Aruleba, and George Obaido. “A Neural Network Ensemble With Feature Engineering for Improved Credit Card Fraud Detection” \[A neural-network ensemble with feature engineering for improved credit-card fraud detection\]. *IEEE Access*. Vol. 10. 2020. pp. 16400–16407. [https://ieeexplore.ieee.org/abstract/document/9698195](https://ieeexplore.ieee.org/abstract/document/9698195)