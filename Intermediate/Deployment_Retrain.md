<img width="807" alt="image" src="https://user-images.githubusercontent.com/80533280/113942840-8cbaaa00-97cf-11eb-9791-b5c3f852c81d.png">


# Bias Post-Deployment


After deploying our model, what kinds of bias do we still need to be wary and cautious about? 

There are two broad categories of bias that we might need to consider. The first of these is *emergent bias*, which is a category of bias involves specific aspects of the application of ML that introduce distortions or errors of some kind. A federal government-related example of this could be benefits classifiers for routing automation that might influences the way those applying for housing or veterans' benefit  self-categorize when writing applications, because those classifiers might tell them how they "should" be describing themselves. 

A second broad category of bias, and that which we focus on in this document, is that of *technical bias.* Technical bias is the set of issues that arise because of shortcoming, failures, or misconfigurations of the technical system itself (data pipeline, deployment, retraining, etc.) and can, alarmingly, amplify (Friedman and Nissenbaum, 1998).  In this section, we focus on the implications of the last category of bias for post-deployment bias. 


# Maintaining your model's "fairness" after deployment

After putting an AI/ML model into production, it will typically require ongoing work and maintenance  to protect from the model's degradation of fairness and accurcy/performance, and further care to improve the model output.  As [Rodolfa et al. (2020)](https://textbook.coleridgeinitiative.org/chap-bias.html#sec:applications) and others observe, even after completing a rigorous series of checks and balances on ones data and methods in the pre-deployment stage, frequently "bad" or incorrect models with mistakes will be put into production. These bad production models are a starting point for answering the question of what one needs to measure and how models need to be tweaked before and after production, which, as has been emphaszied throughot this toolkit, is a highly case-specific endeavor. 

[Even experts have been obseved to fail to obey or misapply best practices](https://arxiv.org/pdf/1911.12587), so beginning data scientists and other practitioners should take particular care about the time after deployment in their model's life. Further complicating these considerations is the fact that these post-deployment technical fairness degradation can be affected by upstream issues discuss in other sections of this toolkit, like bad hyperparamter selection or lack of tuning. 

# Fairness Considerations for Intermediate Data Scientists

One challenge you may face in making these ongoing improvements to your model is with measuring outcomes in the presence of a program that seeks to change them. In particular, the measurement of true positives and false positives in the absence of knowledge of a counterfactual (that is, what would have happened in the absence of intervention) may be difficult or impossible. For instance, among families who have improved nutritional outcomes after receiving a food subsidy, you may not be able to ascertain which families’ outcomes were actually helped by the program versus which would have improved on their own, obfuscating any measure of recall you might use to judge performance or equity. Likewise, for individuals denied bail, you cannot know if they actually would have fled or committed a crime had they been released, making metrics like false discovery rate impossible to calculate.

During a model’s pilot phase, initially making predictions without taking action or using the model in parallel with existing processes can help mitigate some of these measurement problems over the short term. Likewise, when resources are limited such that only a fraction of individuals can receive an intervention, using some degree of randomness in the decision-making process can help establish the necessary counterfactual. However, in many contexts, this may not be practical or ethical, and you will need to consider other means for ongoing monitoring of the model’s performance. Even in these contexts, however, it is important to continually review the performance of the models and seek to both improve its performance in terms of both equity and efficiency. In practice, this may include some combination of considering proxies for the counterfactual, quasi-experimental inference methods, and expert/stakeholder review of the model’s results (both in aggregate and of selected individual cases).

# Tactical Approach: Categorizing and Addressing Post-Deployment Bias 

There are endless permutations of post-deployment fairness issues. What are the most critical to address for someone with intermediate-level experience in machine learning and data science? 

- A model trained for a specific decision can be uncalibrated for other decisions. This decision context creep occurs occasionally (e.g., the reported use of a recidivism risk estimation tool for informing decisions of sentence length). There is the further question of what decisions it may or may not be prudent to automate with ML models. Various factors enter into this decision: Is the goal merely decision effi- ciency? Do stakeholders need decision explana- tions? Are the ML models trusted in that domain? Is the decision high stakes? Is there meaningful human oversight in case of mistakes? Are there relevant, unbiased, historical data with which to train the model?
- A key value of ML decision aids is their ability to off-load expensive cognitive processing for decisionmaking. Over time, that off-loading leads to patterns of decision- making that increasingly and uncritically rely
on such aids. Unfortunately, without careful design, deployed ML models can “fail silently” (i.e., they give no indications of when their out- puts should not be trusted, unlike, for example, failures in physical systems, such as deteriorating infrastructure).
- Another source of bias in this step is the unequal application of discretion. Artificial decision aids are often deployed with direct human oversight. This makes for more robustness in decisionmaking
in that the human can step in to adjudicate or correct edge cases on which the model might fail. Such human oversight involves an amount of discretion that can be subject to implicit or explicit biases. These can lead to decisionmaking having bad and worsening biases. 
- After a model is deployed,
it can be modified through software updates or patches. Following any such updates, an ML decision aid must be reevaluated to identify potential bias. But the time between software upgrades can vary greatly, and conducting postupdate evalu- ations can involve significant costs and effort. Continual monitoring for bias could provide early insight into potential issues that can be addressed early on. Including ongoing auditing procedures in deployment documents could help ensure that Census and other agency programs actually mitigate the misuses and biases described.

# Methods to Address Post-Deployment Bias

Fortunately, there are several new and emerging techniques to mitigate post-deployment bias.

- Creating certification labels on ML resources (see also Google Model Cards): ML models should have certification labels with information on ML model characteristics (e.g., model purpose and limitation, accuracy and error rates, disaggregated evaluation statistics).

Data sets used for training models also need to be clearly characterized for distribution statistics and limitations.
DHS can avoid harmful bias in its machine learning systems by establishing standards for measuring bias, weighing costs of biased outcomes, and providing workforce development for the emerging technologies. Label requirements should be standardized across an agency's components. Every ML model deployed
by an agency unit should also have a routine scheduled recertification process. The standards for such certification should be guided by neutral or independent parties.

- Performance tracking and disaggregated evaluation approach: Clear, consistent processes are required
to continuously measure the performance of deployed ML decision aids. This includes evaluating and tracking the accuracy of the ML model (e.g., false positives and false negatives). The process also includes repeated audits for bias.
Bias audits include disaggregated evaluation of ML models (e.g., measure model performance on different, relevant subdemographics; see **Mitchell et al., 2019**). The need for tracking can place specific demands on operations. For example, one might need to implement experimental design setups to try to estimate traditionally unobserved signals (e.g., false negatives, sensitive attributes of individuals).

- impact assessments and continuous red-teaming: ML models should undergo extensive checks at each step to ensure quality control. This could be in the form of red-teaming or security tests. Where feasible, the use of model implementations can also enable more deeply robust external verification. The continuous application of red-teaming enables ongoing estimation of operational robustness to new ML security threats. Agencies should also require an algorithmic impact assessment **(Reisman et al., 2018).**

For a discussion of directly applicable methods including analytical metric definition and links to code snippets and open source tooling, please see the Advanced Post-Deployment Methods section. 
