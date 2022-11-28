## Exploratory Data Analysis 
This post consists of two examples, made in a google colab script, the first one in which we will analyze all the EDA steps in order to have the best data preprocessing before making our own models, and the second one in which we will analyze the distribution of the Iris data set thanks to the different libraries available.
# EDA
![image](https://user-images.githubusercontent.com/115313115/203810145-818c904e-c8d5-4710-9a6b-b11a5bd0aed1.png)

## Usage - Example 1: Car Price Dataset.
First of all, we will need both data set in our colab workshop, data_price_cars.csv and Iris.csv. By means of the first data set we will perform all the steps of the EDA with the help of the following commands.

```python
df = pd.read_csv("data_price_cars.csv")
# To display the top 5 rows 
df.head(5) 
#Remove irrelevant columns 
df = df.drop(['Engine Fuel Type', 'Market Category', 'Vehicle Style', 'Popularity', 'Number of Doors', 'Vehicle Size'], axis=1)
#Rename columns
df = df.rename(columns={"Engine HP": "HP", "Engine Cylinders": "Cylinders", "Transmission Type": "Transmission", "Driven_Wheels": "Drive Mode","highway MPG": "MPG-H", "city mpg": "MPG-C", "MSRP": "Price" })
#Remove duplicated rows
duplicate_rows_df = df[df.duplicated()]
df = df.drop_duplicates()
# Dropping the missing values.
df = df.dropna()   
```

Next we will detect the outliers,with the seaborn library and remove them from the data set.

![Outliers](https://user-images.githubusercontent.com/115313115/204318788-f175133c-07c8-4e4d-9a77-41a64cd0961d.png)

And we remove them with the following code line.

```python
#Remove outliers
df = df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
df.shape
```

Finally, we can analyze our data using histograms, heat maps or scatterplots. For example:
![image](https://user-images.githubusercontent.com/115313115/204321471-c13048ca-f0e1-4bf1-8e2a-e65601fdd811.png)


## Usage - Example 2: Car Iris data.

In this example, unlike the previous one, we will analyze the different probabilistic distributions of our data, using the different libraries avaible, here are some examples:

**General data:**

![image](https://user-images.githubusercontent.com/115313115/204324769-2c5cd3e5-4e3d-46b8-8d2e-a863b8a24949.png)

**Probability Distribution:**

![image](https://user-images.githubusercontent.com/115313115/204328952-1c0f71a1-ec63-4671-8f23-6ede97beebc1.png)

**Box Plots:**

![image](https://user-images.githubusercontent.com/115313115/204328010-75fa9991-43e9-441b-8c44-16e14ec07852.png)

**Violin Plots:**

![image](https://user-images.githubusercontent.com/115313115/204328066-bfd31e3b-1309-4112-adf2-2b4f83be4580.png)

**Scatter Plots:**

![image](https://user-images.githubusercontent.com/115313115/204328172-9e21266e-de3d-4ebb-9655-37a4aafb5e57.png)

**Pair Plots:**

![image](https://user-images.githubusercontent.com/115313115/204328550-75c80771-3f81-45ef-9557-32b3fb921be9.png)
