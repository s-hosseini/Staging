<img width="807" alt="image" src="https://user-images.githubusercontent.com/80533280/113942840-8cbaaa00-97cf-11eb-9791-b5c3f852c81d.png">


# Bias Post-Deployment


After deploying our model, what kinds of bias do we still need to be wary and cautious about? 

There are two broad categories of bias that we might need to consider. The first of these is *emergent bias*, which is a category of bias involves specific aspects of the application of ML that introduce distortions or errors of some kind. An example of this could be benefits routing automation that influences the way users self-categorize the writing applications. 
A second broad category of bias, and that which we focus on in this document, is that of *technical bias.* Technical bias is the set of issues that arise because of shortcoming, failures, or misconfigurations of the technical system itself (data pipeline, deployment, retraining, etc.) and can, alarmingly, amplify (Friedman and Nissenbaum, 1998).  In this section, we focus on the implications of the last category of bias for post-deployment bias. 


## Maintaining your model after deployment

After putting an AI/ML model into production, it will typically require ongoing work and maintenance  to protect from the model's degradation of fairness and accurcy/performance, and further care to improve the model output.  As Rodolfa et al. (2020) and others observe, even after completing a rigorous series of checks and balances on ones data and methods in the pre-deployment stage, frequently "bad" or incorrect models with mistakes will be put into production. These bad production models are a starting point for answering the question of what one needs to measure and how models need to be tweaked before and after production, which, as has been emphaszied throughot this toolkit, is a highly case-specific endeavor. 

The vast majority of models you put into production will make mistakes, and a responsible data scientist will seek to look closely at these mistakes and understand — on both individual and population levels — how to learn from them to improve the model. Ensuring errors are balanced across groups is a good starting point, but seeking to reduce these errors over time is an important aspect of fairness as well.

One challenge you may face in making these ongoing improvements to your model is with measuring outcomes in the presence of a program that seeks to change them. In particular, the measurement of true positives and false positives in the absence of knowledge of a counterfactual (that is, what would have happened in the absence of intervention) may be difficult or impossible. For instance, among families who have improved nutritional outcomes after receiving a food subsidy, you may not be able to ascertain which families’ outcomes were actually helped by the program versus which would have improved on their own, obfuscating any measure of recall you might use to judge performance or equity. Likewise, for individuals denied bail, you cannot know if they actually would have fled or committed a crime had they been released, making metrics like false discovery rate impossible to calculate.

During a model’s pilot phase, initially making predictions without taking action or using the model in parallel with existing processes can help mitigate some of these measurement problems over the short term. Likewise, when resources are limited such that only a fraction of individuals can receive an intervention, using some degree of randomness in the decision-making process can help establish the necessary counterfactual. However, in many contexts, this may not be practical or ethical, and you will need to consider other means for ongoing monitoring of the model’s performance. Even in these contexts, however, it is important to continually review the performance of the models and seek to both improve its performance in terms of both equity and efficiency. In practice, this may include some combination of considering proxies for the counterfactual, quasi-experimental inference methods, and expert/stakeholder review of the model’s results (both in aggregate and of selected individual cases).






There is a common misunderstanding in the AI/ML practitioners, even in 2021, about whether bias arises from models and algorithms or from 

In this section, we present a high-level overview of tools and techniques for debiasing data that are accessible to beginners with minimal machine learning background. For a more hands-on approach, please consult the [Intermediate Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Intermediate/Intermediate_DataTools.md) or [Advanced Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/Advanced_DataTools.md) sections elsewhere in this repository. 


