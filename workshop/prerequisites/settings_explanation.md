# Settings description

The **settings.ini** file not only specifies the data directory path and subjects to be analyzed, but also contains an extensive array of customizable parameters.

The MEGqc pipeline parameters were selected and estimated to be suitable to the greatest amount of datasets, so the users don't need to select them manually. However, all these parameters are gathered and nicely organized in this script, so researches can edit them to adjust eh pipeline to their specific goals and   research needs.

In this section we'll provide an overview of each parameter group, explaining their purpose and how they can be customized.


|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|**ch_types**| mag, grad|string|defines which channels to process.|
|**STD, PSD, PTP_manual, PTP_auto_mne, ECG, EOG, Head, Muscle**| All true except Head|boolean|activates or deactivates one of the calculation modules. Head is deactivate by default because normally the user doesn't posses the cHPI data to estimate subject's head positions.|
|**data_crop_tmin**|0| |Crop the data, time in seconds|
|**data_crop_tmax**|120| |Crop the data, time in seconds. If you want to use the entire recording, you can leave one or both parameters blank.|
|**plot_mne_butterfly**|False| boolean||
|**plot_interactive_time_series**|False|boolean|Plot interactive time series (each channel on top of others, separated by ch type: mags, grads). This plot may signifcantly increase the time it takes to run the script. If you want to run the script faster, set this to False. Plot will be done on the data resampled to 100Hz/sec. |
|**plot_interactive_time_series_average**|False|boolean|Plot interactive time series average (average over all channels of each type: mags, grads). Plot will be done on the data resampled to 100Hz/sec.|
|**verbose_plots**|Flase|boolean|Show plots when running the script.|

## Filtering

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|apply_filtering|True|boolean|It decides if the bandpass filter is applied or not. Change to Flase to turn off completely this section, the rest of parameters don't matter|
|downsample_to_hz| 1000|int or float|Frequency to downsample to. Must be: 1) at least 5 times higher than h_freq to avoid misrepresentation. 2) small value may lead to misrepresentation of chpi coils signal. They send signals in frequencies in higher than 100 hz. When downsampled this information may disappear. Recommended optimal value: 1000. Recommended minimum value: 500 Unit: Hz. Can be also set to False to avoid downsampling.|
|l_freq|0|int or float|lower frequency for bandpass filter.|
|h_freq|140|int or float|higher frequency for bandpass filter.|
|method |iir|string|Method for filtering|

## Epoching

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|event_durr|0.2|float| the duration of the event in seconds.|
|epoch_tmin|-0.2|float| time before the event, in seconds|
|epoch_tmax|1|float|time after the event, in seconds|
|stim_channel| |string| Leave empty if want it to be detected automaticall or write explicetly|
|even_repeated|merge|string| How to handle duplicates in events. Can be 'error' to raise an error, ‘drop’ to only retain the row occurring first in the events, or 'merge' to combine the coinciding events (=duplicates) into a new event (see Notes for details).|

## STD

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|std_lvl|1|integral|Defines how many std from the mean to use for the threshold|
|allow_percent_noisy_flat_epochs|70|int|Defines how many percept of epochs can be noisy or flat. Over this value, the epoch is marged as noisy/flat|
|noisy_channel_multiplied|1.2|float or int|Multiplier to define noisy channel, if std of this channel for this epoch is over (the mean std of this channel for all epochs  together* multipliar), then this channel is noisy. The higher the value, the less channels are marked as noisy|
|flat_multiplied|0.5|float or int|Multiplier to define flat channel, if std of this channel for this epoch is under (the mean std of this channel for all epochs together*  multipliar), then this channel is flat|

## PSD

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|freq_min|0.5|int or float|lower frequency for PSD calculation in HZ.|
|freq_max|140|int or float|higher frequency for PSD calculation in Hz|
|psd_step_size|0.5|float or int| frequency resolution of the PSD in Hz|

## PTP_manual

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|max_pair_dist_sec|20|float| define the maximum allowed time distance (in seconds) between the positive and negative peaks when calculating the peak-to-peak (PtP) amplitude.|
|ptp_thresh_lvl|10|int|scaling factor for the threshold. The higher the value is, the more peaks will be detected.|
|allow_percent_noisy_flat_epochs | 70 | int | Defines the percent of epochs that can be noisy or flat. Over this number - the epoch is marged as noisy/flat. |
|std_lvl|1|int|Defines how many std from the mean to use for the threshold.|
|noisy_channel_multiplied|1.2| float or int| multiplier to define noisy channels, if the std of this channel for this epoch is under (the mean std of this channel for all epochs together*multipliar), then this channel is flat|
|flat_multiplier|0.5|float or int| Multiplier to define a flat channel, if the std of this channel for this epoch is under (the mean std of this channel for all epochs together*multipliar), then this channel is flat|
|ptp_top_limit | 1e-12 | | this variable and the following are not used. In case instead of by std levle, we want to use Tesla.|
|ptp_bottom_limit| -1e-12|  ||

## PTP_auto

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
| peak_m | 4e-14 | float or int|  minimal PTP amplitude to count as peak for magnetometers. Unit: Tesla or Tesla/meter depending on channel type|
| peak_g | 4e-14 | float or int | minimal PTP amplitude to count as peak for gradiometers. Unit: Tesla or Tesla/meter depending on channel type |
| flat_m | 3e-14 | float or int | max PTP amplitude to count as flat for magnetometers. Unit: Tesla or Tesla/meter depending on channel type|
|flat_g | 3e-14 | float or int | max PTP amplitude to count as flat for gradiometers. Unit: Tesla or Tesla/meter depending on channel type|
| bad_percent | 5 |int | The percentage of the time a channel can be above or below thresholds. Below this percentage, Annotations are created. Above this percentage, the channel involved is return in bads. Note the returned bads are not automatically added to info['bads']. 
| min_duration | 0.002 | float | The minimum duration (s) required by consecutives samples to be above peak or below flat thresholds to be considered. to consider as above or below threshold. For some systems, adjacent time samples with exactly the same value are not totally uncommon. Unit: seconds. |

