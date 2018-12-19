# Topic Modelling

Topic modeling provides a way to discover hidden thematic structure in large collections of texts. The results of topic modeling algorithms can be used to summarize and theorize about a corpus. They take a collection of texts, in this case appeals documents, as inputs and estimate the degree to which each document exhibits various topics. "topics" are essentially a set of tightly co-occurring words that represent recurring themes that are discussed in the collection.

Topic models make two important assumptions about the data. 
1.	There are group of terms that co-occur in the document that we shall refer to as topics. The reason behind calling them topics is that, if the corpus is large enough these group of terms must refer to the same subject. Thus, having large enough corpus is essential to discover coherent topics.
2.	Different documents must exhibit these topics at varying levels for the model to be able to identify coherent topics

## Various approaches:

First, I fed the whole corpus of appeals documents to the model to understand which themes would emerge. The estimated groups of words indicated that the themes were mostly centered around the type of crime. For example, sexual assault, murder etc. While these are useful to directly tag the document based on the type of crime being discussed. They are not very insightful in terms of understanding how social media is discussed. 

Hence, we modified the approach to run topic modelling on the annotated documents. Human annotators extract only relevant information from the appeal documents as described in section XX.X. This way, once sufficient number of documents are annotated, we will be able to see themes that emerge in text describing support for the evidence or themes in text describing outcome of the trial etc. Moreover, we can analyze which themes are dominant in different social media websites or which themes are dominant for different types of evidence like photographs, videos etc.

## Procedure

In this project, I employ Latent Dirichlet Allocation which is a commonly used topic modelling algorithm.  Building a topic model is an iterative process where human evaluative decisions and textual assumptions are encoded in each step of the process. While I will leave out the technical details of pre-processing steps and transformations applied on the corpus, two aspects are worth pointing out.

 * Choosing number of topics: All topic models expect the number of topics to be pre-specified. 
 * Removing common words: I removed words like 'the', 'and' etc. that occur commonly across the corpus but do not hold any significance. They can degrade the performance of the topic model. These words are called stop words. However, we may need to extend the list of stop words to include domain specific stop words like defendant, complainant, testimony etc. 

We will see that some of the tools discussed later in the report will be helpful in making these decisions.

## Understanding the results:

Another key aspect about topic models is that they are unsupervised. As a result, it is upto the user/ domain expert to decipher which subject the topics refer to and appropriately label the topic. In this project, I developed tools to help the expert/ user label the topics discovered. In this section, I will walk you through how the various tools can be used by running a topic model on all texts referring to social media in the court documents. Annotations make it easier to get this information by concatenating

1.	Exploring word clusters
-	keywords in the topic
2.	Examining top documents under each topic
-	understand what the themes are.  While in most cases, a glance at the topic words (top words) belonging to the topic  

The next set of functionalities is used to generate insights from these themes.
1.	Temporal trends
2.	How themes vary by 3rd dimension.

## Conclusion, Limitation and Future Work

In this report, I laid out the analysis approach for how topic modelling can be potentially employed to derive insights once sufficient number of annotations have been labelled. Notebook.py demonstrates the usage of various tools I developed. It is well documented and provides interface to specify the number of clusters and custom stop words and displays results from the various tools described above. 

