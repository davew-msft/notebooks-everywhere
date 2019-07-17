# Notebooks Everywhere:  Using Jupyter and Notebooks for your day-to-day tasks

## Abstract

Notebooks (think "Jupyter") aren't just for data scientists anymore. They are quickly becoming the de facto way to write code. Any code. In this session we'll show you a few different ways to integrate notebook-thinking into your daily life. From SQL Server DBAs to Azure Administrators, there's a notebook use case for everyone. No Powerpoint in this session, we'll even use notebooks to build interactive, data-driven presentations. We'll even show you how Deep Learning works under-the-covers using interactive notebooks. 

## Presentation

[Link to Presentation Notebook](TODO.md)

This presentation is done in RISE.  

What is Jupyter?

* Julia, python, R
* also supports tons of other languages like SQL and scala

screenshot

minimalist
You can see code, comments, and results together.  Comments are not traditional code comments, rather, more like the author/programming is trying to engage the reader with narrative prose, images, videos, visualizations, and anything else that helps "sell" the concept to the reader.  

don't think in a linear fashion 
the documents can be shared
the complete and reproducible record of the computations *and the thought processes that went into the decisions* are recorded for posterity.  
enables a much more collaborative experience

computational narrative
you want to communicate a story based on data and results

OSS
REPL
    literate computing (Donald Knuth):  a program's logic should be explained in a natural language interspersed with traditional source code, that can be compiled and tells a story.  
    comments can be in HTML, Latex, or md
web application to share your code
geared more toward data projects, epecially data science projects
simulations (show an example)

notebook files are ipynb 
    HTML-based
    based on the ipython REPL shell (code blocks are run in individual cells and can be modified and rerun as you "learn" your problem)
    but can be exported in various formats 
    shared python notebooks allow you to share not just code but the entire "python session"
    ie, save the data (or results) with the prose and code
    

notebooks.azure.com
ADS
Azure Notebook VMs
containers on your laptop (don't need to install python on windows for example)
run locally as ipython shell extensions (comes with anaconda python distribution)




separate the code and documentation from the processing engine
    can leverage Spark, SQL Server, Azure Databricks

demo
    navigate notebooks.azure.com
    run on free compute vs Azure VM
    upload github repo
        do a tutorial

how do I connect to data in blob store?  

blob-acct-name=""
blob-acct-key=""
container = ""
blob-name=""
sunspotdata.describe(include='all')  great way to get a data dictionary.  Simple, descriptive statistics.  
show patterns of data with a graph (need a good example)

can you run the notebook in batch mode?  

## Tells a story example

[Model Explainability Example](model_explainability/readme.md)


this is a great example for model explainability and "tells a story"

https://github.com/microsoft/MLOps/tree/master/examples/explainability
move this area to this repo (done)
video demo is near the end:  https://mybuild.techcommunity.microsoft.com/sessions/77150?source=sessions
Let's build a model to help HR figure out better ways to retain employees!

train-deploy-explainer.ipynb


[Machine Learning Tutorial Notebook](ML-tutorial/Machine-Learning-Tutorial.ipynb).  **Does this display in gitlab/gh?**

Discuss *magics*
Save data with notebook or without


