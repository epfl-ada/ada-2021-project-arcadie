# ada-2021-project-arcadie
ada-2021-project-arcadie created by GitHub Classroom

### How can we dynamically visualize the relationships between people by analyzing their quotes?

#### Abstract
The quotebank dataset from 2020 contains approximately 52 million quotes, of these quotes a large fraction is one person mentioning another in a positive, negative or neutral context. This project aims to create a graph where nodes are persons and uni-directional edges are relationships with weights signifying the quality of their relationship. The weight of the edge between two persons will be based on the sum of the sentiment score from all quotes between those two persons. A sentiment analysis will be done on the quotes thanks to a NLP sentiment analizer. Entities in quotes will be extracted using Scapy. The final analysis (in this milestone) of the data from 2020 shows that there are slightly more than 300,000 suitable quotes available for creating the graph. A key part of this project will be to decide how will we display our nodes in a 2D dimensional space and what attributes will we be showing in order to create interesting clusters. The most frequent speakers in the Quotebank dataset are American politicians. This is not surprising as the observational data comes from New York Times, and in 2020 there was the U.S. presidential election. We can expect to find political clusters which would lead, as an example, to the following graph : 

<img width="696" alt="Capture d’écran 2021-11-11 à 19 58 05" src="https://user-images.githubusercontent.com/73229139/141360065-fdde9008-57de-4dd3-9a84-9638787ccb72.png">


#### Research Question
1. Can the interpersonal relationships between celebrities be realistically mapped in a visible manner with thousands nodes and edges?
2. Can changes in the relationships over time be visualized?
3. Can the clusters of relationally close people, such as political parties, be detected?

#### Proposed additional datasets
Apart from the quotebank dataset, an additional dataset extracted from wikidata containing all speakers in the given dataset is used.
This is and will be aiding in properly finding the correct entity (person) mentioned in all quotes as well as finding relevant information about the entity such as political parties.
Note that this means only active speakers will be included in the graph.
In a later stage of the project, more people who are not speakers may be added if a good dataset containing these is found.

#### Methodology

##### Constraints in the current stage
1. Only 2020 dataset is being used.
2. Only quotes where only one person is mentioned are being used.
3. Only people included in the proposed additional dataset. (Show cases of Jesus for example, not interesting).
4. Our data is from english articles, thus we can assume all quotes are in english.

##### Initial analysis of QuoteBank 2020 dataset
Various analysis of the number of quotes, speakers and mentioned persons were performed. A language detection was done on the quotes, the result indicates that more than 99% of the quotes are recognized as English. The other 1%, after looking at them, were actually for the large part English. We decided to keep them. 
The number of speakers were aggregated by simply fetching and counting them from the initially cleaned quotebank dataset.
The number of mentioned people was estimated by sampling a big range of the dataset, using Spacy to find the entities in quotes.
Two versions of the quote entity aggregation were done;
One where only quotes with a single entity were counted, and one where quotes with one or more were kept.
This is relevant because the NLP package used is limited in its utility,
so it’s difficult to evaluate the sentiment between a speaker and a quote entity if there are several in the quote.
Since this is already done in a coarse manner, having several entities per quote will make it even more uncertain.
In both cases only entities that were mentioned more than once were kept to eliminate noise.

#### Next steps
As mentioned earlier, we only used the dataset from 2020 to outline the entire project.
The rest of the Quotebank is going to be processed and used to visualize the relationships in interactive ways.
Furthermore, we will utilize another NLP packages for quantification of the sentiments in order to extract more reliable information
and another funtions to make the difference between the positive and the negative relationships more distinguishable.

#### Proposed timeline
- 19 november : Take into account Milestone 2 feedback 
- 26 november : Find a way to aesthetically represent our nodes and weights (using the quotes of 2020)
- 3 december : Add in our dataset the quotes from the years prior 2020, and generate their graphs 
- 10 december : Analysis our graphs to prepare our final presentation 

#### Questions for TAs : 
- Should we go further in our preprocessing of our quotes before using a sentiment analysis ? Per example : Remove words that are not frequently used ? Replace entities and names by the same token <name> ?  
- We are using the library nltk (SentimentIntensityAnalyzer) to analyse our quotes. Would you recommend this library ?
- What tool should we use for plotting a big network graph interactively ? 
- We are still figuring out how we will represent in 2D our nodes and what information we will be showing (gender, age, political party). It will depend on the results of our analysis once the first graph is done. Do you have suggestions for identifying what should we be showing ? 
