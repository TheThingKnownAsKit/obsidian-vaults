## 1.1 What is data?
<mark style="background: #ADCCFFA6;">Descriptive</mark> data analytics seeks to describe data, providing insight and knowledge. Ex: Based on collected data, the world population in 2015 is about 7 billion.
<mark style="background: #ADCCFFA6;">Predictive</mark> data analytics seeks to make predictions from data. Ex: Using models based on birth rates, death rates, medical care improvements, and other data, the United Nations predicts the world population will reach 11.2 billion in 2100.
<mark style="background: #ADCCFFA6;">Prescriptive</mark> data analytics seeks to make decisions (prescriptions) based on data. Ex: Population predictions for specific countries help the United Nations decide where to focus agricultural development efforts.

A <mark style="background: #ADCCFFA6;">nominal variable's</mark> categories have no ordering, existing in name only, like apples, oranges, and grapes. ("Nominal" means "in name only").
An <mark style="background: #ADCCFFA6;">ordinal variable's</mark> categories have an ordering, like disagree, neutral, and agree.

## 1.2 Data Frames
A <mark style="background: #ADCCFFA6;">data frame</mark> is a two-dimensional tabular data structure with labeled columns and rows
	The index is the set of row labels
	The columns are the labels of the column data
	The values are the data in the data frame
![[Pasted image 20240904210711.png]]

<mark style="background: #ADCCFFA6;">pandas</mark> is a Python library that allows a user to work with data frames by providing tools for reading, writing, subsetting, and reshaping data
![[Pasted image 20240904210819.png]]
![[Pasted image 20240904210843.png]]

<mark style="background: #ADCCFFA6;">Subsetting</mark> is the process of retrieving parts of a data frame

A data frame is in <mark style="background: #ADCCFFA6;">long form</mark> when each column is a variable and each row gives non-repeatable data. Also known as unstacked or in record form
A data frame is in <mark style="background: #ADCCFFA6;">wide form</mark> if each data variable is in a different column. Also known as stacked

<mark style="background: #ADCCFFA6;">Reshaping data</mark> involves converting a data frame from one form into another
<mark style="background: #ADCCFFA6;">Pivoting</mark> converts a data frame from long form to wide form
<mark style="background: #ADCCFFA6;">Melting</mark> converts a data frame from wide form to long form
Pivoting:
![[Pasted image 20240904211432.png]]
Melting:
![[Pasted image 20240904211444.png]]
Commands are pd.pivot, pd.melt

## 1.3 Data Formats
Given data in a data frame, an <mark style="background: #ADCCFFA6;">observation</mark> is a record associated with an individual entity. Usually found in a single row. A <mark style="background: #ADCCFFA6;">feature</mark> is a column containing information associated with each entity
	Rows and columns basically

The three common data formats are CSV, JSON, and XML

<mark style="background: #ADCCFFA6;">CSV</mark> is comma separated value format is a plain text format where the data is laid out with one observation per row and features separated by a delimiter
![[Pasted image 20240904211959.png]]
<mark style="background: #ADCCFFA6;">JSON</mark> or JavaScript Object Notation is an open format data-interchange language based on objects, which are name/value pairs, and arrays
![[Pasted image 20240904212101.png]]
<mark style="background: #ADCCFFA6;">XML</mark> or extensible markup language is a plain text format. Consists of elements which are characters surrounded by tags. The tags are user-defined and denoted by <>. Can be attributes and such
![[Pasted image 20240904212154.png]]

## 1.4 Observational Studies and Experiments
In an <mark style="background: #ADCCFFA6;">observational study</mark>, data is collected by measuring/recording variables of interest without any direct intervention
In an <mark style="background: #ADCCFFA6;">experiment</mark>, some of the variables are controlled when the data is collected due to direct intervention by the researchers conducting the experiment

A <mark style="background: #ADCCFFA6;">lurking variable</mark> is a variable that was not recorded or accounted for in the data collection process that impacts a variable of interest

<mark style="background: #ADCCFFA6;">Causation</mark> exists when a cause-and-effect (causal) relationship exists between two variables
A <mark style="background: #ADCCFFA6;">spurious relationship</mark> (or spurious correlation) occurs when two unrelated variables falsely appear to have a cause-and-effect relationship
A <mark style="background: #ADCCFFA6;">confounding variable</mark> is a variable that influences two other variables into a relationship, obscuring what is actually occurring

## 1.5 Surveys and Sampling Methods
<mark style="background: #ADCCFFA6;">Surveys</mark> are conducted to allow statisticians to make generalizations about a population
A <mark style="background: #ADCCFFA6;">population</mark> is any collection of objects, people, or things about which statistical inferences are made
A <mark style="background: #ADCCFFA6;">sampling unit</mark> is an individual in the population on which a measurement can be taken
The <mark style="background: #ADCCFFA6;">sampling frame</mark> is the subset of the population from which a sample is drawn
The <mark style="background: #ADCCFFA6;">sample</mark> is composed of the sampling units that provide data to be collected

A <mark style="background: #ADCCFFA6;">parameter</mark> of a population is a numerical characteristic of a population, such as mean, median, or standard deviation. A <mark style="background: #ADCCFFA6;">statistic</mark> is a numerical characteristic of a sample, rather than the population

