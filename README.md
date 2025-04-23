# In this directory

Created for reformatting certain ultraviolet background (UVB) models&mdash;[Faucher-Giguère 2009](https://ui.adsabs.harvard.edu/abs/2009ApJ...703.1416F/abstract) (FG09), 
[Haardt and Madau 2012](https://ui.adsabs.harvard.edu/abs/2012ApJ...746..125H/abstract) (HM12),
[Puchwein et al](https://ui.adsabs.harvard.edu/abs/2019MNRAS.485...47P/abstract) (PW19)
and [Faucher-Giguère 2020](https://ui.adsabs.harvard.edu/abs/2020MNRAS.493.1614F/abstract) (FG20)&mdash;such that each model is in the same units
to be utilized in direct comparison between models over a
range of redshifts ($z\approx 10$ to $z=0$).

Additionally, there is also code included in this release for running a [`cloudy_cooling_tools`](https://github.com/brittonsmith/cloudy_cooling_tools)
pipeline to generate ionization tables for different UVB models. This code does require
a working installation of CLOUDY, the code for which can be found [here](https://gitlab.nublado.org/cloudy/cloudy).

All of these scripts come along with plotting scripts to illustrate a few use cases for
the codes in the directory.


## Directories

### cloudy\_formatted\_data (I'm concerned about plagaism here)
Stores data formatted for use with the [`cloudy_cooling_tools`](https://github.com/brittonsmith/cloudy_cooling_tools) repository to generate ionization tables.
Directories are also used by `make_UVB_data_table.py` as input files for reformatting.

### data\_tables
Contains directories for the reformatted UVBs and is the default containter 
for generating UVBs via `make_UVB_data_table.py`. The tables show the intensity
(erg $\mathrm{s^{-1}cm^{-2}}$) binned in different energies (eV). This is done for each UVB
over a range of $z\approx 10$ to $z=0$ with some variation between models.

### generate\_ionization\_tables
Code for running `cloudy_cooling_tools` for creating ionization tables. Takes in
cloudy-formatted data along with a large suite of parameter files that are described
in more detail within.

## Scripts

Several of these scripts have hardcoded paths that need to be edited before they can be run.

### make\_UVB\_data\_table.py
Code for remaking CLOUDY-formatted data into a more user-friendly csv format.

**Arguments:**

* `-out_path`: path to directory where data tables are output

* `-uvb_names`: shorthand names for each UVB. Should be separated by spaces

* `-uvb_paths`: paths to directories containing CLOUDY-formatted UVBs. Each path should be separated by a space

### plot\_uvb\_spec.py
Creates a lineplot of UVB intensity for each UVB from $10$ - $10^{2.3}$ eV. Uses
the data output from `make_UVB_data_table.py` (i.e. `data_tables` directory)

**Arguments:**

* `-out_path`: path to directory where figures are output

* `-table_dir`: directory where UVB tables have been saved

* `-uvb_paths`: redshift to plot. Not all redshifts between UVBs are the sound, so will pick the closest redshift

## Dependencies

### Python

The Python scripts in this repository require the following libraries:

* [yt](https://yt-project.org/)
* [mpi4py](https://mpi4py.readthedocs.io/en/stable/)
* [NumPy](https://numpy.org/)
* [SciPy](https://scipy.org/)
* [matplotlib](https://matplotlib.org/)
* [h5py](https://www.h5py.org/)
* [roman](https://pypi.org/project/roman/)

### Other Software

* [CLOUDY](https://gitlab.nublado.org/cloudy/cloudy)
* [`cloudy_cooling_tools`](https://github.com/brittonsmith/cloudy_cooling_tools)