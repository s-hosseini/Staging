<img width="807" alt="image" src="https://user-images.githubusercontent.com/80533280/113942840-8cbaaa00-97cf-11eb-9791-b5c3f852c81d.png">


# Inspecting your Data for Bias: Basic Overview for Beginners

In this section, we presents a high-level overview of tools and techniques for debiasing data that are accesible to beginners with minimal machine learning background. For a more hands-on approach, please consult the [Intermediate Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Intermediate/Intermediate_DataTools.md) or [Advanced Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/Advanced_DataTools.md) sections elsewhere in this respository. 


- [Sources of Data Bias](#sources-of-data-bias) 

- [How to Address Data Bias](#how-to-address-data-bias)


Before proceeding, note that the general fairness paradigm applied in this resource kit is one that seeks to make the entire AI/ML system fair, and to ensure fair overall outcomes as defined for the AI/ML use case.  In this paradigm, bias and fairness inspection should to span the entire pipeline, and is necessary but not sufficient for ensuring unbiased overall outcomes. 


### Sources of Data Bias

First, what is *data bias* in the context of machine learning in government contexts?  In short, data bias is a data quality issue -- missing values, incorrect values, information distoration, mislabeled data -- that systematically affects a subpopulation, such as a demographic group (women ages 65+) or sub-class of collected data (post offices in New York City specifically).  Where does data bias arise in machine learning contexts? For a beginner's view, there are a few major ways bias can be introduced into the machine learning pipeline in the form of data quality issues:

<img width="689" alt="image" src="https://user-images.githubusercontent.com/80533280/114029026-1b1e4280-9847-11eb-9afc-c4acb5a43645.png">

[Source](https://docs.google.com/presentation/d/17o_NzplYua5fcJFuGcy1V1-5GFAHk7oHAF4dN44NkUE/edit#slide=id.g8d5290cc44_0_278)


-**Data Source Bias**: Where are we obtaining our data? If we have not prepared the data ourselves and are acquiring it from a vendor, or combining our data with databases from a vendor or even other agency, there is always the possibility that this data contains some quality issues, bad data, incorrectly labeled fields, and so on. These quality issues may affect specific subpopulations (i.e., all weight values for left-handed women might be inflated by ten because of a recording error), and thus a lack of data quality uniformity could conceivably introduce bias into our pipeline.

Subtypes of data source error include issues in data collection. For example, if our survey contains biased language that alienates a certain group of people, or induces them to respond a certain way, our data collection is might include gaps or incorrect data about a demographic group or population. Another common type of data source bias arises from data collection technique rests and rests on biased assumptions -- as a crude example, if we assume that women with children are not typically leaders, we might design a sampling technique for a leadership survey that does not include mothers, or a survey that does not allow women leaders to indicate family sizes over two people.   

**Outcome Bias**: As [Rodolfa et al](https://textbook.coleridgeinitiative.org/chap-bias.html#sec:biassources) explain, a separate source of bias inherent arises with the *labels*, or measured outcomes, of the population in your dataset, and the way they are defined and applied. Consider an example of transportation monitoring, in which a stretch of road that is more completely covered with high-quality traffic sensors is more likely to be found to have a high number of accidents, than a stretch of road with faulty sensor or less coverage, simply because more accidents are observed. Imagine the agency objective is to determine which streteches are road are most dangerous with respect to accidents, and therefore most in need of funding for rehabilitation. Using number of accidents measured in this way to when a transportation department is really trying to determine which stretches of highway are inherently dangerous, introduces a bias correlated with number of sensors (and possibly wealthy of an area), and can bias allocation of public works funding toward areas that simply have more or better systems of traffic sensors rather than a genuine need. The label or outcome we really want is true acccidents, not simply number of accidents we happen to capture.


**Data Pipeline Bias** Technical issues like faulty data ingestion, issues with dataset storage, misrouting of datasets, incorrect parsing of datasets, failure to automate consistent data transformation processes from day to day, can all distort and add bias to even perfect datasets collected and cleaned upstream. 


### How to Address Data Bias

We will address in-depth bias and fairness metrics and techniques in the Intermediate and Advanced Data Tools sections. Broadly, there are a few central techqniues for addressing dataset bias: 

- Fix the input data: If missing datasets or incorrect labels are the cause of bad data quality, fix those errors manually or programmatically. 
- Generate more data: If bad data needs to be expunged, or one class of data is underrepresented in the dataset, [generate synthetic data](https://openaccess.thecvf.com/content_CVPRW_2020/papers/w45/Jaipuria_Deflating_Dataset_Bias_Using_Synthetic_Data_Augmentation_CVPRW_2020_paper.pdf) with the expected distribution to balance out the dataset. 
- Resample and/or reweight protected groups: Changing weights assigned to protected class features, or adding/removing dataset elements with these features, in order to ensure sufficient representation inthe 
- Do post-data collection: Choose, train, optimize, and build a fair model, and do post-dhc adjustments to de-bias the output of your ML system -- See materials [here](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/Advanced_Bias_Evaluation.md) and 
[here](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/MachineLearningPipeline.md) within this resource kit for more details. 


We direct the reader to an outstanding set of external tools that can walk the reader through the bias inspection and reduction for machine learning data in one's machine learning training data. Here are two notable toolkits, one of which is written in R, and one of the which is written in Python: 


- [Aequitas](http://www.datasciencepublicpolicy.org/aequitas) Open source python toolkit developed by Carnegie Mellon/University of Chicago researchers. This kit includes a no-code tool that allows the user to upload a dataset, define populations of interest (i.e., a protected class as defined by the Department of Labor when collecting data for an employment study), define fairness metrics that *make sense given the agency or program mission* (i.e., ensure that left-handed students from Mississippi receive, proportionally, the same total amount of grand aid as left-handed students from every other state), and generate an in-depth report of biases contained in one's datasets.  

- [fairmodels](https://github.com/cran/fairmodels) -- an R language package that uses model visualizations to help users identify bias. In particular, it includes pre-processing algorithms that try to mitigate the bias between specific subgroups through inference from data.

