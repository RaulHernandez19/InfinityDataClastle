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

![[Pasted image 20240702144551.png|350]]
> Metodo Plot: Sirve para hacer graficas con series y Dataframes

```python
df = pd.DataFrame(np.random.randn(1000, 4),
                  index=ts.index, columns=list('ABCD'))
df = df.cumsum()
df.plot()
```
![[Pasted image 20240702144617.png|425]]
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
![[2e51609ef2fd421db2f15087d3f366de_MD5.jpeg|Open: Pasted image 20240702152859.png|223]]

```python
division_values.plot(kind="bar", rot=30)
```
![[Pasted image 20240702165018.png]]