# Notebooks Everywhere:  Using Jupyter and Notebooks for your day-to-day tasks

## Abstract

Notebooks (think "Jupyter") aren't just for data scientists anymore. They are quickly becoming the de facto way to write code. Any code. In this session we'll show you a few different ways to integrate notebook-thinking into your daily life. From SQL Server DBAs to Azure Administrators, there's a notebook use case for everyone. No Powerpoint in this session, we'll even use notebooks to build interactive, data-driven presentations. We'll even show you how Deep Learning works under-the-covers using interactive notebooks. 

## Presentation

[Link to Presentation Notebook](TODO.md)

This presentation is done in RISE.  

History
* originally developed as part of the **IPython** project (interactive, online access to Python).  
* the R folks kinda liked it and Jupyter was spun off.  

What is Jupyter?

* Julia, python, R
* also supports tons of other languages like SQL and scala

screenshot of the tree

now do JupyterLab

## Installation Options

### Full Blown Anaconda on Windows or Mac

Jupyter requires Python to be installed.  This is a fine solution but Anaconda is bloated and seems like overkill if you aren't a day-to-day python programmer.  Getting Python working reliably on Windows with `virtualenv`, etc is also a bit difficult and leads to "it works on my machine" mentalities.  Seems like there should be a better way.  

ipynb files

* these are JSON files and are barely human-readable.  
* they can also be difficult to version control using git.  
* this is why notebooks and notebook servers have the concept of "save and checkpoint".  You can roll back to a given checkpoint (`Revert to Checkpoint`)
* also consider judicious use of the `duplicate` option.  

There currently is no built-in "commit and push to git" option. 

* most notebook server implementations will allow you to clone/pull from git servers (github)
* but nothing *built-in* allows you to commit to git.  Instead you need to `Download as` and likely choose ipynb (there are other options).  


## The Execution Environment

Play with the interface on your own, it's intuitive.  Or, choose Help|Uswer Interface Tour.  

Here are some interesting tidbits:

* Split Cell:  Split a cell from the current cursor position
* Merge Cell Above:  merge the current cell with the one above. 
* Run All, Run All Above, Run All Below, etc:  this is useful when you want to save time or made radical changes and need to clear the execution cache.  

### Keyboard Shortcuts

See Help|Keyboard Shortcuts for the complete list.  These are helpful to commit to memory immediately:  

### Saving Output with Code

A new cell will have empty braces next to each code block.  Once the cell is run the braces will be filled with the cell number, and the output of the cells is appended to the bottom of each cell.  The ipynb file will save the output for you automatically or if you checkpoint.  

This is usually what you want, but not always.  Cell|All Output|Clear will eliminate the output if you want to share your notebook code but NOT your data/results/output.  


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


## Notebooks in Azure Data Studio

Azure Data Studio (ADS) is a multi-database, cross-platform desktop environment for data professionals.  It's based on Electron/vscode.  In fact, it's always a few releases *behind* the vscode codebase.  This means it supports extensions and all of the other goodness of vscode.

Open a notebook from your browser
We wanted to make sharing Notebooks from any location easier, so in this release we added a Notebook protocol handler. This lets you add links or buttons that open Azure Data Studio and download a Notebook from an online location such as GitHub.

The link format is as follows:

azuredatastudio://microsoft.notebook/open?url=[Encoded URL]

So, for example, this notebook on GitHub can be opened directly in Azure Data Studio with this link format:

azuredatastudio://microsoft.notebook/open?url= https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2Fazuredatastudio%2Fmaster%2Fsamples%2FnotebookSamples%2FSampleTSQLNotebook.ipynb
This should make it easier to link to notebooks from emails, chat rooms, documentation, and on blogs.

https://github.com/microsoft/azuredatastudio/blob/master/samples/notebookSamples/SampleTSQLNotebook.ipynb

## Widgets

used to gather user input:

* text input
* button clicks
* sliders
* toggles and check boxes
* dropdown boxes

pip install -upgrade ipywidgets
jupyter nbextension enable --py widgetsnbextension

from ipywidgets import interact
def myfunction(arg):
    return arg+1

interact (myfunction, arg=9);

def myfunction(x):
    return x

interact(myfunction, x=('black','white'));



## Multiuser and Sharing Options

You can share a notebook, but multiuser notebooks were an afterthought.  

### JupyterHub is One Solution

* Each user gets a new instance of the Jupyter software when they login.  This avoids environment and variable clashes.  
* JupyterHub-like features are not yet available in notebooks.azure.com
* Azure Notebook VMs are a solution but user mgmt requires you to create users/passwords in JupyterHub, you can't use OAUTH or similar
* you can spin up JupyterHub in docker containers/k8s...or...
* `pip install jupyterhub`

### Docker Containers

You can use Docker to allow multiple users to use the same notebook/data without collisions.  You can package the Jupyter software, conda dependencies, and your notebook as a single image.  This, of course, does not mean that development of a single notebook can be done in a truly multi-user environment.  Currently, this isn't possible natively.  Notebook development/editing 

with increased computation power allows more complex models.  the accuracy goes up and the interpretability goes down dramatically.  

[**Here is a really cool example using Q# (Microsoft's Quantum Computing Language)**](q-sharp/README.md)

