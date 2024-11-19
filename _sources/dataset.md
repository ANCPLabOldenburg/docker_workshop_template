# How to download a dataset

[OpenNeuro](https://openneuro.org/) is a free and open platform with more than 50 thousand participants and more than one thousand public BIDS compliant MRI, PET, MEG, EEG and iEEG datasets. 
In this tutorial, we'll use the data of one subject of one dataset that Gaponsetva (2023) used to validate MEGq. In this section we'll explain how can we get a dataset from OpenNeuro:

1. **Find the dataset:** The previous hyperlink takes you directly there, but if you didn't use it, you can go to the [OpenNeuro](https://openneuro.org/) main page, and introduce the Accession Number (ds003483).
2. **Download options:** If you click in download we get several options, such as download with the browser, fro S3, Node.js, DataLad and shell script. 

As the dataset includes 21 participants, it consist of 24.48 GB. Therefore, we'll just download one subject, for that, the easiest approach is to proceed with **DataLad**.

## Getting started with DataLad
[DataLad](github.com/datalad)is a free and open source data tool for management of large datasets. We can use it download a single subject folder from the the dataset.

0. **Ensure `git-annex` is properly installed on your system:** it might require an update if it's not equal or higher than 8.20200309.    
##
    git annex version
<br>

1. **Install datalad within your environment:** 
##
    pip install datalad
<br>

2. **Clone the dataset repository:** It copies the entire dataset's structure, but only lightweight metada (such as .json). The actual .fif files are not downloaded, even thought they will remain as _"broken links"_ placeholders. Be sure you are working in your desired directory (with **cd**).
##
    datalad install https://github.com/OpenNeuroDatasets/ds003483.git
<br>

![placeholder](static/placeholder.png)


3. **Download only the sub-009 folder:** use the get command to download only the data for subject 009.
##
    datalad get ds003483/sub-009/
<br>





