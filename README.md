## Examining-Collision-Patterns-and-Trends-for-Safety-of-Autonomous-Driving

# Abstract
The objective of this study is to identify key patterns and trends with risk associated with AV collisions. It uses the reports from traffic collisions in California using descriptive analytics with predictive modeling techniques. Due to the increase of AV adoption, public safety and trust remain a concern among the general public. Public data was taken from the California Department of Motor Vehicles (DMV) from 2022 to 2024 and with 338 reports downloaded and analyzed. 
After cleaning the dataset, exploratory data analysis was performed and revealed that most collisions resulted in minor damage, typically in clear weather and dry road conditions. Association rule mining was then performed and explored frequent conditions that contributed to the low impact incidents. Predictive models which included Decision Tree (CART), Logistic Regression, and Naive Bayes were also performed to estimate the collision damage. The Decision Tree model performed the best with an accuracy of 77.5%. However, all the models struggled to predict severe collision due to the nature of the dataset which resulted in a data imbalance. 
Although there were limitations to this study like rare events were difficult to analyze, the analysis highlighted the importance of environmental conditions and factors in AV collision. Insights from the study explored would help inform AV system designs and future research   efforts. As more data gets collected, enhancing these modeling techniques can help with the deployment of AV technology and get consumers to trust in adopting a growing technology. 
# Chapter 1: Introduction

# Objective:
The objective of this analysis is to examine patterns, trends, and key factors contributing to traffic collisions involving autonomous vehicles (AVs) in California. By analyzing and conducting a descriptive analysis of detailed collision reports from the California Department of Motor Vehicles (DMV), this study aims to identify recurring themes in these incidents, such as environmental conditions, vehicle movements, damage severity, and the operational mode of AVs (Autonomous vs. Conventional). Although this study primarily focuses on descriptive analysis, due to limitations in available data, predictive modeling will be explored to highlight potential correlations and future analytical opportunities. The findings will provide insights into the scenarios under which AVs are more likely to be involved in accidents, helping stakeholders better understand AV safety challenges and areas for improvement. 

# Impact:
This study would improve and enhance our understanding of patterns and trends in response to the rise and popularity of AV’s. By studying and analysing the collision report dataset, this would contribute to the safety of passengers on the road. This is critical due to several reasons. Firstly, by researching the situation in conditions that cause the damage severity of the vehicle, AV developers can investigate specific factors and improve and refine their algorithm and technology. This would improve safety by reducing accident rates and enhance the performance of these vehicles. Secondly, this research is a detailed and comprehensive descriptive analysis of the situation based on the reports with development of a strong predictive modeling. The descriptive analysis would serve as a foundation, guiding the selection of key variables such as road conditions and weather. By doing this, public trust of AV’s will be more understood and improved on. Strong research would demonstrate a commitment towards public safety in which the public would see and adopt and lead to greater confidence and acceptance. Lastly, by discussing and refining the models that leverage key data points will help innovative tools to be designed. Additionally, examining the severity of damage across different types of collisions will help determine the most common risks and potential areas for improvement in AV design and traffic policies. These tools and technologies can be integrated into the AV systems to anticipate potential collisions and help further reduce accident rates.

# Chapter 2: Background
Global Development of Autonomous Vehicles (AVs)
Autonomous vehicle (AV) technology has been growing and experiencing rapid advancement globally, with major companies investing heavily in the technology industry for self-driving vehicles. The United States, China, Germany, and Japan are the leading countries in AV development with each country testing, deploying, and researching these technologies. A report by the International Transport Forum (ITF) shows that global AV adoption has steadily increased, with millions of miles tested each year. Over 50 million miles have been driven for testing purposes and commercial applications like robotaxis are being trialed in major cities and an increase of about 3.3 million AV miles from 2021-2023. 
Public perception of AVs remains mixed. Positive perception would vision the potential benefits of self-driving technology which would include improved traffic efficiency and reduced human error. In 2023, Pew Research Center survey found that 68% of Americans feel uncomfortable sharing the road with AVs, primarily due to unpredictable behaviors and liability issues involving AVs. Companies such as Tesla, Waymo, and Cruise have reinforced skepticism and slowed the rate of consumer trust in AV technology. 
A major challenge in AV development is ensuring safety across diverse driving conditions. As AVs rely on sensor technology, machine learning models, and real-time decision-making systems, improving and understanding these conditions is vital. Weather Conditions, road infrastructure, and human behavior will impact AV safety and reliability. 

