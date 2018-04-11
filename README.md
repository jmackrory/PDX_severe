# PDX_severe

This repository will download, clean and play with NOAA Severe Weather Data.
(https://www.ncdc.noaa.gov/data-access/severe-weather).
The Storm Events Database tracks severe weather (tornados, floods, heatwaves) 
since the 1960s or so.  It tracks location (by county), time, cost to property, crops, and separately
contains the fatalities.  Currently the data is split by year.

It can be downloaded from (https://www.ncdc.noaa.gov/stormevents/ftp.jsp),
which also has links to FAQs, sourcing the data, and the scales involved.

## Downloading the data

So a simple bash command works:

"wget ftp://ftp.ncdc.noaa.gov/pub/data/swdi/stormevents/csvfiles/StormEvents_details-ftp_v1.0_*.csv.gz"

Repeated 3 times for details/fatalities/locations. (231MB all told).

## Trimming Data

All of the data can be loaded as a single Pandas dataframe (its around 2GB in RAM) 
I created a smaller version by trimming down most of the columns.
The trimmed version in the joint\_data folder only contains 
these columns:
['BEGIN\_DAY', 'BEGIN\_TIME', 'EPISODE\_ID', 'EVENT\_ID', 'STATE', 'YEAR',
       'MONTH\_NAME', 'EVENT\_TYPE', 'CZ\_TIMEZONE', 'INJURIES\_DIRECT',
       'INJURIES\_INDIRECT', 'DEATHS\_DIRECT', 'DEATHS\_INDIRECT',
       'DAMAGE\_PROPERTY', 'DAMAGE\_CROPS', 'BEGIN\_LAT', 'BEGIN\_LON'].

This has dropped the narratives, end times, duplicate datetimes, 
all tornado information, flood causes, magnitudes for rain/hail.  
Losing Narratives means it's harder to search for named storms, but probably biggest space saver.  
The damage numbers were also processed from letter postfixes to actual powers 
of 10.

The trimmed file is around 30MB when zipped.  Could be trimmed further by
reducing daterange?

# Ipython notebook

Currently contains some test plots (histograms of deaths, damages, injuries)
Also counts numbers of events by type.  
