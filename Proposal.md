![Banner](https://github.com/CeliaSagas/EEG-Classification/blob/ea04509c7d718a20ba113980dbb6475299d47efe/img/EEG%20Class.jpg)



# Toxic-Rank
Ranking Toxic Comments on Wikipedia Talk Page Comments




**Question/Need:**

1. What is the question behind your analysis? What is the purpose of the model/system you plan to build?

      - Identifying toxic comments is a data science problem, but deciding what criteria is considered toxic is an ethical one. Historically, applications of data science in the fields of ethics and morality have yielded mixed results: it's hard to teach a machine the nuances of valence, hubris, and internet humor while also monitoring datasets for implicit and explicit bias towards minority groups.

      One approach that may help address some of these issues is ranking: giving comments a relative toxicity score based on comparisons made to other comments in the set.

      This ranking approach may approximate a true toxicity value better than a single, case by case approach because it may be able to better identify nuanced features in the text. My goal is to create a ranking classifier that is able to compare comments and give a relative toxicity score, then compare that ranking to human scorers.




2. Who benefits from exploring this question or building this model/system?

    - Websites with forums and comments need an unbiased way to tag toxic comments and remove abusive language and dialogue from their sites. Building a model that can accurately and fairly identify toxic comments is crucial to creating safer spaces online.



**Data Description:**

1. What dataset(s) do you plan to use, and how will you obtain the data?

    - The dataset I will be using comes from the [Jigsaw Rate Severity of Toxic Comments Challenge on Kaggle](https://www.kaggle.com/c/jigsaw-toxic-severity-rating/data) and includes 7,537 unique comments to score and 11,678 comment pairs that have already been labeled 'less toxic' and 'more toxic.'

2. What is an individual sample/unit of analysis in this project?

    - A single unit of analysis is one text comment from the Wikipedia Talk Page Comments dataset.


3. What characteristics/features do you expect to work with?

    - I expect to work with a topic classifier to identify the prevalent topics per comment, as well as valence, mood, abuse and violence features.


4. If modeling, what will you predict as your target?

    - My target is the relative toxicity score based on comparison with other comments in the dataset.



**Tools:**

1. How do you intend to meet the tools requirement of the project?

    - I plan to use pandas, seaborn, matplotlib, scipy, defaultdict, os, time, numpy, and sklearn for this project.

2. Are you planning in advance to need or use additional tools beyond those required?

    - I am going to try using the XGBRanker from XGboost to rank comments on toxicity by pairwise comparison in the dataset.



**MVP Goal:**

1. What would a minimum viable product (MVP) look like for this project?

    - My MVP will be a ranking model that will assign a relative toxicity score for each comment. 
