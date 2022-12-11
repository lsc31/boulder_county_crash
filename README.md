Boulder county vehicle crash analysis. A data mining project.

This repository has the data analysis on Boulder county vehicle crashes from the Colorado Department of Transportation(CDOT) dataset https://opendata-bouldercounty.hub.arcgis.com/datasets/bouldercounty::crashes/about.
This project contains two python notebook files for initial analysis where we look into the initial trend analysis of the data, comaparitive analysis between Boulder county data and 
LA county data from https://www.kaggle.com/dsv/3286750 to get insights on the accident trends in two cities of different population and weather features.
The results are saved in the directory Results.

1. Initial Analysis
initial_trend_analysis.ipynb

This code answers the following questions:

  1.	Have car accidents increased over time? 
      Yearly trend is analysed by plotting the number of accidents against year in the bar graph. The result can be observed in the file accident_yearly.PNG.
  
  2.	Temporal analysis of severity of accidents?
      This explains how the severity of accidents have changed over years. Achieved by plotting three severity levels Fatal, Injury, PDO (Property Damage Only) over years and over hour of the day. The result is found in Results/severity_yearly.PNG 
      and Results/severity_hourly.PNG.
  
  3.	When do the highest number of accidents occur?
       a.	Monthly proportion
          Monthly trend analysis is observed by plaotting number of accidents against each month. Result is available in the file Results/accident_monthly.PNG.
       b.	Hourly proportion
          Hourly trend analysis is observed by plaotting number of accidents against hour of the day. Result is available in the file Results/accident_hourly.PNG.        
  
  4. Analyzing accident trend during US holidays
      This answers the accident trend during holidays. For this we have integrated holidays from years 2004-2020 available in dataset https://www.kaggle.com/datasets/donnetew/us-holiday-dates-2004-2021?resource=download.
      We have filtered the crashes on holidays over the years 2004-2020 and compared the crash rate over holidays. Average Accidents count on holidays are plotted and compared against the annual daily average (from Results/accident_average.PNG). The results are found in Results/accident_holiday.PNG.

2. Comparitive analysis between two cities
boulder_la_comparison.ipynb

The similarities and differences between the Boulder county and Los Angeles counties with respect to crashes are analysed.
The data from Crashes dataset of Boulder county and LA county are filtered for years 2016-2020. 
Following comparisons are performed:

  1. Yearly accidents reported in two counties.
      The result is analysed for two cities to see more accidents reported in LA than Boulder. See Results/yearly.png.
      The results obtained in previous graph is normalized. Normalization is based on population and results compared for every 10,000 people in both counties which is observed in Results/yearly_norm.png.
      This shows that 5x more accidents are reported yearly every 10,000 people in Boulder.
  
  2. Hourly accident trend in Boulder and LA county.
      Number of accidents are plotted against hour of the day for two counties. See results in Results/hourly.png and Results/hourly_norm.png (normalised).
  
  3. Monthly accident count in Boulder and LA county.
      Number of accidents are plotted against months for two counties. See results in Results/monthly_norm.png.
  
  4. Weekday and weekend accident rate, Day/Night accident rate.
      Number of accidents are plotted against day of the week for two counties. See results in Results/day_norm.png. The count in day and night for the two counties are compared in day_night_norm.png.
  
  5. Seasonal accident trend in Boulder and LA county.
      The season column is added to the dataframe for Boulder and LA for the accidents in following months divided into seasons as :
      Summer: June, July, August
      Winter: December, January, Feb
      Spring: Mar, April, May
      Fall: Sep, Oct, Nov
      The accidents count is plotted for each season to compare the two counties. See results in Results/season_norm.png.
  
  6. Accidents comparison by weather type
      For LA county dataset, for column weather, there are different degrees of variations for each weather type. For example, light_rain heavy_rain, light_drizzle, drizzle etc are all transformed to weather type rain.
      The count of accidents for each weather type is plotted for the counties Boulder (Results/weather_boulder.png) and LA (Results/weather_la.png) and results are compared.
  
  7. Random forest Feature importance
      Random Forest Regressor from scikit-learn is used to determine feature importance in datasets of two counties. 
      The model is trained with the dataset split into 75:25 randomly and for n_estimators, the number of decision trees argument set to 100 in the regressor. 
      The X features for Boulder county ["system","Hour","city","latitude","longitude","Intersection_Id","location","road_desc","contour","condition","lighting","weather","limit1","acctype","vehicle_1","driver_1","Corridor_1","severity"] 
      are trained with target feature set to severity. The top features are plotted in bar graph against their importance in Results/feature_imp_boulder.png.
      Similarly, the X features for LA county ["Temperature(F)","Hour","City","Start_Lat","Start_Lng","Humidity(%)","Pressure(in)","Visibility(mi)","Weather_Condition","Junction","Sunrise_Sunset","Traffic_Signal","Crossing","Severity"]
      are trained against Y feature Severity indicating the severity of the traffic impact. see the results in Results/feature_imp_la.png.
      Heatmaps for the two counties are plotted to understand which features are highly correlated. (Results/heatmap_bo.png and Results/heatmap_la.png)




   
    
