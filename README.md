# Confounder
---
#### *Inferring Errors of Omission*

&nbsp;&nbsp; One of the most common varieties of information used for [decision-making](https://online.csp.edu/blog/business/decision-making-process) are claims about *how two variables are related,* known as [regression analysis](https://news.mit.edu/2010/explained-reg-analysis-0316). Articles and studies that attempt to infer such relationships between two variables often suffer from formal mistakes. Some may include *poor metrics* for the variables being analyzed, overlooking *confounding variables* that distort how they are related, and failing to demonstrate the *order of causation* between the two. These can be easily summarized as *the three C's* of regression analysis: *Correlation, confounding, and causation.*  
&nbsp;&nbsp; ***Confounder* is a machine learning program that uses binary text classification to infer whether chosen pieces of information are present in a body of text or not.** This can be used to match responses to preselected statements (similar to traditional "fact-checking"), but a more unique use case is vetting statistical claims.

![](http://resources.esri.com/help/9.3/arcgisengine/java/GP_ToolRef/Spatial_Statistics_toolbox/scatterplots.png)

##### What Do Reliable Statistical Inferences Depend On?
---

&nbsp; **1. Well-Defined Variables:** All studies (and often news articles) that assert that one thing influences something else must clearly define what the X (manipulated/independent) and Y (responding/dependent) variables are that are being compared.
&nbsp; **2. Effective Sampling:** Broadly speaking, larger samples are preferable to smaller ones and techniques such as random control trials are often helpful for many kinds of research. Heterogeneity within sample groups is also an issue.
&nbsp; **3. Considers Confounding:** Any additional variables that may distort how X appears to cause Y need to be accounted for. This is a common failure among studies, yet easy to infer the absence of - hence the project name.
&nbsp; **4. Acknowledges Trade-Offs:** A trade-off can be thought of as another Y variable. Example - staying up late (X) may give your more time to study (Y), but that benefit could be offset from being exhuasted in class the next day.
&nbsp; **5. Uses Time Series Analysis:** Does X influence Y, or could it be the other way around? Time series analysis (seeing whether changes in one variable come before another) can help answer this question.

##### Example Scenario: Assessing the impact of college education on lifetime earnings
---

To get an idea of how *Confounder* works in practice, consider the claim that recipients of a 4-year degree typically earn a million dollars more over their lifetime:

![college earnings](http://www.incontext.indiana.edu/2009/mar-apr/images/earnings_fig2.gif)

**That claim (and above chart) results from omitting multiple methodological errors and omissions, which include:**

* The sunk cost of not working as much during school years 
* Any tuition costs including interest on student loans, residency, etc 
* Super-earner outliers skewing the average for degree recipients 
* Aggregating all majors and all non-degree holders into two groups
* Jobs for high-earning majors tend to be in more expensive cities
* Those that complete college may be prone to succeed beforehand

**General Workflow:** First, sample articles and studies that discuss the “college premium” are gathered, read, and labeled by which of the above errors/omissions are made. Once a representative corpus of text has been gathered, they are all pre-processed into a file that contains the name of the document, the raw text itself, and five more columns indicating which of the five factors were mentioned. These are used to iteratively train a natural language processing classifier to accurately detect which of the five factors were omitted or not in unread articles and studies, rather than having to check them all by hand long after they have been published.
