```python
### Do smoker people give more tips?

smokers_count =tips_df['smoker'].value_counts()
tips_by_smokers_chart = smokers_count.plot(kind="pie",
                                           autopct='%1.2f%%',
                                           label="Is smoker?",
                                           title="Proportion of tips by smoker condition")
```
![[Untitled (1).png|250]]

```python
### Do men or women give more tips?
tips_by_sex_count =tips_df['sex'].value_counts()
sex_proportion_chart  = tips_by_sex_count.plot(kind="pie",
                                           autopct='%1.2f%%',
                                           label="Sex",
                                           title="Proportion of tips by sex")
```
![[Untitled (2).png|275]]

```python
### Total bill and Tips amounts by sex
tip_amount_by_sex = tips_df.loc[:, ["sex", "total_bill", "tip"]]
tip_amount_by_separado=tip_amount_by_sex.groupby("sex").mean().reset_index()

tips_by_sex_chart = tip_amount_by_separado.plot(kind="bar",
                                           x="sex",
                                           y=["total_bill", "tip"],
                                           stacked=True,
                                           xlabel="Sex",
                                           ylabel="Amount",
                                           title="Tips and total bill amounts by sex")

```
![[Untitled (3).png|350]]

```python
### Are the best tips on Saturday night?
daily_tips = tips_df["day"].value_counts()
daily_tips_chart   = daily_tips.plot(kind="pie",
                                           autopct='%1.2f%%',
                                           label="Day of week",
                                           title="Tips per day")
```
![[Untitled (4).png|325]]

```python
### Total bill and Tips per day of the week
from pandas.api.types import CategoricalDtype

day_of_week_order = CategoricalDtype(
    ['Thur', 'Fri', 'Sat', 'Sun'],
    ordered=True
)

tips_df['day'] = tips_df['day'].astype(day_of_week_order)
#Todo ese codigo de arriba sirvio para filtrar solo por esos dias los datos
```
```python
# your code goes here
daily_mean = tips_df.loc[:, ["day", "total_bill", "tip"]].groupby("day").mean().reset_index()

tips_by_day_chart = daily_mean.plot(kind="barh",
                                    x="day",
                                    y=["total_bill", "tip"],
                                    stacked=True,
                                    xlabel="Tips and total bill amounts",
                                    ylabel="Day",
                                    title="Tips and total bill amounts per day of the week")
```
![[Untitled (5).png|450]]

```python
### Are there better tips during the day or at night?
dinner_lunch_df = tips_df.loc[:, ["time", "total_bill", "tip"]].groupby('time').mean(numeric_only=True).reset_index()

dinner_lunch_chart = dinner_lunch_df.plot(kind="bar",
                                          x="time",
                                          y=["total_bill", "tip"],
                                          stacked=True,
                                          xlabel="Time",
                                          ylabel="Amount",
                                          title="Total bills and tips amount per moment of the day")
```
![[Untitled (6).png]]
#Ejercicios 