- [Sources of Data Bias](#sources-of-data-bias) 

- [How to Address Data Bias](#how-to-address-data-bias)


Before proceeding, note that the general fairness paradigm applied in this resource kit is one that seeks to make the entire AI/ML system fair, and to ensure fair overall outcomes as defined for the AI/ML use case.  In this paradigm, bias and fairness inspection should to span the entire pipeline, and is necessary but not sufficient for ensuring unbiased overall outcomes. 


### Sources of Data Bias

First, what is *data bias* in the context of machine learning in government contexts?  In short, data bias is a data quality issue -- missing values, incorrect values, information distortion, mislabeled data -- that systematically affects a subpopulation, such as a demographic group (women ages 65+) or sub-class of collected data (post offices in New York City specifically).  Where does data bias arise in machine learning contexts? For a beginner's view, there are a few major ways bias can be introduced into the machine learning pipeline in the form of data quality issues:

<img width="689" alt="image" src="https://user-images.githubusercontent.com/80533280/114029026-1b1e4280-9847-11eb-9afc-c4acb5a43645.png">

[Source](https://docs.google.com/presentation/d/17o_NzplYua5fcJFuGcy1V1-5GFAHk7oHAF4dN44NkUE/edit#slide=id.g8d5290cc44_0_278)


-**Data Source Bias**: Where are we obtaining our data? If we have not prepared the data ourselves and are acquiring it from a vendor, or combining our data with databases from a vendor or even other agency, there is always the possibility that this data contains some quality issues, bad data, incorrectly labeled fields, and so on. These quality issues may affect specific subpopulations (i.e., all weight values for left-handed women might be inflated by ten because of a recording error), and thus a lack of data quality uniformity could conceivably introduce bias into our pipeline.

Subtypes of data source error include issues in data collection. For example, if our survey contains biased language that alienates a certain group of people, or induces them to respond a certain way, our data collection might include gaps or incorrect data about a demographic group or population. Another common type of data source bias arises from data collection technique rests and rests on biased assumptions -- as a crude example, if we assume that women with children are not typically leaders, we might design a sampling technique for a leadership survey that does not include mothers, or a survey that does not allow women leaders to indicate family sizes over two people.   

**Outcome Bias**: As [Rodolfa et al](https://textbook.coleridgeinitiative.org/chap-bias.html#sec:biassources) explain, a separate source of bias inherent arises with the *labels*, or measured outcomes, of the population in your dataset, and the way they are defined and applied. Consider an example of transportation monitoring, in which a stretch of road that is more completely covered with high-quality traffic sensors is more likely to be found to have a high number of accidents, than a stretch of road with faulty sensor or less coverage, simply because more accidents are observed. Imagine the agency objective is to determine which stretches of road are most dangerous with respect to accidents, and therefore most in need of funding for rehabilitation. Using number of accidents measured in this way to when a transportation department is really trying to determine which stretches of highway are inherently dangerous, introduces a bias correlated with number of sensors (and possibly wealthy of an area), and can bias allocation of public works funding toward areas that simply have more or better systems of traffic sensors rather than a genuine need. The label or outcome we really want is true accidents, not simply the number of accidents we happen to capture.


**Data Pipeline Bias**: Technical issues like faulty data ingestion, issues with dataset storage, misrouting of datasets, incorrect parsing of datasets, failure to automate consistent data transformation processes from day to day, can all distort and add bias to even perfect datasets collected and cleaned upstream. 


### How to Address Data Bias

We will address in-depth bias and fairness metrics and techniques in the Intermediate and Advanced Data Tools sections. Broadly, there are a few essential techniques for addressing dataset bias: 

- Fix the input data: If missing datasets or incorrect labels are the cause of bad data quality, fix those errors manually or programmatically. 
- Generate more data: If bad data needs to be expunged, or one class of data is underrepresented in the dataset, [generate synthetic data](https://openaccess.thecvf.com/content_CVPRW_2020/papers/w45/Jaipuria_Deflating_Dataset_Bias_Using_Synthetic_Data_Augmentation_CVPRW_2020_paper.pdf) with the expected distribution to balance out the dataset. 
- Resample and/or reweight protected groups: Changing weights assigned to protected class features, or adding/removing dataset elements with these features, in order to ensure sufficient representation across the dataset for sensitive groups and elements.
- Do post-data collection: Choose, train, optimize, and build a fair model, and do post-dhc adjustments to de-bias the output of your ML system -- See materials [here](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/Advanced_Bias_Evaluation.md) and 
[here](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/MachineLearningPipeline.md) within this resource kit for more details. 


We direct the reader to an outstanding set of external tools that can walk the reader through the bias inspection and reduction for machine learning data in one's machine learning training data. Here are two notable toolkits, one of which is written in R, and one of the which is written in Python: 

