import numpy as np
import pandas as pd

print("🚀 Starting Remote Patient Monitoring Data Pipeline...\n")

# 1. Simulating Raw Patient Data (With Missing Values & Outliers)
np.random.seed(42)
data_size = 100

data = {
    "Patient_ID": range(1001, 1001 + data_size),
    "Age": np.random.randint(18, 85, size=data_size),
    "Heart_Rate_BPM": np.random.randint(55, 110, size=data_size),
    "Blood_Pressure_Systolic": np.random.randint(110, 150, size=data_size),
    "Risk_Score": np.random.uniform(0.1, 0.9, size=data_size),
}

df = pd.DataFrame(data)

# Injecting some synthetic missing values to show cleaning skills
df.loc[df["Age"] % 7 == 0, "Heart_Rate_BPM"] = np.nan

print("📊 Raw Data Sample (With Missing Values):")
print(df.head(), "\n")

# 2. Data Preprocessing (The 'Big 5' Pandas operations)
print("🧼 Cleaning and Preprocessing Data...")

# Handling missing values using median imputation
median_hr = df["Heart_Rate_BPM"].median()
df["Heart_Rate_BPM"].fillna(median_hr, inplace=True)

# Feature Engineering: Flagging High-Risk Patients
df["High_Risk_Flag"] = np.where(
    (df["Heart_Rate_BPM"] > 100) | (df["Blood_Pressure_Systolic"] > 140), 1, 0
)

print("✅ Data Cleaned Successfully!")
print(df[["Patient_ID", "Heart_Rate_BPM", "High_Risk_Flag"]].head())
