##### 1. Calculate the total global sales for each `Platform`.
```python
#MI SOLUCION
total_global_sales_by_platform = games_sales_df.groupby("Platform").agg({
"Global_Sales":'sum'})
total_global_sales_by_platform

#LA "correcta"

total_global_sales_by_platform = games_sales_df.groupby('Platform')['Global_Sales'].sum()

total_global_sales_by_platform
```

##### 2. Find the top-selling genre based on global sales.
```python
top_selling_genre = games_sales_df.groupby('Genre')['Global_Sales'].sum().idxmax()
```

```python
global_sales_chart = games_sales_df.groupby("Genre").agg({
    "Global_Sales":'sum'
})
global_sales_chart.sort_values("Global_Sales",ascending=False,inplace=True)
global_sales_chart["Global_Sales"].plot(kind="bar")

---
#La solucion optima
global_sales_chart = games_sales_df.groupby('Genre')['Global_Sales'].sum().sort_values(ascending=False).plot(kind='bar')

```

![[Pasted image 20240703094809.png]]

#4. Calculate the average global sales for each `Publisher`.
```python
avg_sales_per_publisher = games_sales_df.groupby("Publisher")["Global_Sales"].mean().reset_index()

avg_sales_per_publisher

```

![[Pasted image 20240703094835.png]]

##### 5. Calculate the total `EU_Sales` for each platform-year combination.
```python
platform_year_eu_sales = games_sales_df.groupby(["Platform","Year"])["EU_Sales"].sum()

```
![[Untitled (10).png]]

##### 6. Find the number of publishers in each `Platform`.
```python
no_publisher_per_platform = games_sales_df.groupby('Platform')
['Publisher'].apply(lambda x: x.nunique()).reset_index(name='Publishers_Count')
```
![[Untitled (12).png]]

##### 7. Find the publisher with the most occurences for each `Platform`.
```python


platform_publisher_count = games_sales_df.groupby(['Platform', 'Publisher']).size()

```
![[Untitled (13).png]]

###### 7.5 Find the publisher with the most occurences for each `Platform`.

```python
most_frequent_publisher_platform = platform_publisher_count.groupby('Platform').
apply(lambda x: x.index[x == x.max()].min()[1]).reset_index(name='Publisher')
#lambda x: x.index[x == x.max()].min()[1] con esta seccion lo que hacemos es que nos
#traemos el valor del nombre del index mas alto

```
![[Untitled (16).png]]

##### 8. Find the publisher with the highest total global sales for each `Year`.

```python
yearly_publisher_sales = games_sales_df.groupby(['Year', 'Publisher'])['Global_Sales'].sum()

top_publisher_year = yearly_publisher_sales.groupby('Year').idxmax().apply(lambda x: x[1]).reset_index(name='Top_Selling_Publisher')

top_publisher_year['Global_Sales_Sum'] = top_publisher_year.apply(lambda row: yearly_publisher_sales.loc[row['Year'], row['Top_Selling_Publisher']], axis=1)
top_publisher_year
```
![[Untitled (17).png]]
![[Untitled (18).png]]
![[Untitled (19).png]]
##### 9. Find the maximum sales year for each `Genre`.
```python


max_sales_year_per_genre = games_sales_df.groupby('Genre')['Global_Sales'].idxmax()
max_sales_year_per_genre = games_sales_df.loc[max_sales_year_per_genre, ['Genre', 'Year', 'Global_Sales']]

```
![[Untitled (20).png]]
##### 10. Compute descriptive statistics for each `Genre` using its `Global_Sales`.
```python
descriptive_genres = games_sales_df.groupby("Genre")["Global_Sales"].describe()
descriptive_genres
```
![[Untitled (21).png]]
##### 11. Calculate the total `JP_Sales` and average `Other_Sales` for each `Platform`.
```python
jp_other_sales_platform = games_sales_df.groupby("Platform").agg({
"JP_Sales":'sum',
"Other_Sales":'mean'
})
```
![[Untitled (22).png]]
##### 13. Calculate the percentage of `Global_Sales` contribution by each `Platform`.
```python
def sales_percentage(x):
    return (x.sum()*100)/total

total=games_sales_df.groupby("Platform")["Global_Sales"].sum().sum()

sales_percentage_by_platform = games_sales_df.groupby("Platform")["Global_Sales"].agg(sales_percentage).reset_index(name='sales_percentage')
sales_percentage_by_platform

---

#Forma incomoda
sales_percentage_by_platform = sales_by_platform.apply(lambda x: (x/sales_by_platform.sum())*100).reset_index(name='sales_percentage')
```
![[Untitled (23).png]]
##### 14. Which platforms for playing video games have been the most popular each year?

```python
popular_platform_per_year = games_sales_df.groupby('Year')['Platform'].apply(lambda x: x.value_counts().idxmax())
```
![[Pasted image 20240703095547.png|131]]

##### 15. Which genres have been more or less popular with the passing of time?
```python
genre_popularity_over_time = games_sales_df.groupby('Year')['Genre'].value_counts().unstack(fill_value=0)

```
![[Untitled (24).png|500]]
##### 16. Calculate the z-score normalization for `Global_Sales` for each `Genre`. 
```python
games_sales_df['Global_Sales_Normalized'] = games_sales_df.groupby('Genre')['Global_Sales'].transform(lambda x: (x - x.mean()) / x.std())
```
![[Pasted image 20240703095639.png|450]]

#Ejercicios 