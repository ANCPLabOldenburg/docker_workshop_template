# Introduction to MEG quality control

## MEG data quality control:
Magnetoencephalography (MEG) data are susceptible to  noise and artifacts, which can severely corrupt the data quality. They can originate from environmental noise sources (e.g. powerline noise), internal noise sources (e.g. eye movements of the subject), or systemic noise sources (e.g. malfunction of a sensor). For this reason, quality control of the data is an important step for valid and reproducible science (Niso et al., 2022).  
However, the visual detection and annotation of artifacts in MEG data require expertise, is a tedious and time extensive task, is commonly done manually (vulnerable to biases) and hardly resembles a standardized procedure. Despite the minimization of human biases, a standardized workflow for quality control will additionally make datasets better comparable thereby allowing for between-datasets comparisons as opposed to quality control within a single dataset. Hence, an automated and standardized approach to quality control is desirable for the quality assessment of in-house and shared datasets. 

To address this issue the ANCP lab developed a software tool for automated and standardized quality control of MEG recordings.
*(disclaimer: fragment adapted from MEGQc github)* 

## MEGqc
The MEGqc pipeline is designed to be user-friendly: Researches only need to provide data for evaluation, set analysis parameters if desired (default parameters are available), and run the analysis script. MEGqc is not an artifact removal tool but rather a tool that evaluates the quatlity of raw data to assist researches in making informed decision about further analysis (Gapontseva, 2023).

The different  calculation modules within MEGqc are called ***metrics*** and they are used to evaluate specific types of artifacts or aspects of data quality. There are six independent metrics:
- Standard Deviation calculation 
- Power Spectral Density calculation 
- Peak-to-Peak manual calculation 
- ECG (Electrocardiogram)and EOG (Electrooculography) calculation: it produces 2 reports
- Muscle artifacts calculation  
<br>  


There are 2 other metrics within MEG QC:
- Peak-to-Peak automatic calculation: This module is not used in the final version of the pipeline; we'll use the Peak-to-Peak manual. The name refers to the computation using the MNE library function.
- Head movement calculation: it's actually functioning, but requires a huge amount of head positioning data.

To ensure standardization of the pipeline, MEGqc software is tailored to the BIDS standards.

# What is BIDS?: 

Neuroimaging experiments result in complex data that can be arranged in many different ways, and for a long time, there was no consensus how to organize and share data obtained in neuroimaging experiments. Brain Imaging Data Structure (BIDS), describes a simple and easy to adopt way of organizing neuroimaging and behavioral data (Gorgolewski et al., 2016; Niso et al., 2018) facilitating collaboration between researches and saving time and effort.  _(fragment adapted from BIDS official website)._ 

![bids-logo](static/bids.jpg)

BIDS describes the structure of the data, directories and sub-directories, name-structure, file-naming and file formats. To be able to ensure this standardization, MEGqc uses **ancpBIDS**, a Python library which facilitates working with BIDS, both for identifiying the files and also for writting the results according to BIDS. 

Gapontseva (2023) evaluated the MEGqc software thanks to 21  MEG datasets obtained from the OpenNeuro data library. [OpenNeuro](https://openneuro.org/) is a free and open platform with more than 50 thousand participants and more than one thousand public BIDS compliant MRI, PET, MEG, EEG and iEEG datasets. 



## General Pipeline Stucture

The following figure (Gaponsetva, 2023) describes the general process of the pipeline. It might look  a bit overwhelming, but don't worry, in this workshop will go step-by-step. 

![Pipeline](static/pipeline.png)

The time is on the Y axis, from top to bottom: 

- The configuration file contains the data directory path and the parameters for the selected metrics. Default values for all metrics are preset, but they can be modified as needed.
- The data files are identified thanks to ancpBIDS.
- The dataset are loaded and pre-processed: epoching, resampling and filtering (taking into account users' parameters).
- Every selected metric is executed (taking into account users' parameters) 
- Results for each data file are assembled into  2 different datac structures, the _derivatives_.
- ancpBIDS writes the _derivatives_ into the corresponding dataset directory, keeping the BIDS naming convention.

## MEGqc derivatives  
MEGQc produces the following output from the analysis of a data file:
- json file* with the key information for each of the quality metrics in a Python dictionary format.
- A tsv file** with more detailed results for some of the metrics presented as Pandas Data Frames.

Both of them are Machine-Readable reports that enables further analysis and computations. To ensure the clarity of the metrics, the pipeline has an extra module called _plotting_ which generates html reports with visual representations generated out of the tsv files:  

- An html report for every metric (6 in total).

<br>   
  
In the next section, we'll walk through the key sections of the MEGQc report.       
        
        
---

* *json file: A JSON (JavaScript Object Notation) file is a lightweight data format that stores structured data in a readable, text-based format using key-value pairs, arrays, and nested objects.*  
* **tsv file: A TSV (Tab-Separated Values) file is a simple text file that stores tabular data, with each line representing a row and each value in the row separated by tab characters.*  