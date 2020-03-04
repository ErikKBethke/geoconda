# geoconda

## Creating a basic geospatial conda environment
geoconda is a simple repository of information for setting up a conda environment for geospatial analysis in a Windows environment.

Future versions will potentially include scripts that automatically create the conda environment.

Last Updated: March 4, 2020

To-Do:
- Mac, Linux compatability
- Automate conda environment setup
- Create miniconda compatability with setup


#### Requirements
This guide requires that Anaconda is installed and conda is update to date (conda update conda command).

~~- [Miniconda](https://docs.conda.io/en/latest/miniconda.html) - A minimal version of Anaconda that "includes only conda, Python, the packages they depend on, and a small number of other useful packages, including pip, zlib and a few others"~~
- [Anaconda](https://docs.anaconda.com/anaconda/install/) - Full distribution of Anaconda including conda as well as several libraries

#### Helpful Commands
Helpful commands for troubleshooting include the following:

Get list of all conda environments:

`conda env list`

Get a list of packages in an environment:

`conda list -n myenv`

See if a package has been installed in an environment:

`conda list -n myenv mypackage`

See activate environment configuration:

`conda config --show`

See activate environment channels:

`conda config --show channels`

Remove an environment:

`conda remove --name myenv --all`

### Environment Creation
**Note: manual installation is done via the anaconda prompt terminal that comes with Anaconda distributions**
Creating a new environment is done with the command:

`conda create --name myenv`

However, is it valuable to also specify the python version you are intending on using (for example, if a package you are using is only on certain python versions):

`conda create --name myenv python=3.6`

You can also create environments with specific packages (and specify versions), although it is easy enough to add these later:

`conda create --name myenv scipy=0.15.0 numpy pandas`

**It is strongly recommended to install all programs at the same time to an environment to avoid dependency conflicts. Using a environment.yml file is usually the most ideal for avoiding dependency issues.**

### Package Selection & Installation
There are two different sections of packages to go over: generally useful packages (config, file management, general analytics, etc.) and the geospatial packages.

##### General Packages
Here is a list of generally useful packages:
- [SciPy Pack](https://anaconda.org/anaconda/scipy) - includes scientific computing packages (numpy, pandas, scikit-learn) as well as many other ecosystem components (ipython, dask, additional scipy libraries)
- [IPKernel](https://ipython.readthedocs.io/en/latest/install/kernel_install.html) - to enable usage of Jupyter notebooks with your environment
- [matplotlib](https://matplotlib.org/index.html) - plotting library that also allows spatial plotting
- [xarray](http://xarray.pydata.org/en/stable/why-xarray.html) - multidimensional arrays, particularly useful for dealing with netCDF files and other spatial array data. [optional dependencies](http://xarray.pydata.org/en/stable/installing.html) can be definitely worth installing (dask, etc.)
- [pandas](https://pandas.pydata.org/) - if not already installed (included in several other packages as dependencies)

##### Spatial Packages
Here is a list of packages that are particularly useful for geospatial analytics. Several are redundant to install as they can be dependencies of other packages listed:
- [PySal](https://pysal.org/) - Python Spatial Analysis Library to perform spatial data analytics
- [GDAL](https://pypi.org/project/GDAL/) - Geospatial Data Abstraction Library package for Python, will require [GDAL Windows Binaries](http://www.gisinternals.com/) to be installed
- [PyProj](https://github.com/pyproj4/pyproj) - interface to PROJ
- [geopandas](https://geopandas.org/) - extends pandas functionality to geometric type data
- [Fiona](https://pypi.org/project/Fiona/) - for handling OGR spatial data
- [Shapely](https://shapely.readthedocs.io/en/latest/) -  (included in cartopy)
- [Cartopy](https://scitools.org.uk/cartopy/docs/latest/) - geospatial data processing for plotting
- [netCDF4](https://unidata.github.io/netcdf4-python/netCDF4/index.html) - for handling netCDF data (climate data, etc.)
- [rasterio](https://github.com/mapbox/rasterio) - for handling raster data (GeoTIFF, etc.)
- [pyshp](https://github.com/GeospatialPython/pyshp) - for writing to ESRI format spatial files
- [geojson](https://github.com/jazzband/geojson) - for handling GeoJSON data
- [Pillow](https://python-pillow.org/) - python Imaging Library fork for Python 3. Very valuable for image processing.
- [Descartes](https://pypi.org/project/descartes/) - can be helpful if you plan to plot geometry in matplotlib
- [seaborn](http://seaborn.pydata.org/) - data visualization library that can be used for additional plotting options

**Note: some packages (cartopy, etc.) recommend that you install using [conda-forge](https://conda-forge.org/docs/user/introduction.html) as a channel. This is an optional method but be aware specifying conda-forge as a channel to install from can create endless solving loops upon installing packages. This guide uses conda-forge as recommended.**

##### Installation

After selecting the packages desired from the above (and any additional packages), installing packages can be done as follows:

1. Optionally enable conda-forge for packages that recommend it:

`conda config --add channels conda-forge
conda config --set channel_priority strict`

2. Install packages (recommended to do all at once to avoid dependency issues):

`conda install --channel conda-forge scipy ipykernel xarray matplotlib seaborn cartopy Pillow pysal pyproj gdal shapely descartes pyshp geopandas rasterio fiona netCDF4`

### Additional Options
Below are some more advanced methods that can be used.

#### Use of YML files
YML files can be used to export/import environment configurations. This is extremely helpful when trying to quickly set up/replicate an environment that will work consistently.

To export your active environment yml, navigate in (a non-conda) terminal to a directory you would like the file to be placed:

`conda env export --name myenv > environment_myenv.yml`

To create an environment from a yml file:

`conda env create -f environment_myenv.yml`

### Sample conda environment creation
`conda create --name geospatial python=3.6`
`conda activate geospatial`
`conda config --add channels conda-forge`
`conda config --set channel_priority strict`
`conda install --channel conda-forge scipy ipykernel xarray matplotlib seaborn cartopy Pillow pysal pyproj gdal shapely descartes pyshp geopandas rasterio fiona netCDF4`
