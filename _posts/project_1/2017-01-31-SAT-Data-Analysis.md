
# Project 1

## Step 1: Open the `sat_scores.csv` file. Investigate the data, and answer the questions below.


##### 1. What does the data describe?

Describes SAT scores for verbal and math, and rate, by state

##### 2. Does the data look complete? Are there any obvious issues with the observations?

Yes, the data looks complete, all 50 states are represented and there are no NaNs in the data. There is also a row for "all".

##### 3. Create a data dictionary for the dataset.

Abstract: Analyze the performance on the SAT test by states

Data set Characteristics: Multivariate
Number of instances: 
Missing Values: None
Source: General Assembly
Total entries: 52x4


## Step 2: Load the data.

##### 4. Load the data into a list of lists


```python
test=open("/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/sat_scores.csv","r").read()
data=test.split("\n")
#print(data[0:5])

scores=[]

for element in data:
	scores.append(element.split(","))
```

##### 5. Print the data


```python
print(scores)
```

    [['State', 'Rate', 'Verbal', 'Math'], ['CT', '82', '509', '510'], ['NJ', '81', '499', '513'], ['MA', '79', '511', '515'], ['NY', '77', '495', '505'], ['NH', '72', '520', '516'], ['RI', '71', '501', '499'], ['PA', '71', '500', '499'], ['VT', '69', '511', '506'], ['ME', '69', '506', '500'], ['VA', '68', '510', '501'], ['DE', '67', '501', '499'], ['MD', '65', '508', '510'], ['NC', '65', '493', '499'], ['GA', '63', '491', '489'], ['IN', '60', '499', '501'], ['SC', '57', '486', '488'], ['DC', '56', '482', '474'], ['OR', '55', '526', '526'], ['FL', '54', '498', '499'], ['WA', '53', '527', '527'], ['TX', '53', '493', '499'], ['HI', '52', '485', '515'], ['AK', '51', '514', '510'], ['CA', '51', '498', '517'], ['AZ', '34', '523', '525'], ['NV', '33', '509', '515'], ['CO', '31', '539', '542'], ['OH', '26', '534', '439'], ['MT', '23', '539', '539'], ['WV', '18', '527', '512'], ['ID', '17', '543', '542'], ['TN', '13', '562', '553'], ['NM', '13', '551', '542'], ['IL', '12', '576', '589'], ['KY', '12', '550', '550'], ['WY', '11', '547', '545'], ['MI', '11', '561', '572'], ['MN', '9', '580', '589'], ['KS', '9', '577', '580'], ['AL', '9', '559', '554'], ['NE', '8', '562', '568'], ['OK', '8', '567', '561'], ['MO', '8', '577', '577'], ['LA', '7', '564', '562'], ['WI', '6', '584', '596'], ['AR', '6', '562', '550'], ['UT', '5', '575', '570'], ['IA', '5', '593', '603'], ['SD', '4', '577', '582'], ['ND', '4', '592', '599'], ['MS', '4', '566', '551'], ['All', '45', '506', '514'], ['']]


##### 6. Extract a list of the labels from the data, and remove them from the data.


```python
header=scores[0]
print(header)
scores_noheader=scores[1:len(scores)-1]
print(scores_noheader)
```

    ['State', 'Rate', 'Verbal', 'Math']
    [['CT', '82', '509', '510'], ['NJ', '81', '499', '513'], ['MA', '79', '511', '515'], ['NY', '77', '495', '505'], ['NH', '72', '520', '516'], ['RI', '71', '501', '499'], ['PA', '71', '500', '499'], ['VT', '69', '511', '506'], ['ME', '69', '506', '500'], ['VA', '68', '510', '501'], ['DE', '67', '501', '499'], ['MD', '65', '508', '510'], ['NC', '65', '493', '499'], ['GA', '63', '491', '489'], ['IN', '60', '499', '501'], ['SC', '57', '486', '488'], ['DC', '56', '482', '474'], ['OR', '55', '526', '526'], ['FL', '54', '498', '499'], ['WA', '53', '527', '527'], ['TX', '53', '493', '499'], ['HI', '52', '485', '515'], ['AK', '51', '514', '510'], ['CA', '51', '498', '517'], ['AZ', '34', '523', '525'], ['NV', '33', '509', '515'], ['CO', '31', '539', '542'], ['OH', '26', '534', '439'], ['MT', '23', '539', '539'], ['WV', '18', '527', '512'], ['ID', '17', '543', '542'], ['TN', '13', '562', '553'], ['NM', '13', '551', '542'], ['IL', '12', '576', '589'], ['KY', '12', '550', '550'], ['WY', '11', '547', '545'], ['MI', '11', '561', '572'], ['MN', '9', '580', '589'], ['KS', '9', '577', '580'], ['AL', '9', '559', '554'], ['NE', '8', '562', '568'], ['OK', '8', '567', '561'], ['MO', '8', '577', '577'], ['LA', '7', '564', '562'], ['WI', '6', '584', '596'], ['AR', '6', '562', '550'], ['UT', '5', '575', '570'], ['IA', '5', '593', '603'], ['SD', '4', '577', '582'], ['ND', '4', '592', '599'], ['MS', '4', '566', '551'], ['All', '45', '506', '514']]


