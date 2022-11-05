# Who is dropping out of college? 

College dropouts are often romanticised in popular culture as the rebels who changed the world. But dropping out of college usually entails emotional distress and loss of investment for most students. It also hurts the universities as it affects their performance records and expected outcomes. But, what if we can predict who is likely to drop out? The universities might be able to offer support to those students at risk. The students themselves might be better placed to take an informed decision about their futures.

Why do someone drop out of college? From empirical evidence, we can guess that the social and economic background of the students and their parents would play a major role. Their past and present academic performance would also be key. Most educational institutions already collect this information as part of their enrollment and tracking processes. 

For this case study, I chose publicly available data related to students enrolled in undergraduate courses at the Polytechnic Institute of Portalegre, Portugal.

[Data Source](https://archive-beta.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

For a detailed summary of the analysis with visualisation and some code. Check out my [blog post](https://deepnote.com/@esviswajith/Student-Dropout-Prediction-c7cdc385-bd2f-45d4-98c5-f8c691d0a4cd).

**Key Insights**

* 32% of the students have dropped out and another 18% of students graduated late.
* Most of the students who drop out, do so before completing their first or second semester. Those who drop out later have a lower grade compared to others.
* The following 5 courses have very high dropout and require immediate attention
    * Biofuel production technologies(70%)
    * Informatics engineering(56%)
    * Equinculture(51%)
    * Basic Education(45%)
    * Management(evening attendance)(45%)
* Male students have a much higher dropout rate(45%) than female students(24%).
* 40% of the dropouts are 25 years or older at the time of enrollment, while more than 80% of the students who graduated are younger than 25.
* Parents' backgrounds have an impact on graduation outcomes
    * Students whose parents have finished high school are slightly more likely to graduate than those who haven't. But students whose parents have a bachelor's degree or higher are more likely to drop out or graduate late
    * Students whose parents are blue-collar workers are more likely to graduate than that of white-collar workers.
    * Higher dropout rates are observed among students whose parent is not working.
* The dropout rate among indebted students is very high(64%)
* High dropout rates are observed among students who have joined after completing high school or a bachelor's degree. But a majority of students joining after secondary school are graduating.

For a detailed EDA, check out [this notebook](https://github.com/esviswajith95/enrollment_status/blob/main/notebooks/02-esv-EDA_deep_dive.ipynb).

**Predicting dropouts**

We are only interested in predicting who might drop out. Therefore the problem is framed as a binary classification problem with classes, 'Dropout'(encoded as 1) and 'Graduate'(encoded as 0). 

Since most student dropouts happened within the first two semesters, only the information available at the time of enrollment was considered for predictive analysis. The intention behind predicting the potential dropout is to extend support to them. Therefore, our models must be optimised to capture as many students dropping out as possible. This means that the ML metric to optimise is Recall. 

The best predictions were based on Logistic regression applied after oversampling the data to correct for class imbalance. This model was able to detect 74% of the students dropping out(Recall - 0.74). But, only 51% of the students identified to be at risk of dropping out, eventually dropped out.

For details of the modelling process, check out [this notebook](https://github.com/esviswajith95/enrollment_status/blob/main/notebooks/05-esv-binary_models_for_dropout.ipynb)
