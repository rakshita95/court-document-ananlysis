# Topic Modelling

Topic modeling provides a way to discover hidden thematic structure in large collections of texts. The results of topic modeling algorithms can be used to summarize and theorize about a corpus. They take a collection of texts, in this case appeals documents, as inputs and estimate the degree to which each document exhibits various topics. "topics" are essentially a set of tightly co-occurring words that represent recurring themes that are discussed in the collection.

Topic models make two important assumptions about the data:   
1.	There are group of terms that co-occur in the document that we shall refer to as topics. The reason behind calling them topics is that, if the corpus is large enough these group of terms must refer to the same subject. Thus, having large enough corpus is essential to discover coherent topics.  
2.	Different documents must exhibit these topics at varying levels for the model to be able to identify coherent topics  

## Various approaches:

First, I fed the whole corpus of appeals documents to the model to understand which themes would emerge. The estimated groups of words indicated that the themes were mostly centered around the type of crime. For example, sexual assault, murder etc. While these are useful to directly tag the document based on the type of crime being discussed. They are not very insightful in terms of understanding how social media is discussed in these documents.   

Hence, we modified the approach to run topic modelling on the annotated documents. Human annotators extract only relevant information from the appeal documents as described previously in the data description section. This way, once sufficient number of documents are annotated, we will be able to see themes that emerge in text describing support for the evidence or themes in text describing outcome of the trial etc. Moreover, we can analyze which themes are dominant in different social media websites or which themes are dominant for different types of evidence like photographs, videos etc.

## Procedure

In this project, I employed Latent Dirichlet Allocation which is a commonly used topic modelling algorithm.  Building a topic model is an iterative process where human evaluative decisions and textual assumptions are encoded in each step of the process. While I will leave out the technical details of pre-processing steps and transformations applied on the corpus, two aspects are worth pointing out.

 * Choosing number of topics: 
 All topic models expect the number of topics to be pre-specified. I chose number of topics such that topic coherence score (information theoretic approach) are maximized. For example, the figure below shows how coherence scores vary as number of topics in increased. Based on the plot specifying 5 topics seems to be a good idea.  
 ![coherence](/img/coherence.png)  
 While these coherence scores were found to correlate with human judgement most of the time, the user should feel free to increase/ descrease the number of metrics such that the topics makes most sense.  
 * Removing common words: I removed words like 'the', 'and' etc. that occur commonly across the corpus but do not hold any significance. They can degrade the performance of the topic model. These words are called stop words. However, one may need to extend the list of stop words to include domain specific stop words like defendant, complainant, testimony etc. This can make a huge difference to interpretability of the topic.  

We will see that some of the tools discussed later in the report will be helpful in making these decisions.

## Understanding the results:

Another key aspect about topic models is that they are unsupervised. As a result, it is upto the user/ domain expert to decipher which subject the topics refer to and appropriately label the topic. In this project, I developed tools to help the expert/ user label the topics discovered. In this section, I will walk you through how the various tools can be used by running a topic model on all texts referring to social media in the court documents. In annotated documents, social media specific is obtained by simply concatenating the outcome and support.  

1.	**Exploring word clusters**  
The screenshot below is that of an interactive GUI that can be used to develop a deeper understanding of the topic clusters. In the 2D plot on the left, each circle represents a topic. Topics that are more similar are closer on the 2D plane. We say that two topics are more similar if they share more keywords. By default, the bar plot to the right shows the most frequent words in the keywords. By hovering over one of the topic circles, the bars will rearrange to show the most frequent words in the topic. Moreover, hovering over the words in bar chart also highlights the topic circles that contain the word. Sometimes if frequent stop words are not dealt with as discussed previously, the end up being shared among multiple topics making it difficult to interpret the topic. In such cases, the sliding bar on the top right can be adjusted to set the relevance metric such that words that are more specific to the topic are at the top. 
 ![webapp](/img/webapp.png)  
2.	**Examining top documents under each topic**
-	understand what the themes are.  While in most cases, a glance at the topic words (top words) belonging to the topic  

The next set of functionalities is used to generate insights from these themes.
1.	Temporal trends
2.	How themes vary by 3rd dimension.

## Conclusion, Limitation and Future Work

In this report, I laid out the analysis approach for how topic modelling can be potentially employed to derive insights once sufficient number of annotations have been labelled. Notebook.py demonstrates the usage of various tools I developed. It is well documented and provides interface to specify the number of clusters and custom stop words and displays results from the various tools described above. 

