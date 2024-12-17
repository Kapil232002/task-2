import pandas as pd

# Load the CSV file into a Pandas DataFrame
file_path = '01.Data Cleaning and Preprocessing.csv'
df = pd.read_csv(file_path)

# Display the first few rows of the dataset
print("First 5 rows of the dataset:")
print(df.head())

# Display column names
print("\nColumn Names:")
print(df.columns)

# ---------- Filtering Data ----------
# Filter rows where 'ChipRate' > 16.5
filtered_df = df[df['ChipRate'] > 16.5]
print("\nFiltered rows where 'ChipRate' > 16.5:")
print(filtered_df.head())

# Filter rows where 'Y-Kappa' is between 20 and 25
filtered_ykappa = df[(df['Y-Kappa'] >= 20) & (df['Y-Kappa'] <= 25)]
print("\nFiltered rows where 'Y-Kappa' is between 20 and 25:")
print(filtered_ykappa.head())

# Filter rows where 'BlowFlow' is not null
filtered_blowflow = df[df['BlowFlow'].notnull()]
print("\nFiltered rows where 'BlowFlow' is not null:")
print(filtered_blowflow.head())

# ---------- Handling Missing Values ----------
# Fill missing values with column means
df_filled = df.fillna(df.mean())
print("\nMissing values filled with column means:")
print(df_filled.head())

# Drop rows where any value is missing
df_dropped = df.dropna()
print("\nRows with missing values dropped:")
print(df_dropped.head())

# Fill missing values with a specific value (e.g., 0)
df_filled_specific = df.fillna(0)
print("\nMissing values filled with 0:")
print(df_filled_specific.head())

# ---------- Summary Statistics ----------
# Summary statistics for numerical columns
summary_stats = df.describe()
print("\nSummary Statistics:")
print(summary_stats)

# Calculate statistics for a specific column
chiprate_mean = df['ChipRate'].mean()
print(f"\nMean of 'ChipRate': {chiprate_mean}")

ykappa_median = df['Y-Kappa'].median()
print(f"Median of 'Y-Kappa': {ykappa_median}")

# Count non-null values for each column
non_null_counts = df.count()
print("\nCount of non-null values in each column:")
print(non_null_counts)

# ---------- Sorting, Grouping, and Working with Columns ----------
# Sort values based on 'ChipRate' in descending order
sorted_df = df.sort_values(by='ChipRate', ascending=False)
print("\nData sorted by 'ChipRate' in descending order:")
print(sorted_df.head())

# Group data by a categorical column and calculate mean
grouped_df = df.groupby('Observation')['ChipRate'].mean()
print("\nMean 'ChipRate' for each 'Observation' group:")
print(grouped_df.head())

# Select specific columns
selected_columns = df[['Observation', 'Y-Kappa', 'ChipRate']]
print("\nSelected Columns (Observation, Y-Kappa, ChipRate):")
print(selected_columns.head())
