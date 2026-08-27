# Applied Data Science Capstone Project

**Author: Gaurang Vaidya**

**Date: 28 August 2026**

**GitHub Repository:** [https://github.com/GaurangVaidya29/IBM-Applied-Data-Science-Capstone-Gaurang](https://github.com/GaurangVaidya29/IBM-Applied-Data-Science-Capstone-Gaurang)

**Capstone Presentation:** [DS-Capstone-Coursera.pdf](DS-Capstone-Coursera.pdf)

---

## Overview
Welcome to the Applied Data Science Capstone Project, where we embark on a journey to predict the successful landing of the Falcon 9 first stage. SpaceX, known for revolutionizing space travel, advertises Falcon 9 rocket launches at a competitive cost of 62 million dollars, compared to other providers' costs upwards of 165 million dollars. This significant cost-saving is largely attributed to SpaceX's ability to reuse the first stage of the rocket. By accurately predicting the landing success of the first stage, we can better estimate the launch costs, providing valuable insights for companies bidding against SpaceX for rocket launches.

## Objectives
The project is structured into several comprehensive modules, each designed to build on the previous one, culminating in a robust predictive model. Below is a detailed description of the tasks and goals achieved in each module:

### 1. Request to the SpaceX API and Data Wrangling
- **Data Collection**: We initiated our project by making a GET request to the SpaceX API to gather historical launch data. This data included various parameters essential for our analysis.
- **Data Cleaning**: After obtaining the data, we performed cleaning and formatting to ensure consistency, removing any anomalies or missing values, and preparing it for analysis.
- **Notebook**: [1. jupyter-labs-spacex-data-collection-api.ipynb](1.%20jupyter-labs-spacex-data-collection-api.ipynb)

### 2. Web Scraping Falcon 9 Launch Records
- **Web Scraping with BeautifulSoup**: We extracted Falcon 9 launch records from Wikipedia using BeautifulSoup, a powerful Python library for web scraping.
- **Data Parsing**: The extracted HTML table was parsed and converted into a Pandas DataFrame, facilitating easy manipulation and analysis of the data.
- **Notebook**: [2. jupyter-labs-webscraping.ipynb](2.%20jupyter-labs-webscraping.ipynb)

### 3. Exploratory Data Analysis (EDA) and Training Labels
- **Exploratory Data Analysis**: We conducted extensive EDA using visualization tools like Matplotlib and Seaborn to uncover patterns and correlations in the data.
- **Training Labels**: Identified and labeled the training data, crucial for the subsequent machine learning models.
- **Notebook**: [3. labs-jupyter-spacex-Data wrangling.ipynb](3.%20labs-jupyter-spacex-Data%20wrangling.ipynb)

### 4. Database Integration & SQL Analysis
- **Loading Data into SQLite**: We loaded the dataset into an SQLite database (my_data1.db) to leverage SQL for structured querying and analysis.
- **SQL Queries Executed**:
  - All unique launch site names
  - Launch sites beginning with 'CCA'
  - Total payload mass carried by NASA (CRS) — **45,596 kg**
  - Average payload mass for F9 v1.1 booster — **2,928.4 kg**
  - First successful ground pad landing date — **2015-12-22**
  - Boosters with successful drone ship landings and payloads between 4000–6000 kg
  - Total successful vs. failure mission outcomes — **98 successes**
  - Boosters carrying maximum payload (15,600 kg)
  - 2015 monthly launch records
  - Ranked landing outcomes between 2010-06-04 and 2017-03-20
- **Notebook**: [4. jupyter-labs-eda-sql-coursera_sqllite.ipynb](4.%20jupyter-labs-eda-sql-coursera_sqllite.ipynb)

### 5. Feature Engineering and EDA Visualization
- **Feature Engineering**: Created new features from the existing data to enhance the predictive power of our models.
- **EDA Visualizations**:
  - Flight Number vs. Launch Site scatter plot
  - Payload vs. Launch Site scatter plot
  - Success rate by orbit type bar chart
  - Flight Number vs. Orbit Type scatter plot
  - Payload vs. Orbit Type scatter plot
  - Launch success yearly trend line chart
- **Notebook**: [5. jupyter-labs-eda-dataviz.ipynb](5.%20jupyter-labs-eda-dataviz.ipynb)

### 6. Interactive Visual Analytics with Folium
- **Folium Maps Created**:
  - Task 1: All launch sites marked on an interactive map
  - Task 2: Success/failure launches color-coded per site using clustered markers
  - Task 3: Distance calculations from launch sites to nearest coastline, city, railway, and highway
- **Key Findings**:
  - VAFB SLC-4E (latitude 34.63°) is furthest from the equator
  - All launch sites are within close proximity to the coastline
  - CCAFS SLC-40 is approximately 0.51 km from the nearest coastline
- **Notebook**: [6. lab_jupyter_launch_site_location.ipynb](6.%20lab_jupyter_launch_site_location.ipynb)

### 7. Interactive Visual Analytics with Plotly Dash
- **Dashboard Components**:
  - Pie chart showing success counts per launch site (All Sites view)
  - Pie chart for the site with highest success ratio (KSC LC-39A: 76.9% success)
  - Scatter plot for Payload vs. Mission Outcome filtered by launch site and payload range
- **Key Dashboard Findings**:
  - KSC LC-39A has the highest success rate at 41.7% of total successful launches
  - Booster version "FT" shows consistently high success across all payload ranges
- **Script**: [spacex_dash_app.py](spacex_dash_app.py)
- **Screenshot**: [spacex_dash_app_screenshot.png](spacex_dash_app_screenshot.png)

### 8. Machine Learning Models and Hyperparameter Tuning
- **Data Standardization and Splitting**: Standardized the dataset and split it into training and test sets to ensure robust model evaluation.
- **Models Evaluated**:
  - Logistic Regression
  - Support Vector Machine (SVM)
  - Decision Tree Classifier
  - K-Nearest Neighbors (KNN)
- **Hyperparameter Tuning**: Performed hyperparameter tuning using GridSearchCV for all models.
- **Model Evaluation**: Evaluated each model's performance on the test data to identify the best-performing model.
- **Notebook**: [7. SpaceX_Machine_Learning_Prediction_Part_5.jupyterlite.ipynb](7.%20SpaceX_Machine_Learning_Prediction_Part_5.jupyterlite.ipynb)

## Results

| Model | Test Accuracy |
|-------|--------------|
| Decision Tree Classifier | **94.44%** ✅ Best |
| Support Vector Machine (SVM) | 83.33% |
| K-Nearest Neighbors (KNN) | 83.33% |
| Logistic Regression | 83.33% |

### Decision Tree Confusion Matrix
- **True Positives**: High — model correctly identifies successful landings
- **False Negatives**: 0 — the model never misses a successful landing
- **False Positives**: 1 — minor over-prediction of success (acceptable in practice)
- **Overall Accuracy**: 94.44%

## Key Innovative Insights

1. **Launch Site Reliability**: CCAFS LC-40 shows the highest overall success rate at 43.7% of all successful launches, suggesting optimal operational conditions at this facility.

2. **Booster Version Performance**: Booster version "FT" demonstrates consistently high success rates across all payload masses, making it the most reliable booster version for future missions.

3. **Payload Mass is NOT a Primary Factor**: No clear correlation was found between higher payload mass and lower success rates, indicating that launch site conditions and booster version are more dominant success factors.

4. **Orbit-Specific Reliability**: VLEO, ES-L1, GEO, HEO, and SSO orbits have achieved 100% success rates, while GTO shows significantly lower success rates due to mission complexity.

5. **Temporal Learning Effect**: Launch success rate improved dramatically from ~50% in 2013 to over 80% by 2020, demonstrating SpaceX's iterative engineering improvements over time.

6. **Geographic Proximity**: All SpaceX launch sites are within close proximity to coastlines, which is strategically important for over-water flight paths and safe stage recovery operations.

## Conclusion
Through meticulous data analysis, feature engineering, and model tuning, this project successfully predicted the landing success of the Falcon 9 first stage. The Decision Tree classifier emerged as the best model with 94.44% accuracy. The insights gained are invaluable for estimating launch costs and aiding companies in their competitive bids against SpaceX.

## Repository Structure

```
IBM-Applied-Data-Science-Capstone-Gaurang/
├── 1. jupyter-labs-spacex-data-collection-api.ipynb    # SpaceX API Data Collection
├── 2. jupyter-labs-webscraping.ipynb                   # Wikipedia Web Scraping
├── 3. labs-jupyter-spacex-Data wrangling.ipynb         # Data Wrangling
├── 4. jupyter-labs-eda-sql-coursera_sqllite.ipynb      # SQL EDA with SQLite
├── 5. jupyter-labs-eda-dataviz.ipynb                   # EDA with Data Visualization
├── 6. lab_jupyter_launch_site_location.ipynb           # Folium Interactive Maps
├── 7. SpaceX_Machine_Learning_Prediction_Part_5.jupyterlite.ipynb  # ML Models
├── spacex_dash_app.py                                  # Plotly Dash Application
├── spacex_dash_app_screenshot.png                      # Dashboard Screenshot
├── spacex_launch_geo.csv                               # Launch Site Geographic Data
├── spacex_launch_dash.csv                              # Dashboard Dataset
├── my_data1.db                                         # SQLite Database
├── DS-Capstone-Coursera.pdf                            # Final Presentation (PDF)
└── README.md                                           # Project Documentation
```

## How to Run the Dash App

```bash
# Install dependencies
pip install dash plotly pandas

# Run the application
python spacex_dash_app.py

# Open browser at http://localhost:8060
```

## Acknowledgments
- **IBM**: For providing the course and learning materials.
- **Coursera**: For the platform to access and complete the course.
- **SpaceX**: For making launch data publicly available via their API.

---

Explore this repository to dive into the complete workflow, methodologies, and innovative techniques employed in this capstone project. Whether you're a data science enthusiast, a space exploration aficionado, or a professional seeking insights into predictive modeling, this project offers something for everyone.