## PTP_auto
|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
| peak_m | 4e-14 | float or int |minimal PTP amplitude to count as peak for magnetometers. Unit: Tesla or Tesla/meter depending on channel type|
|peak_g  | 4e-14 | float or int | minimal PTP amplitude to count as peak for gradiometers. Unit: Tesla or Tesla/meter depending on channel type|
|flat_m | 3e-14 | float or int | max PTP amplitude to count as flat for magnetometers. Unit: Tesla or Tesla/meter depending on channel type|
|flat_g|3e-14|float or int| max PTP amplitude to count as flat for gradiometers. Unit: Tesla or Tesla/meter depending on channel type|
|bad_percent |5|int|The percentage of the time a channel can be above or below thresholds. Below this percentage, Annotations are created. Above this percentage, the channel involved is return in bads. Note the returned bads are not automatically added to info['bads']. Unit: percent.|
|min_duration|0.002|float|The minimum duration (s) required by consecutives samples to be above peak or below flat thresholds to be considered. to consider as above or below threshold. For some systems, adjacent time samples with exactly the same value are not totally uncommon. Unit: seconds.|

## ECG
_This channel data will be scaled from 0 to 1, so the setting is universal for all data sets. The peaks will be detected on the scaled data. The average std of all peaks has to be within the allowed range; if it is higher, the channel has too high deviation in peaks height and is counted as noisy._

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|drop_bad_ch | True | bool | if True - will drop the bad ECG channel from the data and attempt to reconstruct ECG data on base of magnetometers. If False - will not drop the bad ECG channel and will attempt to calculate ECG events on base of the bad ECG channel.|
|n_breaks_bursts_allowed_per_10min| 3 |int|number of breaks in ECG channel allowed per 10 minutes of recording. (This setting is for ECG channel only, not for any other channels Used to detect a noisy ECG channel)|
|allowed_range_of_peaks_stds | 0.14|float|the allowed range of peaks in standard deviations. (This setting is for ECG channel only, not for any other channels Used to detect a noisy ECG channel). Unit: arbitrary (the data using this setting is always scaled between 0 and 1)|
|height_multiplier | 0.6|float|defines how high the peaks on the ECG channel should be to be counted as peaks. Higher value - higher the peak need to be, hense less peaks will be found.|
|norm_lvl | 1 | int|The norm level is the scaling factor for the threshold. The mean artifact amplitude over all channels is multiplied by the norm_lvl to get the threshold.|
|gaussian_sigma|4|int|he sigma of the gaussian kernel used to smooth the data. The higher the sigma, the more smoothing. Typically ECG data is less noisy than EOG nd requires smaller sigma.|
|thresh_lvl_peakfinder | 5|int|higher - more peaks will be found on the ecg artifact for both separate channels and average overall. As a result, average over all may change completely, since it is centered around the peaks of 5 most prominent channels.|


## EOG
_This channel data will be scaled from 0 to 1, so the setting is universal for all data sets. The peaks will be detected on the scaled data. The average std of all peaks has to be within the allowed range; if it is higher, the channel has too high deviation in peaks height and is counted as noisy._

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|n_breaks_bursts_allowed_per_10min|3|int|number of breaks in EOG channel allowed per 10 minutes of recording. (This setting is for EOG channel only, not for any other channels Used to detect a noisy EOG channel).|
|allowed_range_of_peaks_std|0.15||the allowed range of peaks in standard deviations. (This setting is for EOG channel only, not for any other channels Used to detect a noisy EOG channel). Unit: arbitrary (the data using this setting is always scaled between 0 and 1.)|
|norm_lvl|1|int|The norm level is the scaling factor for the threshold. The mean artifact amplitude over all channels is multiplied by the norm_lvl to get the threshold.|
|gaussian_sigma|6|int|The sigma of the gaussian kernel used to smooth the data. The higher the sigma, the more smoothing. Typically EOG data is more noisy than EG nd requires larger sigma.|
|thresh_lvl_peakfinder|3|int|the higher the value, the more peaks will be found on the eog artifact for both separate channels and average overall. As a result, average over all may change completely, since it is centered around the peaks of 5 most prominent channels.|

## Muscle

|**Variable**|**Default Value**|**type**|**Description**|
|---     |---           |---         |--- |
|muscle_freqs | 110, 140 | 2 ints or 2 float|Defines the frequency band for detecting muscle activity. Unit: Hz. Default: by mne|
|threshold_muscle|5|int or float|threshold for muscle detection. Zscores detected above this threshold will be considered as muscle artifacts. Unit: z-scores. If lower than 5 it will just count random noise as muscle artifacts.|
|min_length_good|0.2|int or float|The shortest allowed duration of "good data" between adjacent muscle annotations; shorter segments will be incorporated into the surrounding annotations. Unit: seconds.|
|min_distance_between_different_muscle_events|1|int or float|minimum distance between different muscle events in seconds. If events happen closer to each other - they will all be counted as one event and the time will be assigned as the first peak. Unit: seconds.|
