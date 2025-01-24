# Geomagnetic Superstorm of May 2024

This repository contains codes to reproduce the results in Weiler et al. (2025): [First observations of a geomagnetic superstorm with a sub-L1 monitor](https://arxiv.org/abs/2411.12490) (in revision)

If you have any questions, feel free to contact me: eva.weiler@geosphere.at

## Usage

To use this python-scripts make sure you have [Anaconda](https://docs.anaconda.com/anaconda/install/) or [Miniconda](https://docs.anaconda.com/miniconda/install/) installed.

Go to a directory of your choice and clone the repository:
```
git clone https://github.com/EvaWeiler/may_2024_superstorm.git
```

Now go in the 'envs' directory and install the environments: 
```
conda create -f helio4.yml
```
```
conda create -f sunpy-env.yml
```

You can now activate the environment: 
```
conda activate helio4
```
```
conda activate sunpy-env
```

To run the Jupyter notebooks, jupyter lab has to be started:
```
jupyter lab
```

## Codes
The data needed for the python-scripts are stored in a figshare repository: https://doi.org/10.6084/m9.figshare.27792873

### 1. source_regions_may2024.ipnyb
This code produces Figure 2 in the paper. It requires the fits-files from the figshare repository which should be saved in a folder called 'data'.

### 2. elevo_may_2024.ipynb
This code is used to create Figure 4 in the paper. It contains the [ELEvo model](https://doi.org/10.1038/ncomms8135), which is a semi-empirical propagation tool, that propagates the CMEs as elliptical fronts through the heliosphere. It requires the real-time data files of the STEREO-A and ACE spacecraft ('noaa_rtsw_last_35files_now.p', 'stereoa_beacon_gsm_last_35days_now') as well as positions for other spacecraft and planets ('positions_psp_solo_sta_bepi_wind_planets_HEEQ_10min_rad'). These files should again be saved in a folder called 'data'.
The script outputs the predicted arrival times and arrival speeds at STEREO-A and L1, which are saved to text files called 'ELEvo_may2024_STA.txt' and 'ELEvo_may2024_L1.txt', respectively.
One can also create a movie using [ffmpeg](https://www.ffmpeg.org/download.html), visualising the whole propagation of the 5 CMEs causing the geomagnetic superstorm of May 2024. This movie can also be found in the figshare repository ('ELEvo_may_2024_movie.mp4' as well as one with LASCO observations: 'ELEvo_LASCO_movie.mp4') 

### 3. May_2024_superstorm.ipynb
This code produces Figure 7 in the paper as well as the geomagnetic indices from STEREO-A and L1 data using the [Temerin & Li (2006)](https://doi.org/10.1029/2005JA011257) model. It includes the whole data parapartion for the STEREO-A beacon data in order to apply the Temerin and Li model as well as functions to calculate error metrics and calculations for shock parameters.
It needs again the real-time files from the STEREO-A and ACE spacecraft (see above). Furthermore, it requires a position file for L1 ('l1_pos_2024.p'), science data from the spacecraft ACE in GSM coordinates to calculate the shock parameters ('ACE_gsm.p'), the text-file with the arrival times and arrival speeds at STEREO-A (= ELEvo output and also on figshare) and the observed Dst and SYM-H values ('omni_1963_now.p', 'omni_high_res2024.p'). 

The code for creating Figure 5 can be found here: https://github.com/cmoestl/heliocats/blob/master/scripts/lineups_may_2024.ipynb





