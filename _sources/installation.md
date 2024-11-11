# Installation

Now we'll start with the installation process of MEG QC. Before that we want to explain you about virtual environments and containerization:
<br>

## Virtual environments
Virtual environments create isolated and sel-contained workspaces, allowing us to manage project-specific dependencies separated from the system-wide installation. This isollation has several benefits:
- Avoid interference among dependencies of other project-specific and system-wide dependencies avoiding common errors related to depencies, versions.
- Transparency and Open Science: Ensure that others can replicate your results or able to reproduce your analysis.
<br>

### Python Environment

MEG QC has compatiblity issues with older Python versions (prior to 3.9), therefore it's necessary to upgrade your Python version. Environments allows one to work with specific versions of Python itself without affecting other projects within the same network or the OS itself.
**[pyenv](https://github.com/pyenv/pyenv)** is a simple python version management. It let's you easily swtich between multiple versions of Python. In their github you can find the instruction to install pyenv, create your own environment with your desired Python version and activate it. 
<br>

## Install MEG QC Package
Once within your project environment or Python environment, use pip to install MEG QC core functionality by running the following command in bash:
##
        pip install --upgrade meg-qc
<br>

Then you will need to down the [github repository](https://github.com/ANCPLabOldenburg/MEGqc) and unzip it. This will be necessary to access the starting script *(run_megqc.py)*.
<br>

## Other Packages:
For MEG QC to function, you'll need to pip install the following depencies:

- **[ancpbids](https://ancpbids.readthedocs.io/en/latest/userDocCombined.html):** it helps handling and querying information in a BIDS format.
##
        pip install ancpbids
<br>

- **[mne](https://mne.tools/stable/index.html):** a popular open-source package for processing MEG and EEG data.
##
        pip install --upgrade mne
<br>

- **[pandas](https://pandas.pydata.org/docs/):** This library is necessary for data manipulation and analysis in Python.
##
        pip install pandas
<br>

- **[plotly](https://plotly.com/python-api-reference/)**: This library is necessary for creating plots and visualizing the results.
##
        pip install plotly