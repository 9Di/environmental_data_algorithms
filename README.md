# Environmental remote sensing data processing 
<p>MOPAR is an environmental research project focused on primary production analysis in the ocean. This README provides an overview of the project, its objectives, and key components.
The algorithms and code in this repository were developed by Manurov Rustam. The plots were composed using Python's packages (PyGMT, Seaborn) and Photoshop.
This repository stores certificates in Python, Data Analysis, and Data Science, demonstrating my expertise in these fields.</p>

### Project Overview
<p>MOPAR aims to analyze primary production in the ocean using a combination of in-situ data and satellite observations. The project comprises primary algorithms, each with multiple variations, designed to collect, process, compare data, and estimate Primary Production over 2 decades. These algorithms help obtain valuable insights into primary production and its geographical distribution.</p>


### Algorithms
#### <b>Algorithm 1:</b> **[In-Situ Data Integration](https://github.com/9Di/environmental_data_algorithms/blob/main/Algorithms/Point_PP.py)**.<br>
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
</p>




### Model variations establishment using local in-situ data
<p>The 'Point_PP.py' algorithm were composed in order to find the best suited model based on the correlation with in-situ data and statistical parameters (RMSD, BIAS, normalized values, Pearson correlation coefficient, standard deviation). As a result, we were able to filter the output by necessary statistical values in order to highlight the most suitable model. The algorithm takes the following parameters as an input: year and month of interest, CHL-a satellite data level, Photosynthetically avaliable radiation satellite data level, Gaussian equiation involvment in the calculation, type of spectra data, 2 versions of depth either based on Gaussian or Linear law.</p>

![Map!](/Plots/PyGMT_map.PNG)
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
<br>
#### <b>Algorithm 2:</b> **[Regional Primary Production Estimation](https://github.com/9Di/environmental_data_algorithms/blob/main/Algorithms/Area_PP.py)**.<br>
* The second algorithm utilizes parameters that have been validated as effective in the first algorithm.
* It calculates geographical data for primary production (PP) across a span of two decades.
* The algorithm generates tables with approximately 400,000 bins to estimate monthly PP values for 1998-2022.
* It calculates the sum of PP values and obtains monthly mean values, allowing for regional primary production estimation.

### Area PP calculation with the most suitable model
The 'Area_PP.py' algorithm were used to calculate the sum and monthly mean values of Primary Production monthly over 2 decades (1998 - 2022) using Copernicus, Hermes, Nasa remote sensing data. Basically, this code is a successor of 'Point_PP.py' algorithm. As we achived the model variations passed through the filter using the 'Point_PP.py' file, we were able to use those variations to calculate the sum and monthly mean values of chlorophyll-a Primary Production (PP) filtered by the area of interest. In our case, we had an option to digitalize the Norway sea to store the coordinates of the border of the sea. 

![Monthly Mean PP!](/Plots/Monthly_mean.JPG)
<b>Figure 4.</b> Monthly primary production for 1998-2022.
<br>
<br>
<br>
### CO2 exchange variability using Turbulence Kinetic Energy and Dissipation Rate
The 'Spectra_bin.py' algorithm works with CO2 exchange data. It takes the data from 2 sensors (master sensor in the actual point, slave sensor is near the area), which have measured x,y,z components of velocities and pressure. The algorithm synchronizes both sensors, estimates the number of time bins and divides data arrays into several bins (depending on how many there are according to the records), calculates the value of Turbulence Kinetic Energy (TKE) for both sensors in every bin, as well as conducts the fast fourier transform (FFT) in order to tranform the area into spectra field. Working with the spectra we're able to find the area with the right tangent in order to calculate the rate dissipation. The output of the algorithm is a bin-by-bin sequence of plots sorted by the sensor, visualizing log-scaled spectra for every component of velocity, showing the whole signal as a reference and emphasizing the current bin in there with a horizontal line.    