<mark style="background: #ADCCFFA6;">Selection bias</mark> exists when the sampling units selected from a population are not representative of the entire population, and are instead biased toward certain subsets of the population. A population should be surveyed in such a way to minimize sampling bias. Several types of selection bias follow
<mark style="background: #ADCCFFA6;">Undercoverage</mark> occurs when certain members of a population are inadequately represented in a sample
<mark style="background: #ADCCFFA6;">Nonresponse bias</mark> occurs when a sample is biased toward members of a population that participate in a survey
<mark style="background: #ADCCFFA6;">Voluntary response bias</mark> occurs when a sample is biased toward members that self-select for participation in a survey
<mark style="background: #ADCCFFA6;">Response bias</mark> can result if the responses of survey participants are affected by how a question is asked or the behaviors or attitudes of the participant. Several types of response bias follow
<mark style="background: #ADCCFFA6;">Acquiescence bias</mark> occurs when respondents tend to agree with a statement in a survey
<mark style="background: #ADCCFFA6;">Extreme responding</mark> occurs when respondents tend to select the most extreme options available
<mark style="background: #ADCCFFA6;">Social desirability bias</mark> occurs when respondents tend to answer questions in a way that is socially accepted by others. In other words, a social desirability bias exists when respondents over-report "good" behaviors or under-report "bad" behaviors

In <mark style="background: #ADCCFFA6;">simple random sampling</mark>, a sample is constructed by random selection from the population. Mathematically, simple random sampling is a sampling method in which all possible samples consisting of n units selected from a population of N units are equally likely
In <mark style="background: #ADCCFFA6;">systematic sampling</mark>, every kth unit from a population of N units is selected to be in a sample
In <mark style="background: #ADCCFFA6;">stratified sampling</mark>, the population is first divided into groups, or strata, depending on some characteristic. Next, samples within each stratum are randomly selected in a proportional manner
In <mark style="background: #ADCCFFA6;">cluster sampling</mark>, the population is first divided into groups, or clusters, depending on some characteristic. Next, the sample is constructed by randomly selecting one or more clusters
In <mark style="background: #ADCCFFA6;">convenience sampling</mark>, units are drawn from a subset of the population that is readily available

## 1.6 What is Statistics?
For descriptive statistics:
The <mark style="background: #ADCCFFA6;">distribution</mark> of a variable is the possible values the variable can take on and a measure of how often each value occurs. Visualizing a variable's distribution with a graph gives insights into the distribution's shape
A <mark style="background: #ADCCFFA6;">cluster</mark> is a distinct group of neighboring values in a distribution that occur noticeably more often than the values on either side of the group
The <mark style="background: #ADCCFFA6;">tails</mark> of a distribution are the end values of the distribution. The left tail refers to the lowest values of the distribution, and the right tail refers to the highest values of the distribution

For inferential statistics:
A numerical quantity of the population, such as the population mean or population proportion, is called a <mark style="background: #ADCCFFA6;">parameter</mark>. Population parameters are usually unknown, and inferential statistics allow for generalizations to be made about the population based on the observed sample

## 1.7 Measures of Center
The mean is just the sum divided by the length of dataset. Average
The <mark style="background: #ADCCFFA6;">weighted mean</mark> is a measure of center where some values are counted more than once. Often expressed either as positive integers or percentages
![[Pasted image 20240904214406.png]]
![[Pasted image 20240904214437.png]]

The median is the middle value in a sorted dataset
![[Pasted image 20240904214535.png]]

The mode is the most frequently-occurring value in a dataset

## 1.8 Measures of Variability
The <mark style="background: #ADCCFFA6;">variability</mark> is the difference between values in a dataset and the center of the dataset
<mark style="background: #ADCCFFA6;">Variance</mark>, is the average of the square difference from the mean. <mark style="background: #ADCCFFA6;">Standard deviation</mark> is the square root of the variance. By definition, the variance is the square of the standard deviation
![[Pasted image 20240904214832.png]]

![[Pasted image 20240904214902.png]]

CODE:
```python
import numpy as np

arr1 = np.array([10, 2, 5, 7, 3, 5])

# Population standard deviation for the array
print(np.std(arr1))

# Population variance of the array
print(np.var(arr1))

# Sample standard deviation for the array
print(np.std(arr1, ddof=1))

# Sample variance of the array
print(np.var(arr1, ddof=1))
```
```python
import pandas as pd

# Loads the ExamScores dataset
scores = pd.read_csv('ExamScores.csv')

# Sample standard deviation for each exam
print(scores.std())

# Sample standard deviation for Exam1 only
print(scores[['Exam1']].std()) 

# Sample variance for each exam
print(scores.var())

# Sample variance for Exam1 only
print(scores[['Exam1']].var())
```
```python
import pandas as pd

# Loads the ExamScores dataset
scores = pd.read_csv('ExamScores.csv')

# Prints the mean absolute deviation of all scores
print(scores.mad())

# Prints the mean absolute deviation of Exam 1
print(scores['Exam1'].mad())
```
