# How to make the calculation module run

After completed the installation steps, follow these final setting to get the software to run:

![gif](https://c.tenor.com/MsuBYU4-fI0AAAAM/confused-math.gif)

## Setting File Paths

So within the folder `docker` of the cloned repository, you'll find the script **run_megqc.py** and within it there are 2 filepaths to edit:
- **config_file_path=** here you'll need to write the path to the **settings.ini_**.

- **internal_config_file_path=** here you'll need to write the path to the **settings_internal.ini**.

Both files are located in  the `settings` folder within the `meg_qc` in the `site-packages` folder of your environment. The path should look something like this:

        /home/<user>/<environment_name>/lib/python3<.version>/site-packages/meg_qc/settings/settings.ini

<br>

## Specifying Dataset Path and subjects

Next open the file **setttings.ini** to edit the data directory path and subjects to be analyzed:

- **subjects=** is a string variable, you shall write the code of the participant you want to analye (f.e., 009), a list of subjects separated by a comma (001, 002, 003) or write "all".

- **data_directory=** Here, you only need to specify the path to the dataset, the pipeline will automatically process multiple subjects and files thanks to the ancpBIDS library. 

The file **setttings.ini** also contains an extensive amount of customizable parameters, but you can always use the default values (calculated to fit the majority of datasets). If you want to know more about this parameters, [please click here](settings_explanations.md).


## Running the calculation module

Finally, we are ready to run *rung_megqc.py*! Ensure that you activate the environment first:

        source home/<user>/<environment>/bin/activate


Then, the run command is given from the terminal and **not** from the command pannel. The command might be a similar line as:

        python3 /home/user/folder/MEGqc/docker/run_megqc.py

Now we are ready to analyze our data. In the next section we will see how the html reports are created.    