# AV Landscape in California
Autonomous vehicle (AV) technology has been a growing industry especially within the state of California, where it has positioned itself as the global leader. Innovative companies with a large presence are driving advancement in the industry with top talents being attracted toward California. Major companies such as Waymo, Cruise, and Zoox have established operations within the state, driving a competitive environment in the AV industry. Each company has different solutions but are all focused on enhancing both safety and performances of AV technology. As AV adoption continues to increase, so has the number of vehicles testing and deployment. Between 2021 and 2024, AV miles driven increased by approximately 3.3 million, highlighting the expansion of AV technology. With this rapid growth comes a growing concern over road safety, prompting for stricter and clearer regulations to monitor such new technologies. To ensure public safety and maintain transparency, the California Department of Motor Vehicles (DMV) has mandated that all AV-related collision reports be available to the public. By analysing the collision data, understanding the situation would be crucial and inform future research by providing a data-driven rationale for improving AV safety. 
Problems Faced By AV Developers
Adoption of AV has been faced with several challenges despite the progress over the years. These challenges are important to be addressed to enhance safety and public trust  of AV operational capabilities. 
1.	Limited Understanding of AV collision Risk Factors
A challenge that AV development faces is the lack of understanding of AV collision dynamics. Although AVs are designed to reduce human error and increase efficiency, accidents still occur due to unexpected environmental conditions and sensor failures. It is important that companies have insights into how and why these incidents happen. 
2.	External Factors on AV safety
○	Weather - Rain or foggy conditions can obscure or reduce AV visibility and increase misinterpretation. 
○	Lighting conditions - Can cause challenges in object detection due to the lighting that causes the camera to pick up wrong details.
○	Road Conditions - AVs may struggle in construction zones or pedestrian-heavy areas where unpredictable behavior is common. 
3.	Public Skepticism and Safety Concerns
Many consumers remain wary of AV safety, with a McKinsey report indicating that only one in three consumers would feel comfortable sharing the road with fully autonomous vehicles. Negative media coverage related to these accidents would also further reinforce public doubts and a strong and regulatory policy is important. Safety requirements would be in legal frameworks and ensure clear guidelines. 
Motivation For This Study
The primary motivation for this analysis stems from the critical need to ensure that autonomous vehicles (AVs) can operate safely under a wide range of conditions. It is essential to evaluate the real-world collision data to understand the risks and challenges that come with AV adoption. By identifying key risk factors and situations, companies can develop targeted solutions that improve vehicle safety and reliability. Another aspect of this study is to contribute to public trust and acceptance of AVs. Demonstrating a commitment to continuous improvement would build consumer confidence. A deeper understanding of AV collision will unlock the full potential of AVs and a successful integration into the transportation systems. Thus, this study is focused on descriptive analysis and using predictive modeling to further solidify the analysis  on these conditions and situations. 

# Chapter 3: Data
The data used in this study was obtained from the California Department of Motor Vehicles (DMV). Every collision report is published and uploaded onto their website within 10 days of each incident. The DMV has recorded over 735 collision reports as of August 30, 2024 and organized by year dating back to 2014. These reports are publicly available in PDF format on the DMV website. 

 
PDF Collision Report
A sample of the report is shown above. The report shows each section of the collision report and the cross which indicates which collision details happened to the vehicle. 
For the purpose of this analysis, the reports from 2022 to 2024 were downloaded using a Chrome extension to speed up the process. It is then extracted and compiled into a single CSV file. In each report, there are variables such as the model, type of collision, weather, and area of vehicle damage etc.  After cleaning and preprocessing, the final dataset consisted of 338 rows and 279 columns, representing individual collision incidents with the associated variables. 
Below is a table of the raw data before cleaning and data preparation. 
BuSINESS NAME	DATE OF ACCIDENT	TIME of ACCIDENT	AM	PM	MODEL	MINOR	MODERATE	MOVING
Zoox	3182024	446	FALSE	TRUE	ZOOX SEDAN	TRUE	FALSE	FALSE
Waymo LLC	


