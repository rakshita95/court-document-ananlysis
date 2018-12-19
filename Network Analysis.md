# Network analysis of citations:
The appeal documents often cite other court cases at multiple instances. During annotation phase, the cases cited in the context of Social Media were also recorded.  This information can be analyzed to understand which cases were most influential and whether any specific attributes contributed to those papers being cited more often.  

## Network Construction: 

We construct a graph network such that the nodes represent court cases and two court cases are connected by an edge if one court case cites the other one.  These edges have a direction as we know which case cites which one. A network constructed this way has a total of 125 nodes and 101 edges.  The network formed this way can be visualized as shown in figure below. Note that the nodes have been positioned in a force directed layout so that there are as few crossing edges as possible. Red dots indicate various cases. Also, arrows in the edges have been omitted for simplicity.

![Figure1](/img/whole_network.png)
**Figure 1: Visualization of the whole citation network**

However, given the large number of cases, the properties of the network are not evident from the visualization. Hence, we need to look at a few objective metrics as shown in Table below. 

Metric | Value
------------ | -------------
Number of nodes | 125
Number of edges | 101
Average in-degree | 0.8
Average out-degree | 0.8
Density of the network | 0.0065

We see that, on average, a case in the dataset cites 0.8 other cases and is cited by 0.8 other cases. The density of network denotes how dense the citation network is and is a value between 0 and 1.  It takes a value of 1 when each case is cited by every other case. The value of 0.0065 indicates that the citation network is quite sparse. This could be because most cases cite other cases that are not cited by any other cases in the corpus.

## Analysis

Having constructed the graph, we can answer some interesting questions about the network. In this section, I will demonstrate how some of the functionality I have included can be used to generate insights. 

**a.	Uncovering relationships**  
One direct application of creating a network is that it can used to understand how different cases are related even though they donot cite each other directly. For example, on querying for cases - 'people v spears' and 'people v scaringe' we see that both of them cite 'people vs romero' and hence are related. More interesting relationships can be uncovered as more cases in the corpus are annotated and the network is allowed to grow larger.

**b.	Most influential cases**  
The cases that were cited most often in the corpus being analyzed are shown in Table below. Since we donot have these cases in the corpus, I was unable to theorize why they were influential. But later in the analysis, I describe visualizations that can help understand the reason behind these cases being cited more often. 

Case Name | Number of papers citing the case
------------ | -------------
people v romero | 4
people v bleakley | 3
people v williams | 3
people v edmonson | 2
people v lynes | 2

**c.	Cases which refer to any cases**
On average, an appeal document in the corpus cites ~3 different cases. The cases with most number of references are listed in table below. 

Case Name	| Number of papers referred to by the case
------------ | -------------
people v arnold	| 6
people v scaringe	| 6
people v simonetta	| 6
people v spears	| 6

All the above cases are murder or sexual assault cases and where mostly Facebook photographs, posts and messages were used as evidence.

**d.	Connected networks**  
As we saw in the beginning, the citation network is sparse and not fully connected. In other words, there are many instances where an appeals document cites a case or two but these are not cited by another documents in the corpus. I observed that there are 25 such completely disconnected networks or cliques in the citation network. Most of the cliques consist of only 2 nodes and are very small. Such smaller networks are not very insightful and can be ignored. So, let's start by analyzing the largest clique.

The largest component of the network that is fully connected has 29 nodes and 28 edges. On average, every case either references or is referenced by atleast one other case. This large connected network can be visualized much more clearly as shown in figure below. The yellow nodes represent the cases and edges are directed with the thicker side denoting the head of the arrow and thinner line denoting the tail. The nodes are labelled by the case names. The size of the node represents the number of cases citing that case. The largest nodes represent the most influential cases that were cited most often.

![Figure2](/img/large_comp.png)

We observe that people vs romero and people vs williams are the most influential papers with 4 and 3 cases citing them. The rest of the cases cited by only one of the case documents.

In order to better understand the dynamics of citations better, we can color the nodes based on other attributes. To demonstrate this, I colored the nodes with the type of social media instrument used as evidence as shown in Figure 3. This time, the size of node represents the number of cases cited by the node. Among other things, such a visualization can help theorize in which context a case was cited most often

![Figure3](/img/label.png)
![Figure3](/img/col_large_comp.png)


## Conclusion, Limitations and Future Work

I demonstrated how network analysis tools and visualizations can be employed to understand the dynamics of how various cases were cited. The code to reproduce the analysis can be found in notebook.py. Since only a subset of appeal documents have been annotated, the network is incomplete and we are unable to make any claims with high confidence. However, as more data is accumulated, the network will become denser and trends and clusters will become more apparent.

For next steps, it would be useful to automate the process of detecting citations without relying on manual annotations. The challenge here is limit the citations to only those that were cited in relation to social media. Future work may also focus on leveraging 3D graph visualization tools like Gephi and Neo4j to visualize the network. This is quite straightforward and can help the user better interact with the graph as network grows.

