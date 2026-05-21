---
title: "What is upsampling?"
source: "https://www.ibm.com/think/topics/upsampling#1003835709"
author:
  - "[[Jacob  Murel Ph.D.]]"
published: 2002-05-31
created: 2026-05-21
description: "Upsampling increases the number of data samples in a dataset. In doing so, it aims to correct imbalanced data and thereby improve model performance."
tags:
  - "clippings"
---
## Resources

[Level up your ML expertise](https://developer.ibm.com/technologies/machine-learning/courses/)

[

Learn fundamental concepts and build your skills with hands-on labs, courses, guided projects, trials and more.

](https://developer.ibm.com/technologies/machine-learning/courses/)

[^1]: Haobo He and Edwardo Garcia, Learning from Imbalanced Data, IEEE, September 2009, [https://ieeexplore.ieee.org/document/5128907](https://ieeexplore.ieee.org/document/5128907) (link resides outside ibm.com). (1,2,10)

<sup>2</sup> Kumar Abishek and Mounir Abdelaziz, Machine Learning for Imbalanced Data, Packt, November 2023, [https://www.packtpub.com/product/machine-learning-for-imbalanced-data/9781801070836](https://www.packtpub.com/en-us/product/machine-learning-for-imbalanced-data-9781801070836) (link resides outside ibm.com). (3,4,6,8,9,12,14-17)

[^2]: Kumar Abishek and Mounir Abdelaziz, Machine Learning for Imbalanced Data, Packt, November 2023, [https://www.packtpub.com/product/machine-learning-for-imbalanced-data/9781801070836](https://www.packtpub.com/en-us/product/machine-learning-for-imbalanced-data-9781801070836) (link resides outside ibm.com). Alberto Fernandez, et al., Learning from Imbalanced Data Sets, 2018.

[^3]: Nitesh Chawla, et al., SMOTE: Synthetic Minority Over-sampling Technique, JAIR, 01 June 2002, [https://www.jair.org/index.php/jair/article/view/10302](https://www.jair.org/index.php/jair/article/view/10302) (link resides outside ibm.com).

[^4]: Kumar Abishek and Mounir Abdelaziz, Machine Learning for Imbalanced Data, Packt, November 2023. Haobo He and Edwardo Garcia, Learning from Imbalanced Data, IEEE, September 2009, [https://ieeexplore.ieee.org/document/5128907](https://ieeexplore.ieee.org/document/5128907) (link resides outside ibm.com).

[^5]: Alberto Fernandez, et al., Learning from Imbalanced Data Sets, Springer, 2018.

[^6]: Connor Shorten and Taghi Khoshgoftaar, A survey on Image Data Augmentation for Deep Learning, Springer, 06 July 2019\*\*,\*\* [https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0197-0](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0197-0) (link resides outside ibm.com).

[^7]: Zhen Wei, Li Zhang, and Lei Zhao, Minority prediction probability based oversampling technique for imbalanced learning, Science Direct, 06 December 2022, [https://www.sciencedirect.com/science/article/abs/pii/S0020025522014578?casa\_token=TVVIEM3xTDEAAAAA:LbzQSgIvuYDWbDTBKWb4ON-CUiTUg0EUeoQf9q12IjLgXFk0NQagfh0bU3DMUSyHL\_mjd\_V890o](https://www.sciencedirect.com/science/article/abs/pii/S0020025522014578?casa_token=TVVIEM3xTDEAAAAA:LbzQSgIvuYDWbDTBKWb4ON-CUiTUg0EUeoQf9q12IjLgXFk0NQagfh0bU3DMUSyHL_mjd_V890o) (link resides outside ibm.com).

[^8]: Zeyu Teng, et al., Multi-label borderline oversampling technique, ScienceDirect, 14 September 2023, [https://www.sciencedirect.com/science/article/abs/pii/S0031320323006519?casa\_token=NO8dLh60\_vAAAAAA:AWPCvCP8PQG43DvkQFChZF2-3uzB1GJBBtgPURevWe\_-aR0-WTbLqOSAsiwxulNAuh\_4mIDZx-Y](https://www.sciencedirect.com/science/article/abs/pii/S0031320323006519?casa_token=NO8dLh60_vAAAAAA:AWPCvCP8PQG43DvkQFChZF2-3uzB1GJBBtgPURevWe_-aR0-WTbLqOSAsiwxulNAuh_4mIDZx-Y) (link resides outside ibm.com).

[^9]: Justin Engelmann and Stefan Lessmann, Conditional Wasserstein GAN-based oversampling of tabular data for imbalanced learning, 15 July 2021, ScienceDirect, [https://www.sciencedirect.com/science/article/abs/pii/S0957417421000233?casa\_token=O0d1BtspA8YAAAAA:n2Uv3v2yHvjl9APVU9V\_13rQ9K\_KwT0P\_\_nzd6hIngNcZJE-fmQufDgR6XT1uMmDBHx8bLXPVho](https://www.sciencedirect.com/science/article/abs/pii/S0957417421000233?casa_token=O0d1BtspA8YAAAAA:n2Uv3v2yHvjl9APVU9V_13rQ9K_KwT0P__nzd6hIngNcZJE-fmQufDgR6XT1uMmDBHx8bLXPVho) (link resides outside ibm.com). Shuai Yang, et al., Fault diagnosis of wind turbines with generative adversarial network-based oversampling method, IOP Science, 12 January 2023, [https://iopscience.iop.org/article/10.1088/1361-6501/acad20/meta](https://iopscience.iop.org/article/10.1088/1361-6501/acad20/meta) (link resides outside ibm.com).