##### 7. Create a list of State names extracted from the data. (Hint: use the list of labels to index on the State column)


```python
state_list=[]
for element in scores_noheader:
	state_list.append(element[0])
#remove final element, because last entry is not a state, but 'All'
state_list=state_list[0:len(state_list)-1]
#print(state_list)
print(sorted(state_list))
print(len(state_list))
```

    ['AK', 'AL', 'AR', 'AZ', 'CA', 'CO', 'CT', 'DC', 'DE', 'FL', 'GA', 'HI', 'IA', 'ID', 'IL', 'IN', 'KS', 'KY', 'LA', 'MA', 'MD', 'ME', 'MI', 'MN', 'MO', 'MS', 'MT', 'NC', 'ND', 'NE', 'NH', 'NJ', 'NM', 'NV', 'NY', 'OH', 'OK', 'OR', 'PA', 'RI', 'SC', 'SD', 'TN', 'TX', 'UT', 'VA', 'VT', 'WA', 'WI', 'WV', 'WY']
    51


##### 8. Print the types of each column


```python
for element in scores_noheader[0]:
	print(type(element))
```

    <type 'str'>
    <type 'str'>
    <type 'str'>
    <type 'str'>


##### 9. Do any types need to be reassigned? If so, go ahead and do it.


```python
#strings are find for the state column, but the other columns should be floats
for element in scores_noheader:
	element[1]=int(element[1])
	element[2]=int(element[2])
	element[3]=int(element[3])
print(scores_noheader)
```

    [['CT', 82, 509, 510], ['NJ', 81, 499, 513], ['MA', 79, 511, 515], ['NY', 77, 495, 505], ['NH', 72, 520, 516], ['RI', 71, 501, 499], ['PA', 71, 500, 499], ['VT', 69, 511, 506], ['ME', 69, 506, 500], ['VA', 68, 510, 501], ['DE', 67, 501, 499], ['MD', 65, 508, 510], ['NC', 65, 493, 499], ['GA', 63, 491, 489], ['IN', 60, 499, 501], ['SC', 57, 486, 488], ['DC', 56, 482, 474], ['OR', 55, 526, 526], ['FL', 54, 498, 499], ['WA', 53, 527, 527], ['TX', 53, 493, 499], ['HI', 52, 485, 515], ['AK', 51, 514, 510], ['CA', 51, 498, 517], ['AZ', 34, 523, 525], ['NV', 33, 509, 515], ['CO', 31, 539, 542], ['OH', 26, 534, 439], ['MT', 23, 539, 539], ['WV', 18, 527, 512], ['ID', 17, 543, 542], ['TN', 13, 562, 553], ['NM', 13, 551, 542], ['IL', 12, 576, 589], ['KY', 12, 550, 550], ['WY', 11, 547, 545], ['MI', 11, 561, 572], ['MN', 9, 580, 589], ['KS', 9, 577, 580], ['AL', 9, 559, 554], ['NE', 8, 562, 568], ['OK', 8, 567, 561], ['MO', 8, 577, 577], ['LA', 7, 564, 562], ['WI', 6, 584, 596], ['AR', 6, 562, 550], ['UT', 5, 575, 570], ['IA', 5, 593, 603], ['SD', 4, 577, 582], ['ND', 4, 592, 599], ['MS', 4, 566, 551], ['All', 45, 506, 514]]


##### 10. Create a dictionary for each column mapping the State to its respective value for that column. 


```python
SAT_Rate={}
SAT_Verbal={}
SAT_Math={}

for element in scores_noheader:
	SAT_Rate[element[0]]=element[1]
	SAT_Verbal[element[0]]=element[1]
	SAT_Math[element[0]]=element[1]

```

##### 11. Create a dictionary with the values for each of the numeric columns


```python
pdata=pd.read_csv("/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/sat_scores.csv")

SAT_Rate_col={}
SAT_Verbal_col={}
SAT_Math_col={}

SAT_Rate_col['Rate']=pdata['Rate']
SAT_Verbal_col['Verbal']=pdata['Verbal']
SAT_Math_col['Math']=pdata['Math']
```

## Step 3: Describe the data

##### 12. Print the min and max of each column


```python
import pandas as pd
import numpy as np
pdata=pd.read_csv("/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/sat_scores.csv")

max_rate=pdata['Rate'].max()
min_rate=pdata['Rate'].min()
max_verbal=pdata['Verbal'].max()
min_verbal=pdata['Verbal'].min()
max_math=pdata['Math'].max()
min_math=pdata['Math'].min()

print(max_rate, min_rate, max_verbal, min_verbal, max_math, min_math)

```

    (82, 4, 593, 482, 603, 439)


