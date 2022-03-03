# Using Jupyter Notebooks to Implement Methods on Google Cloud
Owner: Joseph Sarro
GitHub: jsarro13

## When creating a notebook
* Begin with a detailed summary of what the workflow does. What is the purpose of this workflow? What are the output objects? What will these objects be used for? How were the input objects generated?
* Describe any dependencies needed. Descriptions of novel tools and possible links should also be included. For example, Trellis may not be a tool a user is familiar with and background information could be useful.
* Limit use of acronyms i.e., BQ for 15000 sample list. Instead use Base Quality(BQ) for 15000 sample list.
* Provide a brief description of each object.
  * What is the object?
  * Where does it comes from?
  * What it is used for?
  * Who can view/access this object? The sensitivity of the contents should be stated in the case of medium or high risk data.
* Limit the use of object paths to those that are contained in the repo. All other objects should be accessed through gsutil.
* Adding line numbers to code could help in debugging.
* Make sure final product is clean of junk code.
  * Are lines of commented out code needed?
  * Is every step necessary?
* When generating dataframes/tables, display a small section of the output so users can see what the data looks like.
* Each code cell should perform a single operation. Split compound operations into separate cells. This will make your notebook
  * More flexible to use
  * Easier to debug
  * More robust

## When running a notebook
* Make sure that all dependencies are installed.
* Before running any command on cloud services:
  * Make sure you have proper dependencies installed.
  * Check object sizes. Running very large objects can be expensive.
  * Double check memory usage of software being run. Memory intensive programs can be expensive to run.
* Familiarize yourself with Jupyter Notebooks.
  * If you do not have Jupyterlab installed on you local machine, you can install using: pip install jupyterlab
  * Jupyterlab can be opened from the GitHub repo directory using: <br> jupyter-lab
* Familiarize yourself with GitHub.
  * You may need to clone a repo to your local machine. Once cloned, the notebook will need to be run from the repo directory so that objects contained within can be accessed. Repos can be cloned using: <br> git clone repo_address
* Familiarize yourself with the Google Cloud environment.
  * If you do not have CloudSDK installed on your local machine, you can do so by clicking [this link](https://cloud.google.com/sdk/docs/install).
  * The Google Cloud [console](console.cloud.google.com) is a great place to begin working in the cloud environment. "