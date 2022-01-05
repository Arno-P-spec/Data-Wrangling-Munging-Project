# Data-Wrangling-Munging-Project
Data Wrangling Lab
Estimated time needed: 45 to 60 minutes

In this assignment you will be performing data wrangling.

Objectives
In this lab you will perform the following:

Identify duplicate values in the dataset.

Remove duplicate values from the dataset.

Identify missing values in the dataset.

Impute the missing values in the dataset.

Normalize data in the dataset.

Hands on Lab
Import pandas module.

import numpy as np
import pandas as pd
import numpy as np
Load the dataset into a dataframe.

df = pd.read_csv("https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/LargeData/m1_survey_data.csv")
df.head(5)
Respondent	MainBranch	Hobbyist	OpenSourcer	OpenSource	Employment	Country	Student	EdLevel	UndergradMajor	...	WelcomeChange	SONewContent	Age	Gender	Trans	Sexuality	Ethnicity	Dependents	SurveyLength	SurveyEase
0	4	I am a developer by profession	No	Never	The quality of OSS and closed source software ...	Employed full-time	United States	No	Bachelor’s degree (BA, BS, B.Eng., etc.)	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	22.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Easy
1	9	I am a developer by profession	Yes	Once a month or more often	The quality of OSS and closed source software ...	Employed full-time	New Zealand	No	Some college/university study without earning ...	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	NaN	23.0	Man	No	Bisexual	White or of European descent	No	Appropriate in length	Neither easy nor difficult
2	13	I am a developer by profession	Yes	Less than once a month but more than once per ...	OSS is, on average, of HIGHER quality than pro...	Employed full-time	United States	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	Computer science, computer engineering, or sof...	...	Somewhat more welcome now than last year	Tech articles written by other developers;Cour...	28.0	Man	No	Straight / Heterosexual	White or of European descent	Yes	Appropriate in length	Easy
3	16	I am a developer by profession	Yes	Never	The quality of OSS and closed source software ...	Employed full-time	United Kingdom	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	NaN	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	26.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Neither easy nor difficult
4	17	I am a developer by profession	Yes	Less than once a month but more than once per ...	The quality of OSS and closed source software ...	Employed full-time	Australia	No	Bachelor’s degree (BA, BS, B.Eng., etc.)	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	29.0	Man	No	Straight / Heterosexual	Hispanic or Latino/Latina;Multiracial	No	Appropriate in length	Easy
5 rows × 85 columns

Finding duplicates
In this section you will identify duplicate values in the dataset.

Find how many duplicate rows exist in the dataframe.

# your code goes here
df.duplicated().sum()
154
df.duplicated(subset='Respondent')
0        False
1        False
2        False
3        False
4        False
         ...  
11547    False
11548    False
11549    False
11550    False
11551    False
Length: 11398, dtype: bool
Removing duplicates
Remove the duplicate rows from the dataframe.

