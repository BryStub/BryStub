- Hello, I’m Bryce Stuber
- I’m currently interested in the business analysis side of IT.
- I’m currently learning a bit of AWS.

<!---
BryStub/BryStub is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

#!/usr/bin/env python
# coding: utf-8


I have a small code sample below from when I was learning about BI in college.

#Import data 
import pandas as pd
import matplotlib.pyplot as plt
get_ipython().run_line_magic('matplotlib', 'inline')


#Define the file & read the csv file path.
df= pd.read_csv(r"C:\Users\Harry\Desktop\dacworkspace\final_project\data_covid\Texas_Hospital_Capacity.csv")
#Prints the general info about characteristics in file.
df.info()


#Counts & prints the first 20 rows of the file for us to analyze the type of data.
df.head(20)


#Defines & reads the second CSV file to merge the data with.
df1= pd.read_csv(r"C:\Users\Harry\Desktop\dacworkspace\final_project\data_covid\US-States.csv")

#Prints the ending 20 rows of the file characteristics.
df1.tail(20)
df1.info()


#Prints the beginning characteristics for the state of Texas from the second file being used for data merge.
df1.head()
df1_texas = df1[df1['state']=='Texas']
df1_texas


# # Data Merging

#Merges the data in the two files & prints the HEADER for each rows' data.
df_date_merge=pd.merge(df, df1_texas, on = "date", how = "inner")
df_date_merge

#Presents us with an insight on the type of data in each field
df_date_merge.info()


#Merges & compares the Cases vs. Deaths.
plt.scatter(df_date_merge.cases,df_date_merge.deaths)
plt.xlabel('Cases')
plt.ylabel('Deaths')

#Total Available Beds vs. Total Beds Occupied
plt.scatter(df_date_merge.Total_Available_Beds,df_date_merge.Total_Occupied_Beds)
plt.xlabel('Total Available Beds')
plt.ylabel('Total Occupied Beds')


