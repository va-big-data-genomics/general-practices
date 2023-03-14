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

### Installing Python packages

These guidelines are informed by Jake VanderPlas's guide to Jupyter Python installs:
[https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter).

Recommended syntax example:

```
!{sys.executable} -m pip install python-library
```

There are two main elements to take note of here.

1. Use the `sys` module to perform installs using `pip`. This will ensure that you are using the `pip` version associated with the active Python kernel.

2. Use the `python -m pip` syntax to call `pip`. This will make sure your `pip` matches your Python version.

### Loading secrets

We want to create Jupyter notebooks that can become public resources, shared widely. We also want to organize project metadata in a way that makes in easy for internal team members to reproduce or replicate existing analyses. However, we don't want to share project specific details that could compromise the security of our environment of private information.
 
**Do not hardcode private paths into notebooks.**

There are (2) recommended practice for loading project specific information into a notebook.

1. Use <ins>[Secret Manager](https://cloud.google.com/secret-manager)</ins> to store the information as a secret, associated with the Google Cloud Project.
2. Store the information in a configuration file (YAML or JSON) in a storage bucket and create a secret with the path to that object. The most optimal time to use this approach is probably when there is a single bucket dedicated to the initiative described in your notebook. For instance: if your notebook describes an analysis for releasing data, and each data release has its own bucket with a configuration file.

A vulnerability of approach #2 is that the mapping from the secret to the configuration object can be broken if the object is moved or renamed. An advantage is that the configuraiton object is easier to interact with and find as it can be stored closer to the data.

An example of interacting with Secret Manager in Python
```
# Install Secret Manager library
import sys
!{sys.executable} -m pip install --upgrade google-cloud-secret-manager

from google.cloud import secretmanager

# Create the Secret Manager client.
client = secretmanager.SecretManagerServiceClient()

# Access the YAML doc stored as a secret.
response = client.access_secret_version(request={"name": "projects/123456789123/secrets/secret-name/versions/1"})

# Load YAML doc into a dictionary
config_yaml_doc = yaml.safe_load(response.payload.data.decode('utf-8'))
```

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
Hail is an open-source, general-purpose, Python-based data analysis tool with additional data types and methods for working with genomic data (https://hail.is/). Vertex AI notebooks are managed instances with JupyterLab and other data science libraries already installed and configured.

* Access Vertex AI notebooks through the Googe Cloud console: https://console.cloud.google.com/vertex-ai/workbench.
* Launch a Vertex AI notebook from the the Google Cloud Platform web console with with the Python3 environment. I also recommend using the **Ubuntu** operating system since I have experienced permissions issues running commands as an administrator (user "root").
* Click "OPEN JUPYTERLAB" in the console.
* Once Jupyter Lab opens in your browser, open a terminal within Jupyter Lab.

### From the terminal
* Following these instructions to link your GitHub account to the notebook and clone your repository: 
  https://cloud.google.com/vertex-ai/docs/workbench/user-managed/save-to-github. Make sure to use the **SSH** address of your repository.
* Install Java (required for Hail)
Run the following commands in the terminal. From this DigitalOcean guide:  
https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-debian-10. And make sure that either Java 8 or 11 have been installed, as these are the only version supported by Hail.
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
