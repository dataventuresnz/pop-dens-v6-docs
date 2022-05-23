# v6 Population Density Methodology Summary
 
## Overview

The hourly population estimates provide the number of international visitors, domestic visitors, and local residents in each Statistical Area 2 (SA2; A neighbourhood size area). 
 
## Definitions

* International visitors are people from outside New Zealand, who are staying in the country for less than 90 days.
* Domestic visitors are people outside their home region in New Zealand.
* Local residents are people in their home region.
* Home regions are currently defined based on Regional Tourism Organisation (RTO) areas. 

## How do we produce our estimates?

* Data Ventures gets information from Spark and Vodafone about device locations.
* All the input data we get is anonymised, meaning it cannot be used to identify an individual.
* We classify devices as international, domestic, or local using a combination of SIM card and location information.
* The device location information is turned into device counts which show how many devices are in each SA2 each hour.
* We combine the device counts from the two providers.
* We then convert the device counts to population counts using supplementary datasets. We account for people without phones and people with several phones. 
* To protect confidentiality, we randomly round population counts to base three.
 
## Latest version

The latest version of the population estimates is version 6.0.0.

Compared to previous versions, version 6.0.0 has:
* Higher confidence and accuracy in population estimates, due to a new feed of data from telecommunication providers.
* Improved accuracy in population estimates in areas bordering water bodies such as lakes or oceans.
* A much more accurate approach to estimating the number of international visitors.
* Greater accuracy of domestic visitor estimates, letting us see peaks and troughs more clearly in the data. This means the data is now more useful for understanding the number of visitors associated with events such as festivals.
