# Running the plotting module

Once the calculation module has completed the analysis, it generates JSON and TSV files that are saved in the `derivatives` folder within the dataset folder. The path to your `derivatives` might look something like this:

        /path/to/dataset/derivatives/Meg_QC/calculation/subjects/
        
As you can see, the calculation module generates numerous metadata files. But what if we want the data to be neatly organized and presented in a visual and interactive way?
Luckily MEGqc will automatically ask you wether `Do

Luckily MEGqc also contains the plotting module, which generates the HTML reports we saw earlier. Let's see how can we produce them:

## Automatic


## Setting File Paths

First, locate the script *meg_qc_plots.py* within the `plotting`folder in the `meg_qc` package, which is located in the `site-packages` folder of your environment. The path might look like this:

        /path/to/environment/lib/python3.9/site-packages/meg_qc/plotting/


Open the *meg_qc_plots.py*, and at the very last line where **tsvs_to_plot=** is defined, add your path to your dataset (e.g., ds003483). The line should look similar to this:

        tsvs_to_plot = make_plots_meg_qc(ds_paths=['/path/to/dataset/'])

## Running the plotting module

Ensure that you are working within your environment and then run the script from the command line. The command might look like:

        python3 /path/to/environment/lib/python3.9/site-packages/meg_qc/plotting/meg_qc_plots.py

## GUI
After running the plotting command, a text-based GUI will appear in the terminal, asking you several questions about specific parameters. The available options are based on the metadata MEGqc finds in your dataset.:
- Subjects: ALL or a specific one
- Sessions: ALL or a specific one
- Tasks: ALL or a specific one
- Runs: ALL or a specific one
- Metrics: ALL or a specific one
- Sensors: ALL, or only magnetometers or gradiometers

![gui](static/gui.png)

## Congrats!

You did it! Now you have the HTML reports within the `derivatives` folder of your dataset. You can open them with Chrome or Firefox to view the interactive plots of the quality control analysis of your dataset!




