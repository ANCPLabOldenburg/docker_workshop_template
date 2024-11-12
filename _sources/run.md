# How to make MEGqc run

Once you've finished with the installation steps, now comes the last settings before making it run. 

## Configuration of filepaths

### To run calculation module
So within the folder _docker_ of the cloned repository, you'll find the script *run_megqc.py* and within it there are 2 filepaths to edit:
- **config_file_path=** here you'll need to write the path to the _settings.ini_ file within the _settings_ folder of your *meg_qc*, in the _site-packages_ of your python environment.

- **internal_config_file_path=** here you'll need to write the path to the *settings_internal.ini* file within the _settings_ folder of your *meg_qc*, in the _site-packages_ of your python environment.

Then you'll have to open the file _setttings.ini_ within the _settings_ folder of your *meg_qc*, in the _site-packages_ of your python environment and edit one last filepath:
- **data_directory=** it's in the line 54 of the script. "It's not necessary to write the entire path to every data file; insteaad, only the path to the entire dataset is rquired. The pipeline can be executed for several subjects and datasets in one click" (Gapontseva, 2023)


## Ain't no workshop good enough
The reality of workshops like these is that they really don't teach attending folks all they need to know to subsequently apply the respective content sufficiently, not to mention the training aspect. At best, workshops provide folks with the materials, overview and pointers necessary to continue and actually dive into the taught topics (the truth hurts sometimes, doesn't it?). Another important aspect that is frequently overlooked is that attendees usually need a certain set of skills and experience to really benefit from a given workshop, especially considering the diverse backgrounds folks have. We want to be fair, open and welcoming to everyone and while we know that we unfortunately can't achieve and assume a truly similar level of training and experience across all participants, we can at least do our best to work towards certain opportunities. That being said, workshops like the one you're currently looking at, usually by default (should) require basic to advanced programming skills and knowledge about file handling/input/output, signal processing, statistics and linear algebra (vectors much?). Tough stuff, eh?  

![logo](https://c.tenor.com/MsuBYU4-fI0AAAAM/confused-math.gif)\
<sub><sup><sub><sup>https://c.tenor.com/MsuBYU4-fI0AAAAM/confused-math.gif
</sup></sub></sup></sub>

## Let there be pre-workshop training
So what can we actually do to provide the entire attending gang with the chance to get up to speed for the workshop and ideally beyond? Unfortunately, we can't hold pre-workshop-workshops and various consultations. Instead we decided to utilize the fantastic [jupyter](https://jupyter.org/)-[python](https://www.python.org/)-open science world and build upon the framework of [jupyter books](https://jupyterbook.org/intro.html) employed to host this workshop and its materials. 

**Important**: we know that everyone has a lot of stuff to do and that not everyone will be able to go through the stuff we collected here. We've tried to keep this part minimal, but not everything can be skipped if we want this workshop to work for you.

We will try our best to bring the core points across, even if you don't have a substantial amount of experience. Please just make sure that you ask **all** the questions that might pop up, the same holds true for any problems you might encounter. 