##### 13. Write a function using only list comprehensions, no loops, to compute Standard Deviation. Print the Standard Deviation of each numeric column.


```python
def std_calc (myscores):
	mymean=myscores.mean()
	n=len(myscores)
	return( ((sum([(score-mymean)*(score-mymean) for score in myscores])/n)**(0.5)) )

#print(pdata.columns)

print(std_calc(pdata['Verbal']))
print(std_calc(pdata['Math']))
print(std_calc(pdata['Rate']))

# To check my math:
# print(np.std(pdata['Verbal']))
# print(np.std(pdata['Math']))
# print(np.std(pdata['Rate']))
```

    32.9150949616
    35.6669961643
    27.0379964945


## Step 4: Visualize the data

##### 14. Using MatPlotLib and PyPlot, plot the distribution of the Rate using histograms.


```python
import matplotlib.pyplot as plt
%matplotlib inline
fig, ax=plt.subplots()

#bx=plt.hist(pdata["Rate"])

import seaborn as sns

ax=sns.distplot(pdata["Rate"])
```


![output_31_0](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_31_0.png "output_31_0")


##### 15. Plot the Math distribution


```python
ax=sns.distplot(pdata["Math"])
```


![math dist plot](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_33_0.png)


##### 16. Plot the Verbal distribution


```python
ax=sns.distplot(pdata["Verbal"])
```


![verbal dist plot](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_35_0.png)


##### 17. What is the typical assumption for data distribution?


```python
#Typical assumptions for data is that they are normally distributed
```

##### 18. Does that distribution hold true for our data?


```python
#No, rate and verbal variable look like they are bimodal, and math looks skewed right.

print(pdata['Rate'].skew())
print(pdata['Math'].skew())
print(pdata['Verbal'].skew())

print(pdata['Rate'].kurtosis())
print(pdata['Math'].kurtosis())
print(pdata['Verbal'].kurtosis())

print(pdata['Rate'].mean())
print(pdata['Math'].mean())
print(pdata['Verbal'].mean())

print(pdata['Rate'].median())
print(pdata['Math'].median())
print(pdata['Verbal'].median())

#The skew should be zero for normal distributions. The three distributions are not large (<.3 but not close to 0)

#The kurtosis for should be 3 for normal distributions. All three are negative.

#Looking at the mean and medians, the mean is larger than the median for all three variables, so these are all skewed right distributions

```

    0.145534434089
    0.171609869094
    0.260311951237
    -1.6319275104
    -0.376327073939
    -1.33835902815
    37.1538461538
    531.5
    532.019230769
    33.5
    521.0
    526.5


##### 19. Plot some scatterplots. **BONUS**: Use a PyPlot `figure` to present multiple plots at once.


```python
#ax=sns.regplot(pdata["Verbal"], pdata["Math"])
#bx=sns.regplot(pdata["Rate"], pdata["Math"])
#cx=sns.regplot(pdata["Rate"], pdata["Verbal"])

from scipy import stats

f, (ax1, ax2, ax3) = plt.subplots(3)
sns.regplot(pdata["Math"], pdata["Verbal"], ax=ax1)
sns.regplot(pdata["Rate"], pdata["Verbal"], ax=ax2)
sns.regplot(pdata["Rate"], pdata["Math"], ax=ax3)

plt.show()

```


![3 var regploat](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_41_0.png)


##### 20. Are there any interesting relationships to note?


```python
test=pdata[["Rate","Verbal","Math"]]
sns.pairplot(test, kind="reg")

plt.show()

# def r2(x, y):
#     return stats.pearsonr(x, y)[0] ** 2
# sns.jointplot(pdata["Verbal"], pdata["Math"], kind="reg", stat_func=r2)

#Rate has a negative correlation with both math and verbal, while math and verbal have a positive correlation with each other


```


![correlations](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_43_0.png)


##### 21. Create box plots for each variable. 


```python
test=pdata[["Rate","Verbal","Math"]]
ax=sns.boxplot(data=test, palette="Set3")
```


![box plot](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_45_0.png)


##### BONUS: Using Tableau, create a heat map for each variable using a map of the US. 


```python
import matplotlib.pyplot as plt
import matplotlib.image as mpimg

img = mpimg.imread('/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/Verbal_Heat_Map.png')
plt.imshow(img)
plt.show()

img = mpimg.imread('/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/Math_Heat_Map.png')
plt.imshow(img)
plt.show()

img = mpimg.imread('/Users/hanman/DSI-NYC-4/project/project-1-sat-scores/assets/Rate_Heat_Map.png')
plt.imshow(img)
plt.show()
```


![Verbal Heat Map Tableau](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_47_0.png)



![Math Heat Map Tableau](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_47_1.png)



![Rate Heat Map Tableau](https://github.com/hanbman/hanbman.github.io/blob/master/_posts/project_1/output_47_2.png)

