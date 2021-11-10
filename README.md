# ada-2021-project-arcadie
ada-2021-project-arcadie created by GitHub Classroom


### How can we dynamically visualize the relationships between people by analyzing their qoutes?

#### Abstract

We expect the majority of the speakers in the Qoutebank dataset to be american politicians since this observational data comes from New York Times.
The aim of our project derived from this idea(especially there was the U.S. presidential election in 2020.
Most of the time the relationships between politicians significantly change depending on what they say about their counterparters(whether true or not),
and we would like to see how dynamically they change along with timeflow.
Also we have found a large fraction of these qoutes is one person mentioning another in a positive, negative or neutral context
which can be quantified using NLP sentiment analizer.
Therefore, this project aims to visualize the relationships between the major spearkers and people mentioend in the qoutes with graphs,
where the nodes indicate people and the uni-directional edges are relationships with weights signifying the sentiment(positive or negative) of their relationship.
The weight of each edge between two people will be based on the sum of the sentiment score calculated by NLP packages from all quotes between those two people.
The final analysis(in this milestone) of the data from 2020 shows that there are slightly more than 300,000 suitable quotes available for creating the graph.

#### Research Question

1. Can the interpersonal relationships between celebrities be realistically mapped in a visible manner with millions nodes and edges?
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
Various analysis of the number of quotes, speakers and mentioned persons were performed.
The number of speakers were aggregated by simply fetching and counting them from the initially cleaned quotebank dataset.
The number of mentioned people was estimated by sampling a big range of the dataset, using Spacy to find the entities in quotes.
Two versions of the quote entity aggregation were done;
One where only quotes with a single entity were counted, and one where quotes with one or more were kept.
This is relevant because the NLP package used is limited in its utility,
so it’s difficult to evaluate the sentiment between a speaker and a quote entity if there are several in the quote.
Since this is already done in a coarse manner, having several entities per quote will make it even more uncertain.
In both cases only entities that were mentioned more than once were kept to eliminate noise.


#### Nest steps

As mentioned earlier, we only used the dataset from 2020 to outline the entire project.
The rest of the Qoutebank is going to be processed and used to visualize the relationships in interactive ways.
Furthermore, we will utilize another NLP packages for quantification of the sentiments in order to extract more reliable information
and another funtions to make the difference between the positive and the negative relationships more distinguishable.
