<img width="807" alt="image" src="https://user-images.githubusercontent.com/80533280/113942840-8cbaaa00-97cf-11eb-9791-b5c3f852c81d.png">


# Inspecting your Data for Bias: Basic Overview for Beginners

In this section, we presents a high-level overview of tools and techniques for debiasing data that are accesible to beginners with minimal machine learning background. For a more hands-on approach, please consult the [Intermediate Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Intermediate/Intermediate_DataTools.md) or [Advanced Data Tools](https://github.com/XDgov/MLBias/blob/main/Build/Advanced/Advanced_DataTools.md) sections elsewhere in this respository. 


- [Sources of Data Bias](#sources-of-data-bias) 

- [Why Address Data Bias](#why-address-data-bias)

- [How to Address Data Bias](#how-to-address-data-bias)


Before proceeding, note that the general fairness paradigm applied in this resource kit is one that seeks to make the entire AI/ML system fair, and to ensure fair overall outcomes as defined for the AI/ML use case.  In this paradigm, bias and fairness inspection should to span the entire pipeline, and is necessary but not sufficient for ensuring unbiased overall outcomes. 


### Sources of Data Bias

First, what is *data bias* in the context of machine learning in government contexts?  In short, data bias is a data quality issue -- missing values, incorrect values, information distoration, mislabeled data -- that systematically affects a subpopulation, such as a demographic group (women ages 65+) or sub-class of collected data (post offices in New York City specifically)  Where does it come from? For a beginner's view, there are a few major ways bias can be introduced into the machine learning pipeline in the form of data quality issues:

<img width="689" alt="image" src="https://user-images.githubusercontent.com/80533280/114029026-1b1e4280-9847-11eb-9afc-c4acb5a43645.png">


**need to recreate this image in a quick file, don't want to use someone else's image where***



-**Data Source** Where are we obtaining our data? If we have not prepared the data ourselves and are acquiring it from a vendor, or combining our data with databases from a vendor or even other agency, there is always the possibility that this data contains some quality issues, bad data, incorrectly labeled fields, and so on. These quality issues may affect specific subpopulations (i.e., all weight values for left-handed women might be inflated by ten because of a recording error), and thus a lack of data quality uniformity could conceivably introduce bias into our pipeline.

Subtypes of data source error include issues in data collection. For example, if our survey contains biased language that alienates a certain group of people, or induces them to respond a certain way, our data collection is might include gaps or incorrect data about a demographic group or population. Another common type of data source bias arises from data collection technique rests and rests on biased assumptions -- as a crude example, if we assume that women with children are not typically leaders, we might design a sampling technique for a leadership survey that does not include mothers, or a survey that does not allow women leaders to indicate family sizes over two people.   



The way the target variable/label is defined and each data point is labeled might represent disparities between groups.


Differential measurement accuracy across groups (labeling quality).

A variable can be positively correlated with target variable within the majority group but negatively on other groups.

Police Internal Investigations for example






### Why Address Data bias

A significant proportion of AI/ML progress in government is fueled by agency acquisitions of off-the-shelf software, and/or building of tools by outside vendors. Whether these software is trained and developed with data or even methods well-understood to the agency or the build and training process is less transparent, the vendor selection and software acquisition can be rife with sources of bias, leading to eventual unfairness. As recent work [from the RAND Institute](https://www.rand.org/content/dam/rand/pubs/perspectives/PEA800/PEA862-1/RAND_PEA862-1.pdf) suggests, language in vendor solicitation or criteria for selection could discourage diverse vendors, or unintentionally promote certain classes of applicants over others. The paper suggests assessment criteria should be in some fashion validated for equity, as it relates to both applications or respondents and solution proposals.  Another relevant source of bias could be selection of a vendor that is not equipped, or is not instructed by the proposal, to develop a bias assessment, monitoring, or mitigation. A third possible source of bias at this stage is incomplete or misguided articulation of agency goals for the potential acquisition, which could guide vendors to develop products that are developed for a different application entirely.

### How to Address Data Bias

Government agencies typically collect their own data and build their own databases, but sometimes acquire or supplement their data from outside vendors, whose data 
might not be as well-vetted, or supplement their datasets with data from other agencies, whose data their are less familiar with.  There are a host of well-known survey-related biases, from sampling biases to nonrespondent bias to question design that biases respondents toward a particular answer, that can skew internal data such that machine learning work is biased in some way.  A lack of familiarity with datasets, such as those acquired from outside vendors or agency, makes it even more likely to encounter data quality issues that go unrecognize and taint ML training and testing sets during the later ML development lifecycle.  

A futher source of bias is methods commonly used for missing value imputation that are based on incorrect assumptions about whether data is missing at random. Some of these methods are known to distort demographic group proportions. As **XYZ** note, methods for multi-class classification for missing value imputation the most frequent classes as target variables, leading to a distortion for small population groups, because membership in these groups will never be imputed. As illustrated in paper **XYZ** suppose that some individuals identify as non-binary. Because the system only supports male, female, and unspecified as options, these individuals will leave gender unspecified. If mode imputation is used, then their gender will be set to male. A more sophisticated imputation method will still use values from the active domain of the feature, setting the missing values of gender to either male or female. This example illustrates that bias can arise from an incomplete or incorrect choice of data representation.  Another pitfall is a form that has home address as a field. A homeless person will leave this value unspecified, and it is incorrect to attempt to impute it. While dealing with null values is known to be difficult and is already considered among the issues in data cleaning, the needs of responsible data management introduce new problems. 

Data filtering and cleaning are minefields for dataset bias as well. As noted in **XYZ**,  when combining tables from the same dataset, OR combining datasets from varying sources, sdoing elections and joins can arbitrarily change the proportion of protected groups (e.g., for certain age groups) even if they do not directly use the sensitive attribute (e.g., age) as part of the predicate or of the join key. This change in proportion may be unintended and is important to detect, particularly when this happens during one of many preprocessing steps in the ML pipeline. During model development, Ann might have filtered the data by zip code or county to get a sample that is easier to work with. Demographic attributes such as age and income are highly correlated with places of residency, so such a seemingly innocent filtering operation might have heavily biased the data.

Yet another source of bias worth pointing out for agencies hoping to do NLP work is using pre-trained word embeddings. An example given in  **reference ABC** is that of code might replace a textual name feature with the corresponding vector from a word embedding that is missing for rare, non-Western names -- possible if there is a lack of representative data in a training set. If we then filter out records for which no embedding was found, we may disproportionately remove individuals from specific ethnic groups.

Unsound experimentation pre-development. Design and evaluation of ML models is a difficult and tedious undertaking, much more challenging in some aspects than conventional software development, and requires data scientists to engage in heavy experimentation at different stages of the development lifecycle.  It is unfortunately easy to make subtle mistakes that can heavily impact the quality of the resulting model.


### Model Selection Development and Training

For guidance on model selection and traning, please refer to the Intermediate ML Pipleine guide here. 

### Model Development and Beyond


For guidance on model selection and traning, please refer to the Advanced ML Pipeline guide here. 



