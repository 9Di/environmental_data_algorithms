# Environmental remote sensing data processing 
<p>MOPAR is an environmental research project focused on primary production analysis in the ocean. This README provides an overview of the project, its objectives, and key components.</p>

* The algorithms and plots in this repository were developed by Manurov Rustam. The plots were composed using Python's packages (PyGMT, Seaborn) and Photoshop.
* This repository stores certificates in Python, Data Analysis, and Data Science, demonstrating my expertise in these fields.

### Project Overview
<p>MOPAR aims to analyze primary production in the ocean using a combination of in-situ data and satellite observations. The project comprises primary algorithms, each with multiple variations, designed to collect, process, compare data, and estimate Primary Production over 2 decades. These algorithms help obtain valuable insights into primary production and its geographical distribution.</p>


### Algorithms
#### <b>Algorithm 1:</b> **[In-Situ Data Integration](https://github.com/9Di/environmental_data_algorithms/blob/main/Algorithms/Point_PP.py)**.
* The first algorithm gathers in-situ data of primary production values.
* Utilizes satellite data collected over the years to obtain geographical parameters.
* Compares in-situ and satellite-derived values to assess primary production variations.<br>

<b>Customizable Calculation:</b><br>
* Users can modify the year and month for the calculation, allowing flexibility in analyzing specific time periods.<br>
* Our time range of interest, due to the lack of data over 80 degrees North, is April - September / 1998 - 2022.<br>

<b>Algorithm Variations:</b><br>
* Choice of Chlorophyll-a concentration satellite data levels (3 and 4).
* Selection of Photosynthetically Avaliable Radiation (PAR) values (2, 3) from satellite data and 1 for reanalysis data.
* Use of Gaussian or Linear law in calculation.
* Spectra information choices: mean spectra of chlorophyll and spectra data obtained during cruises (optional).
* Depth variations for calculation (2 options).



### Model variations establishment using local in-situ data
<p>The 'Point_PP.py' algorithm were composed in order to find the best suited model based on the correlation with in-situ data and statistical parameters (RMSD, BIAS, normalized values, Pearson correlation coefficient, standard deviation). As a result, we were able to filter the output by necessary statistical values in order to highlight the most suitable model. The algorithm takes the following parameters as an input: year and month of interest, CHL-a satellite data level, Photosynthetically avaliable radiation satellite data level, Gaussian equiation involvment in the calculation, type of spectra data, 2 versions of depth either based on Gaussian or Linear law.</p>

![Map!](/Plots/PyGMT_map.PNG)<br>
<b>Figure 1.</b> Schematic image of the area of interest and the circulation patterns: East Greenland, West Spitsbergen, Norwegian Atlantic, Return Atlantic.

![Model variations!](/Plots/Models_variations.PNG)
<b>Figure 2.</b> NPP - Net Primary Production, GPP - Gross Primary Production interpolated data analysing.
<br>
<br>
<br>
![Model boxplot!](/Plots/Models_boxplot.PNG)
<b>Figure 3.</b> Data distibution analysing.
<br>
<br>
#### <b>Algorithm 2:</b> **[Regional Primary Production Estimation](https://github.com/9Di/environmental_data_algorithms/blob/main/Algorithms/Area_PP.py)**.<br>
* The second algorithm utilizes parameters that have been validated as effective in the first algorithm.
* It calculates geographical data for primary production (PP) across a span of two decades.
* The algorithm generates tables with approximately 400,000 bins to estimate monthly PP values for 1998-2022.
* It calculates the sum of PP values and obtains monthly mean values, allowing for regional primary production estimation.
<br>

### Area PP calculation with the most suitable model
The 'Area_PP.py' algorithm were used to calculate the sum and monthly mean values of Primary Production monthly over 2 decades (1998 - 2022) using Copernicus, Hermes, Nasa remote sensing data. Basically, this code is a successor of 'Point_PP.py' algorithm. As we achived the model variations passed through the filter using the 'Point_PP.py' file, we were able to use those variations to calculate the sum and monthly mean values of chlorophyll-a Primary Production (PP) filtered by the area of interest. In our case, we had an option to digitalize the Norway sea to store the coordinates of the border of the sea. 

![Monthly Mean PP!](/Plots/Monthly_mean.JPG)
<b>Figure 4.</b> Monthly primary production for 1998-2022.
<br>
<br>
<br>
### CO2 exchange variability using Turbulence Kinetic Energy and Dissipation Rate
#### <b>Algorithm 3:</b> **[Synchronization and Analysis of CO2 Exchange Sensors](https://github.com/9Di/environmental_data_algorithms/blob/main/Algorithms/Spectra_bin.py)**.<br>
* The third algorithm is an example from a related project focused on CO2 exchange in the context of ocean research.
* This algorithm takes the names of two sensors as arguments: the main sensor and the slave sensor. These sensors measure components of speed, pressure, and time while floating on the sea. The main sensor measures these values within a chamber to avoid turbulence, while the slave sensor measures them outside the chamber.

<b>Algorithm Process:</b>
* Synchronizes data from both sensors to ensure consistent time alignment.
* Estimates the number of time bins and divides data arrays into several bins according to the recorded data.
* Calculates the Turbulence Kinetic Energy (TKE) for both sensors in each bin.
* Conducts a fast Fourier transform (FFT) on the data to transform it into a spectra field.
* Analyzes the spectra to determine the area with the right tangent, enabling the calculation of the rate of dissipation.

<b>Output:</b>
* The algorithm generates a sequence of plots, organized by the sensor.
* These plots visualize log-scaled spectra for each component of velocity.
* The plots display the entire signal as a reference and emphasize the current bin with a horizontal line.

![TKE Calculation!](/Plots/TKE.png)
<b>Figure 5.</b> The graph illustrates the processed velocity data and spectra for every velocity component by FFT for one bin for the main sensor. The bin is emphasized on the plot with the whole signal as a horizontal line.<br>
<br>
<br>
# Certification
**[Data Scientist career track](/Certificates/Data_Scientist.pdf)**<br>
**[Intermediate SQL](/Certificates/Intermediate_SQL.pdf)**<br>
**[Basic SQL](/Certificates/Intro_SQL.pdf)**<br>
**[GIT](/Certificates/Git.pdf)**<br>
**[Climate ocean school](/Certificates/Climate%20and%20ocean%20processes.pdf)**<br>
# Contact information
### My contacts
* <b>e-mail: </b> manurovrus@gmail.com
* <b>GitHub: </b> https://github.com/9Di
* <b>Phone number: </b> +48 506945010 / +49 152 06049353
### References 
* <b> Dr. Alexandra Cherkasheva: </b> acherkasheva@iopan.pl
* <b> Prof. Piotr Kowalczuk : </b> piotr@iopan.pl
   
