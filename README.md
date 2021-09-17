# Pump-it-Up-Data-Mining-the-Water-Table

Link to the Colab Notebook - https://colab.research.google.com/drive/1gobxLmJgIQpioZV3ktVEO40HeGJEPoXf?usp=sharing
Score - 0.8187
Rank - 1348(2021-09-17 13:45:43 UTC)

<p><span style="color: #0e101a;"><strong>Preprocessing & Feature engineering techniques</strong></span></p>
<ul>
<li><span style="color: #0e101a;">Identify and handle missing NaN values.</span></li>
<ul>
<li><span style="color: #0e101a;">Any NaN Values in numerical columns were not there.</span></li>
<li><span style="color: #0e101a;">There were some NaN values in categorical columns.</span></li>
</ul>
<li><span style="color: #0e101a;">Zero values of the following attributes were replaced with NaNs due to these reasons.</span></li>
<ul>
<li><span style="color: #0e101a;">Tanzania is Situated in 00&deg;59' S, 11&deg;45' S, 29&deg;10' E, 40&deg;29' E (longitude, latitude) therefore having zero values for </span><span style="color: #0e101a;"><strong>longitude, latitude</strong></span><span style="color: #0e101a;"> cannot happen here.</span></li>
<li><span style="color: #0e101a;">Also, there are many zero values for the </span><span style="color: #0e101a;"><strong>construction_year </strong></span><span style="color: #0e101a;">attribute. It is also not possible.</span></li>
<li><span style="color: #0e101a;"><strong>amount_tsh </strong></span><span style="color: #0e101a;">- Total static head (amount water available to waterpoint) cannot contain many zero values as if it is zero; there is no point in building a waterpoint</span></li>
<li><span style="color: #0e101a;"><strong>population </strong></span><span style="color: #0e101a;">- Population around the well cannot contain many zero values as if it is zero, there is no point in building a waterpoint</span></li>
<li><span style="color: #0e101a;">According to the maps mentioned in the notebook, regions with zero altitudes are less in Tanzania and have tropical savannah climates. Therefore we can assume that zero values for the gps_height variable are not that meaningful.</span></li>
</ul>
<li><span style="color: #0e101a;">After that, NaN values of gps_height were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The mean value of the gps_height attribute of the group(grouped by region and district_code )</span></li>
<li><span style="color: #0e101a;">The mean value of the gps_height attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #0e101a;">The mean value of the gps_height attribute as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">After that, NaN values of the population were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The median value of the population attribute of the group(grouped by region and district_code )</span></li>
<li><span style="color: #0e101a;">The median value of the population attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #0e101a;">The median value of the population attribute as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">After that, NaN values of amount_tsh were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The median value of the amount_tsh attribute of the group(grouped by region and district_code )</span></li>
<li><span style="color: #0e101a;">The median value of the amount_tsh attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #0e101a;">The median value of the amount_tsh attribute as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">After that, NaN values of latitude were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The mean value of the latitude attribute of the group(grouped by region and district_code ) as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">Thereafter NaN values of longitude were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The mean value of the longitude attribute of the group(grouped by region and district_code )</span></li>
<li><span style="color: #0e101a;">The mean value of the amount_tsh attribute of the group(grouped by region) as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">Thereafter NaN values of construction_year were replaced with</span></li>
<ul>
<li><span style="color: #0e101a;">The median value of the construction_year attribute of the group(grouped by region and district_code )</span></li>
<li><span style="color: #0e101a;">The median value of the construction_year attribute of the group(grouped by region)</span></li>
<li><span style="color: #0e101a;">The median value of the construction_year attribute of the group(grouped by district_code) and finally with</span></li>
<li><span style="color: #0e101a;">The median value of the construction_year attribute as there is a relationship with region and district_code</span></li>
</ul>
<li><span style="color: #0e101a;">Convert the values of the date_recorded column to DateTime data type</span></li>
<li><span style="color: #0e101a;">Created a new feature called construction_to_recorded using the year of the date_recorded and construction_year</span></li>
<li><span style="color: #0e101a;">Min Max scaling was done for gps_height, population, amount_tsh attributes as those were not normally distributed.</span></li>
<li><span style="color: #0e101a;">Mode imputations were carried out for all the remaining categorical variables. (Different imputation techniques such as mean, median, "Missing" value imputations were tried, but mode imputation gave the best results)</span></li>
<li><span style="color: #0e101a;">Converted all the categorical variables into lowercase</span></li>
<li><span style="color: #0e101a;">Identified following features are redundant and decided to use only one out of those.</span></li>
<ul>
<li><span style="color: #0e101a;">'management' and 'scheme_management'</span></li>
<li><span style="color: #0e101a;">'payment' and 'payment_type'</span></li>
<li><span style="color: #0e101a;">'extraction_type', 'extraction_type_group', 'extraction_type_class'</span></li>
<li><span style="color: #0e101a;">'region' and 'region_code'</span></li>
<li><span style="color: #0e101a;">'source' and 'source_type'</span></li>
<li><span style="color: #0e101a;">'waterpoint_type' and 'waterpoint_type_group'</span></li>
<li><span style="color: #0e101a;">'quantity' and 'quantity_group'</span></li>
</ul>
<li><span style="color: #0e101a;">Following features were selected using filter methods, and label encoding and one hot encoding method were used to encode these attributes.&nbsp;</span></li>
<ul>
<li><span style="color: #0e101a;">Label encoding - amount_tsh, funder, gps_height, longitude, latitude, basin, region, district_code, lga, population, scheme_management, extraction_type, management, payment_type, water_quality, quantity, source, waterpoint_type, construction_to_recorded</span></li>
<li><span style="color: #0e101a;">One hot encoding - Installer&nbsp;</span></li>
</ul>
<li><span style="color: #0e101a;">'wpt_name' and 'subvillage' were not used since categorical cardinality is high.</span></li>
</ul>
