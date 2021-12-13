# ada-2021-project-arcadie
ada-2021-project-arcadie created by GitHub Classroom

![Last_version](https://user-images.githubusercontent.com/73229139/145901280-a08bc241-3f35-48af-becf-7e6d5b8d086f.png)


### How can we dynamically visualize the relationships between people by analyzing their quotes?

#### Abstract
The quotebank dataset from 2020 contains millions of quotes, of which a large fraction is one person mentioning another in a positive, negative or neutral way. This project aims to create a graph where nodes represent people and oriented edges represent the fact that person A mentioned person B in a quote in a positive/negative way. The weight of the edge between two people will be based on the average of the sentiment score from all quotes between those two people. A sentiment analysis will be done on the quotes using a NLP sentiment analyzer. Entities (i.e tokens representing mentioned people in the sentence) in quotes will be extracted using Spacy. The milestone 2 final analysis of the data from 2020 shows that there are plenty of quotes available for creating the graph. A key part of this project will be to decide how we will display our nodes in a 2D dimensional space and what attributes we will be showing in order to create interesting clusters. The most frequent speakers in the Quotebank dataset are American politicians. This is not surprising as the quotebank data comes from English articles and in 2020 there was the U.S. presidential election. We can expect to find political clusters which would lead, as an example, to the following graph:





#### Research Question
1. Can the interpersonal relationships between celebrities be realistically mapped in a visible manner using quotes between the celebrities?
2. Can changes in the relationships over time be visualized?
3. Can the clusters of relationally close people, such as political parties, be detected?


#### Proposed additional datasets
Apart from the quotebank dataset, an additional dataset extracted from wikidata containing all speakers in the given dataset is used. This will assist in properly mapping entity aliases to full names of entities as well as finding relevant information about the entity such as political parties. Note that this means only active speakers will be included in the graph. In a later stage of the project, more people who are not speakers may be added if a good dataset containing these is found.

#### Methodology

##### Constraints in the current stage
1. Only the 2020 dataset will be used.
2. Only keep people that are reasonable and relevant in this context (not Jesus for example). 
3. The data is from English articles and the language will be assumed to be in english.
4. Since one quote can contain several entities, this will affect the correctness of using sentiment analysis directly applied on the quotes, because we can't say if the sentiment is referred to one entity or another. However this is disregarded in the project. The reason for this is that the NLP toolbox available for the project is limited in its utility to analyse sentiment for quotes with double entities. These quotes can also be assumed to be a small minority among the quotes with entity mentions.


##### Initial analysis of QuoteBank 2020 dataset
Various analyses of the number of quotes, speakers and mentioned people were performed. A language detection was done on the quotes, the result indicates that more than 99% of the quotes are recognized as English. The other 1% were upon examination mostly false negatives of the detection and the dataset is assumed to be 100% english. The number of speakers was obtained by simply counting them from the initially cleaned quotebank dataset. The number of mentioned people was estimated by sampling a big range of the dataset, using Spacy to find the entities in quotes. Only entities that were mentioned more than once were included in the count to eliminate noise. 
 
To construct our graph, each quote is analysed for entities. For the quotes containing entities (i.e mentioned people) the compound sentiment is calculated. This information is used to create a weighted edge or increment the weight of an existing edge between two nodes representing people in the graph. Initially this will be presented as a dataframe. Every row in the dataframe represents a quote denoted by its quote ID, the speaker and mentioned person name is represented by a speaker_id and mention_id. Since people have different aliases except for their full name, their aliases are mapped directly to the assumed corresponding id. The distance is calculated based on the compound score. 

![unnamed-2](https://user-images.githubusercontent.com/73229139/141379068-e186e834-dcf6-4951-bced-984d2a7f1bb8.png)

#### Next steps
As mentioned earlier, we only used the dataset from 2020 to outline the entire project. The rest of the Quotebank is going to be processed and used to visualize the relationships in interactive ways. This will allow us to see if there is an evolution of the relationships in the graph with respect to the date and time of the quotes. Furthermore, we can improve our sentiment analysis by using other NLP packages. In the end we would like to perform clustering on the graph in order to verify if there is a correspondence between the clusters found in the data and the political parties, or well-known groups, in the real world.


#### Proposed timeline
- 19 november : Take into account Milestone 2 feedback.
- 26 november : Find a way to visually represent our nodes and weights (using the quotes of 2020).
- 3 december : Add in our dataset the quotes from the years prior 2020, and generate their graphs. 
- 10 december : Analysis of our graphs (e.g: clustering) to prepare our final presentation.

#### Questions for TAs : 
- Should we go further in our preprocessing of our quotes before using a sentiment analysis? For example : Remove words that are not frequently used? Replace entities and names by the same token?
- We are using the library nltk (SentimentIntensityAnalyzer) to analyse our quotes. Would you recommend this library?
- What tool should we use for plotting a big network graph interactively?
- We are still figuring out how we will represent in 2D our nodes and what information we will be showing (gender, age, political party). It will depend on the results of our analysis once the first graph is done. Do you have suggestions for identifying what we should be showing?

