# PDX_severe

This repository will download, clean and play with NOAA Severe Weather Data.
(https://www.ncdc.noaa.gov/data-access/severe-weather).
The Storm Events Database tracks severe weather (tornados, floods, heatwaves) 
since the 1960s or so.  It tracks location (by county), time, cost to property, crops, and separately
contains the fatalities.  Currently the data is split by year.

It can be downloaded from (https://www.ncdc.noaa.gov/stormevents/ftp.jsp),
which also has links to FAQs, sourcing the data, and the scales involved.

We're going to work in Python to download the data from NOAA. 
(A quick estimate suggested it would be 400MB!)
We'll put the whole shebang into one big data frame, and trim the beast down
to something manageable. 

## Downloading the data

So a simple bash command works:

"wget ftp://ftp.ncdc.noaa.gov/pub/data/swdi/stormevents/csvfiles/StormEvents_details-ftp_v1.0_*.csv.gz"

Repeated 3 times for details/fatalities/locations. (231MB all told).

