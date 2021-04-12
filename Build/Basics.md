<img width="107" alt="image" src="https://user-images.githubusercontent.com/80533280/114314548-36988000-9ac9-11eb-921d-835debe6a9b6.png">


# Start here: Primer
Explore the basics of AI Ethics and build a solid foundation for navigating potential bias in government contexts. 

Navigate through the document using the following links: 
- [Overview of Ethical AI: Introductory Concepts ](#introductory-concepts)
- [Ethical AI: A Shared Responsibility ](#ethical-ai-a-shared-responsibility)
- [Machine Learning and Government](#machine-learning-and-government)
- [Why AI at Census?](#why-ai-at-census)
- [Principles of Ethical AI Systems in Government](principles-of-ethical-ai-systems-in-government)



# Introductory Concepts 

In order to understand AI Ethics material shared in this resource, it is essential to understand a few fundamentals terms. Some of the most important are highlighted below:

**Artificial intelligence**: A system composed of an algorithm or model that solves complex tasks, including those in the vision, language, and learning domains.

**Machine Learning**: Sometimes colloquially used interchangeably with artificial intelligence, machine learning describes a series of methods and systems in which 
"learns" from input data to predict outcomes and draw inferences from new data it has never seen drawn from a similar distribution as the training data. For example, we can train a predictive model on job and college admission outcomes from last year's cohort of US high school students to try to predict what this year's cohort of US high school seniors will achieve.

**Natural Language Processing**: An example common NLP task is sentiment analysis of user comments in a post-service survey to gauge user satisfaction with government services. Natural language processing is a branch of artificial intelligence, distinct from machine learning, describing a series of methods that enable the analysis, interpretation, and manipulation of various aspects of written and spoken human language. A closely-linked term is **Natural Language Generation**, which refers to the field encompassing various computer-based methods use dto generate "human" language. 

**Computer Vision**: The field of AI that develops techniques to "teach" computers to process, understand, analyze, and manipulate images and videos. Facial recognition technologies deployed by law enforcement agencies around the world are build on a core of computer vision techniques. Optical Character Recognition (OCR) used to extract machine-readable text from tables in PDFs is one example of how computer vision could be used around the Census Bureau.

**Model Accuracy**: Percentage of correct predictions to predictions made overall by a classifier model. There are various accuracy metrics that can be used, usually as some combination of proportions of true and false negatives and positives. One common way of representing a model's accuracy in classification tasks is a **confusion matrix** -- essentially a table of false positives and negatives (see below).


<img width="500" alt="image" src="https://user-images.githubusercontent.com/80533280/114404662-e62a2c80-9b73-11eb-90d6-adb4c34ea7be.png">


**Deep Learning**: An artificial intelligence model that relies on multiple layers of neural networks --  collections of nodes modeled on neurons in the human brain -- each of which transforms the input data in progressively more abstract ways. Examples of deep learning networks are RNNs, or recurrent neural nets, used in language applications, and CNNs, or convolutional neural nets, which are used most commonly in computer vision applications. Deep learning's utility lies in the fact that these models automatically detect features, so that the user does not have to create or engineer them.

**Model Training**: Training is the process of developing a model by exposing it to labeled examples (training data) in order for it to “learn” how the features relate to the labels.

**Model Deployment**: One of the last steps of the ML development process. Deploying your model means putting it into a production environment, such that it can be accessed by others (for example, through an API) and begins making decisions/predictions using "real" data post-training and testing. Models still require testing and maintenance and possible retraining post-deployment.

**Features**: Input to an AI/ML model. For instance, features a model build to predict economic mobility of a population could include educational attainment and work history.  The process of extracting features from data, which could include complex processing, is known as **feature engineering.** Features can be categorical (a set of occupations) or continuous (income), and could also be images, such as in computer vision.

**Labels**: What a model is trying to predict; model output. 

**Bias**: In the AI Ethics sense, bias refers to errors introduced to an AI system because of bad data collection, cleaning, sampling, reporting, or other technical pipeline-related failures, or a general favoritism or unfairness introduced by either algorithm or data for or against some (sub)populations in the dataset. If a system for accessing government services relies on facial recognition technology, and the computer vision algorithms underlying this technology have not been trained on images of people with darker skin, then that technology might enact a bias against darker-skinned people trying to access that service, excluding them because it cannot recognize their faces.  


<img width="402" alt="image" src="https://user-images.githubusercontent.com/80533280/114315080-444f0500-9acb-11eb-87db-df3d3ac3cd02.png">


<!-- https://docs.google.com/drawings/d/1N6hKXUiWYiW_M9M9tvCPJNXrB-w_TyY_yn_H-yA7Mr8/edit -->


# Ethical AI: A Shared Responsibility

One reason this shared resources includes material for people across the spectrum of technical knowledge and ML expertise is that building or buying and deploying truly ethical AI systems requires the involvement of many stakeholders. It is absolutely essential to involve subject matter and domain experts who may be nontechnical, but whose mastery of data and agency processes and systems is superior to that of anyone else, or who have an intuition for what outcomes might be biased or unfair for a specific problem setting. Furthermore, ethical assessment, building, and testing for AI/ML systems is an enormously complex undertaking must necessarily encompass stakeholders across agencies, and that requires constant testing, data refreshing, and general vigilance post-deployment. Thus, it is important to educate all federal employees, contractors, and vendors interfacing with any any aspect of AI system design, deployment, application in the field, or acquisiton purchases, in some of the basics introduced in this document. 


# Machine Learning and Government

Most of our work throughout this toolkit reflects work in government, and therefore focuses primarily on machine learning and some natural language processing tasks.  

The main categories of machine learning tasks are prediction, detection, and description, causal inference, and detection.  Detection is the identification of new, unusual types of events, data points, patterns, a set of techniques that might help Census identify dataset outliers that represent bad data collection practices, or fraudulent survey responses. Causal inference describes a series of methods that capture the relationship between data and outcomes, such as when one  determines whether switching to an online survey causes certain classes of businesses to not respond to surveys. This resource will focus on prediction and description, which have the most relevance to Census, and civic good settings more broadly.

Prediction with Machine Learning: Prediction involve determining the value of some element of a dataset that we do not already know. For instance, given the demographic growth history across 49 states, what do we think will be the demographic growth over the next year across the 50th state for which we have no data?

Description with Machine Learning:  Description tasks analyze properties of a dataset. An example of a descriptive task is summarizing text data, or clustering, which seeks to move unlabeled data we have not classified in any way into groupings ("clusters") of data that bear meaningful similarities. 

# Why AI at Census?

The Census Bureau, the principal agency in the US Federal Statistical System, collects a vast amount of data used in high-stakes decisions. Census data is used to decide how to allocate services like job training services, transportation resources, and education across communities, how to distribute Congressional seats to states, and helping people qualify for retirement benefits, and informs many other critical initiatives at the local, state, and federal levels.

To extract value from this data, Census uses a range of computational tools and methods to analyze the data it collects across a range of data collection instruments. [Some of these computational tools include machine learning methods](https://www.census.gov/topics/research/data-science/about-machine-learning.html), which can be used to automate and speed up time-consuming, costly tasks, and improve existing tools. Machine learning can also used complement a range of survey instruments and methodologies when coupled with the array of administrative and survey data from across agencies that the Census Bureau houses.   

How is machine learning used at Census? Some examples of machine learning use cases across the Bureau are: Estimating people’s or businesses’ propensity to respond to surveys in certain Census tracts; building automatic classifiers for various survey elements, saving humans many hours of hand-coding; use satellite images to supplement traditional survey instruments in estimating population size and growth. Outside of survey-focused project work, Census could conceivably use several well-established machine learning techniques to create more robust search capabilities for public resources accessed through www.census.gov. 

AI/ML could also be leveraged to power operational effiency, such as with automatic mapping of skillsets or datasets around the Bureau as inferred directory and publication authoriship information;  automatic labelling of images and tables hosted on the Census website with captions using natural language generation based on transformers; and the rapid cleaning of data from disparate sources before combining into one dataset. 

# Principles of Ethical AI Systems in Government

Data collected by humans is imperfect. When there are missing or incorrect values, distorted information, or mislabeled data, these can interact with an AI system, which can also be incorrect becauase of human biases or tecnhnial issues, that create systematic inaccuracies that represent the world in a biased way. Because of the particulary sensititvies of work in the public sector, building trustworthy AI systems free of biases to the greatest possible extent is an enormously important undertaking. 

Government has an obvious obligation to ensure robust and accurate yet fair AI systems, such that benefits adjudication, survey data collection, standardization, and analysis, and other common AI/ML with public sector applications do not introduce, perpetuate, or amplify biases against any particular group of people, whether these biases reflect human cognitive distortions that seeps into data, labelling, or modeling, or they are introduced purely by model or computation. This obligation is enshrined in policy documents like the recent [White House Executive Order on Trustworthy AI](https://www.federalregister.gov/documents/2020/12/08/2020-27065/promoting-the-use-of-trustworthy-artificial-intelligence-in-the-federal-government).  

Given the fact that anything from bad data collection practices to problematic interactions AI systems to poor judgment about what fairness entails can lead to biased system output, building "ethical" AI systems can seem daunting to government development teams. Before going any further, we outline the general characteristics of “ethical” AI systems, guided by recent work across various units of the Department of Commerce.

The main principles of Ethical AI are shaped by the following concepts: 

- **Interpretability**
- **Explainability** 
- **Transparency**
- **Trustworthiness**

First, *Interpretability*: Interpretable AI systems are those that create output that depends on input in a way that can be recognized or predicted by human beings. 

In other words, if a team at Census creates a model to predict future housing prices, and one of the features used to build the model is literacy rate, a (locally) interpretable model could be one for which a person can predict with reasonable confidence the change in housing prices that result from increasing the literacy rate in a geographic region.

Next is *Explainability*: Although used mistakenly as a synonym for “interpretability”, explainability is a distinct concept. Rather than model output, it relates to the internal structure of the model itself. If a human can explain how a model works and why, without relying on sensitivity of output as in interpretability, then we can call that model "explainable." Methods for assessing explainability can include statistical assessments. 

One of the interesting aspects of explainability that we delve into elsewhere in this toolkit is the idea that there might be some tradeoff between explainability and accuracy, because simpler models tend to be more explainable in a sense. The existence of this tradeoff is debated within the AI research community, however.

Third is *Transparency*, which is the property of explainability that is attained by  using models that are easily interpreted or intuitive to humans -- for example, random forest or linear models.

Fourth is *Trustworthiness*:  Trustworthy systems, as outlined in a response to a Federal Executive Order by the Secretary of Commerce, combines several of the above principles.
“Trustworthy AI systems,” as defined by the government’s [Plan for Federal Engagement in Developing AI Technical Standards and Related Tools](https://www.nist.gov/topics/artificial-intelligence/plan-federal-engagement-developing-ai-technical-standards-and-related), are those that meet a set of standards across several dimensions:  accuracy, explainability, resiliency, safety, reliability, objectivity, and security. Some of these standards are works in progress, and may vary by agency, problem setting, model type, various particulars of an application, etc. 

Government, including untis of the Department of Commerce, has thought deeply about trustworthiness, including explainable AI, which will require specific guidance to agencies and federal contractors and vendors working with government to develop standards and guidance for ethics, privacy and so on, in collaboration with outside research organizations and academia, which have not yet converged on a consensus definition for explainability. DARPA's 
[Explainable AI program, XAI](https://www.darpa.mil/program/explainable-artificial-intelligence) endeavors to fund reseaerch and testing and training programs and certification standards for government tecnhnology. Establish Standards and Guidance to Navigate Risks.  

National Institute of Standards, another unit of the Department of Commerce, has begun outlining standards for government AI, including ensuring ethical and trustworthy systems, as outlined in its evolving [Plan for Leadership in AI](https://www.nist.gov/system/files/documents/2019/08/10/ai_standards_fedengagement_plan_9aug2019.pdf). Contributing to this stream of policy work and research are NIST's recent Workshops on [Exploring AI Trustworthiness](https://www.nist.gov/news-events/events/2020/08/exploring-ai-trustworthiness-workshop-series-kickoff-webinar), [Bias in AI](https://www.nist.gov/news-events/events/2020/08/bias-ai-workshop), and [2021 Workshop on Explainable AI](https://www.nist.gov/news-events/events/2021/01/explainable-ai-workshop).  







