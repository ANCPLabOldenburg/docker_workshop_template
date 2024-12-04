# Introduction to MEGqc

## MEG data quality control
Magnetoencephalography (MEG) data is susceptible to  noise and artifacts, which can severely corrupt the data quality. These artifacts may arise from:
- Environmental noise sources (e.g. powerline noise)
- Internal noise sources (e.g. eye movements of the subject)
- Systemic noise sources (e.g. malfunction of a sensor).

For this reason, quality control of MEG data is an essential step for ensuring valid and reproducible science (Niso et al., 2022).  
However, the visual detection and annotation of artifacts in MEG data requires expertise, and still can be:
- A tedious and time-consuming task
- Commonly performed manually
- Vulnerable to biases
- Not standardized 

*(fragment adapted from the MEGqc github)* 

![maths](https://media1.tenor.com/m/DCycRQnBpOYAAAAd/math-hmm.gif)



## MEGqc
To address this issue, the ANCP lab developed the MEGqc, a software tool for automated and standardized quality control of MEG recordings. By providing a standardized workflow, it helps minimize human bias and facilitates comparisosn between datasets.

MEGqc Evaluates the quality of raw data, but is **not** an artifact removal tool. The MEGqc pipeline is designed to be user-friendly, so researches only need to:
- Provide data for evaluation
- Set analysis parameters if desired (default parameters are available), and 
- Run the analysis script.

To ensure standardization of the pipeline, MEGqc software is tailored to the [**BIDS standards**](details.md).


### Metrics in MEGqc
The different  calculation modules within MEGqc are called `metrics` and they are used to evaluate specific types of artifacts or aspects of data quality. There are six independent metrics:
- **Standard Deviation calculation**
- **Power Spectral Density calculation**
- **Peak-to-Peak manual calculation**
- **ECG (Electrocardiogram)and EOG (Electrooculography) calculation:** it produces 2 reports
- **Muscle artifacts calculation**
<br>  


There are 2 other metrics within MEG QC:
- **Peak-to-Peak automatic calculation:** This module, which relies on MNE library functions, is not used in the final version of the pipeline. Instead, the manual "Peak-to-Peak manual" is recommended.
- **Head movement calculation:** This module functions, but requires extensive head position data.

For a deeper understanding of MEGqc's core functionality, [visit the pipeline basics page](details.md).



## MEGqc derivatives  
MEGqc produces two types of [machine-readable outputs](details.md):
- **JSON files*** with the key information for each of the quality metrics.
- **TSV files**** with more detailed results for some of the metrics.

To ensure the clarity of the results, the pipeline includes a **plotting module** that generates visual HTML reports based on the TSV files. For each metric, an html report is created (6 in total). The next section will delve in the kind of information included within each report. These outputs also maintain the **BIDS standards.**


### Next section
In the next section, we'll walk through the content of the HTML reports.      

        