5202024
	302	TRUE	FALSE	JAGUAR	TRUE	FALSE	FALSE
WERIDE	3022024	1256	TRUE	FALSE	TOYOTA	FALSE	TRUE	FALSE

Table 1:Raw data 
Note: This is a simplified sample showing key columns before data cleaning. Several binary flags (TRUE/FALSE) were used across many columns.
Key Issues In The Dataset
●	Inconsistent capitalization: Headers like "BuSINESS NAME" and "VEhICLE YEAR" used mixed cases and were generalized across all the columns. 
●	Multiple columns for similar variables: E.g., "Left Rear 1" and "Left Rear 2" needed to be merged into a single "left_rear" column to simplify the dataset for easier analysis.
●	TRUE/FALSE flags: These were one hot encoded and converted to binary 1 (True) and 0 (False) values for easier analysis.
●	Non-standard formatting: Spacing in column names (e.g., "Daylight" vs "Dark with streetlights") was replaced with underscores and lowercase formatting for consistency.
●	Dropped Irrelevant Columns: Columns like “License Plate” and “Vehicle Identification Number” were dropped as they would not be used for analysis. 
Issues in the dataset were identified and the appropriate data type was used and a test for duplicates was performed. 
 After data preparation and cleaning, Table 1 was created and shows the data variables and description of the dataset for easier interpretability. The table presents each variable grouped by its purpose, indicates the corresponding attribute, and includes a summary statistic showing the percentage next to each attribute.
Variables	Description 	Values
Time	Time of collision	AM (39.76%)
PM (60.24%)
Date	Date of collision	Date of accident
2022-2024
AV mode	If it’s in autonomous or disengaged 	Autonomous (61.01%)
Conventional (38.99%)
AV movement	Movement of AV when it collided	Stopped (40.95%), proceeding straight (31.45%), Right turn (4.75%), left turn (4.45%), U turn (0.59%), Backing (5.04%), Slowing/stopping (8.90%), changing lanes (1.48%), Parking (1.48%), Entering Traffic (1.48%), Parked (2.67%), Merging (0.59%), Travelling wrong way (0%), Other1(1.48%)
Object it collided	What the AV collided with	Bicyclist (10.78%), pedestrian (2.94%), undefined (58.82%), hit object (27.45%)
Weather	Weather during the collision	Clear (83.09%), Cloudy (10.98%), Raining (6.23%), Fog/visibility (0.30%)
Lighting	Lighting during the collision	Daylight (64.69%), Dusk/Dawn (2.97%), Dark with streetlights (30.86%)
Roadway Condition	Condition of the road where it collided	No unusual conditions (91.69%), Reduced roadway width (0.89%), obstruction (1.19%), construction area (0.59%), other2 (2.37%)
Surface	Surface of the road where it collided	Dry (89.02%), Wet (10.98%)
Type of collision	Type of collision 	Head On (15.91%), Side swipe (32.95%), Rear end (44.32%), broadside (6.82%), overturned (0%)
Damage area	Where the damage of the AV is	Left Rear (17.27%), Rear Bumper (18.88%), Right Rear (16.87%), Left Rear Passenger (5.02%), Right Rear Passenger (3.21%), Front Driver Side (7.03%), Front Passenger Side (5.62%), Left Front Corner, (10.44%) Right Front Corner (10.04%), Front Bumper (5.62%)
Damage Type	Damage level of the AV. 	unknown_damage(0.3%), none(8%), minor(72.8%), moderate(15.7%), major(3.3%)
Table 2: Data after cleaning (rounded up)
Below is a line graph of a  time series created in Python of the number of monthly accidents of the dataset from January 2022 to August 2024. The number of accidents reported fluctuates throughout the span of these years. There was a consistent high number of AV reports during 2022, ranging between 5-22 and a sharp decline of accidents during the tail end of 2023. Several news events and regulatory changes during this period occurred. 
●	Cruise Suspension: In October 2023, the DMV suspended self-driving car permits following safety concerns and incidents which included a pedestrian collision. This led to Cruise halting its robotaxi operations nationwide. 

 
Figure 1: Number of Monthly Accidents


 
Figure 2: Pie Chart of Damage Distribution
The pie chart above shows the distribution of severity of damage sustained on the AV vehicle collisions. The data highlights the majority of reported AV collisions resulting in minor damages or low-impact outcomes. 
●	Minor damage accounted for 72.8% of cases which aligns with the notion that AVs tend to operate at lower speeds particularly in urban or testing environments. 
●	Moderate damage represents 15.7% of cases which reflect that the vehicle would likely require some repairs but no threat to the occupant safety. 
●	No damage reported in 8% of cases which indicates near misses or very light contact.
●	Major damage, while more serious, occurred 3.3% in the reports. This could be interesting for regulators and developers in understanding the risk factors involved here. 
●	Unknown damage was reported in just 0.3% of reports which would indicate unreported data or incomplete data in the report. 
In conclusion, the dataset has been checked and thoroughly cleaned, making it suitable for further analysis. A sample of the report has been shown with the data extracted into a CSV file and compiled into a raw table. After cleaning the raw data, a summary of the table with key variables and description has been presented to provide an overview of the dataset's structure. Additionally, important variables such as type of collision and damage severity have been visualized using pie charts to offer a clearer understanding of the underlying patterns within the data. 







