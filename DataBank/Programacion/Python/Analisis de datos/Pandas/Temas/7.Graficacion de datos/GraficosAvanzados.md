```python
import pandas as pd
import numpy as np

ts = pd.Series(np.random.randn(1000),
               index=pd.date_range('1/1/2000', periods=1000))

ts = ts.cumsum()

ts.head()
----
2000-01-01   -0.797178
2000-01-02   -0.993884
2000-01-03   -2.111682
2000-01-04   -1.261867
2000-01-05   -0.787492
---
ts.plot()
```

![[Pasted image 20240702144551.png|300]]
> Metodo Plot: Sirve para hacer graficas con series y Dataframes

```python
df = pd.DataFrame(np.random.randn(1000, 4),
                  index=ts.index, columns=list('ABCD'))
df = df.cumsum()
df.plot()
```
![[Pasted image 20240702144617.png|300]]
# Plot types

When we used the `plot()` without any parameter we got a **line plot**, but it can be used to create a wide variety of different plots.

You can always access documentation and see some commonly used types of plots by using `df.plot?`

Plotting methods allow for a handful of plot styles other than the default line plot. These methods can be provided as the `kind` keyword argument to `plot()`, and include:

- ‘bar’ or ‘barh’ for bar plots
- ‘hist’ for histogram
- ‘box’ for boxplot
- ‘kde’ or ‘density’ for density plots
- ‘area’ for area plots
- ‘scatter’ for scatter plots
- ‘hexbin’ for hexagonal bin plots
- ‘pie’ for pie plots

# Bar

```python
division_values = sales_df['division'].value_counts()
division_values

division_values.plot(kind="bar")
```
![[2e51609ef2fd421db2f15087d3f366de_MD5.jpeg|Open: Pasted image 20240702152859.png|148]]

```python
division_values.plot(kind="bar", rot=30)
```
![[Pasted image 20240702165018.png|151]]

```python
division_values.plot(kind="bar",
                     rot=30,
                     color=["red", 
                     "blue", 
                     "green", 
                     "yellow", 
                     "orange"])
```
![[Pasted image 20240703082253.png]]

```python
division_values.plot(kind="barh",
                     rot=30,
                     color=["red", 
                     "blue", 
                     "green", 
                     "yellow", 
                     "orange"])
```
![[Pasted image 20240703082318.png]]

```python
sales_per_division = sales_df[["division", "sales"]].groupby("division").mean().reset_index()
sales_per_division["next_year_sales"] = sales_per_division["sales"] * 1.3
```
![[Pasted image 20240703082355.png]]

![[Pasted image 20240703082416.png]]
![[Pasted image 20240703082447.png]]

# Scatter pot
![[Pasted image 20240703082520.png|400]]

# Histogram

```python
sales_df['work experience'].plot(kind="hist")
```
![[Pasted image 20240703082609.png|250]]

```python
sales_df['work experience'].plot(kind="hist", bins=20)
```
![[Pasted image 20240703082634.png|225]]

# KDE 

![[Pasted image 20240703082708.png|375]]

# Pie char 

```python
education_values.plot(kind="pie")
```
![[Pasted image 20240703082809.png]]

```python
education_values.plot(kind="pie", figsize=(8,8))
```
![[Pasted image 20240703082828.png|375]]

```python
education_values.plot(kind="pie",
                      figsize=(8,8),
                      autopct='%1.2f%%')
```
![[Pasted image 20240703082849.png|375]]
# Area char

```python
experience_values = sales_df['work experience'].value_counts()
experience_values = experience_values.sort_index()
experience_values.head()
---
work experience
0    34
1    46
2    63
3    66
4    84
---
experience_values.plot(kind="area")
```
![[Pasted image 20240703082913.png|350]]

```python
experience_values_2 = experience_values / 2
experience_values_3 = experience_values / 7
new_df = pd.DataFrame({
    "exp_1": experience_values,
    "exp_2": experience_values_2,
    "exp_3": experience_values_3,
})

new_df.head()
```
![[Pasted image 20240703082952.png]]

```python
new_df.plot(kind="area")
```
![[Pasted image 20240703083013.png|350]]

# Boxlot 

```python
sales_df.plot(kind="box")
```
![[Pasted image 20240703083103.png]]

```python
sales_df["salary"].plot(kind="box")
```
![[Pasted image 20240703083117.png]]

# Personalizaciones extras-Exportacion

```python
my_chart = sales_df['work experience'].plot(kind="hist",
                                            color="salmon",
                                            figsize=(10,6),
                                            grid=True,
                                            fontsize=14,
                                            label="Work experience in years",
                                            title="Histogram of Work experience")

plt.legend()
```
![[Pasted image 20240703083206.png]]

```python
#Salvando como imagenes

my_chart.figure.savefig("my-chart.png")
my_chart.figure.savefig("my-chart.svg")
```

# Ejercicios

[[Plotting Practice_Analyzing Restaurant Tips]]

[[Practice Plotting with Pandas by analyzing Happiness]]