
```python
### Activity 2: Create a histogram showing the distribution of happiness score.
happiness_hist = df["Happiness score"].plot(kind="hist",
                                title="Histogram of Happiness Scores",
                                xlabel="Happiness score",
                                ylabel="Frequency" )
```
![[Pasted image 20240703084440.png|450]]

```python
### Activity 3: Create a horizontal bar chart with the combined top 10 
#and bottom 10 countries.

# Extract top and bottom 10 countries based on happiness score
top_10 = df.head(10)[['Country', 'Happiness score']]
bottom_10 = df.tail(10)[['Country', 'Happiness score']]

# Create a new column to differentiate between top and bottom countries
top_10['Type'] = 'Top'
bottom_10['Type'] = 'Bottom'

# Combine the two dataframes into one
combined = pd.concat([top_10, bottom_10])

# Pivot the dataframe to have country names as index and type as columns
pivot_df = combined.pivot(index='Country', columns='Type', values='Happiness score')
```
![[Untitled (7).png|163]]

```python
happiness_gap_chart = pivot_df.plot(kind="barh",
                                   color=["red", "blue"],
                                   title="Top and Bottom 10 Countries by Happiness Score",
                                   ylabel="Country ",
                                   xlabel="Happiness Score",
                                   figsize=(10,6))
```
![[Untitled (8).png|500]]

```python
### Activity 4: Create a horizontal bar chart with the combined top 5 and bottom 5 countries sorted by generosity.

# Sort by generosity
df_by_generosity = df.sort_values('Explained by: Generosity')[['Country', 'Happiness score']]

# Extract top 5 and bottom 5 countries
top_5 = df_by_generosity.copy().tail(5)
bottom_5 = df_by_generosity.copy().head(5)

top_5.loc[:, 'Type'] = 'Top'
bottom_5.loc[:, 'Type'] = 'Bottom'

# Combine the two dataframes into one
combined = pd.concat([top_5, bottom_5])

# Pivot the dataframe to have country names as index and type as columns
generosity_pivot_df = combined.pivot(index='Country', columns='Type', values='Happiness score')

# Write your code here
generosity_gap_chart=generosity_pivot_df.plot(kind="barh",
                                              color=["red", "green"],
                                              title="Happiness Score of Top and Bottom 5 Countries by Generosity",
                                              ylabel="Country",
                                              xlabel="Happiness Score",
                                              figsize=(10,6)
```
											  
![[Untitled (9).png|525]]

#Ejercicios 