##### 1. Simple Pivot Table: Calculate the average G1 grade by moother job (`Mjob`).
```python
pivot_table_g1_by_Mjob = pd.pivot_table(
    data=student_mat_df,               # Specify the DataFrame
    values='G1',                       # Column to aggregate
    index='Mjob',                    # Index column
    aggfunc='mean'                     # Aggregation function (mean in this case)
)
```
![[Pasted image 20240703100414.png]]

##### 2. Pivot Table with Index and Columns: Calculate the average G2 grade by school and sex.
```python
pivot_table_avg_g2_by_school_sex = pd.pivot_table(
    data=student_mat_df,               # Specify the DataFrame
    values='G2',                       # Column to aggregate
    index=['school'],                   # Index columns (school)
    columns=['sex'],                    # Columns (sex)
    aggfunc='mean'                      # Aggregation function (mean)
)
```
![[Pasted image 20240703100433.png]]

##### 3. Pivot Table with Functions: Calculate the maximum G3 grade by age.
```python
pivot_table_max_g3_by_age = pd.pivot_table(
    data=student_mat_df,
    values='G3',
    index=['age'],
    aggfunc='max'
)
```
![[Pasted image 20240703100445.png]]

##### 4. Pivot Table with Fill Values: Calculate the average health (`health`) by family size (`famsize`) and fill missing values with 0.
```python
pivot_table_avg_g1_by_famsize = pivot_table_max_g3_by_age = pd.pivot_table(
    data=student_mat_df,
    values='health',
    index=['famsize'],
    aggfunc='mean',
    fill_value=0
)

```
![[Pasted image 20240703100456.png]]

##### 5. Pivot Table with Margins: Calculate the average G2 grade by school and include row and column totals.
```python
pivot_table_avg_g1_by_famsize = pivot_table_max_g3_by_age = pd.pivot_table(
    data=student_mat_df,
    values='G2',
    index=['school'],
    aggfunc='mean',
    margins=True
)
```
![[Pasted image 20240703100507.png]]

##### 6. Pivot Table with Multiple Columns: Calculate the average free time (`freetime`) grade by school, and include sex and age as columns (fill missing values with 0).
```python
pivot_table_avg_freetime_by_school_sex_age = pd.pivot_table(
    data=student_mat_df,              
    values='freetime',                       
    index=['school'],                  
    columns=["sex",'age'],                    
    aggfunc='mean',
    fill_value=0
)
```
![[Pasted image 20240703100520.png]]


##### 7. Pivot Table with Multiple Index: Calculate the average absences by school and address.
```python
pivot_table_avg_absences_by_school_address = pd.pivot_table(
    data=student_mat_df,              
    values='absences',                       
    index=['school','address'],                                      
    aggfunc='mean'
)
```
![[Pasted image 20240703100534.png]]

##### 8. Pivot Table with Multiple Values: Calculate the average freetime and number of absences by school.
```python
pivot_table_avg_freetime_absences_by_school = pd.pivot_table(
    data=student_mat_df,               # Specify the DataFrame
    values=['freetime', 'absences'],          # Columns to aggregate
    index='school',                     # Index column (school)
    aggfunc={'freetime': 'mean', 'absences': 'sum'} ,  # Aggregation functions (mean for G1, sum for absences)
)
```
![[Pasted image 20240703100543.png]]

##### 9. Pivot Table with Custom Aggregation Function: Calculate the sum of absences by guardian.
```python
pivot_table_sum_absences_by_guardian = pd.pivot_table(
data=student_mat_df,
index=["guardian"],
values="absences",
aggfunc="sum"
)
```
![[Pasted image 20240703100554.png]]


##### 10. Pivot Table with Custom Fill Value: Calculate the average G1 grade by school and fill missing values with "N/A".
```python
pivot_table_avg_g1_by_school = pd.pivot_table(
data=student_mat_df,
index="school",
values="G1",
aggfunc="mean",
fill_value=0

)
```
![[Pasted image 20240703100604.png]]

##### 11. CrossTab with Multiple Index: Count the number of students by guardian and age and include sex as column.
```python

cross_tab_students_by_guardian_age_sex = pd.crosstab(
    index=[student_mat_df['guardian'], student_mat_df['age']],   # Index columns (school and age)
    columns=student_mat_df['sex'],                             # Column column (sex)
    rownames=['Guardian', 'Age'],                                 # Names for the index
    colnames=['Sex'],                                           # Name for the columns
    margins=False                                               # Exclude row and column totals
)
```
![[Pasted image 20240703100616.png]]

##### 12. CrossTab with Multiple Columns and Margins: Count the number of students by school, and include sex and age as columns and include row and column totals.
```python
cross_tab_students_by_school_sex_age = pd.crosstab(
    index=student_mat_df['school'],     # Index column (school)
    columns=[student_mat_df['sex'], student_mat_df['age']],    # Column columns (sex and age)
    rownames=['School'],                # Name for the index
    colnames=['Sex', 'Age'],             # Names for the columns
    margins=True                        # Include row and column totals
)
```
![[Pasted image 20240703100638.png]]

##### 13. CrossTab with Multiple index and Value : Calculate the average travel time (`traveltime`) by address, sex, and age.
```python
crosstab_avg_traveltime_by_address_sex_age = pd.crosstab(
    index=[student_mat_df['address'], student_mat_df['sex'], student_mat_df['age']],  # Specify the multiple index columns
    columns='',  # Specify the column for the cross-tabulation
    values=student_mat_df['traveltime'],  # Column to calculate the average (G1 grade in this case)
    aggfunc='mean',  # Aggregation function (mean to calculate average)
    rownames=['Address', 'Sex', 'Age'],  # Specify the names for the row index levels
    colnames=[''],  # Specify an empty string as the column name
    margins=False  # Exclude the row and column totals
)
```
![[Pasted image 20240703100650.png|212]]

##### 14. CrossTab with Custom Aggregation Function: Count the number of students who have participated in extracurricular activities by school and sex.
```python
crosstab_activities_by_school_sex = pd.crosstab(
    index=[student_mat_df['school'], student_mat_df['sex']],
    columns='',
    values=student_mat_df['activities'],
    aggfunc=lambda x: (x == 'yes').sum(),
    rownames=['School', 'Sex'],
    colnames=[''],
    margins=False
)
```
![[Pasted image 20240703100707.png]]

##### 15. CrossTab with Custom Aggregation Function: Calculate the percentage of students who have internet access, categorized by school and sex.
```python
crosstab_internet_access_by_school_sex = pd.crosstab(
    index=student_mat_df['school'],  # Specify the multiple index columns (school and sex)
    columns = student_mat_df['sex'],
    values=student_mat_df['internet'],  # Column to calculate the percentage (internet access in this case)
    aggfunc=lambda x: (x == 'yes').sum() / len(x),  # Custom aggregation function to calculate the percentage
    rownames=['School'],  # Names for the row index levels
    margins=False  # Exclude row and column totals
)

```
![[Pasted image 20240703100719.png]]

#Ejercicios 