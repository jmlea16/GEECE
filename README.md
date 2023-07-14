# GEECE - Google Earth Engine CMIP6 Explorer
**If you use this tool please cite Lea et al. (submitted) and any citations from the data extracted using the tool.**
**© Copyright, Dr James Lea, University of Liverpool 2023. All Rights Reserved.**

The Google Earth Engine CMIP6 Explorer (GEECE) is an easy to use point and click interface to extract, process, create custom model ensembles and resample CMIP6 simulation data for historical (1950-2015), SSP2-4.5 and SSP5-8.5 scenarios (2015-2100). More details about the tool and case studies of its use can be found in the associated paper (Lea et al., submitted). Users who are interested in reanalysis data output for a variety of difference environments may also wish to use GEECE’s partner tool, the Google Earth Engine Climate Tool (GEEClimT). More information on GEEClimT can be found [here](https://github.com/jmlea16/GEEClimT).

## Getting started with GEECE
GEECE and its code is run through Google Earth Engine using JavaScript API. A direct link to the interface can be found at here INSERT LINK. Once the interface has been opened through the link provided above a welcome page will appear as shown below.

![image](https://github.com/jmlea16/GEECE/assets/40822976/97f02c92-ab5c-4848-bbd4-b888a8bee08b)

The welcome screen above shows the GEECE user interface, while the code editor, console and tasks windows can be seen above the map. If the interface does not appear initially click the “Run” button above the code editor window. Otherwise this part of the window can be minimised as shown below.

![image](https://github.com/jmlea16/GEECE/assets/40822976/445d32e4-458a-4c69-83ea-e9b42725f364)

In step 1, the user interface provides the option to choose which scenario users wish to process data for. These are:
- ***Historical scenario*** (1950 to end 2014)
- ***SSP 2-4.5*** (medium emissions scenario, 2015 to 2100)
- ***SSP 5-8.5*** (high emissions scenario, 2015 to 2100)
  
Once the scenario of interest has been selected, users can select the model simulation results that are of interest. Clicking on the button will bring up the list of all available simulations as shown below.

![image](https://github.com/jmlea16/GEECE/assets/40822976/f15c59c8-e16f-4505-a7e4-25fb2a451dce)

Results of 34 different model simulations that can be accessed through GEECE for all three different simulation scenarios. Users should note that simulations highlighted in blue text do not have complete results for all different variables, and should therefore check before selecting these for further processing. This information is provided in the accompanying paper, and can also be viewed through the Google Earth Engine Data Catalog [here](https://developers.google.com/earth-engine/datasets/catalog/NASA_GDDP-CMIP6#image-properties). Selecting these simulations for processing where data do not exist may result in the user interface failing to provide an output. In this example, we select three different model simulations before clicking the Ok button at the bottom of the screen that returns the user to the main interface page.

![image](https://github.com/jmlea16/GEECE/assets/40822976/53246c6e-1268-420b-9c82-9a1d5fe596ee)

In step 3, the user can select the variables that are of interest by clicking on the “Click to select variables” button. This brings up a menu as shown below.

![image](https://github.com/jmlea16/GEECE/assets/40822976/4c20c088-a9e2-4992-915a-242b1fc50568)

This brings up a menu showing the list of nine variables that are common to all the simulations (noting the previously mentioned exceptions where simulations were highlighted in blue). These are:
- ***hurs*** - near surface relative humidity - %
- ***huss*** - near surface specific humidity - mass fraction
- ***pr*** - precipitation (mean of daily precipitation rate) - kg/m2/s
- ***rlds*** - surface downwelling longwave radiation - W/m2 
- ***rsds*** - surface downwelling shortwave radiation - W/m2
- ***sfcWind*** - daily mean near surface wind speed - m/s
- ***tas*** - daily near surface air temperature - degrees Kelvin
- ***tasmin*** - daily minimum near surface air temperature - degrees Kelvin
- ***tasmax*** - daily maximum near surface air temperature - degrees Kelvin

More information on the variables and their availability in different model simulations can be found [here](https://developers.google.com/earth-engine/datasets/catalog/NASA_GDDP-CMIP6#bands). Once you are happy with the variable selection, click OK to return to the main interface page.

![image](https://github.com/jmlea16/GEECE/assets/40822976/56f3d54d-6e23-45ef-981a-54178cce2967)

After selecting the scenario, models, and variables, in step 4 users should select how they would like to data to be provided; either as:
Results from individual model simulations selected
- The mean of the selected model results (i.e. a model ensemble)
- The mean of the selected model results, and the associated standard deviation.
  
Once this is done, users should select the date and month range of interest (step 5). Note that if users wish to access a month range that straddles a year (e.g. November to February), this can be achieved by setting the start month as November and end month as February.

In step 6, users should select the time interval that they wish the output data to be processed to. The options for this include:
- Daily output
- Monthly output
- Annual output
- Mean of the date range

Where monthly, annual or mean intervals are selected GEECE will calculate the mean of each individual model simulation over the selected time interval. Where ensemble output has been selected, the interface will then calculate the mean of the model simulation results (e.g. for monthly output, the monthly mean of each simulation will be calculated, and then the mean/standard deviation of these results).

Users should note that where they are interested in a seasonal average that straddles a year (e.g. meteorological winter that spans December to February) they are encouraged to select data output in monthly format.

In step 7, users should select whether they want output in CSV format or as a GeoTIFF. Depending on the choice made, this will bring up different options in the user interface.

### Outputting data as a CSV
On selecting data to output in CSV format the following options will appear in the main interface page (see below). To view the workflow for outputting data in GeoTIFF format click [here](https://github.com/jmlea16/GEECE/edit/main/README.md#outputting-data-as-a-geotiff).

![image](https://github.com/jmlea16/GEECE/assets/40822976/717137b5-749f-4002-b55c-c6bc899c09c1)

In step 8, users can select whether they would like output provided as either:
- The mean of results across the entire region of interest (RoI), or
- Results from each individual point provided in the RoI
  
In this example, we select the latter.

Step 9 asks whether results should be provided from the nearest full grid cell, or as a spatially weighted mean calculated from the grid cells nearest to the locations that will be subsequently defined in the RoI. In this example we select the latter (see below).

![image](https://github.com/jmlea16/GEECE/assets/40822976/2061f2ef-a17d-44f3-8dbc-0cac1d7144e0)

Once steps 8 and 9 have been completed, the RoI can be defined (step 10) through either:
- Using the drawing tools (top left of the map) to manually draw points, or a single line, polygon or rectangle, or
- Import comma separated lists of latitude and longitude coordinates. For this option, users should note that the interface will automatically remove any spaces or trailing commas from the lists.
  
Once this has been completed, users should click the “Generate gridded area of interest” button (step 11) to finalise the RoI, and then click the “Generate export tasks” button (step 12).

![image](https://github.com/jmlea16/GEECE/assets/40822976/97a05e77-76db-4458-8a30-a383ad0cbf2c)

Once step 12 is completed, the interface will process the data, and a “Please wait” menu will appear on the map. Once the data have been processed, the export tasks will have been submitted to the server and the screen above will be shown. Note at this point that there are a couple of extra steps to take before data are available for download (see below).

![image](https://github.com/jmlea16/GEECE/assets/40822976/bd32527e-8704-4ca4-8841-a2714a76166d)

Once the tasks have been submitted to the server, users should go to the Tasks tab, where the uncompleted export tasks generated by the interface are shown in grey (above, top right). Given that in this example we have asked GEECE to provide results of individual simulations for three different models, three export tasks have been generated. To execute these tasks, users should click the ‘Run’ button on the right of each export task.

*Tip: if your query generates a lot of export tasks, the [Open Earth Engine Google Chrome browser extension](https://chrome.google.com/webstore/detail/open-earth-engine-extensi/dhkobehdekjgdahfldleahkekjffibhg) developed by Mathieu Gravey provides users with the "Run all tasks" option shown in the top right of the tasks menu.*

Once submitted, users should wait for the servers to process the task. When successfully completed, these export tasks will turn from grey to blue (see bottom of tasks tab for an example), and the data will be available to download from the Google Drive associated with the users Google Earth Engine account.

### Outputting data as a GeoTIFF
On selecting data to output in GeoTIFF format the following options will appear in the main interface page (see below). To view the workflow for outputting data in CSV format click [here](https://github.com/jmlea16/GEECE/edit/main/README.md#outputting-data-as-a-csv).

![image](https://github.com/jmlea16/GEECE/assets/40822976/a9ab0967-b7be-4ffc-a330-f8006ab54482)

For this step, users can define their region of interest (RoI) through either:
- Using the drawing tools (top right of the map) to manually draw a polygon or rectangle, or
- Import comma separated lists of latitude and longitude coordinates representing a polygon. For this option, users should note that the interface will automatically remove any spaces or trailing commas from the lists, and check whether there have been sufficient vertex locations entered to define a polygon (i.e. at least three).

![image](https://github.com/jmlea16/GEECE/assets/40822976/a0bc48d4-bb60-436a-bfee-9d66518773f2)

In this example, the drawing tools have been used to manually define an irregular polygon covering the British Isles. Once a user is happy with their RoI they should click the “Generate export tasks” button. At this point a “please wait” notice will appear on the map while export tasks are being generated.

![image](https://github.com/jmlea16/GEECE/assets/40822976/7acfcd40-09c1-4fa4-8441-375a178bc0aa)

Once the export tasks have been generated, a new notice will appear on the map instructing users to navigate to the Tasks tab shown above, where all the export tasks that have been generated are shown. In this example, output for two variables from three different model simulations have been requested. This generates nine export tasks in total (two multiband GeoTIFF export tasks per model simulation, each representing individual variables from the time intervals requested; and one CSV export task per model simulation, that provide information regarding the timestamp that each band in the GeoTIFF image relates to). Users should note that where export tasks exceed 5000 bands per image, these tasks will be split into two, and will have a separate accompanying CSV table with associated band information.

To execute these tasks, users should click the ‘Run’ button on the right of each export task.

*Tip: if your query generates a lot of export tasks, the [Open Earth Engine Google Chrome browser extension](https://chrome.google.com/webstore/detail/open-earth-engine-extensi/dhkobehdekjgdahfldleahkekjffibhg) developed by Mathieu Gravey provides users with the "Run all tasks" option shown in the top right of the tasks menu.*

Once submitted, users should wait for the servers to process the task. When successfully completed, these export tasks will turn from grey to blue (see bottom of tasks tab for an example), and the data will be available to download from the Google Drive associated with the users Google Earth Engine account.









