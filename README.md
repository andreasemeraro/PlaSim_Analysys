## INTRODUCTION ##
These codes were developed during my Thesis work where I perfmored a good number of simulation with the Planet Simuator Model (PlaSim). This Climate Model is open source and you can find the original version [here](https://github.com/HartmutBorth/PlaSim). However, during this project I started from another version [here](https://github.com/jhardenberg/plasim). Even if the code in this repository was used for the former model I believe that with some tips can be be performed for other model that save their data in Netcdf format. In the following part I will explain how to use the code. This is far for perfection and could be some unclear things and error. Feel free to open issues in that case.

**N.B. The following instruction are thought for ubuntu**

## PRE-REQUISITES ##
1. Download cdo `sudo apt install cdo`;
2. Install netcdf `sudo apt-get install libnetcdf-dev libnetcdff-dev`;
3. Install Anaconda distribution with Jupyter Notebook (except for the file in CDO and application) with the following important packages:
   - netcdf:
    `conda install -c anaconda netcdf4`;
    - cdo:
    `pip install cdo`;
    - basemap:
    `conda install -c anaconda basemap`;
    - cartopy:
    `conda install -c conda-forge cartopy` or see [here](https://anaconda.org/conda-forge/cartopy).
    
The basemap package is deprecated and a complete transition to cartopy is needed in the future. However, basemap holds some features still not present in cartopy. So for now I've decided to not change to cartopy. Unfortunately, for the former reason you have to use a python version=2.6. I suggest to create a new conda environment with this python version: `conda create -n envname python=2.6`, then activate the environment `conda activate envname`.

**N.B. In ubuntu I found very useful to run directly `jupyter notebook` from the desired path**

## DIRECTORIES ##
### PlaSim simulations ##
In the repository you can find two direcotries called:
- NSM2_100_70_30_ML_SI_T21;
- WGAO2_100_70_30_ML_SI_T21.

The name structure is composed as follows: simulation_name (the same name that you have to put in the [most_plasim_run](NSM2_100_70_30_ML_SI_T21/most_plasim_run) and that appear in the [output files](NSM2_100_70_30_ML_SI_T21/output/))+years of simulation+start time for the average+years of average (this input have to correspond to the ones in the [cdo_start_2.0.sh](CDO_pre_analysis/cdo_start_2.0.sh))+simulation_feature (ex: Mixed Layer, Sea Ice)+resolution (T21 or T42).

### CDO_pre_analysis ###
Before to start you have to run the [cdo_start_2.0.sh](CDO_pre_analysis/cdo_start_2.0.sh) in order to generate the anlized files that will be used by the python and jupyter script. In this file you have to set the followign parameter:
-name_dir=path to the PlaSim simulation
-name_sim="simulation_name"
-year=years of simulation
-step=years of average
-start=start time for the average

**N.B: the day start and day stop are not used in this file actually**
Then you may run the [cdo_start_2.0.sh](CDO_pre_analysis/cdo_start_2.0.sh) from bash `./cdo_start_2.0.sh`

###  File_ analysis ###
In this directory there are two files:
1. study_file_mod.ipynb
2. module_study_file.ipynb
The first one is the files that you have to open with jupyter. The second one is just the module used from the first one and where the classes and functions are stored.In the first one you have to set:
-folderPath="/home/andry/Andrea/repo/PlaSim-analysis/NSM2_100_70_30_ML_SI_T21"
-file_analysis=folderPath+"/output/analisi/"
-file_graph=folderPath+"/output/analisi/grafici/"
These file works for both the two types of resolutions (T21/T42)

### File comparison ###
