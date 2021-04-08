<img width="687" alt="image" src="https://user-images.githubusercontent.com/80533280/113980982-1fca0300-9815-11eb-8c91-9ebf4ec42f09.png">

- [Understanding Bias in the AI Acquisition Process](#understanding-bias-in-the-AI-acquisition-process) 

- [Acquisition Bias: Where?](#acquisition-bias-where)

- [Looking Ahead](#looking-ahead)


## Understanding Bias in the AI Acquisition Process

To build (in house) versus to buy (commercial off-the-shelf or bespoke solution, from a vendor or contracting company) software decisions are common among large organizations, and [government agencies](https://www.acquisition.gov/policy-network) at [every level](https://doit.maryland.gov/SDLC/Documents/Build%20Versus%20Buy.pdf) are no exception. These decisions take on an added degree of complexity, however, when dealing with AI/ML solutions, and taking into account issues of bias and fairness.  

Government build/buy decisionmaking has additional complexity compared to the private sector because of the government's increased concern with fairness and bias standards, and [its mandate across different program areas, agencies, and settings](https://www.epa.gov/laws-regulations/summary-executive-order-12898-federal-actions-address-environmental-justice) -- [sometimes a legislative mandate](https://home.treasury.gov/footer/privacy-act/computer-matching-programs) -- to ensure that protected or vulnerable subpopulations are treated fairly, and not subject to disproportionate risk or harm compared to other demographic groups or subpopulations.  

There exists a significant literature and many guidelines addressing the build/buy paradigm for software acquisitions across the federal govenrment. Rather than repeat that information, we instead augment that knowledge by outlining specific bias and fairness considerations that figure into the machine learning acquisition decisions.  Possible ways to use these recommendations include to re-work the acquisition process and policies at the agency level; to delay acquisition until biasing factors are removed; or to build solutions in-house, if the expense and effort to de-bias the acquisition process is too steep. 



## Acquisition Bias: Where?

There are several points in the general acquisition process [(RAND, 2021)](https://www.rand.org/content/dam/rand/pubs/perspectives/PEA800/PEA862-1/RAND_PEA862-1.pdf) at which bias can arise. We break these down as follows:  

- Pre-acquisition Stage: 
- Vendor selection stage
- Model development
- System deployment and maintenance

In the **pre-acquisition** stage, which for general software acquisitions at the Census Bureau [entails an assessment of need, analysis of requirement, competitive assessment, and source selection planning](https://www.census.gov/about/business-opportunities/resources/faaps.html), a misunderstanding or mischaracterization of the AI/ML problem for which software is being procured could introduce bias into the system output, particularly if there is a mismatch between model and use case. Lack of involvement of subject matter or domain experts in software acqusitions teams -- which is quite common in many large oragnizations -- can exacerbate these issues, as can general misunderstandings of AI/ML application context, or a lack of sufficient diversity in the acquiring or acquisition planning team, which is generally known to contribute to biased outcomes in AI/ML work. Acquisition teams may be less likely to have training in AI/ML ethics than actual practitioners, and simply not apply bias mitigation thinking to the acquisition until it is too late. Thus, these teams might not incorporate essential bias and fairness assessment and mitigation guidance into the design documentation, software requiremnts, and early documentation so critical in deciding the eventual solution acquired, and its deployment.    

The **vendor selection** has several points of vulnerability with respect to AI/ML bias, some of which can be carried over from the previous stage if not adequately addressed [(Rubenstein, 2021)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3731106). These vulnerabilities include a misunderstanding or insufficient characterization of the actual machine learning use case. For example, if a supervised classification model is requested for a fraud detection use case in which there are very few labeled instances of fraudulent case data of a specific type, that specific type of fraud will likely be underrepresented in the model put into production. Another issue is written solicitations, which might be written in biased lanaguge, discouraging certain groups of vendors from submitting proposals, or written in such a way that does not specify the need for bias audits and migitation efforts. Finally, if the vendor selection does not formally consider bias awareness and mitigation plans, acquisition teams will introduce yet another potential source of dangerous bias into the selection process.

After vendors are selected, the **model development** phase begins (if the software is not an off-the-shelf solution). At this point, some of the same biases discussed throughout the build section of this resource and toolkit can seep into the model, especially if best practices discussed throughout those resources are not deployed. As a review, the data (training or test) could be polluted or incomplete, overrepresent or underrepresent a vulnerable population because of bad or biased data collection processes or bad data governance. The model might be developed inappropriately for the use case, and initial tests of performance and accuracy could be badly or incompletely run (particularly if vendors are not presented with a highly specific and practical bias-focused testing plan by the acquistion team). Further its errors might not be well aligned with the true impact in resource, financial, or human terms. Either situation could lead vendors and development teams to deploy a bad, potentially biased model that should never have been put into production, and would never have been deployed by a skilled internal team staffed with federal agency subject matter expert.  

The final step of the process is a stage of processes we call **system deployment and maintenance**. In this stage, there are again several possible points of bias-related weakness. First, processes downstream of initial model testing, including model verification or validation, might not encompass bias issues [(Osoba et al., 2019)](https://www.rand.org/pubs/research_reports/RR2708.html). The results of the model might lack intepretability or explainability, leading to misapplication or bias misinterpretation fo results. Further, there could be misconfigurations and technical failures in the system deployment (e.g., failure of model deployment APIs), or shift in distribution of data compared to training data, rendering the model's predictions incorrect and possibly biased. Another possible issue at this stage could be model degration from lack of maintenance and performance monitoring, which can lead to biased AI system outputs, which could happen if these activities are not specified in a vendor contract, or not related to the internal development team after handoff. Also, if there is no ongoing calibration of model output to practical decisions, the model could generate output that does not make sense for real-world application, leading to biased application of the ML system's results by policymakers and nontechnical practitioners [(RAND, 2021)](https://www.rand.org/content/dam/rand/pubs/perspectives/PEA800/PEA862-1/RAND_PEA862-1.pdf). 


# Looking Ahead

In conclusion, despite all of the recent progress made in AI ethics, some researchers have opined that federal procurement law remains a "dangerous blind spot" in the race to deploy ethical ML in algorithmic govenrnance settings [(Rubenstein, 2021)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3731106). We encourage AI/ML engineers, data scientists, and other federal government stakeholders to weigh the consequences of unaddressed sources of bias in the software acquistion pipeline as they decide whether to build or acquire ML tools. This resource will be updated as agencies remodel their acquistion processes and guidelines to address issues of AI ethics, bias and fairness.


