# Environmental remote sensing data processing 
This repository contains some of examples of the algorithms composed in Python by me, as well as obtained certificates related to the field.

### Model variations establishment using local in-situ data
The 'Point_PP.py' algorithm were composed in order to find the best suited model based on the correlation with in-situ data and statistical parameters (RMSD, BIAS, normalized values, Pearson correlation coefficient, standard deviation). As a result, we were able to filter the output by necessary statistical values in order to highlight the most suitable model. The algorithm takes the following parameters as an input: year and month of interest, CHL-a satellite data level, Photosynthetically avaliable radiation satellite data level, Gaussian equiation involvment in the calculation, type of spectra data, 2 versions of depth either based on Gaussian or Linear law.    

![Model variations!](/Plots/Models_variations.PNG)

![Model boxplot!](/Plots/Models_boxplot.PNG)


### Area PP calculation with the most suitable model
The 'Area_PP.py' algorithm were used to calculate the sum and monthly mean values of Primary Production monthly over 2 decades (1998 - 2022) using Copernicus, Hermes, Nasa remote sensing data. Basically, this code is a successor of 'Point_PP.py' algorithm. As we achived the model variations passed through the filter using the 'Point_PP.py' file, we were able to use those variations to calculate the sum and monthly mean values of chlorophyll-a Primary Production (PP) filtered by the area of interest. In our case, we had an option to digitalize the Norway sea to store the coordinates of the border of the sea. 

![Monthly Mean PP!](/Plots/Monthly_mean.JPG)


### CO2 exchange variability using Turbulence Kinetic Energy and Dissipation Rate
The 'Spectra_bin.py' algorithm works with CO2 exchange data. It takes the data from 2 sensors (master sensor in the actual point, slave sensor is near the area), which have measured x,y,z components of velocities and pressure. The algorithm synchronizes both sensors, estimates the number of time bins and divides data arrays into several bins (depending on how many there are according to the records), calculates the value of Turbulence Kinetic Energy (TKE) for both sensors in every bin, as well as conducts the fast fourier transform (FFT) in order to tranform the area into spectra field. Working with the spectra we're able to find the area with the right tangent in order to calculate the rate dissipation. The output of the algorithm is a bin-by-bin sequence of plots sorted by the sensor, visualizing log-scaled spectra for every component of velocity, showing the whole signal as a reference and emphasizing the current bin in there with a horizontal line.    
