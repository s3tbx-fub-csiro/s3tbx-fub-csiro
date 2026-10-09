### S3 FUB-CSIRO Coastal Water Processor - Official and public release

This joint research project between Freie Universität Berlin (FUB, Germany) 
and the Commonwealth Scientific and Industrial Research Organisation (CSIRO, 
Australia) aims to develop and provide a plugin for the Sentinel Application 
Platform (SNAP), which is developed and maintained by Brockmann Consult (Germany). 
SNAP is funded by the European Space Agency (ESA) in the framework of the Science 
Toolbox Exploitation Platform (STEP) initiative.

This plugin is designed to derive the concentration of optically active water 
constituents (chlorophyll-a, yellow substance and total suspended matter) as well as 
spectral above water remote sensing reflectance (Rrs), for optically complex coastal 
waters from OLCI (Ocean and Land Colour Instrument) Level-1B top-of-atmosphere data. 
In addition, spectral aerosol optical thickness (AOT) values are 
estimated. However, these products should be used with caution, as they have not yet been validated against in-situ measurements.

For a detailed description of the methodology, please refer to the online help pages of this plugin and the 
reference listed below.

The plugin itself is distributed as a SNAP-compatible NetBeans Module plugin (```*.nbm```) implemented in C for Linux. The previously available Python version for Windows has been discontinued. The latest version is 1.0.1.0.5.4, and a brief version history is provided below.

The filename of the cartridge is:
```
s3tbx-py-fub-csiro-water-1.0.1.0.5.4-C.nbm   (C version)
```
This project is scientifically managed by Thomas Schroeder (CSIRO) and Michael 
Schaale (FUB) who gratefully acknowledge the generous support by Marco Peters and 
Carsten Brockmann (Brockmann Consult), as well as EUMETSAT (the European Organisation for 
the Exploitation of Meteorological Satellites), within the framework of the Copernicus 
Collaborative Exchange Program.

<br>

#### Brief version history

| Version | Description |
|:---|:---|
| < 1.0.0.0.5.3 | All versions prior to version 1.0.0.0.5.3 were non-public developer's versions and thus their history is not recorded here. |
| 1.0.0.0.5.3 (2105270600) | This version is the first official release of the *S3 FUB-CSIRO Coastal Water Processor*. A detailed description of this version is given in the reference below. |
| 1.0.0.0.5.4 (2209271200) | Corrected several return statements by adding brackets around return parameter(s) to ensure Python 3 compability. <br><br> A change was made to the initialize() method to suppress the calculation of the instrument noise variance when the in the number of ANNs is less than two. <br><br> Suppressed warnings caused by numpy.exp() in the ANN methods. These warnings occur when the exponent in the exp() function of the hidden-layer sigmoidal functions becomes very large. Although the warning is issued, the returned result remains correct. The line line warnings.filterwarnings('ignore') was added to prevent these warnings from being issued. <br><br> Cleaned the Python code in the accompanying classes: fub_csiro_ann.py, fub_csiro_evt.py, fub_csiro_evt0.py, fub_csiro_evtTS.py and fub_csiro_sigdata.py <br><br> All ANNs remain unchanged compared to the previous version.|


<br>

<font color="red">

#### Known issues

</font>

| Issue | Description | Comment |
|:---|:---|:---|
| 1 | 'Validation Warning' pop-up box during installation. | Non-critical. Can be ignored. |
| 2 | Using single operator with GPT or standard GUI processing can cause multiple computation of tiles (tile counter overflow).<br><br>Incorrect computation of tile numbers may result in significant excess processing time both in GPT and GUI mode. Background: When launched from command-line the processor generates a console output, which can be  used to monitor the progress of the calculations. SNAP does not process a scene in one piece it rather breaks down the data into smaller chunks - so called tiles - internally. The processor estimates the total number of tiles from internal information and produces a console output during  each tile processing while incrementing the number of processed tiles which is displayed together with the total number of tiles. <br><br>The  underlying tile counter overflow issue is not caused by the plugin but  by SNAP itself that provides 3 different processing pathways and that are implemented differently in the software. (1) standard GUI  processing, (2) GPT processing using an XML input configuration file and (3) GPT single operator processing. | (1) Standard GUI processing:<br>Solved for plugin version  1.0.1.0.5.5 in combination with SNAP version 9 and latest updates applied only if an additional optimization of the System Performance is applied. To apply the optimization select 'Tools>Options>Performance' from the GUI menu and under 'System' use 'Compute' to calculate the parameters automatically. Press 'Apply' to save them. Under the processing section (same tab) the optimum tile size should be 512.<br><br>(2) GPT processing using an XML input file:<br>Solved for plugin version 1.0.1.0.5.5 in combination with SNAP version 9 and latest updates. No optimization of the System Performance is required. <br><br>(3) GPT single operator processing:<br>The issue still persists and requires further changes to be implemented by the SNAP development team. See also:<br>https://senbox.atlassian.net/browse/SNAP-1542 <br><br> |
| 3 | Python operators are not shown in the GraphBuilder. | No work-around available. For SNAP development team to fix. See: https://senbox.atlassian.net/browse/SNAP-277 |
| 4 | If NetCDF4 input files are used, only NetCDF4-BEAM will work with the plugin. NetCDF4-CF lacks a number of attributes needed by the plugin to identify a proper input file. | No work-around available. For SNAP development team to fix.|


<br>

**References:** <br>
[1] https://doi.org/10.1016/j.rse.2021.112848

**Contact & Feedback:** <br>
Thomas.Schroeder@csiro.au
