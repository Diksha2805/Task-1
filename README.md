# Task-1
Data cleaning and feature engineering on customer personality dataset using Python and Pandas.

import pandas as pd
from datetime import datetime

df = pd.read_csv('customer_personality.csv', sep="\t")

print(df.info())
print(df.describe())
print(df.head().to_string())
print(df.tail())
print(df.shape)
print(df.columns.to_list())

df.sample(50).to_csv('customer_personality_sample.csv', index=False)

print(df.isnull().sum())
print("Number of duplicate rows:", df.duplicated().sum())
df.drop_duplicates(inplace=True)
df["Income"]=pd.to_numeric(df["Income"], errors='coerce')
df["Income"] = df["Income"].fillna(df["Income"].median())
df["Education"] = df["Education"].fillna("Unknown")
df.dropna(subset=["Marital_Status"], inplace=True)
df["Marital_Status"]=df["Marital_Status"].replace({
    "Together": "Partner",
})
print(df["Marital_Status"].value_counts())

df["Total_Children"] = df["Kidhome"] + df["Teenhome"]
df["Total_Spending"] = df["MntWines"] + df["MntFruits"] + df["MntMeatProducts"] + df["MntFishProducts"] + df["MntSweetProducts"] + df["MntGoldProds"]

df["Total_Purchases"] = df["NumDealsPurchases"] + df["NumWebPurchases"] + df["NumCatalogPurchases"] + df["NumStorePurchases"]

df["Campaign_Response"] = df["AcceptedCmp1"] + df["AcceptedCmp2"] + df["AcceptedCmp3"] + df["AcceptedCmp4"] + df["AcceptedCmp5"] + df["Response"]
df["Campaign_Response"] = df["Campaign_Response"].clip(upper=1)

df["Age"] = df["Year_Birth"].apply(lambda x: datetime.now().year - x)
df["Dt_Customer"] = pd.to_datetime(df["Dt_Customer"], errors='coerce')

df.to_csv('customer_personality_cleaned.csv', index=False)

print("Data cleaning completed. Cleaned data saved to 'customer_personality_cleaned.csv'.")
print(df)
