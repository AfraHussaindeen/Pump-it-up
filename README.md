# Pump it Up: Data Mining the Water Table

## Challenge Summary
![Capture](https://user-images.githubusercontent.com/47135592/133779220-3ccdc9c5-b3ce-49d7-aad8-c1c33a99a716.PNG)
### Can you predict which water pumps are faulty?

Using data from Taarifa and the Tanzanian Ministry of Water, can you predict which pumps are functional, which need some repairs, and which don't work at all? This is an intermediate-level practice competition. Predict one of these three classes based on a number of variables about what kind of pump is operating, when it was installed, and how it is managed. A smart understanding of which waterpoints will fail can improve maintenance operations and ensure that clean, potable water is available to communities across Tanzania.

## Dataset 
### Features in the dataset
* ```amount_tsh``` - Total static head (amount water available to waterpoint)
* ```date_recorded``` - The date the row was entered
* ```funder``` - Who funded the well
* ```gps_height``` - Altitude of the well
* ```installer``` - Organization that installed the well
* ```longitude``` - GPS coordinate
* ```latitude``` - GPS coordinate
* ```wpt_name``` - Name of the waterpoint if there is one
* ```num_private``` 
* ```basin``` - Geographic water basin
* ```subvillage``` - Geographic location
* ```region``` - Geographic location
* ```region_code``` - Geographic location (coded)
* ```district_code``` - Geographic location (coded)
* ```lga``` - Geographic location
* ```ward``` - Geographic location
* ```population``` - Population around the well
* ```public_meeting``` - True/False
* ```recorded_by``` - Group entering this row of data
* ```scheme_management``` - Who operates the waterpoint
* ```scheme_name``` - Who operates the waterpoint
* ```permit``` - If the waterpoint is permitted
* ```construction_year``` - Year the waterpoint was constructed
* ```extraction_type``` - The kind of extraction the waterpoint uses
* ```extraction_type_group``` - The kind of extraction the waterpoint uses
* ```extraction_type_class``` - The kind of extraction the waterpoint uses
* ```management``` - How the waterpoint is managed
* ```management_group``` - How the waterpoint is managed
* ```payment``` - What the water costs
* ```payment_type``` - What the water costs
* ```water_quality``` - The quality of the water
* ```quality_group``` - The quality of the water
* ```quantity``` - The quantity of water
* ```quantity_group``` - The quantity of water
* ```source``` - The source of the water
* ```source_type``` - The source of the water
* ```source_class``` - The source of the water
* ```waterpoint_type``` - The kind of waterpoint
* ```waterpoint_type_group``` - The kind of waterpoint

### Labels in the dataset
* ```functional``` - the waterpoint is operational and there are no repairs needed
* ```functional needs repair``` - the waterpoint is operational, but needs repairs
* ```non functional``` - the waterpoint is not operational

## Data Preprocessing 

### Data Cleaning

Here the features with missing values greater than 40% were removed and a common transformation in statistical analysis with grouped data was used to replace the missing data of the rest of the features. Moreover, unique values in each features were examined manually & the impossible values encountered were updated using groupby + transform method. Furthermore, the duplicate features were also removed.


### Feature Engineering 

New features were created using mathematical transformations as well using general norms.
* Example : 
    - ```population_log``` feature was created by performing log transformation on skewed ```population``` feature.
    -  ```season``` feature was created by taking into account the month the data was recorded.


### Feature encoding and normalization

For encoding the categorical features, techniques like One-hot encoding and Label-encoding were used. 

The performance of different models when adapting feature normalization were also experimented. From the experiment results, it was noticed that the feature normalization tends to reduce the performance when used with models like RandomForest, XGBoost. Therefore, for the final version, feature normalization was not adapted.


### Feature Selection

For selecting the most significant set of features, the feature importance with **RandomForest** model was used.
Following diagram shows the top 15 features.

![Capture](https://user-images.githubusercontent.com/47135592/133787081-8c64292c-85d3-495f-8081-99cec085c528.PNG)


## Models

Models such as **XGBoost**, **RandomFoorest** were experimented with the dataset. Apart from that an ensemble model - **Stacking classifier** was also experimented.

Out of all the models, **RandomForest** outperformed the rest. 

## Proof of submission

![Capture](https://user-images.githubusercontent.com/47135592/133778709-03a45e8b-798b-4278-960c-7a829c6cbc29.PNG)
![Capture](https://user-images.githubusercontent.com/47135592/133778862-c7f8ad57-2c69-4f78-a4ef-ae26ab8f49a6.PNG)
