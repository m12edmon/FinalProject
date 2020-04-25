# FinalProject
Final Data Analytics project on water quality in N.C.

# <Analysis of Fecal Coliform Concentrations within North Carolina Surface Waters>

## Summary

North Carolina is a national leader in livestock production ranking 2nd pork production.The vast majority of livestock are grown on concentrated animal feeding operations (“CAFOs”) designed to maximize production efficiency and raise as many animals as possible, as quickly as possible.Though CAFOs have resulted in massive expansion and record profits in the livestock industry, they presents significant waste management challenges. The purpose of this repository is to obtain all known fecal coliform samples from surface waters gathered by USGS and analze the data to see which counties have the fecal concentrations higher than the proposed EPA standard, and if any of those counties are located in the major industrial swine farming areas. I will determine through a one-way ANOVA which counties could have a signfificant correlation between fecal concentrations, and then from that data, if any have a significant correlation, do a deep dive into that data looking into changes across years, seasons, or anthing that may seem unusual.

## Investigators

Masha Edmondson is primary investigator using data collected by USGS through STORET and NWIS.

## Keywords

fecal coliform, surface water, water quality monitoring

## Database Information

ALl data for this repository was collected by the Water Quality Data Portal that took USGS water quality samples from stored NWIS and STORET data. The selection process only selected all North Carolina counties that had a record of microbiological contaminates in surface waters, specifically fecal coliform. This data was accessed on April 10, 2020, and downloaded April 10, 2020. Additionally parameters that included E. coli, were also considered, but lacked consitancy across N.C. counties.

## Folder structure, file formats, and naming conventions 

Folders:

R Studio Final Project, which is a new R project file.
README.md doument that describes the nature of the repository 
R markdown document, which contains the coding for analysis of the data
all_fecal_coliform, is a folder that contains a csv file with all N.C. county sample data
county_fecal_coliform folder, that contains multiple csv files of six counties that had the highest amount of fecal coliform concentrations in surface waters.

file naming conventions follow the data that it is analysisng. For example the csv file that contains all fecal coliform samples for N.C. is named All_fc. Additionally country specific data is name "County Name.fc".


## Metadata

The data downloaded from the Water Quality Data Protal contained detailed csv file of records obtained per USGS data recording protocol. Infomation in each column and rows included:
Organization Identifier – the organization responsible for the data collection (USGS-NC)
Organization Formal Name- the organization responsible for the data (USGS- North Carolina)
Monitoring Location Identifier – USGS specific location identifier per each surface water monitor 
Monitoring Location Name- location of the surface water monitoring station
Monitoring Location Type Name- type of surface water (stream, river, reservoir)
Monitoring Location Description Text- text description of monitor location
HUC Eight Digit Code- Assigned HUC code for the watershed the monitor is in
Latitude-  Latitude coordinates
Horizontal Coordinates -NAD83
County Code – USGS assigned county code for each N.C. county
Longitude- Longitude coordinates
Activity Identifier – Specific NWIS code applied to the data (nwisnc.01.97600261)
Activity Type Code – why was this data collected, all were routine sample collections
Activity Media Name – type of media used, water
Activity Subdivision Name- subdivision of media used, surface water
Activity Start Date- the date the sampling occurred m/d/yy
Activity Start Time- Time the sampling occurred
Activity Conducting Organization Text -list of any Organization other than U.S. Geological Survey involved
Hydrologic condition – description of the hydrologic condition of surface water: fair, poor, not determined
Sample collection method – what method was used for sampling, USGS method
Characteristic Name – what was being sampled, which is fecal  coliform
Results Measured – the concentration of the sample
Results Measured units- the units of the sample collected
Results Status – was this a recent collection or historical collection
Result Value – did USGS conduct the study the column will say “actual”
USGSP Code- a code assigned by USGS per each sample
Detection Quantitation Limit Type – notes section on if there were changes in historical records of sampling
Detection Quantitation Limit Measure- the associated lower or higher pervious sample concentration
Provider Name – who collected the data which is either NWIS or STORET


For specific analysis of counties and fecal concentrations, filtering of data only included the date, the concentration, and the county. For specific counties, filtering of the data set included just the date, month, and concentration of fecal coliform. 

## Scripts and code
Ongoing updates to scripts and code will continue throughout this analysis.
I am currently using nine packages to conduct anlaysis of my project as seen below: 
library(dataRetrieval)
library(tidyverse)
library(cowplot)
library(lubridate)
library(viridis)
library(readr)
library(dplyr)
library(agricolae)
library(knitr)

I will also be using previous lessons that were conducted in the Environmental Data Analytics 2020 GitHub Respository, and Hydrology Repository.

## Quality assurance/quality control
I would check for outliers in data to make sure nothing was out of range. I would only consider fecal coliforms filter to 0.7 (cfu/100 ml) because that is the most consistent data collection method for this parameter. I will only consider surface water ways (not groundwater wells or other types of aquifers). I am also only considering areas where there are swine CAFOs in my deeper analysis. Counties that have a high fecal concentration that do not have any recorded industrial farming activity will be noted but not included in the deeper analysis. Finally I am only selecting data from 1970 to 2018. I chose this data frame because 19070 was the first recorded year to have a fecal sample condected all twelve months out of the year.