# Chapter 4: Modeling and Evaluation 
This study employed both predictive modeling and association rule mining (ARM) techniques to better understand patterns and factors contributing to AV collisions. The predictive models identified key variables which influenced damage severity and association rule showed co-occurrences and conditional relationships between specific accident conditions. A focus on minor and moderate damage were used as they had the most significance based on the dataset. 
Association Rule Mining Analysis
The association rule mining was applied and used on the dataset with conditions associated with minor damage. The Apriori algorithm was applied to the dataset using the mlxtend library in Python. This would help discover the antecedents (features) that frequently lead to a minor collision (consequent). As mentioned previously, all the categorical variables have been converted into boolean format which is more suitable for binary encoding and mining and unnecessary columns were dropped. The min_support = 0.05 was used  to keep only items that would appear in 5% of the data to balance performance. The metric of lift was used to measure how much more likely items would occur together instead of chance. 
239 frequent features were found in the dataset and some were notably high. A table below shows the patterns with high support. 

 
Table 3: Frequent Features
Based on the table, the patterns suggest that collisions that occur in the morning, the AV going straight and Right Rear damage on the vehicle was very common. This could be taken a look at more seriously by AV developers on why the right side of the damages are more common. 
The Apirori algorithm was used with a minimum support threshold of 5% to identify the frequent features. The association rules were generated based on the confidence metric with a minimum threshold of 50% as this would focus on predictive strength. The focus on the feature where the consequent “minor damage” was narrowed down. A filter was used to focus on these rules.
●	2-3 antecedent items 
●	Confidence ratio >10%
●	High support and lift values
These filters were used to ensure that the insights remain practical and easier to understand. 2-3 antecedents were used as any more would become overly complex and difficult to interpret and often results in overfitting. The confidence ratio of >10% would help identify stronger rules than average and ensure that only good performing and meaningful rules were retained. A high support and lift values helps with reliable and non-random rules that would have potential for further application. 
 
Table 4: Top Rules of Consequent in Minor Damage
The top 6 rules were identified and shown in the table below in order of highest confidence for minor damage. Based on the rules in the table above, minor damage occurs mostly under conditions such as: 
●	Clear Weather
●	Dry Road Surface
●	Straight-line or stopped movement
●	Rear-end or side-swipe collisions
Although these environmental features are powerful, these weather conditions are the most common weather conditions in California which may mask edge cases. While AVs seem to perform well under these ideal conditions, further testing is required so that the model would have more exposure. 
An interesting observation from the rules generated is the 3rd rule of Autonomous mode + rear_end + stopped in traffic with its high lift value compared to the rest. This suggests that when AVs are in autonomous mode, they are likely to be involved in rear-end collisions, possibly due to slow speeds and controlled environments. The lift values are above average as most cases had above 1.0 but this rule has a 2.87. This  indicates that these conditions have a very strong association likely worth investigating further, strengthening their predictive association. 
The damage for “major” as the consequent was also performed. The Apriori Algorithm was changed to a min support of 0.01 as the rules generated were very minimal. The minimum confidence was also changed to 30%. These were used as the dataset did not have many major outcomes for damage as it is rare in this dataset. 
 
