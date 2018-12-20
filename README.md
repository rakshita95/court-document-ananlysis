# court-document-analysis

The goal of this project is to develop tools to mine the court documents to analyze in which context social media was used as an evidence. 

## Description of the data
The dataset consists of 81 appeal documents of court cases in the pdf format. Among these, 39 have been annotated and converted into a semi structured format. Each document has been annotated according to the following codes:

* Case Name
* Type of offence: Nature of offence. For example, murder, robbery etc.
* Overall Outcome of the appeal (exactly as it appears in the document)
* Outcome in relation to the social media evidence (exactly as it appears in the document)
* Evidence Type: Type of social media evidence cited in the document such as photographs, videos etc.
* Platform: Facebook,twitter etc.
* Support: Discussion around authenticating the social media evidence (exactly as it appears in the document)
* Prior cases influence: List of other cases cited in relation to social media.

## Analysis

To achieve the goal of the project, I developed tools to analyze the semi-structured and unstructured data along multiple dimensions. 

* [Overall Analysis:](https://github.com/rakshita95/court-document-ananlysis/blob/master/overall-analysis.md) Analyzing the annotated court documents for social media platforms and evidence used for various offences. 
* [Topic Modelling:](https://github.com/rakshita95/court-document-ananlysis/blob/master/Topic%20Modelling.md) Analyzing the results of topic modelling of appeal documents to uncover hidden themes from the unstructured text.
* [Network Analysis:](https://github.com/rakshita95/court-document-ananlysis/blob/master/Network%20Analysis.md) Analysing the citation Network of cases referenced in the documents in corpus to understand the influence of prior cases.

Click on the corresponding links for details of each of the analyses, description of tools and future work.



