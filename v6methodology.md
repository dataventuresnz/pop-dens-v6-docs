# v6 Population Density Methodology Documentation
 
## Overview
 
The hourly population estimates provide a breakdown of international visitors, domestic visitors, and local residents in each Statistical Area Level 2 (SA2; A neighbourhood size area). 
 
## Segment definitions
- International visitors are people from outside New Zealand, who are staying in the country for less than 90 days.
- Domestic visitors are people outside their home region in New Zealand.
- Local residents are people in their home region.
- Home regions are currently defined based on Regional Tourism Organisations (RTOs). 

## Methodology
 
- Data Ventures receives device counts from Spark and Vodafone (the data providers). 
    - The data providers use methods supplied by Data Ventures to process their cellphone location data into aggregated device counts.
    - Devices are assigned to an SA2 area based on the signal strength to nearby cell towers.
    - Non-cellphone devices (e.g., Internet of Things devices) are excluded from the device counts.
- If a device is not observed for a given hour, the data providers impute the location based on the device location in the following or preceding hours. At nighttime, a lot more devices get imputed as less people are using their phones or have their phones on.
- The data providers classify devices as international, domestic, or local using a combination of SIM card and location information.
    - If the device has an international SIM card, it is classed as an international device.
    - To separate domestic from local devices, a home region (RTO area) is assigned to each device with an NZ SIM card. The home region is based on the most common nighttime location over the previous 14 days.
    - Domestic devices are those outside their home RTO area.
    - Local devices are those in their home RTO area.
- We combine the counts from the two providers.
- We then convert the device counts to population counts by applying a weight. The weighting process accounts for people without phones and people with several phones. 
    - We use supplementary datasets to inform the weights, including data about how many people are entering and leaving the country.
- To ensure privacy, we randomly round numbers to base three and suppress counts below ten.

## Version information
Our current version is 6.0.0, which was implemented in late April 2021.
This version includes the following enhancements:
 
| Change 	| Effect on data 	|
| :---	| :---	|
| We now receive new streams of data from telecommunication providers. The new streams result in a much higher quality of device counts as well as better coverage of device counts across the country. 	| Improved accuracy of population estimates. 	|
| We have applied a correction to stop devices near water bodies (such as lakes and oceans) from being assigned to the water body. These devices are now assigned to neighbouring land SA2s.  This also corrects a bug where there were large swings in the proportion of people being assigned to water bodies. 	| Greater accuracy in population estimates in coastal areas and areas bordering lakes. 	|
| We have significantly increased the accuracy of domestic visitor assignment by adjusting our weighting methodology. 	| Bigger peaks and troughs in domestic visitor population than previously observed.   This has also had a smaller, less noticeable impact on local resident populations. (If more people are domestic, fewer people must be local.) 	|
| We use a 90-day window to define an international visitor. This definition is used to calculate the weights when converting international device counts into international visitor numbers.  Previous versions already used the 90-day definition. However, this was implemented during COVID under the assumption that borders were closed. We have identified that this method was not fit for use post-COVID. 	| Expect extremely large differences in the numbers of international visitors between version 6.0.0 and the previous version (5.1.1).    For periods before 19 April (the opening of the travel bubble), the version 6.0.0 data shows roughly 35 times fewer international visitors than version 5.1.1.  After this date, version 6.0.0 shows around 8 times fewer international visitors than version 5.1.1. 	|
| We have now updated our methodology to produce more accurate estimates and better meet post-COVID data needs. 	|  	|

 
### Other major improvements that have been introduced since version 1.0.0 include:
- If a device is not registered for a given hour we impute the device. The model for imputation was significantly enhanced in version 5.0.0.
- Before version 5.0.0, domestic visitors were outside their home SA2. In version 5.0.0, we redefined a domestic visitor as someone outside their home RTO.
- Random rounding to base 3 and suppression for confidentiality was introduced in version 4.0.0.
- Segmentation (i.e., estimates broken down by local, domestic, and international) was introduced in version 2.0.0.


## Caveats

| Caveat 	| Effect on data 	|
| :---	| :---	|
| Occasionally there are outages in cell towers, often due to hardware faults and maintenance.  | Depending on the extent of the missing data, we will allow our usual methodology to impute a dropout which has minimal impact to data quality. If, however, the data is a complete drop out, we will usually leave that period blank rather than report data for a single cell phone provider.    |
| When assigning home location, we look at the overnight location. If the phone does not appear at that time, we start scanning back until a location is found (up to the previous night). This has caused some error when assigning a home location.   | Potential misclassifications of local vs domestic visitors.   |
| At night, there is less cell phone activity, particularly around 3 am to 5 am.  | Some bias may be introduced at this time, but we are still investigating the impact on the data.    |
| The distribution of international visitors is determined by devices that contain an international SIM card. This means residents and migrants with international SIM cards will contribute to the distribution of international visitors. As a result,a higher proportion of visitors appear in residential areas and a lower proportion of visitors are located in the correct tourist locations.    | During normal travel periods, this has only minor impacts on the data. However, during the pandemic the proportion of residents and migrants to visitors is substantially higher. This means more bias is introduced to device counts.
For periods impacted by travel restrictions, it may be better to rely on the proportion change in international visitors rather than relying solely on a single visitor count.  | 
| Repatriated New Zealanders are likely the majority of international visitors after 20th March 2020 - especially until 19 April, when the Trans-Tasman bubble opened.  | International visitor numbers during COVID-impacted periods may not accurately reflect international tourism. |


## Data quality issues
### Data is missing for the following period(s):
2021-02-28 06:00 to 2021-03-01 02:00
2021-05-28 09:00 to 12:00 and 19:00 to 23:00

### Data quality is lower than usual for the following period(s):
2021-05-27 12:00 to 2021-05-28 08:00
 
### Note
Over time, we will refine our methodology, which may result in adjustments to population estimates. We will communicate changes when they take effect.
