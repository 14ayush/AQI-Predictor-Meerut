# AQI_Predictor-for-Meerut-City


## **Air Quality Prediction Using Machine Learning (2016–2022)**

**An End-to-End Project Featuring Data Scraping, Cleaning, Visualization, Modeling, and Deployment**

In this project, I developed a complete machine learning pipeline to analyze and predict air quality over a six-year period (2016–2022). The goal was to build a robust end-to-end system that collects raw data from online sources, processes and transforms it, applies machine learning algorithms, and ultimately provides an interactive interface for real-time prediction using Streamlit.

---

### **1. Data Collection (Web Scraping)**

The project began with collecting data from the **Tutiempo** website, which provides historical weather data such as temperature, humidity, and wind speed. Since the site displays data in tabular form for each hour of every day, I used Python’s **BeautifulSoup** library to automate the scraping process.

#### Key steps:

* Dynamically constructed URLs for each month and year from 2016 to 2022.
* Extracted hourly weather parameters from HTML tables.
* Parsed and structured the scraped data into  **CSV files** .
* Saved files locally to ensure reproducibility and efficient access.

This process resulted in a comprehensive dataset of hourly environmental data, totaling over **50,000** records.

---

### **2. AQI Data Integration**

To provide a reliable target for prediction, I collected **Air Quality Index (AQI)** values from a separate trusted source. AQI is a standard measure of air pollution, making it an ideal output variable.

Steps involved:

* Scraped AQI data using similar methods.
* Merged it with the weather dataset based on date and time.
* Addressed formatting issues and resolved inconsistencies due to missing timestamps or mismatches.

---

### **3. Data Transformation: Hourly to Daily Aggregation**

AQI is typically reported on a daily basis, so I converted the hourly data into **daily averages** using  **pandas** . This involved:

* Grouping data by date.
* Calculating the **mean** for each parameter.
* Creating a simplified dataset where each row represents a day.

This not only matched AQI's format but also helped smooth out random hourly fluctuations.

---

### **4. Data Cleaning and Preprocessing**

After merging datasets, I identified **missing values** in multiple columns. Instead of dropping rows (which would shrink the dataset), I used a more effective strategy:

* Identified null counts and calculated null-to-non-null ratios.
* Used **mean imputation** to fill missing values.
* Verified that the final dataset was complete and consistent.

This approach ensured we preserved valuable data while improving reliability.

---

### **5. Exploratory Data Analysis (EDA)**

Before modeling, I explored the data to identify trends and relationships.

Tools used:

* **Matplotlib** and **Seaborn** for visualizations.
* **Line plots** to show seasonal AQI changes.
* **Heatmaps** to visualize feature correlations.
* **Box plots** to examine outliers and distribution.

Key insights:

* AQI levels were consistently higher in winter.
* Some features, such as temperature and humidity, showed mild correlation with AQI.

---

### **6. Machine Learning Model Development**

I tested multiple regression models to predict AQI using the cleaned and transformed data. An **80/20** split was used for training and testing.

Models and results:

* **Linear Regression** : ~50% accuracy.
* **Ridge Regression** : Improved slightly to ~55%.
* **Decision Tree Regressor** : Captured non-linear relationships, ~65% accuracy.
* **Random Forest Regressor** : Best base performance, ~75%.

Based on its performance and robustness, I selected **Random Forest** for final deployment.

---

### **7. Hyperparameter Tuning**

To enhance the model’s performance, I tuned the Random Forest using  **GridSearchCV** . Parameters optimized included:

* `n_estimators` (number of trees)
* `max_depth` (maximum depth of each tree)
* `min_samples_split` (minimum samples to split a node)

This process improved the final model’s accuracy to  **80%** , making it suitable for real-world use.

---

### **8. Model Serialization with Pickle**

To enable easy reuse and deployment, I serialized the trained model using Python’s **Pickle** module. This allowed the model to be saved as a `.pkl` file and loaded for instant predictions without retraining.

---

### **9. Streamlit Frontend Deployment**

To complete the end-to-end pipeline, I built an interactive web app using  **Streamlit** . This provided a user-friendly interface for AQI prediction.

Features:

* Accepts user input for daily weather parameters (temperature, humidity, wind speed, etc.).
* Loads the trained model from the Pickle file in real time.
* Displays the **predicted AQI value** with a basic interpretation (e.g., Good, Moderate, Poor).
* Simple UI with clean layout and quick response time.

This step made the model accessible to non-technical users and demonstrated real-world applicability.

---

### **10. Key Takeaways and Challenges**

✅  **Achievements** :

* Built a **modular and scalable** system with well-defined stages: scraping, preprocessing, modeling, and deployment.
* Improved model accuracy from **50% to 80%** through experimentation and tuning.
* Integrated a wide range of skills from  **data engineering to full-stack deployment** .

⚠️  **Challenges** :

* Handling year-wise scraping across thousands of URLs required robust error handling.
* Merging datasets from different sources introduced formatting and consistency challenges.
* Streamlit UI needed optimization for efficient real-time interaction.

---

### **Conclusion**

This project showcases a fully developed machine learning solution—from data acquisition to deployment. It addresses a pressing environmental issue and demonstrates the power of  **data science and modular Python programming** . By integrating scraping, analysis, modeling, and deployment, I built a system that’s both functional and extensible. This approach can easily be adapted to other environmental or public health domains in future work.
