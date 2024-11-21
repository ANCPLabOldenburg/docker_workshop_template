# Installation of MEGqc

Now we'll start with the installation process for MEGqc. Before diving in, we'll briefly explain virtual environments and containerization:
<br>

## Virtual environments
Virtual environments create isolated and sel-contained workspaces, allowing us to manage project-specific dependencies separatedly from system-wide installation. This isollation has several benefits:
- **Avoid dependency conflicts:** prevents interferences between project-specific and system-wide dependenciesm, such as common erors related to version mismatches.
- **Transparency and Open Science:** Ensures that others can replicate your results and reproduce your analysis reliably.

![environments](static/python-virtual-envs1.webp)

To create and activate your virtual environment, follow these steps:
1. Navigate to the directory where you want to create the environment using the `cd` command in the terminal.
2. Create the virtual environment:

        python3 -m venv <your_environment_name>

3. Activate the virtual environment:

        source /path/to/environment/bin/activate

4. Once activated, you should see `(<your_environment_name>)` in the  terminal prompt. 

<!--
### Python Environment

MEG QC has compatiblity issues with older Python versions (prior to 3.9), therefore it's necessary to upgrade your Python version. Environments allows one to work with specific versions of Python itself without affecting other projects within the same network or the OS itself.


**[pyenv](https://github.com/pyenv/pyenv)** is a simple python version management. It let's you easily swtich between multiple versions of Python. In their github you can find the instruction to install pyenv, create your own environment with your desired Python version and activate it. 
-->

## Install & clone the MEGqc Package
Once your environment is activated, you can install Python packages with `pip`, and these installations will only apply to your virtual environment. To install MEGqc core functionality, run the following command in the terminal:
##
        pip install --upgrade meg-qc
<br>

Next, you will need to clone the [Github Repository](https://github.com/ANCPLabOldenburg/MEGqc). 

![repository](static/github.png)

- The folder _docker_ contains the starting script *run_megqc.py*.
- The folder *meg_qc* is a copy of the previously installed MEGqc package via `pip`.

## Install depencies
For MEG QC to function, you'll need to pip install the following depencies. All the hyperlinks take you to the documentation page:

- **[mne (Magnetic and Electric Neuroimaging)](https://mne.tools/stable/index.html):** "MNE is an open-source package for exploring, visualizing and analyzing human neuropshysiological data (...). This package is also the basis for the MEGqc pipeline" (Gapontseva, 2023). It has been extensively documented and constantly updated by an active community support. 
##
        pip install --upgrade mne
<br>

- **[ancpBIDS](https://ancpbids.readthedocs.io/en/latest/userDocCombined.html):** This library, developed in the ANCP lab, is used to read and query BIDS datasets as well as write the derivatives back. 
##
        pip install ancpbids
<br>

- **[Numpy (Numerical Python)](https://numpy.org/doc/)** and **[pandas](https://pandas.pydata.org/docs/):** Both libraries are necessary for scientific computing and data manipulation in Python, particulary for working with multidimensional arrays and large matrices. 
## 
        pip install numpy
##
        pip install pandas
<br>

- **[plotly](https://plotly.com/python-api-reference/)**: This library is used to create the interactive plots and visualize results. Plotly also supports exporting the figures in HTML format.
##
        pip install plotly

