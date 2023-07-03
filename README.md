![](https://github.com/chatala1/IBM-Capstone/blob/master/spacex.png)
# Winning Space Race with Data Science
### IBM-Data-Science-Capstone-SpaceX

## Introduction
SpaceX is a leader in the space industry, and strives to make space travel accessible and affordable. SpaceX's growing list of achievements include sending spacecraft to the ISS, unmanned missions, satellite launches and more. The reuse of the first stage ("S1") of its Falcon 9 rocket, allow for a much more fiscally efficient rocket. Launches are inexpensive compared with the costs of other manufacturers who are not able to reuse S1.

## Objective(s)

By determining if S1 will launch, we can roughly estimate the price of the launch. This was achieved with public data and machine learning models to predict whether SpaceX could reuse S1 on a given launch.


## Deliverables

**Notebooks**
* [00 Report Presentation]()
* [01 Data Collection](https://github.com/chatala1/IBM-Capstone/blob/fe84a87136220ba1265ca73e744d2e304d99f964/01_spacex_data_collection_api.ipynb)
* [02 Web Scraping](https://github.com/chatala1/IBM-Capstone/blob/8ce1cd23972a079486e147ee8cc7c2ab914622e9/02_spacex_webscraping.ipynb)
* [03 Data Wrangling]()
* [04 EDA SQL]()
* [05 EDA Data Visualization]()
* [06 Interactive Visual Analytics - Folium]()
* [07 Interactive Visual Analytics - Plotly (Python)]()
* [08 Predictive Analytics]()


### Exploration
* How do payload mass, launch site location, the number of flights, and orbits; affect Stage1 landing(s)?
* What is the rate of successful landings over time?
* What is the best predictive model for successful landing (use binary classification)?

### Executive Summary
Research attempts to identify indicators for a successful rocket landing. The following methodologies where used:
* **Collect** data using SpaceX REST API and web scraping techniques
* **Wrangle** data to create success/fail outcome variable
* **Explore** data with data visualization techniques, considering the following factors: payload, launch site, flight number and yearly trend
* **Analyze** the data with SQL, calculating the following statistics: total payload, payload range for successful launches, and total # of successful and failed outcomes
* **Explore** launch site success rates and proximity to geographical markers
* **Visualize** the launch sites with the most success and successful payload ranges
* **Build Models** to predict landing outcomes using logistic regression, support vector machine (SVM), decision tree and K-nearest neighbor (KNN)


## Results

### Exploratory Data Analysis:
* Launch success has improved over time
* KSC LC-39A has the highest success rate among landing sites
* Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate

### Visualization / Analytics:
* Most launch sites are near the equator, and all are in coastal areas.

### Predictive Analytics
* All models performed similarly on the test set. The decision tree model slightly outperformed when looking at .best_score_

## Methodology

### Data Collection - API
* **Request data** from SpaceX API (rocket launch data)
* **Decode response** using .json() and convert to a dataframe using .json_normalize()
* **Request information** about the launches from SpaceX API using custom functions
* **Create dictionary** from the data
* **Create dataframe** from the dictionary
* **Filter dataframe** to contain only Falcon 9 launches
* **Replace missing values** of Payload Mass with calculated .mean()
* **Export data** to csv file

### Data Collection - Web Scraping
* **Request data** (Falcon 9 launch data) from Wikipedia
* **Create BeautifulSoup object** from HTML response
* **Extract column names** from HTML table header
* **Collect data** from parsing HTML tables
* **Create dictionary** from the data
* **Create dataframe** from the dictionary
* **Export data** to csv file

### Data Wrangling
* **Convert outcomes** into 1 for a successful landing and 0 for an unsuccessful landing

### EDA with Visualization
* **Create charts** to analyze relationships and show comparisons

### EDA with SQL
* **Query the data** to understand more about the data

### Maps with Folium
* **Create maps** to visualize launch sites, view launch outcomes and see distance to proximities

### Dashboard with Plotly Dash
* **Create dashboard**
* Pie chart showing successful launches
* Scatter chart showing Payload Mass vs. Success Rate by Booster Version

### Predictive Analytics
* **Create** NumPy array from the Class column
* **Standardize** the data with StandardScaler. Fit and transform the data.
* **Split** the data using train_test_split
* **Create** a GridSearchCV object with cv=10 for parameter optimization
* **Apply** GridSearchCV on different algorithms: logistic regression (LogisticRegression()), support vector machine (SVC()), decision tree (DecisionTreeClassifier()), K-Nearest Neighbor (KNeighborsClassifier())
* **Calculate** accuracy on the test data using .score() for all models
* **Assess** the confusion matrix for all models
* **Identify** the best model using Jaccard_Score, F1_Score and Accuracy

## Conclusion
* **Model Performance:** The models performed similarly on the test set with the decision tree model slightly outperforming
* **Equator:** Most of the launch sites are near the equator for an additional natural boost - due to the rotational speed of earth - which helps save the cost of putting in extra fuel and boosters
* **Coast:** All the launch sites are close to the coast
* **Launch Success:** Increases over time
* **KSC LC-39A:** Has the highest success rate among launch sites. Has a 100% success rate for launches less than 5,500 kg 
* **Orbits:** ES-L1, GEO, HEO, and SSO have a 100% success rate
* **Payload Mass:** Across all launch sites, the higher the payload mass (kg), the higher the success rate

### Additional Things to Consider
* **Dataset:** A larger dataset will help build on the predictive analytics results to help understand if the findings can be generalizable to a larger data set
* **Feature Analysis / PCA:** Additional feature analysis or principal component analysis should be conducted to see if it can help improve accuracy
* **XGBoost:** Is a powerful model which was not utilized in this study. It would be interesting to see if it outperforms the other classification models
