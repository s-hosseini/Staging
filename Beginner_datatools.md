

<img width="807" alt="image" src="https://user-images.githubusercontent.com/80533280/113942840-8cbaaa00-97cf-11eb-9791-b5c3f852c81d.png">


# Inspecting your Data for Bias

In this section, we present a high-level conceptual overview of tools and techniques for debiasing data used to develop AI/ML systems.
 


## Sources of Data Bias

First, what is *data bias* in the context of machine learning in government?  
In short, data bias is a data quality issue -- missing values, incorrect values, information distortion, mislabeled data -- that systematically affects a subpopulation, such as a demographic group (for example, women ages 65+) or sub-class of collected data (post offices in New York City specifically).  Where does data bias arise in machine learning contexts? For a beginner's view, there are a few major ways bias can be introduced into the machine learning pipeline in the form of data quality issues:


<img width="635" alt="image" src="https://user-images.githubusercontent.com/80533280/114435545-462fcb80-9b92-11eb-8b88-1620d0229028.png">


<!-- -- Recreated the image and changed the wording a bit -- the link is here  https://docs.google.com/drawings/d/1vwYNGQV3wjqxe-y7-tnA58JIAUqalP4RPqXGBaAUxl0/edit  -- note that if you paste this note into Github markdown file, it will look invisible-->



What are common sources of bias in these contexts?

- **Data Source Bias**: Where are we obtaining our data? 
If we have not prepared the data ourselves and are acquiring it from a vendor, or combining our data with databases from a vendor or even other agency, there is always the possibility that this data contains some quality issues, bad data, incorrectly labeled fields, and so on. These quality issues may affect specific subpopulations (i.e., all weight values for left-handed women might be inflated by ten because of a recording error), and thus a lack of data quality uniformity could conceivably introduce bias into our pipeline.

Subtypes of data source error include issues in data collection. For example, if our survey contains biased language that alienates a certain group of people, or induces them to respond a certain way, our data collection might include gaps or incorrect data about a demographic group or population. Another common type of data source bias arises from data collection technique rests and rests on biased assumptions -- as a crude example, if we assume that women with children are not typically leaders, we might design a sampling technique for a leadership survey that does not include mothers, or a survey that does not allow women leaders to indicate family sizes over two people.   

- **Outcome Bias**: How are we labeling our data?
As [Rodolfa et al](https://textbook.coleridgeinitiative.org/chap-bias.html#sec:biassources) explain, a separate source of bias inherent arises with the *labels*, or measured outcomes, of the population in your dataset, and the way they are defined and applied. Consider an example of transportation monitoring, in which a stretch of road that is more completely covered with high-quality traffic sensors is more likely to be found to have a high number of accidents, than a stretch of road with faulty sensor or less coverage, simply because more accidents are observed. Imagine the agency objective is to determine which stretches of road are most dangerous with respect to accidents, and therefore most in need of funding for rehabilitation. Using number of accidents measured in this way to when a transportation department is really trying to determine which stretches of highway are inherently dangerous, introduces a bias correlated with number of sensors (and possibly wealthy of an area), and can bias allocation of public works funding toward areas that simply have more or better systems of traffic sensors rather than a genuine need. The label or outcome we really want is true accidents, not simply the number of accidents we happen to capture.


- **Data Pipeline Bias**: How is our data moving through our systems?
Technical issues like faulty data ingestion, issues with dataset storage, misrouting of datasets, incorrect parsing of datasets, failure to automate consistent data transformation processes from day to day, can all distort and add bias to even perfect datasets collected and cleaned upstream. 


### How might we Address Data Bias?
Broadly, there are a few essential techniques for addressing dataset bias: 

- Fix the input data: If missing datasets or incorrect labels are the cause of bad data quality, fix those errors manually or programmatically. 

- Generate more data: If bad data needs to be expunged, or one class of data is underrepresented in the dataset, [generate synthetic data](https://openaccess.thecvf.com/content_CVPRW_2020/papers/w45/Jaipuria_Deflating_Dataset_Bias_Using_Synthetic_Data_Augmentation_CVPRW_2020_paper.pdf) with the expected distribution to balance out the dataset. 

- Resample and/or reweight protected groups: Changing weights assigned to protected class features, or adding/removing dataset elements with these features, in order to ensure sufficient representation across the dataset for sensitive groups and elements.

- Do post-data collection: Choose, train, optimize, and build a fair model, and do post-dhc adjustments to de-bias the output of your ML system -- See materials on Advanced Data Evaluation in this toolkit. 


## Example: False Positive Rate Parity 

Here, we guide the reader through a basic exercise for identifying and dataset bias that one might encounter working with Census or other federal agency data. 

There are several types of metrics that one can define to capture “fairness” in a dataset. One of these is **false positive rate parity** -- 
equivalence of false positives among different populations in one’s datasets.

Let us assume we have a dataset with arrest outcomes in a geographic region for women ages [<18], [19-35], [36-50], and [51+], which our team 
hopes to use to train a machine learning model linking crime rates to home values or economic prosperity.  If we want to enforce fairness using 
false positive rate parity,we hope to see that in each of these groups, the false positive rate -- meaning, the percentage of people arrested despite
NOT having committed to crime -- is roughly equal across the three age groups we have defined:  


<img width="611" alt="image" src="https://user-images.githubusercontent.com/80533280/114435718-7bd4b480-9b92-11eb-8865-4327a33da74a.png">

Other examples of populations across which we might want parity of false positives, false negatives, and similar metrics in government machine learning work include ensuring applicant success rates of a protected class as defined by the Department of Labor do not differ from those of non-protected classes. Another example in the spirit of defining fairness metrics that *make sense given the agency or program mission*, could be ensuring that left-handed students from Mississippi receive, proportionally, the same total amount of grant aid as left-handed students from every other state using education-related datasets Census might work with to model optimal funding allocation and delivery models.

Once we have defined our metric of interest for a potential training set, we can choose a *disparity tolerance* level -- for example, one might specify that they are 90% tolerant, such that if we have a reference group with a false positive rate 20%, the comparison groups must be within 90% of that figure, or range from 18% to 22% false positive rate, in order to have “parity” with the first group.

Using these figures, and any of a number of open source dataset debiaising tool, statistical software packages, simple computations in a spreadsheet, or even a hand-computation], we calculate parity across our reference groups and obtain a set of values like the following: 


<img width="668" alt="image" src="https://user-images.githubusercontent.com/80533280/114435813-9c047380-9b92-11eb-8450-29f8a66145ad.png">



<!--  (shaudi) -- this is the linke to the spreadsheet https://docs.google.com/spreadsheets/d/1-LOiqpGQUdBgmxWMG2sPFzXA02HprGr1ACtNmjm2hHw/edit?usp=sharing-->

Given a reference population of 36-50, the cohorts 51+ and 19-35 clearly fall within 10% tolerance we specified above. The <18 cohort we reject, however, for falling outside of the 10% error range with respect to reference. We interpret this as meaning that according to our definition of “fairness” three populations are fair with respect to arrest rates, and we must expunge or resample our <18 age cohort in order to avoid introducing a source of avoidable bias.



Other methods can be walked through and executed in our Python fairness [Jupyer notebooks](http://jupyter.org); see below for an example of a fairness exercise assessing the fairness and bias in a dataset of grant applicants from different geographic groups.





To see how Census uses some of these techniques to combat data bias that distort survey results, read about how the US Census is addressing data bias Commodity Flows survey here [ADD LINK]. 

Have a use practical public sector case, tip, paper, or method to contribute to our resources? Let us know here [ADD LINK], and we will add your work to our resource kit! 








