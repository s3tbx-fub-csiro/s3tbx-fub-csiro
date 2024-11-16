### S3 FUB-CSIRO Coastal Water Processor - Official and public release

This is a joint research project of the Freie Universitaet Berlin (FUB, Germany) 
and the Commonwealth Scientific and Industrial Research Organisation (CSIRO, 
Brisbane/Australia) for the development of a plugin for the Sentinel Application 
Platform (SNAP) which is developed and updated by Brockmann Consult (Bergedorf/Germany). 
SNAP is funded by the European Space Agency (ESA) in the framework of the Science 
Toolbox Exploitation Platform (STEP).

This plugin is designed to derive the concentration of optically active water 
constituents (chlorophyll-a, yellow substance and total suspended matter) in and 
spectral above water remote sensing reflectances (Rrs) over optically complex coastal 
waters from OLCI (Ocean and Land Colour Instrument) Level-1B top-of-atmosphere data. 
Additionally spectral aerosol optical thickness (AOT) values in the atmosphere are 
estimated. However, we do not recommend their usage yet because those values lack 
validation against in-situ data. Also the validation of the water constituents 
remains preliminary for plugin version 1.0.0.0.5.4 and should be used with caution.

For a broader description please refer to the online help pages of this plugin and the 
reference provided below.

The plugin itself is provided as SNAP-conform NetBeans Module plugin (```*.nbm```) in 
a C and a Python version. The C version works with Linux only while the 
Python version works with Linux and Windows (test bed: Windows 10 with Python 
3.6.8). **Note:** the C version is about 5 times faster than the Python version. The 
latest version is 1.0.0.0.5.4 and is **compatible with SNAP 10+ only**.

The file names of the cartridges are:
```
s3tbx-py-fub-csiro-water-1.0.0.0.5.4-C.nbm   (C version)
s3tbx-py-fub-csiro-water-1.0.0.0.5.4-Py.nbm  (Python version)
```
This project is scientifically managed by Thomas Schroeder (CSIRO) and Michael 
Schaale (FUB) who appreciate very much the generous support by Marco Peters and 
Carsten Brockmann (Brockmann Consult) and EUMETSAT (European Organisation for 
the Exploitation of Meteorological Satellites) in the framework of the Copernicus 
Collaborative Exchange Program.

<br>

<font color="red">

#### Known issues

</font>

| Issue | Description | Comment |
|:---|:---|:---|
| 1 | 'Validation Warning' pop-up box during installation. | Non-critical. Can be ignored. |
| 2 | Using single operator with GPT or standard GUI processing can cause multiple computation of tiles (tile counter overflow).<br><br>Incorrect computation of tile numbers may result in significant excess processing time both in GPT and GUI mode. Background: When launched from command-line the processor generates a console output, which can be  used to monitor the progress of the calculations. SNAP does not process a scene in one piece it rather breaks down the data into smaller chunks - so called tiles - internally. The processor estimates the total number of tiles from internal information and produces a console output during  each tile processing while incrementing the number of processed tiles which is displayed together with the total number of tiles. <br><br>The  underlying tile counter overflow issue is not caused by the plugin but by SNAP itself that provides 3 different processing pathways and that are implemented differently in the software. (1) standard GUI  processing, (2) GPT processing using an XML input configuration file and (3) GPT single operator processing. | (1) Standard GUI processing:<br>Solved for plugin version  1.0.0.0.5.4 in combination with SNAP version 10 and latest updates applied only if an additional optimization of the System Performance is applied. To apply the optimization select 'Tools>Options>Performance' from the GUI menu and under 'System' use 'Compute' to calculate the parameters automatically. Press 'Apply' to save them. Under the processing section (same tab) the optimum tile size should be 512.<br><br>(2) GPT processing using an XML input file:<br>Solved for plugin version 1.0.0.0.5.4 in combination with SNAP version 10 and latest updates. No optimization of the System Performance is required. <br><br>(3) GPT single operator processing:<br>The issue still persists and requires further changes to be implemented by the SNAP development team. See also:<br>https://senbox.atlassian.net/browse/SNAP-1542 <br><br> |
| 3 | Python operators are not shown in the GraphBuilder. | No work-around available. For SNAP development team to fix. See: https://senbox.atlassian.net/browse/SNAP-277 |
| 4 | Internal plugin help page does not open when connected to the internet. In this case the request is directed to the SNAP Online Help on an ESA server and provides '404 Help page not found'. The internal help page opens fine without an internet connection. | For SNAP development team to fix. See:  https://forum.step.esa.int/t/online-help-opened-even-when-it-not-exists/43508?u=marco_eom and https://senbox.atlassian.net/browse/SNAP-3883 |



<br>

**Reference:** <br>
https://doi.org/10.1016/j.rse.2021.112848

**Contact & Feedback:** <br>
Michael.Schaale@fu-berlin.de <br>
Thomas.Schroeder@csiro.au
