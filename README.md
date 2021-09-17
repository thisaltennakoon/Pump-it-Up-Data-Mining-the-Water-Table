# Pump-it-Up-Data-Mining-the-Water-Table
<p><strong>Preprocessing Feature engineering techniques</strong></p>
<ul>
<li>Identify and handle missing NaN values</li>
<ul>
<li>Could not find any NaN Values in numerical columns</li>
<li>There were some NaN values in categorical columns</li>
</ul>
<li>Zero values of following attributes were replaced with NaNs due to the these reasons</li>
<ul>
<li>Tanzania is Situated in 00&deg;59' S, 11&deg;45' S, 29&deg;10' E, 40&deg;29' E (longitude, latitude) therefore having zero values for <strong>longitude, latitude</strong> cannot happen here</li>
<li><span style="color: #212121;">Also, there are many zero values for the </span><span style="color: #212121;"><strong>construction_year </strong></span><span style="color: #212121;">attribute. It is also not possible</span></li>
<li><span style="color: #212121;"><strong>amount_tsh </strong></span><span style="color: #212121;">- Total static head (amount water available to waterpoint) cannot contain many zero values as if it is zero; there is no point in building a waterpoint</span></li>
<li><span style="color: #212121;"><strong>population </strong></span><span style="color: #212121;">- Population around the well cannot contain many zero values as if it is zero, there is no point in building a waterpoint</span></li>
<li><span style="color: #212121;">According to the maps mentioned in the notebook, regions with zero altitudes are less in Tanzania and have tropical savannah climates. Therefore we can assume that zero values for the gps_height variable are not that meaningful.</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of gps_height were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The mean value of the gps_height attribute of the group(grouped by region and&nbsp; district_code )</span></li>
<li><span style="color: #212121;">The mean value of the gps_height attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #212121;">The mean value of the gps_height attribute as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of population were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The median value of the population attribute of the group(grouped by region and&nbsp; district_code )</span></li>
<li><span style="color: #212121;">The median value of the population attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #212121;">The median value of the population attribute as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of amount_tsh were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The median value of the amount_tsh attribute of the group(grouped by region and&nbsp; district_code )</span></li>
<li><span style="color: #212121;">The median value of the amount_tsh attribute of the group(grouped by region) and finally with&nbsp;</span></li>
<li><span style="color: #212121;">The median value of the amount_tsh attribute as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of latitude were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The mean value of the latitude attribute of the group(grouped by region and&nbsp; district_code ) as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of longitude were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The mean value of the longitude attribute of the group(grouped by region and&nbsp; district_code )</span></li>
<li><span style="color: #212121;">The mean value of the amount_tsh attribute of the group(grouped by region) as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Thereafter NaN values of construction_year were replaced with</span></li>
<ul>
<li><span style="color: #212121;">The median value of the construction_year attribute of the group(grouped by region and&nbsp; district_code )</span></li>
<li><span style="color: #212121;">The median value of the construction_year attribute of the group(grouped by region)</span></li>
<li><span style="color: #212121;">The median value of the construction_year attribute of the group(grouped by district_code) and finally with</span></li>
<li><span style="color: #212121;">The median value of the construction_year attribute as there is a relationship with region and&nbsp; district_code</span></li>
</ul>
<li><span style="color: #212121;">Convert the values of the date_recorded column to datetime data type</span></li>
<li>Created a new feature called&nbsp; construction_to_recorded using year of the date_recorded and construction_year</li>
<li><span style="color: #212121;">Min Max scaling was done for gps_height, population, amount_tsh attributes as those were not normally distributed</span></li>
<li><span style="color: #212121;">Mode imputations were carried out for all the remaining categorical variables.(Different imputation techniques such as mean, median, &ldquo;Missing&rdquo; value imputations ware tried but mode imputation gave the best results)</span></li>
<li><span style="color: #212121;">Converted all the categorical variables into lowercase</span></li>
<li><span style="color: #212121;">Identified following features are redundant and decided to use only one out of those</span></li>
<ul>
<li><span style="color: #212121;">'management' and 'scheme_management'</span></li>
<li><span style="color: #212121;">'payment' and 'payment_type'</span></li>
<li><span style="color: #212121;">'extraction_type', 'extraction_type_group', 'extraction_type_class'</span></li>
<li><span style="color: #212121;">'region' and 'region_code'</span></li>
<li><span style="color: #212121;">'source' and 'source_type'</span></li>
<li><span style="color: #212121;">'waterpoint_type' and 'waterpoint_type_group'</span></li>
<li><span style="color: #212121;">'quantity' and 'quantity_group'</span></li>
</ul>
<li><span style="color: #212121;">Following features were selected using filter methods and label encoding and one hot encoding methods were used to encode these attributes&nbsp;</span></li>
<ul>
<li>Label encoding - amount_tsh, funder, gps_height, longitude, latitude, basin, region, district_code, lga, population, scheme_management, extraction_type, management, payment_type, water_quality, quantity, source, waterpoint_type, construction_to_recorded</li>
<li>One hot encoding - Installer&nbsp;</li>
</ul>
<li><span style="color: #212121;">'wpt_name' and 'subvillage' were not used since categorical cardinality is high.</span></li>
</ul>
