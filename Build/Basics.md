<img width="107" alt="image" src="https://user-images.githubusercontent.com/80533280/114314548-36988000-9ac9-11eb-921d-835debe6a9b6.png">


# Start here: Primer
Explore the basics of AI Ethics and build a solid foundation for navigating potential bias in government contexts. 

Navigate through the document using the following links: 
- [Overview of Ethical AI: Introductory Concepts ](#introductory-concepts)
- [Ethical AI: A Shared Responsibility ](#ethical-ai-a-shared-responsibility)
- [Machine Learning at Census ](#machine-learning-and-the-US-census-bureau)
- [Principles of Ethical AI Systems in Government: A Practical View ](principles-of-ethical-ai-systems-in-government)


## Introductory Concepts 

In order to understand AI Ethics material shared in this resource, it is essential to understand a few fundamentals terms. Some of the most important are highlighted below:

Artificial intelligence: 

Machine Learning: 

Natural Language Processing: 

Computer Vision: 

Accuracy: 

Robustness: 

Model Deployment: 

Features: Input to the model. 

Labels: What a model is trying to predict; model output. 

Model Training: Training is the process of developing a model by exposing it to labeled examples (training data) in order for it to “learn” how the features relate to the labels.


Model Testing: 

Model Evaluation: 



An Algorithm is a set of rules that a machine follows to achieve a particular goal2. An algorithm can be considered as a recipe that defines the inputs, the output and all the steps needed to get from the inputs to the output. Cooking recipes are algorithms where the ingredients are the inputs, the cooked food is the output, and the preparation and cooking steps are the algorithm instructions.
Machine Learning is a set of methods that allow computers to learn from data to make and improve predictions (for example cancer, weekly sales, credit default). Machine learning is a paradigm shift from "normal programming" where all instructions must be explicitly given to the computer to "indirect programming" that takes place through providing data.

A Learner or Machine Learning Algorithm is the program used to learn a machine learning model from data. Another name is "inducer" (e.g. "tree inducer").
A Machine Learning Model is the learned program that maps inputs to predictions. This can be a set of weights for a linear model or for a neural network. Other names for the rather unspecific word "model" are "predictor" or - depending on the task - "classifier" or "regression model". In formulas, the trained machine learning model is called 
.

FIGURE 1.1: A learner learns a model from labeled training data. The model is used to make predictions.
A Black Box Model is a system that does not reveal its internal mechanisms. In machine learning, "black box" describes models that cannot be understood by looking at their parameters (e.g. a neural network). The opposite of a black box is sometimes referred to as White Box, and is referred to in this book as interpretable model. Model-agnostic methods for interpretability treat machine learning models as black boxes, even if they are not.

Interpretable Machine Learning refers to methods and models that make the behavior and predictions of machine learning systems understandable to humans.
A Dataset is a table with the data from which the machine learns. The dataset contains the features and the target to predict. When used to induce a model, the dataset is called training data.
An Instance is a row in the dataset. Other names for 'instance' are: (data) point, example, observation. An instance consists of the feature values 

The Features are the inputs used for prediction or classification. A feature is a column in the dataset. Throughout the book, features are assumed to be interpretable, meaning it is easy to understand what they mean, like the temperature on a given day or the height of a person. The interpretability of the features is a big assumption. But if it is hard to understand the input features, it is even harder to understand what the model does. The matrix with all features is called X and 
 for a single instance. The vector of a single feature for all instances is 

 and the value for the feature j and instance i is 

xj(i)
.
The Target is the information the machine learns to predict. In mathematical formulas, the target is usually called y or 
y
i
yi
 for a single instance.
A Machine Learning Task is the combination of a dataset with features and a target. Depending on the type of the target, the task can be for example classification, regression, survival analysis, clustering, or outlier detection.
The Prediction is what the machine learning model "guesses" what the target value should be based on the given features. In this book, the model prediction is denoted by 
^
f
(
x
(
i
)
)
f^(x(i))
 or 
^
y
y^
.


<img width="402" alt="image" src="https://user-images.githubusercontent.com/80533280/114315080-444f0500-9acb-11eb-87db-df3d3ac3cd02.png">

// https://docs.google.com/drawings/d/1N6hKXUiWYiW_M9M9tvCPJNXrB-w_TyY_yn_H-yA7Mr8/edit



# Machine Learning and the US Census Bureau

Most of our work throughout this toolkit reflects work in government, and therefore focuses primarily on machine learning and some natural language processing tasks.  

The main categories of machine learning tasks are prediction, detection, and description, causal inference, and detection.  Detection is the identification of new, unusual types of events, data points, patterns, a set of techniques that might help Census identify dataset outliers that represent bad data collection practices, or fraudulent survey responses. Causal inference describes a series of methods that capture the relationship between data and outcomes, such as when one  determines whether switching to an online survey causes certain classes of businesses to not respond to surveys. This resource will focus on prediction and description, which have the most relevance to Census,  and civic good settings more broadly.

Prediction with Machine Learning: 

Description with Machine Learning:  

## Machine Learning and the Census Bureau

The Census Bureau, the principal agency in the US Federal Statistical System, collects a vast amount of data used in high-stakes decisions. Census data is used to decide how to allocate services like job training services, transportation resources, and education across communities, how to distribute Congressional seats to states, and helping people qualify for retirement benefits, and informs many other critical initiatives at the local, state, and federal levels.

To extract value from this data, Census uses a range of computational tools and methods to analyze the data it collects across a range of data collection instruments. Some of these computational tools include machine learning methods, which can be used to automate and speed up time-consuming, costly tasks, and improve existing tools. Machine learning can also used complement a range of survey instruments and methodologies when coupled with the array of administrative and survey data from across agencies that the Census Bureau houses.   

How is machine learning used at Census? Some examples of machine learning use cases across the Bureau are: Estimating people’s or businesses’ propensity to respond to surveys in certain Census tracts; building automatic classifiers for various survey elements, saving humans many hours of hand-coding; use satellite images to supplement traditional survey instruments in estimating population size and growth. Outside of survey-focused project work, Census could conceivably use several well-established machine learning techniques to create more robust search capabilities for public resources accessed through www.census.gov. 

Building robust yet fair and unbiased AI, systems can seem challenging. Before going any further, we outline the general characteristics of “ethical” AI systems. 


Interpretability: Interpretable AI systems are those that create output that depends on input in a way that can be recognized or predicted by human beings. 

In other words, if a team at Census creates a model to predict future housing prices, and one of the features used to build the model is literacy rate, a (locally) interpretable model could be one for which a person can predict with reasonable confidence the change in housing prices that result from increasing the literacy rate in a geographic region.

Explainability: Although used mistakenly as a synonym for “interpretability”, explainability is a distinct concept. 

Government, and the Department of Commerce, has thought deeply about Explainable AI. 


Transparency -- definition
Trustworthy systems, as outlined in a response to a Federal Executive Order by the Secretary of Commerce, combines several of the above principles
“Trustworthy AI systems,” as defined by the government’s “Plan for Federal Engagement in Developing AI Technical Standards and Related Tools,”  are those that meet a set of standards across several dimensions:  accuracy, explainability, resiliency, safety, reliability, objectivity, and security



 
   
 
 
 
 



Ethical AI

Who should be thinking about Ethical AI? Personas

Bias

Fairness

Measuring Bias and Fairness 

Explainability 



Data collected by humans is imperfect. When there are missing or incorrect values, distorted information, or mislabeled data, we can see instances where these lead to systematic inaccuracies that represent the world in a biased way. 

What do we mean when we say artificial intelligence or machine learning?

How do we define what makes a “Good” model?

How do we define what makes a “Biased” or “Fair” model?

	One of the most confusing aspects of bias and fairness for newcomers to the AI Ethics space is that there is no universally-held, consensus definition of either. 

Where might bias arise?


How might AI bias impact government contexts in particular?


Equity in delivery of services
Acquisition