df
# your code goes here
df.drop_duplicates(subset=None,inplace=True)
df
Respondent	MainBranch	Hobbyist	OpenSourcer	OpenSource	Employment	Country	Student	EdLevel	UndergradMajor	...	WelcomeChange	SONewContent	Age	Gender	Trans	Sexuality	Ethnicity	Dependents	SurveyLength	SurveyEase
0	4	I am a developer by profession	No	Never	The quality of OSS and closed source software ...	Employed full-time	United States	No	Bachelor’s degree (BA, BS, B.Eng., etc.)	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	22.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Easy
1	9	I am a developer by profession	Yes	Once a month or more often	The quality of OSS and closed source software ...	Employed full-time	New Zealand	No	Some college/university study without earning ...	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	NaN	23.0	Man	No	Bisexual	White or of European descent	No	Appropriate in length	Neither easy nor difficult
2	13	I am a developer by profession	Yes	Less than once a month but more than once per ...	OSS is, on average, of HIGHER quality than pro...	Employed full-time	United States	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	Computer science, computer engineering, or sof...	...	Somewhat more welcome now than last year	Tech articles written by other developers;Cour...	28.0	Man	No	Straight / Heterosexual	White or of European descent	Yes	Appropriate in length	Easy
3	16	I am a developer by profession	Yes	Never	The quality of OSS and closed source software ...	Employed full-time	United Kingdom	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	NaN	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	26.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Neither easy nor difficult
4	17	I am a developer by profession	Yes	Less than once a month but more than once per ...	The quality of OSS and closed source software ...	Employed full-time	Australia	No	Bachelor’s degree (BA, BS, B.Eng., etc.)	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Indu...	29.0	Man	No	Straight / Heterosexual	Hispanic or Latino/Latina;Multiracial	No	Appropriate in length	Easy
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
11547	25136	I am a developer by profession	Yes	Never	OSS is, on average, of HIGHER quality than pro...	Employed full-time	United States	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	Computer science, computer engineering, or sof...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Cour...	36.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Difficult
11548	25137	I am a developer by profession	Yes	Never	The quality of OSS and closed source software ...	Employed full-time	Poland	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	Computer science, computer engineering, or sof...	...	A lot more welcome now than last year	Tech articles written by other developers;Tech...	25.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Neither easy nor difficult
11549	25138	I am a developer by profession	Yes	Less than once per year	The quality of OSS and closed source software ...	Employed full-time	United States	No	Master’s degree (MA, MS, M.Eng., MBA, etc.)	Computer science, computer engineering, or sof...	...	A lot more welcome now than last year	Tech articles written by other developers;Indu...	34.0	Man	No	Straight / Heterosexual	White or of European descent	Yes	Too long	Easy
11550	25141	I am a developer by profession	Yes	Less than once a month but more than once per ...	OSS is, on average, of LOWER quality than prop...	Employed full-time	Switzerland	No	Secondary school (e.g. American high school, G...	NaN	...	Somewhat less welcome now than last year	NaN	25.0	Man	No	Straight / Heterosexual	White or of European descent	No	Appropriate in length	Easy
11551	25142	I am a developer by profession	Yes	Less than once a month but more than once per ...	OSS is, on average, of HIGHER quality than pro...	Employed full-time	United Kingdom	No	Other doctoral degree (Ph.D, Ed.D., etc.)	A natural science (ex. biology, chemistry, phy...	...	Just as welcome now as I felt last year	Tech articles written by other developers;Tech...	30.0	Man	No	Bisexual	White or of European descent	No	Appropriate in length	Easy
11398 rows × 85 columns

Verify if duplicates were actually dropped.

# your code goes here
df.duplicated().sum()
0
Finding Missing values
Find the missing values for all columns.

# your code goes here
missing_data = df.isnull()
missing_data.head(5)
Respondent	MainBranch	Hobbyist	OpenSourcer	OpenSource	Employment	Country	Student	EdLevel	UndergradMajor	...	WelcomeChange	SONewContent	Age	Gender	Trans	Sexuality	Ethnicity	Dependents	SurveyLength	SurveyEase
0	False	False	False	False	False	False	False	False	False	False	...	False	False	False	False	False	False	False	False	False	False
1	False	False	False	False	False	False	False	False	False	False	...	False	True	False	False	False	False	False	False	False	False
2	False	False	False	False	False	False	False	False	False	False	...	False	False	False	False	False	False	False	False	False	False
3	False	False	False	False	False	False	False	False	False	True	...	False	False	False	False	False	False	False	False	False	False
4	False	False	False	False	False	False	False	False	False	False	...	False	False	False	False	False	False	False	False	False	False
5 rows × 85 columns

Find out how many rows are missing in the column 'WorkLoc'

# your code goes here
df['WorkLoc'].isnull().sum()
32
EdLevel
#missing rows in the column 'EdLevel'
df['EdLevel'].isnull().sum()
112
#missing rows in the column 'Country'
df['Country'].isnull().sum()
0
​
Imputing missing values
Find the value counts for the column WorkLoc.

# your code goes here
df['WorkLoc'].value_counts()
Office                                            6806
Home                                              3589
Other place, such as a coworking space or cafe     971
Name: WorkLoc, dtype: int64
#majority category under the column Employment
df['Employment'].value_counts().idxmax()
'Employed full-time'
#category with the minimum number of rows in the column UbdergradMajor
df['UndergradMajor'].value_counts().idxmin()
'A health science (ex. nursing, pharmacy, radiology)'
df['ConvertedComp'].value_counts()
2000000.0    138
1000000.0    105
100000.0      99
150000.0      92
120000.0      86
            ... 
53148.0        1
256000.0       1
54423.0        1
392.0          1
41280.0        1
Name: ConvertedComp, Length: 3515, dtype: int64
#what is the best approach to inpute the missing value in the column ConvertedComp
df['ConvertedComp'].median()
57745.0
Identify the value that is most frequent (majority) in the WorkLoc column.

#make a note of the majority value here, for future reference
#the majority value is Office=6806,Home=3589,Other place,such as coworking space or cafe=971
df['WorkLoc'].value_counts().idxmax()
'Office'
Impute (replace) all the empty rows in the column WorkLoc with the value that you have identified as majority.

# your code goes here
df['WorkLoc'].replace(np.nan,"Office",inplace=True)
After imputation there should ideally not be any empty rows in the WorkLoc column.

Verify if imputing was successful.

# your code goes here
df['WorkLoc'].isnull().sum()
0
Normalizing data
There are two columns in the dataset that talk about compensation.

One is "CompFreq". This column shows how often a developer is paid (Yearly, Monthly, Weekly).

The other is "CompTotal". This column talks about how much the developer is paid per Year, Month, or Week depending upon his/her "CompFreq".

This makes it difficult to compare the total compensation of the developers.

In this section you will create a new column called 'NormalizedAnnualCompensation' which contains the 'Annual Compensation' irrespective of the 'CompFreq'.

Once this column is ready, it makes comparison of salaries easy.

List out the various categories in the column 'CompFreq'

# your code goes here
df['CompFreq'].value_counts()
Yearly     6073
Monthly    4788
Weekly      331
Name: CompFreq, dtype: int64
Create a new column named 'NormalizedAnnualCompensation'. Use the hint given below if needed.

Double click to see the Hint.

# your code goes here
#find missing value in CompFreq column
df['CompFreq'].isnull().sum()
206
#find majority value in CompFreq column
df['CompFreq'].value_counts().idxmax()
'Yearly'
 = 3
#how many(number of) unique values are there in the CompFreq column = 3
df['CompFreq'].unique()
array(['Yearly', 'Monthly', 'Weekly'], dtype=object)
df['CompFreq'].unique().sum()
'YearlyMonthlyWeekly'
#replace missing values with majority value in CompFreq column
df['CompFreq'].replace(np.nan,"Yearly",inplace=True)
#verify if replacing was successful
df['CompFreq'].isnull().sum()
0
#find missing value in CompTotal column
df['CompTotal'].isnull().sum()
809
#find mean(average)of CompTotal column
df['CompTotal'].mean()
757047.7255642648
#replace missing values in CompTotal with mean
df['CompTotal'].replace(np.nan,757047.7,inplace=True)
#verify if replacing was successful
df['CompTotal'].isnull().sum()
0
#create new Normalized Annual Compensation column 
df['NormalizedAnnualCompensation']=np.where(df['CompFreq']=='Yearly',df['CompTotal'],0)
df['NormalizedAnnualCompensation']=np.where(df['CompFreq']=='Monthly',df['CompTotal']*12,df['NormalizedAnnualCompensation'])
df['NormalizedAnualCompensation']=np.where(df['CompFreq']=='Weekly',df['CompTotal']*52,df['NormalizedAnnualCompensation'])
df['NormalizedAnnualCompensation']
0         61000.0
1        138000.0
2         90000.0
3        348000.0
4         90000.0
           ...   
11547    130000.0
11548     74400.0
11549    105000.0
11550     80000.0
11551    757047.7
Name: NormalizedAnnualCompensation, Length: 11398, dtype: float64
#find median of Normalized Annual Compensation column
df['NormalizedAnnualCompensation'].median()
104000.0
#create dataframe with CompFreq, CompTotal and Normalized Annual Compensation columns
df[['CompFreq','CompTotal','NormalizedAnnualCompensation']].head()
CompFreq	CompTotal	NormalizedAnnualCompensation
0	Yearly	61000.0	61000.0
1	Yearly	138000.0	138000.0
2	Yearly	90000.0	90000.0
3	Monthly	29000.0	348000.0
4	Yearly	90000.0	90000.0
Authors
Ramesh Sannareddy

Other Contributors
Rav Ahuja

Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2020-10-17	0.1	Ramesh Sannareddy	Created initial version of the lab
Copyright © 2020 IBM Corporation. This notebook and its source code are released under the terms of the MIT License.
