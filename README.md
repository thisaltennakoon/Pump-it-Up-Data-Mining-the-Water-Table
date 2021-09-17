# Pump-it-Up-Data-Mining-the-Water-Table
Preprocessing Feature engineering techniques

Identify and handle missing NaN values
Could not find any NaN Values in numerical columns
There were some NaN values in categorical columns
Zero values of following attributes were replaced with NaNs due to the these reasons
Tanzania is Situated in 00°59' S, 11°45' S, 29°10' E, 40°29' E (longitude, latitude) therefore having zero values for longitude, latitude cannot happen here
Also, there are many zero values for the construction_year attribute. It is also not possible
amount_tsh - Total static head (amount water available to waterpoint) cannot contain many zero values as if it is zero; there is no point in building a waterpoint
population - Population around the well cannot contain many zero values as if it is zero, there is no point in building a waterpoint
According to the maps mentioned in the notebook, regions with zero altitudes are less in Tanzania and have tropical savannah climates. Therefore we can assume that zero values for the gps_height variable are not that meaningful.
Thereafter NaN values of gps_height were replaced with
The mean value of the gps_height attribute of the group(grouped by region and  district_code )
The mean value of the gps_height attribute of the group(grouped by region) and finally with 
The mean value of the gps_height attribute as there is a relationship with region and  district_code
Thereafter NaN values of population were replaced with
The median value of the population attribute of the group(grouped by region and  district_code )
The median value of the population attribute of the group(grouped by region) and finally with 
The median value of the population attribute as there is a relationship with region and  district_code
Thereafter NaN values of amount_tsh were replaced with
The median value of the amount_tsh attribute of the group(grouped by region and  district_code )
The median value of the amount_tsh attribute of the group(grouped by region) and finally with 
The median value of the amount_tsh attribute as there is a relationship with region and  district_code
Thereafter NaN values of latitude were replaced with
The mean value of the latitude attribute of the group(grouped by region and  district_code ) as there is a relationship with region and  district_code
Thereafter NaN values of longitude were replaced with
The mean value of the longitude attribute of the group(grouped by region and  district_code )
The mean value of the amount_tsh attribute of the group(grouped by region) as there is a relationship with region and  district_code
Thereafter NaN values of construction_year were replaced with
The median value of the construction_year attribute of the group(grouped by region and  district_code )
The median value of the construction_year attribute of the group(grouped by region)
The median value of the construction_year attribute of the group(grouped by district_code) and finally with
The median value of the construction_year attribute as there is a relationship with region and  district_code
Convert the values of the date_recorded column to datetime data type
Created a new feature called  construction_to_recorded using year of the date_recorded and construction_year
Min Max scaling was done for gps_height, population, amount_tsh attributes as those were not normally distributed
Mode imputations were carried out for all the remaining categorical variables.(Different imputation techniques such as mean, median, “Missing” value imputations ware tried but mode imputation gave the best results)
Converted all the categorical variables into lowercase
Identified following features are redundant and decided to use only one out of those
'management' and 'scheme_management'
'payment' and 'payment_type'
'extraction_type', 'extraction_type_group', 'extraction_type_class'
'region' and 'region_code'
'source' and 'source_type'
'waterpoint_type' and 'waterpoint_type_group'
'quantity' and 'quantity_group'
Following features were selected using filter methods and label encoding and one hot encoding methods were used to encode these attributes 
Label encoding - amount_tsh, funder, gps_height, longitude, latitude, basin, region, district_code, lga, population, scheme_management, extraction_type, management, payment_type, water_quality, quantity, source, waterpoint_type, construction_to_recorded
One hot encoding - Installer 
'wpt_name' and 'subvillage' were not used since categorical cardinality is high.
