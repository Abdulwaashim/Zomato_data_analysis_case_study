# Zomato Data Analysis Case Study

This repository contains an in-depth case study of Zomato's restaurant data. The project demonstrates data analysis techniques to extract insights from the dataset and provides actionable findings for stakeholders in the food and hospitality industry.

## Project Overview

The goal of this project is to explore, analyze, and visualize Zomato's data to uncover trends and patterns that can guide business decisions. This analysis includes aspects such as restaurant ratings, online ordering behavior, and location-based insights.

## Activities and Analysis

### 1. Data Cleaning

- **Objective**: Prepare the dataset for analysis by handling missing values and inconsistencies.
- **Steps**:
  - Removed null or duplicate values.
  - Standardized data formats for better analysis.
- **Code Snippet**:
  ```python
  # Drop duplicate and null values
  data = data.drop_duplicates()
  data = data.dropna()
  ```

### 2. Average Rating Calculation

- **Objective**: Identify restaurants with the highest average ratings.
- **Insight**: Top restaurants have the highest number of average ratings.
- **Code Snippet**:
  ```python
  # Calculate average ratings
  average_ratings = data.groupby('Restaurant')['Aggregate rating'].mean().sort_values(ascending=False)

  # Visualization
  plt.figure(figsize=(15, 8))
  sns.barplot(x=Rating[0:20].Rating, y=Rating[0:20].index, orient="h", color="red")
  plt.show()
  ```
  ![average_rating](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/Avg_rating.png)

### 3. Distribution of Ratings

- **Objective**: Understand the distribution of ratings across all restaurants.
- **Visualization**: Created histograms to display the frequency of ratings.
- **Code Snippet**:
  ```python
  # Plot histogram of ratings
  plt.hist(data['Aggregate rating'], bins=20, color='skyblue', edgecolor='black')
  plt.title('Distribution of Ratings')
  plt.xlabel('Ratings')
  plt.ylabel('Frequency')
  plt.show()
  ```
  ![Distribution_of_ratings](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/distribution_of_Ratings.png)

### 4. Top Restaurant Chains

- **Objective**: Identify the most popular restaurant chains.
- **Insight**: 'Cafe Coffee Day' is the leading chain with the highest number of outlets.
- **Code Snippet**:
  ```python
  # Count restaurants by chain
  top_chains = data['Restaurant Name'].value_counts().head(10)

  # Visualization
  plt.figure(figsize=(10,7),dpi=110)
  sns.barplot(x=chains,y=chains.index,palette='deep')
  plt.xlabel("no. of outlets")
  plt.show()
  ```
  ![Top_restaurant_chains](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/Top_restaurant_chains.jpg)

### 5. Online Orders Analysis

- **Objective**: Determine the percentage of restaurants accepting online orders.
- **Insight**: 74.3% of restaurants accept online orders.
- **Code Snippet**:
  ```python
  # Calculate percentage of restaurants accepting online orders
  online_order_percentage = data['Online order'].value_counts(normalize=True) * 100
  labels = ['Yes','No']
  plt.pie(x,labels=labels,explode=[0.0,0.1],autopct='%1.1f%%')
  plt.show()
  ```
  ![Online_orders](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/restaurant_accept_online_orders.png)

### 6. Table Booking Analysis

- **Objective**: Analyze the availability of table bookings in restaurants.
- **Insight**: Around 85.4% of restaurants offer table bookings.
- **Code Snippet**:
  ```python
  # Calculate percentage of restaurants offering table bookings
  table_booking_percentage = data['Table booking'].value_counts(normalize=True) * 100
  x=data.Table_booking.value_counts()
  labels = ['Yes','No']
  plt.pie(x,labels=labels,explode=[0.0,0.1],autopct='%1.1f%%')
  plt.show()
  ```
  ![Table_booking](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/retaurant_have_table_booking.png)

### 7. Voting Analysis

- **Objective**: Find the restaurants with the highest and lowest votes.
- **Findings**:
  - **Highest Votes**: Identified restaurants with the most votes.
  - **Lowest Votes**: Highlighted restaurants with the least votes.
- **Code Snippet**:
  ```python
  # Analyze votes
  highest_votes = data.nlargest(1, 'Votes')
  lowest_votes = data.nsmallest(1, 'Votes')

  # Visualization
  plt.figure(figsize=(15,12),dpi=100)
  plt.barh(high_votes.index,high_votes['Votes'])
  plt.show()
  ```
  ![Vote_analysis](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/based%20on%20votes.jpg)

### 8. Location Analysis

- **Objective**: Determine locations with the highest number of restaurants.
- **Visualization**: Bar plots to showcase restaurant distribution across locations.
- **Code Snippet**:
  ```python
  # Plot number of restaurants by location
  location_counts = data['Location'].value_counts()
  location_counts.head(10).plot(kind='bar', color='coral')
  plt.title('Top Locations by Number of Restaurants')
  plt.xlabel('Location')
  plt.ylabel('Number of Restaurants')
  plt.show()
  ```
  ![Location_based_analysis](https://github.com/Abdulwaashim/Zomato_data_analysis_case_study/blob/main/img/Location_analysis.png)

## Tools and Technologies

- **Language**: Python
- **Libraries**: Pandas, NumPy, Matplotlib, Seaborn
- **Notebook**: Jupyter Notebook


## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/Abdulwaashim/Zomato_data_analysis_case_study.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the Jupyter Notebook to explore the analysis:
   ```bash
   jupyter notebook Zomato_da_case_study.ipynb
   ```

## Key Insights

- **Online Ordering Trends**: Most restaurants (74.3%) accept online orders, indicating a shift toward digital convenience.
- **Table Booking Preferences**: A majority (85.4%) of restaurants provide table booking options, enhancing customer experience.
- **Top Restaurants**: Some restaurants stand out with the highest votes and ratings.
- **Location-Based Analysis**: Certain locations dominate in terms of restaurant density.

## Conclusion

This case study highlights the importance of data in understanding customer behavior and optimizing restaurant operations. The insights derived can help businesses improve their offerings and better meet customer expectations.

## Future Work

- Expand the dataset to include more cities and cuisines.
- Incorporate machine learning models for predictive insights.
- Develop an interactive dashboard for real-time data visualization.

## Acknowledgments

- Data Source: Zomato dataset
- Tools: Python, Jupyter Notebook

