# How to run the calculation module

After completing the installation steps, follow these final settings to get the software running:

![gif](https://c.tenor.com/MsuBYU4-fI0AAAAM/confused-math.gif)

## Setting File Paths

Within the `docker` folder of the cloned repository, you'll find the script **run_megqc.py**. To configure the software, you need to edit 2 filepathsin this script:
- **config_file_path=** here you'll need to write the path to the **settings.ini_**.

- **internal_config_file_path=** here you'll need to write the path to the **settings_internal.ini**.

Both setting files are located in  the `settings` folder within the `meg_qc` package, which reside in the `site-packages` directory of yourPython  environment. The path should look something like this:

        /path/to/environment/lib/python3./site-packages/meg_qc/settings/settings.ini

<br>

## Specifying Dataset Path and Subjects

Next open the file **setttings.ini** to edit the data directory path and specify the subjects to be analyzed:

- **subjects=** is a string variable, you shall write the code of the participant you want to analyze (f.e., 009). You can also provide a list of subjects separated by a comma (001, 002, 003) or write "all" to process all subjects.

- **data_directory=** SEt this to the path to the dataset directory. In case that you want to analyze more subject, the pipeline will find them within the dataset thanks to the ancpBIDS library. 

The file **setttings.ini** also contains an extensive amount of customizable parameters. However, the default values are optimized to to work with the majority of datasets. For more details about these parameters, [please click here](settings_explanations.md).


## Running the calculation module

Now, we're ready to run *rung_megqc.py*! But first, ensure that you activate your virtual environment:

        source /path/to/environment/bin/activate


Once the environment is active, execute the script from the **terminal** (*not** from the command panel). The command might look somehting like this:

        python3 /path/to/MEGqc/docker/run_megqc.py

### Next section
With this, you're all set to analyze your data! In the next section you'll learn how to produce the HTML reports.   