Table 5: Top Rules of Consequent in Major Damage
Above are the rules generated. Only 2 rules were generated as expected as only a few feature combinations met the support and confidence thresholds. When it is dark with streetlights, there is a 30.77% chance of major damage with a strong lift of 10.37. This could be due to the night driving of vehicles which are more likely for a major accident to happen. However, this can also be an outlier due to the nature of the dataset being very small and this result should just be noted instead. 

Predictive Modeling Analysis
Exploring the relationship between the conditions and the severity of AV collisions was further performed by exploring 3 machine learning models. Decision Tree (CART), Logistic Regression, and Naive Bayes. Due to limitations in the available data, these models would be used and highlight any potential correlations that can be used for further analysis in the future. The target variable was simplified into a binary classification. The damage severity was simplified and broken into “0” representing minor or no damage, and “1” representing moderate or major damage. Across the models, several features were identified and were potential influences in the predictor of collision severity. The input features used were “Weather conditions”, “Road Conditions”, “Number of vehicles involved”, and if the vehicle was in “autonomous mode” at the time of collision.  
The dataset was very imbalanced due to the reports involved being mostly involved with minor damages and thus the class distribution was imbalanced. The training of the data was balanced with random undersampling of the majority damage class. Undersampling was used instead of oversampling due to the smaller dataset size (338 observations after cleaning) and was at risk of overfitting. This was in favor of a simpler and cleaner approach in the small dataset used and provided a straightforward method. The models were then trained on this balanced dataset and evaluated with a split into a 70% training set and a 30% testing set. Performance was assessed and evaluated by using the metrics of accuracy, precision, recall, and F1-score. 
Decision Tree (CART)
The best performing model was the decision tree, which achieved an accuracy of 77.5%. By using the grid_search with 5-fold cross validation, the model would evaluate the performance and ensure the results are reliable and not overly reliant on the training/testing split. The best parameters were identified as max_depth 3, min_samples_leaf = 2, and min_samples_split = 2. The class 0 (minor damage) was predicted with high precision (0.82) and high recall (0.93) indicating a strong performance in this class. However, the recall for class 1 (moderate/major damage) had low recall (0.11) and precision (0.25), which revealed the imbalance issue in the dataset. 
 
Table 6: CART Results
The feature importance was also identified with weather conditions being the most influential followed by number of vehicles involved, road conditions, and autonomous mode. 
 
Table 7: Feature Importance of CART
Logistic Regression
Logistic regression model was evaluated with both before and after hyperparameter tuning. Before tuning, the model achieved an accuracy of 64.7% while the tuned parameter achieved 66.7%. The random state of 42, ensured reproducibility and the model was then fit on the balanced training data after undersampling. A hyperparameter tuning with grid search was performed and “C” which controls the regularization strength and “solver” optimized the algorithm for solving the logistic regression.The logistic regression was then trained using the optimal parameters found and evaluated and compared against the untuned version.  C = 0.1 and liblinear solver was the best configuration and a slight performance increase was seen. Despite the hyperparameter tuning, the model performed similarly to the decision tree where it performed better on the majority class of minor damage. The performance of the logistic regression model is shown below.
 
Table 8: Logistic Regression Results
The feature importance for logistic regression is shown in the table below. The most influential factor that was found was the weather condition which was similar to the decision tree. It then showed autonomous mode and number of vehicles had a slight negative relationship with the target variable which implied a weak association which was interesting. .  
Table 9: Feature Importance for Logistic Regression
Naive Bayes
The Naive Bayes classifier achieved an accuracy of 64.7% and was similar to the logistic regression before its hypertuning. This was expected as it was limited due to the assumption of feature independence.This dataset likely had conditions where weather or road surface may often be interrelated which affected the performance of the model. 
 
