# Running MEGqc

## Running the calculation module
Now, we're ready to run MEGqc! First, ensure that your environment is activated by checking the terminal prompt. It should look like this:

        (<your_environment_name>) user_name: ~$



Once the environment is activated, execute the script from the **terminal** and not from the command panel. The command requires 2 inputs:
1. **inputdata:** path to the root of your BIDS MEG dataset.
2. **subs:** ID code to the subject you want to analyze:
        - If you want more than one subject, the ID codes should be separated by a space.
        - If you want to analyze all the subjects of your dataset, you may write `all`.

YOur command line might look something like this:

        run-megqc --inputdata </path/to/your/dataset/> --subs <ID>

For example, if you want to analyze only subject `009` of the dataset `ds003483`, the command line might look like:

        run-megqc --inputdata /path/to/ds003483/ --subs 009



## Settings

### Default settings
When you enter the command, a terminal-based GUI will prompt you with the question: `Do you want to proceed with the default settings? (y/n)`. A hyperlink in the terminal will direct you to the [setting explanation page](../settings_explanation.md), where each parameter is described with more detail.

If you enter **y**, the program will use the default values for the parameters of each **metric**. The default settings, as calculated by Gaponsetva (2023), are designed to be compatible with a broad variety of datasets. 

### Customized Settings
If you enter `n`, you will be instructed to use the following command LINE to specify a path to your `target directory` where a copy of the config file (`setting.ini`) will be created: 
        
        get-megqc-config --target_directory <path/to/your/target/directory>

Then you can open your copy of `settings.ini` and adjust the settings. 
- For instance, if you want to skip a specific metric, locate the section `For which metrics to run the pipleline?` at the  begining of the file and change the value from `True` to `False`.

Once your config file is customized, you can run MEGqc including the option --config and the path to your customized **config file**. Make sure to include _"settings.ini"_ in the command line:

        run-megqc --inputdata </path/to/your/dataset/> --subs 009 --config </path/to/your/config/file/setting.ini>

### Already used config files?
If you have already processed the dataset, MEGqc will be able to find the already used config file(s) and will prompt you if `Do you want to use any of them again?`.
A **numbered list** of paths to previous config file will be displayed in ther terminal.
Then it will ask you to `Enter the number of the config file you want to use, or press Enter to use the default one`. Enter the corresponding **number** of the config file path you want to reuse.
If you don't want to use any previous config file, just press Enter to continue with your default setting or customized config file.

## Next section
With the calculation module successfully executed, let's explore how to generate the HTML report! 





<!--
OLD VERSION

## Setting File Paths

Within the `docker` folder of the cloned repository, you'll find the script **run_megqc.py**. To configure the software, you need to edit 2 filepaths of this script:
1. **config_file_path=** here you'll need to write the path to the **settings.ini_**.

2. **internal_config_file_path=** here you'll need to write the path to the **settings_internal.ini**.

Both setting files are located in  the `settings` folder within the `meg_qc` package, which reside in the `site-packages` directory of yourPython  environment. The path should look something like this:

        /path/to/environment/lib/python3./site-packages/meg_qc/settings/settings.ini

<br>


## Specifying Dataset Path and Subjects

Next open the file **setttings.ini** to edit the data directory path and specify the subjects to be analyzed:

- **subjects=** is a string variable, you shall write the code of the participant you want to analyze (f.e., 009). You can also provide a list of subjects separated by a comma (001, 002, 003) or write "all" to process all subjects.

- **data_directory=** SEt this to the path to the dataset directory. In case that you want to analyze more subject, the pipeline will find them within the dataset thanks to the ancpBIDS library. 

The file **setttings.ini** also contains an extensive amount of customizable parameters. However, the default values are optimized to to work with the majority of datasets. [In the next section you can find  more details about these parameters](settings_explanations.md).

-->
