# geoconda

## Creating a basic geospatial conda environment
geoconda is a simple repository of information for setting up a conda environment for geospatial analysis in a Windows environment.

Future versions will potentially include scripts that automatically create the conda environment.

Last Updated: March 4, 2020

To-Do:
- Initial setup
- Package install
- Yaml install
- Package selections
- Mac, Linux compatability
- Automate conda environment setup
- Create miniconda compatability with setup


-#### Requirements
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

### Environment Creation
**Note: manual installation is done via the anaconda prompt terminal that comes with Anaconda distributions**
Creating a new environment is done with the command:
`conda create --name myenv`

However, is it valuable to also specify the python version you are intending on using (for example, if a package you are using is only on certain python versions):
`conda create --name myenv python=3.6`

You can also create environments with specific packages (and specify versions), although it is easy enough to add these later:
`conda create --name myenv scipy=0.15.0 numpy pandas`

**It is strongly recommended to install all programs at the same time to an environment to avoid dependency conflicts. Using a environment.yml file is usually the most ideal for avoiding dependency issues.**

### Package Installation
There are two different sections of packages to go over: generally useful packages (config, file management, general analytics, etc.) and the geospatial packages.

##### General Packages
Here is a list of generally useful packages:
- [SciPy Pack](https://anaconda.org/anaconda/scipy) - includes scientific computing packages (numpy, pandas, scikit-learn) as well as many other ecosystem components (ipython, setuptools, dask, additional scipy libraries)
- [IPKernel](https://ipython.readthedocs.io/en/latest/install/kernel_install.html) - to enable usage of Jupyter notebooks with your environment
- [matplotlib](https://matplotlib.org/index.html) - plotting library that also allows spatial plotting

##### Spatial Packages
Here is a list of packages that are particularly useful for geospatial analytics:
- PySal
- GDAL
- PyProj
- Geopandas
- Fiona
- Shapely
-


### Sample conda environment creation
conda create --name usgcrp python=3.8
conda activate usgcrp
conda install scipy ipykernel
