### OFFICIAL AND PUBLIC RELEASE

This is a joint research project of the Freie Universitaet Berlin (FUB, Germany) 
and the Commonwealth Scientific and Industrial Research Organisation (CSIRO, 
Brisbane/Australia) for the development of a plugin for the Sentinel Application 
Platform (SNAP) which is developed and updated by Brockmann Consult (Bergedorf/Germany). 
SNAP is funded by the European Space Agency (ESA) in the framework of the Science 
Toolbox Exploitation Platform (STEP).

This plugin is designed to derive the concentration of optically active water 
constituents (chlorophyll-a, yellow substance and total suspended matter) in and 
spectral above water remote sensing (RS) reflectances over optically complex coastal 
waters from OLCI (Ocean and Land Colour Instrument) Level-1B top-of-atmosphere data. 
Additionally spectral aerosol optical thickness (AOT) values in the atmosphere are 
estimated however, we do not recommend their usage yet because those values lack 
validation against in-situ data. Also the validation of the water constituents 
remains preliminary for plug version 1.0.0.0.5.3 and should be used with caution.

For a broader description refer to the online help pages of this plugin.

The plugin itself is provided as SNAP conform NetBeans Module plugin (```*.nbm```) in 
a C version and a Python version. The C version works with Linux only while the 
Python version works with Linux and Windows (test bed: Windows 10 with Python 
3.6.8). **Note:** the Python version is about 5 times slower than the C version.

The file names of the cartridges are:
```
s3tbx-py-fub-csiro-water-1.0.0.0.5.3-C.nbm   (C version)
s3tbx-py-fub-csiro-water-1.0.0.0.5.3-Py.nbm  (Python version)
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
|:-----:|-------------|---------|
| 1     | ‘Validation Warning' pop-up box during installation.  | Non-critical. Can be ignored. |
| 2     | ‘Writing target product' pop-up box shows slow update of progress bar. | Non-critical. For SNAP development team to fix. |
| 3     | Tile counter overflow. Incorrect computation of tile numbers may result in significant excess processing time both in GPT and GUI mode. Background: When launched from command-line the processor generates a console output, which can be used to monitor the progress of the calculations. SNAP does not process a scene in one piece it rather breaks down the data into smaller chunks - so called tiles - internally. The processor estimates the total number of tiles from internal information and produces a console output during each tile processing while incrementing the number of processed tiles which is displayed together with the total number of tiles. | Critical. Under investigation in collaboration with SNAP development team. |

<br>