Table 10: Naive Bayes Results
It also does not provide the feature importance unlike the other models as it is a probabilistic model that makes strong independent assumptions. Naive Bayes calculates the features independently and thus does not evaluate or rank feature importance. Overall, the model still provided consistent findings on the environmental conditions that are the most important predictors of collision. 
In conclusion, the models used showed several insights that can be considered for future use regarding factors and patterns of AV collisions. The application of both association rule mining and predictive modeling helped uncover features that were co-occuring conditions in the dataset and few predictive features influencing the outcome of damage severity. Although the models had reasonable accuracy, it continued to struggle with identifying the minority class even after balancing the dataset. The “major” outcome was also very rare in the dataset and the modeling techniques struggled in identifying a pattern or trends which showcased the limitation with this dataset as major damages in real-world AV data is rare. Despite the limitation, the significance of weather conditions, road conditions and operational conditions offered valuable results. 










# Chapter 5: Recommendation and Conclusion 
This study analyzed the traffic collision data from the DMV involving autonomous vehicles from California. With the rise of AV adoption, it is important for engineers and scientists to continue to enhance the public trust of using such new technology.  An exploration of the dataset was performed as the project aimed to uncover insights into how AVs operate under different conditions and what factors were the most associated with the damage of the vehicle. Doing a descriptive analysis and predictive modeling techniques to add to the study was done for future opportunities. 
Observations and Insights
Based on the exploratory analysis done, it was found that the majority of the damage collision was minor damages. This was then explored further using association rule mining and predictive modeling techniques. The top feature importance was then identified and explored with each of the models. 
For association rule mining, minor damage frequently appeared under clear weather, dry roads and straight line movement. This could suggest that AVs are generally safe under certain conditions but would need further testing in more complex situations. Another insight found in the data was the recurrence of right-sided damage, which could point to the sensors at the right side being less effective and can be investigated further. Predictive modeling also further reinforced the observations found with weather conditions, road conditions, and number of vehicles involved were identified to be influencing the damage severity of the vehicle. The CART model performed the best overall with its highest accuracy. However, all the models struggled in identifying major collisions due to the highly imbalanced data due to 72.7% of the dataset having minor collisions. 
Limitations of the study
There were few factors in the dataset that hindered the overall performance of the models. A limited dataset with only 338 records was a major limitation and the models struggled to perform with rare outcomes like the major collisions. The class imbalance was also an issue even with undersampling techniques with the recall of major collisions struggling to perform. The lack of more detailed information like speed of the vehicle and more data to work with would have further improved the accuracy and overall study. The model Naive Bayes performed poorly due to this as it relied on independent assumptions and likely oversimplified the interactions of the features. 
Improvements in the future
Improvements for this study can include a larger dataset. This would help with the class imbalance issue of the data and reveal more key trends and patterns. As adoption of AV rises, this would have a clearer picture on the conditions and situations and more data could be used for further analysis. Including more variables in the future like speed of the car would also help determine the conditions and provide more insights. By evaluating the insights from this study, it can be integrated into real-world AV systems and gain the trust of the public. 
In conclusion, while this study has provided insights and analysis on the AV vehicle industry, further data and analysis can be collected and researched on to deliver more substantial insights to the public. Researchers could use the insights found and refine their systems and improve which in turn would enhance AV adoption by the public. 

# References
Novak, M. (2023, March 2). 68% of Americans afraid of self-driving cars, up from 55% in 2022. Forbes. https://www.forbes.com/sites/mattnovak/2023/03/02/68-of-americans-afraid-of-self-driving-cars-up-from-55-in-2022/

The Robot Report. (2023). Autonomous vehicles drove more than 9M miles in California in 2023. https://www.therobotreport.com/autonomous-vehicles-drove-more-than-9m-miles-in-california-in-2023/

California Department of Motor Vehicles. (2024). Autonomous vehicle collision reports. https://www.dmv.ca.gov/portal/vehicle-industry-services/autonomous-vehicles/autonomous-vehicle-collision-reports/

International Transport Forum. (2023). Preparing infrastructure for automated vehicles. OECD Publishing. https://www.itf-oecd.org/sites/default/files/docs/preparing-infrastructure-automated-vehicles.pdf
