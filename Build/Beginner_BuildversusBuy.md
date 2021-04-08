<img width="687" alt="image" src="https://user-images.githubusercontent.com/80533280/113980982-1fca0300-9815-11eb-8c91-9ebf4ec42f09.png">




## Build versus Buy Decisions

To build (in house) versus to buy (commercial off-the-shelf or bespoke solution, from a vendor or contracting company) software decisions are common among large organizations, and [government agencies](https://www.acquisition.gov/policy-network) at [every level](https://doit.maryland.gov/SDLC/Documents/Build%20Versus%20Buy.pdf) are no exception. These decisions take on an added degree of complexity, however, when dealing with AI/ML solutions, and taking into account issues of bias and fairness.  

Government build/buy decisionmaking has additional complexity compared to the private sector because of the government's increased concern with fairness and bias standards, and [its mandate across different program areas, agencies, and settings](https://www.epa.gov/laws-regulations/summary-executive-order-12898-federal-actions-address-environmental-justice) -- [sometimes a legislative mandate](https://home.treasury.gov/footer/privacy-act/computer-matching-programs) -- to ensure that protected or vulnerable subpopulations are treated fairly, and not subject to disproportionate risk or harm compared to other demographic groups or subpopulations.  

There exists significant documentation addressing the build/buy paradigm for software acquisitions. We expand that view by outlining specific bias and fairness considerations that figure into the machine learning acquisition decisions.   

In this section presents a high-level view of AI/ML bias, as might be encountered by a typical government practitioner. To this end, this section walks the reader through common sources of bias along the length of the machine learning pipeline, extended here to include composition of research and development and implementation teams before development even begins, and application of results to inform policies or programs at the tail end of the process. 




In this section, we walk through common sources of bias along the machine learning pipeline, to prepare users for a later discussions of how to assess and mitigate bias along the workflow. 

- [Institutional Knowledge and Configuration](#institutional-knowledge-and-configuration) 

-  [Vendor or software selection](#vendor-selection)

- [Data Collection and Preparation](#data-collection-and-preparation)

- [Model Selection, Development, and Training](#model-selection-development-and-training)

- [Model Deployment and Beyond](#model-development-and-beyond)



### Institutional Knowledge and Configuration 

[As noted in Engstrom et al. (2020)](https://law.stanford.edu/wp-content/uploads/2020/02/ACUS-AI-Report.pdf), agencies lack protocols around ensuring diversity of AI/ML practitioners, and none of the largest federal agencies with active AI programs had any working protocols and processes to assess the potential impact of bias, as of 2020. The lack of practical tools and guidance to complement high-level recommendations like the [OMB](https://www.omb.gov) Guidance for Regulation of Artificial Intelligence Applications, which recommends agencies employ a tiered AI/ML risk management approach, suggests that agency workforces are not currently best configured to plan to navigate the bias landscape. Compounding this is lack of sufficiently diverse AI/ML, across demographic and other classficiations, which is troubling when studies suggest that the identity-based experiences of vulnerability resulting from diverse lived experiences have been associated [in recent research (McDonald and Pan, 2020)](https://dl.acm.org/doi/abs/10.1145/3415218) with complex thinking about AI, such as a heightened ability to reason about fairness across groups as well bias. 

### Vendor Selection

A significant proportion of AI/ML progress in government is fueled by agency acquisitions of off-the-shelf software, and/or building of tools by outside vendors. Whether these software is trained and developed with data or even methods well-understood to the agency or the build and training process is less transparent, the vendor selection and software acquisition can be rife with sources of bias, leading to eventual unfairness. As recent work [from the RAND Institute](https://www.rand.org/content/dam/rand/pubs/perspectives/PEA800/PEA862-1/RAND_PEA862-1.pdf) suggests, language in vendor solicitation or criteria for selection could discourage diverse vendors, or unintentionally promote certain classes of applicants over others. The paper suggests assessment criteria should be in some fashion validated for equity, as it relates to both applications or respondents and solution proposals.  Another relevant source of bias could be selection of a vendor that is not equipped, or is not instructed by the proposal, to develop a bias assessment, monitoring, or mitigation. A third possible source of bias at this stage is incomplete or misguided articulation of agency goals for the potential acquisition, which could guide vendors to develop products that are developed for a different application entirely.

### Data Collection and Preparation

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



