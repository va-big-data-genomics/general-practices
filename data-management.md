# Effective Practices for Data Management in Biomedical Research
Contributors (alphabetical): Paul Billing-Ross, Daniel Cotter, Tao Wang, 

## Terminology
* **Data generation site**: An institution, such as a University or research lab that is responsible for generating processed experimental data and submitting it to a centralized data repository (Data Coordination Center)
* **Data generator**: A person such as a technician, graduate student, post-doc, or other researcher who is responsible for transforming “raw data” (e.g. biological sample, sequencing reads) into an experiment-specific processed data (e.g. DNA variants, RNA-seq results, imaging data). This person is responsible for sharing meta/data with the data manager.
* **Data coordination center (DCC)**: The organization responsible for compiling data collected from every member data generation site and transforming it into a medium that is accessible to the broader research community
* **Data manager**: A person with the technical expertise and responsibility to compile data generated at a data generation site and, …
  * Demonstrate to all stakeholders the value of effective data management
  * Establish effective practices for data generators to manage meta/data during the data generation and sharing process
  * Establish effective practices for data generators to share meta/data
  * Recommend technologies to improve the data generation & sharing process
  * If necessary, generate new tools to streamline procedures
  * Streamline the process of getting metadata from 3rd parties/vendors
  * Work with data generators to streamline data generation and sharing procedures
  * Ensure the completeness of data and metadata submission
  * Ensure the validity of the data and metadata
  * Perform necessary metadata cleaning and massaging
  * Restructure meta/data to fit the structure required by the DCC
* **Data sharing**: The process of the data generator sharing the processed data with the data manager, in preparation for data submission
  * Also can involve moving data around internally, by data manager (outside of DCC)
* **Data submission**: The process of the data manager submitting the compiled and finalized dataset to the data coordination center
  * Also can involve submission to internal LIMS system, likely before DCC submission
  * Data > Internal LIMS > DCC LIMS
  * Includes metadata submission as well as data submission (50/50)
  * Different modes of submission for different stakeholders
* **Project manager**: A person who sends emails.
## Goals
* Eliminate points of failure between the data generator, data manager, and data coordination center (DCC) 
* (As a data manager) Make a significant effort to understand the workflows and challenges of researchers, and help develop solutions that make their lives easier
* Standardize methods for managing data (across different projects)
  * Leverage existing infrastructure & tools between projects
  * Leverage existing knowledge
  * Minimize the cognitive load and migration load, to new methods
  * Limitations:
    * Constraints from DCC
    * Resistance to change
* Federate data sharing to support different research populations
  * Researchers within a lab
  * Researchers with an institution
  * Researchers outside of the institution
## Project initiation
* Formalize the role of the data manager in project management.
  * Recognize that effective project management cannot occur without data management. 
  * The data manager becomes a de facto project manager by virtue of their position at the center of all data operations. They should be formally recognized as a project manager or clearly establish a mode of working in tandem with the project manager
  * Establish the scope of responsibilities (for the data manager)
* Have everyone go through checklist of prerequisites for the data generation and management process
* Establish agreed upon modes of communication (Email, Slack, etc.) and what kind of information should be exchanged using them.
  * People use email/slack when things don’t go as planned
* Establish how data management meetings will occur
  * For smaller groups this, data management discussions may occur in the context of other meetings (e.g lab meetings)
  * For large consortiums, with many members, it may be necessary to schedule separate meetings dedicated to data management
* Establish what kind of project management software will be used (Trello, Jira, GitHub, Asana, etc.)
* The data manager should try to establish a connection with at least one person within each data generation site
  * Confirm that established practices are being followed
  * Resolve interpersonal or technical issues that arise
* Establish mapping of terms and IDs within project resources and between other projects
  * Identify ontologies to use or how terms relate to other ontologies
  * Map site specific IDs to global IDs or establish what/how IDs will be used
## Data generation
* Work with the DCC and researchers to establish the dictionary of metadata that will be included with data
* Establish the data sharing methods and have all data generators run through the procedures with a dummy dataset to expose any road blocks (e.g. permissions issues)
* Based on the frequency of submissions and volume of data, establish a schedule for data sharing that leaves enough buffer time to resolve any meta/data issues
## Data sharing
* Pre-hoc: If possible, use structured templates for data submission (e.g. web page, Google Forms)
  * Also for issue submission
    * Ensure completeness of issue tickets (e.g. code snippet, SCG submission scripts)
  * Set expectations for communication
* Post-hoc: If a pre-hoc solutions is not feasible or adequate, write a program that will validate the structure and format of data once it has been submitted to the data manager
