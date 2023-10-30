# Time-series-model-Project
 Craigslist Vehicles Dataset
 Creating a Time-Series Model for the Craigslist Vehicles dataset involves several steps, as outlined

## Data Preprocessing
Load the dataset.
Handle missing values by filling in missing values with the median for numerical columns and the mode for categorical columns.

```
import pandas as pd

# Load the data
data = pd.read_csv("craigslistVehicles.csv")

# Fill missing values
data.fillna(data.median(), inplace=True)
data.fillna(data.mode().iloc[0], inplace=True)
```

## Data Type Conversion
Convert the 'posting_date' column to a datetime data type.

```
data['posting_date'] = pd.to_datetime(data['posting_date'])
```

## Datetime Index
Utilize the 'posting_date' column to create a datetime index for the dataset.

```
data.set_index('posting_date', inplace=True)
```

## Exploratory Data Analysis
Explore the data using visualizations and statistical analysis techniques to understand temporal patterns, identify seasonal trends, and analyze demand-supply dynamics by region and vehicle type.

 ### Region and Vehicle Type Analysis
    Analyze how vehicle listings vary by region and vehicle type.

```
region_count = data['region'].value_counts()
vehicle_type_count = data['manufacturer'].value_counts()

# Visualize top regions and vehicle types
plt.figure(figsize=(12, 6))
region_count.head(10).plot(kind='bar', title='Top 10 Regions with Listings')
plt.show()

plt.figure(figsize=(12, 6))
vehicle_type_count.head(10).plot(kind='bar', title='Top 10 Vehicle Types')
plt.show()
```

## Time-Series Chart
Build a time-series chart using the data.

```
plt.figure(figsize=(12, 6))
data['price'].resample('D').mean().plot(title='Average Daily Price')
plt.xlabel('Date')
plt.ylabel('Average Price')
plt.show()
```

