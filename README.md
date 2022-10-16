# 3D Point Clouds Earthquake Model

Thousands or even millions of georeferenced points are combined together making a 3D visualization, which not only describe the land mask all over the world, but also is available for earthquake information. As for the earthquakes, you can request any time period or any magnitude range from the request API by adding formatted query.


https://user-images.githubusercontent.com/109449521/196058705-3490bb64-468c-4294-9544-10e0312d7fb5.mov



## Installation
Lots of python modules are used in this project. Some common and simple ones do not have to install, like `os`, `numpy`, `json`, `urllib.request`, `math` and `matplotlib`.

The other two modules are `netCDF4` and `open3d`. `netCDF4` is short for Network Common Data Format Version 4, which is used to open and read `lsmask.nc`file. And `open3d` is an open-source library that supports rapid development of software that deals with 3D data. In this project, the final ouput format of 3D point clouds model is `.ply`file, which can be displayed through this module successfully. 


Since`netCDF4` and `open3d`modules are not common, they need to be installed in the libraray first. And there are two ways to install the package.

- install packages using Anaconda prompt
	netCDF4: `conda install -c anaconda netcdf4`
	open3d: `conda install -c open3d-admin open3d`


- install packages using pip
	netCDF4: `pip install netCDF4`
	open3d: `pip install open3d`

[More documentations about `netCDF4` module](https://unidata.github.io/netcdf4-python/netCDF4/index.html)
[More documentations about `open3d` module](http://www.open3d.org/docs/release/index.html)


## Data
- Land mask
The land mask data is download from [Physical Sciences Laboratory](https://psl.noaa.gov/data/gridded/data.noaa.oisst.v2.html) website . The latitude/longitude values in the netCDF `coordinate` variables are the centers of the one-degree grid cells. Besides, the `mask` variable in the netCDF has two values, `0 and 1`. The value `0` refers to the land mask, whereas the value `1` refers to the ocean mask. Thus, the mask that equals to 0 can perfectly descfrible the point clouds of land all over the world.

- Earthquake API
Since earthquakes happen frequently almost everyday in the world, the data I selected is a real-time updated data from an API offered by [USGS](https://earthquake.usgs.gov/fdsnws/event/1/). More specificly, you can name the `time period` as well as the `magnitude range` by adding query paramerers. Besides, `GeoJSON` is one of the format you can read from that API.

- Earthquake JSON
When we access the GeoJSON data from the API remotely, we can extract the information like `lon/lat`, `depth` as well as `magnitude level` and save them all in a new json file locally. 

- PLY model
PLY model is the local file for the final output. It can be opened in applications like `Meshlab` or can be read through the `open3d` python module in the jupyter notebook.

## Code
For this project, `python` is the only programming language. `Jupyter Notebook` are used to check errors, run codes and alsp save the entire scripts. More detailed markdowns and comments can be found in the `script.ipynb` file through jupyter notebook.


## User Input 
Time period and magnitude range are able to be requested, so that the user should choose to input the `start time`, `end time`, `lowest magnitude` as well as the `highest magnitude`.

For the start time and end time, the format should follow `YYYY-MM-DD`, for example `2020-01-01`. The `connecting dash (-)` should stay here to separate year, month and date. Besides, the number of digit should follow the demo as well, so you cannot remove the `0` if there is only one digit for month or date.

For the magnitude level, you can input whatever integer or float as you want. However, if you try to input the number that might be impossible for the real magnitude level, the request might cause error.

## Limitations
If you have already run the code once, the `earthquake.json` and `earthquake.ply` file might exist in the workspace. If you would like to run the code for another time, you should delete the existing files or change the name of any file to avoid error.

More functions and ideas can be added in this project. For example, zoom in and click any earthquake point, a pop-up window may be available to display, showing some key information as well. Moreover, if we zoom out at one scale, a mark of each country may show up and will be clickable to show some generall information for whole country.


