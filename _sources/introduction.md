# Introduction to MEG quality control and BIDS


**MEG data quality control:**  
Magnetoencephalography (MEG) data are susceptible to  noise and artifacts, which can severely corrupt the data quality. They can originate from environmental noise sources (e.g. powerline noise), internal noise sources (e.g. eye movements of the subject), or systemic noise sources (e.g. malfunction of a sensor). For this reason, quality control of the data is an important step for valid and reproducible science (Niso et al., 2022).  
However, the visual detection and annotation of artifacts in MEG data require expertise, is a tedious and time extensive task, is commonly done manually (vulnerbale to biases) and hardly resembles a standardized procedure. Despite the minimization of human biases, a standardized workflow for quality control will additionally make datasets better comparable thereby allowing for between-datasets comparisons as opposed to quality control within a single dataset. Hence, an automated and standardized approach to quality control is desirable for the quality assessment of in-house and shared datasets.  
To address this issue the ANCP lab developed a software tool for automated and standardized quality control of MEG recordings, MEGqc, which is inspired by software for quality control in the domain of fMRI, called mriqc (Esteban et al., 2017). MEGqc is designed to detect specific noise patterns in the data and visualize them in easily interpretable human-readable reports.  

*(disclaimer: fragment adapted from MEGQc github)* 

## What is BIDS: 
 
 
Neuroimaging experiments result in complex data that can be arranged in many different ways. For a long time, there was no consensus how to organize and share data obtained in neuroimaging experiments. Lack of consensus (or a standard) leads to misunderstandings and time wasted on rearranging data or rewriting scripts expecting certain structure. Brain Imaging Data Structure (BIDS), describes a simple and easy to adopt way of organizing neuroimaging and behavioral data.

Since neuroimaging data can be very diverse (concerning their structural organization) MEGQc software is tailored to the BIDS standard (Gorgolewski et al., 2016; Niso et al., 2018). Thus MEGqc requires the data to be organized according to BIDS.

[EXPAND WITH SPECIFICATIONS AND EXAMPLES]

_(discalimer: fragment adapted from BIDS official website)_

# MEG Qc Results  
MEGQc produces the following output from the analysis of a data file:
- A csv file* with the results for some metrics.
- json file** with the resulsts for all metrics.

Once the csv files have been produced, another module within MEG Qc called ***plotting*** can be used to create:
- An html report for every metric (6 in total).

Metrics are the diferent ***calculation modules*** within MEGQc used to evaluate specific types of artifacts or aspects of data quality. There are six metrics, which we'll explore in detail later, but we'll mention them now:
- Standard Deviation calculation 
- Power Spectral Density calculation 
- Peak-to-Peak manual calculation 
- ECG (Electrocardiogram)and EOG (Electrooculography) calculation: it produces 2 reports
- Muscle artifacts calculation  
<br>  


There are 2 other metrics within MEG QC:
- Peak-to-Peak automatic calculation: This module is not used in the final version of the pipeline; we'll use the manual one.
- Head movement calculation: it's actually functioning, but requires a huge amount of head positioning data.

<br>   
  
In the next section, we'll walk through the key sections of the MEGQc report.       

      
        
        
---


**csv file: A CSV (Comma-Separated Values) file is a simple text file that stores tabular data, with each line representing a row and each value in the row separated by a comma.*  
***json file: A JSON (JavaScript Object Notation) file is a lightweight data format that stores structured data in a readable, text-based format using key-value pairs, arrays, and nested objects.*  

