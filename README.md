# Notebooks Everywhere:  Using Jupyter and Notebooks for your day-to-day tasks

* clone this repo:  `https://github.com/davew-msft/notebooks-everywhere`
* this repo is available in [Azure Notebooks](https://notebooks.azure.com/davew/projects/notebooks-everywhere)

## Agenda 

* [Link to Presentation Notebook in RISE format](presentation.ipynb)
* [Interface Walkthrough](01_interface.ipynb)
* [Demo: Electric Vehicle Routing and Reachable Range with Azure Maps](02_ElectricVehicle.ipynb)


screenshot of the tree

now do JupyterLab

## Installation Options

### Full Blown Anaconda on Windows or Mac




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

## Scheduling 

Netflix created Papermill to do this.  

https://papermill.readthedocs.io/en/latest/index.html

https://github.com/nteract/papermill

## SQL

https://hub.gke.mybinder.org/user/mariasql-notebooks-2bwuqvzh/notebooks/sqlserver_sql%20magics.ipynb

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

