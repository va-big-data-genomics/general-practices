# Using Jupyter Notebooks to Implement Methods on Google Cloud
Authors: Joseph Sarro, Paul Billing-Ross

## Style guide
* Talk directly to the user.
  * **Yes**: "When you connect to the database"
  * No:  "When the user connects to the database"
* Use the imperative mood when giving directions.
  * **Yes**: "Connect to the database"
  * No: "You may connect to the database"
* For code snippets, use keywords to specify arguments to functions and put each argument on a separate line.
  * **Yes**:
    
        connection = dbConnect(  
          drv = bigrquery::bigquery(),  
          project = project,  
          dataset = data_set,  
          billing = billing)  
  * No:
    
        conn = dbConnect(bigquery(), project, data_set, billing)

## Creating a notebook
### Notebook header
* Create a header section with the following section
  * **Authors**: Include names of anyone who has made significant contributions, ordered chronologically by when the first made a contribution.
  * **Notebook kernel**: Include the name of the kernel and link to relevent webpage if appropriate.
  * **Recommended (Cloud Platform) machine/cluster type**: Indicate the machine type using Google format (e.g. "e2-standard-2"). If you need to provide more configuration information, add it in a separate notebook section.
  * **Predicted runtime**: If less than an hour, provide time in minutes. If more than an hour, provide time in hours. Make sure this is using the recommended machine type.
  * **Predicted cost**: Predicted cost based on machine/runtime in US dollars.

 > Authors: Sam Science  
 > Notebook kernel: R (https://irkernel.github.io/installation/)  
 > Recommended Google Cloud Platform machine type: e2-standard-2  
 > Predicted runtime: 45 minutes  
 > Predicted cost: $50  

### Notebook body
* Begin with a detailed summary of what the workflow does. What is the purpose of this workflow? What are the output objects? What will these objects be used for? How were the input objects generated?
* Describe any dependencies needed. Descriptions of novel tools and possible links should also be included. For example, Trellis may not be a tool a user is familiar with and background information could be useful.
* As much as possible, use words instead of acronyms. This will improve readability especially for users unfamiliar with the domain.
  * **Yes**: Base Quality (BQ) for 15000 sample list
  * No: BQ for 15000 sample list
* Provide a brief description of each object.
  * **What** is the object?
  * **Where** does it comes from?
  * **How** is it used?
  * **Who** can view/access this object? The sensitivity of the contents should be stated in the case of medium or high risk data.
* Limit the use of object paths to those that are contained in the repo. All other objects should be stored in Google Cloud Storage.
* Adding line numbers to code could help in debugging.
* Make sure final product is clean of unnecessary code.
  * Are lines of commented out code needed?
  * Is every step necessary?
* When generating dataframes/tables, display a small section of the output so users can see what the data looks like.
* Each code cell should perform a single operation. Split compound operations into separate cells. This will make your notebook
  * More flexible to use
  * Easier to debug
  * More robust
* As much as possible, add coherence checks, such as summary metrics, to code cells that involve data transformations so that users can check, as they go, that their results look good.

## When running a notebook
* Make sure that all dependencies are installed.
* Before running any command on cloud services:
  * Make sure you have proper dependencies installed.
  * Check object sizes. Running very large objects can be expensive.
  * Double check memory usage of software being run. Memory intensive programs can be expensive to run.
* Familiarize yourself with Jupyter Notebooks.
  * If you do not have Jupyterlab installed on you local machine, you can install using: pip install jupyterlab
  * Jupyterlab can be opened from the GitHub repo directory using:

    ```
    jupyter-lab
    ```

* Familiarize yourself with GitHub.
  * You may need to clone a repo to your local machine. Once cloned, the notebook will need to be run from the repo directory so that objects contained within can be accessed. Repos can be cloned using:

    ```
    git clone repo_address
    ```
    
* Familiarize yourself with the Google Cloud environment.
  * If you do not have CloudSDK installed on your local machine, you can do so by clicking [this link](https://cloud.google.com/sdk/docs/install).
  * The Google Cloud [console](console.cloud.google.com) is a great place to begin working in the cloud environment.

## Run Hail on a Vertex AI Workbench notebook
### Create a notebook
Hail is an open-source, general-purpose, Python-based data analysis tool with additional data types and methods for working with genomic data (https://hail.is/).
* Launch a Vertex AI notebook from the the Google Cloud Platform web console with with the Python3 environment.
* Click "OPEN JUPYTERLAB" in the console.
* Once Jupyter Lab opens in your browser, open a terminal within Jupyter Lab.

### From the terminal
* Following these instructions to link your GitHub account to the notebook and clone your repository: 
  https://cloud.google.com/vertex-ai/docs/workbench/user-managed/save-to-github. Make sure to use the **SSH** address of your repository.
* Install Java (required for Hail)
Run the following commands in the terminal. From this DigitalOcean guide:  
https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-debian-10
    ```
    sudo apt update  
    sudo apt install default-jre  
    java -version
    ```
* Install Hail
    ```
    python3 -m pip install hail
    ```
* Authenticate your credentials with gcloud
You need to do this for the next step.
    ```
    gcloud auth application-default login
    ```
* Install the Google Cloud Storage connector
The connector will allow Hail to read objects directly from Google Cloud Storage. From the Hail docs (https://hail.is/docs/0.2/cloud/google_cloud.html#):
    ```
    curl -sSL https://broad.io/install-gcs-connector | python3
    ```
Now you should be set to run Hail locally from your notebook!
