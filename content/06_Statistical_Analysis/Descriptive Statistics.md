---
tags:
  - statistics
  - concept
created: 2026-04-18
---

Branch of statistics concerned with **summarizing**, **organizing** and **describing** a [[Dataset]].

It answers questions like:
- What is typical?
- How spread out is the data?
- Are there extreme values?
- How is the data distributed?
- Are there patterns or irregularities?

Importantly, descriptive statistics **do not** attempt to make predictions or draw conclusions about a larger population. They simple **describe** the data you have.

For example:

> "The average daily sales were $2,300, with most days ranging between $1,500 and $3,000."

This is descriptive statistics.

## Main Categories
- Measures of Central Tendency
- Measures of Dispersion (Variability)
- Measures of Position
- Measures of Shape
- Measures of Frequency and Distribution

### Measures of Central Tendency
These describe the **center** or "typical" value of the data.

#### Mean

The arithmetic average of all observations.$$\bar{x}=\frac{\Sigma x_{i}}{n}$$
##### Usefulness
Provides a single value representing the dataset.
##### Use Cases
- Average sales
- Average salary
- Average response time
- Average test score
##### Limitations
Highly sensitive to outliers: 100, 150, 10000 -> Mean = 3,416.67
-> Not representative
#### Median

The middle value after sorting the data.
##### Usefulness
Represents the "typical" value when data contains outliers.
##### Use Cases
- Income distributions
- Housing prices
- Daily sales with occasional spikes
##### Advantages
Very robust against extreme values.

#### Mode

The most frequently occurring value.

##### Usefulness
Identifies the most common observation

##### Use Cases
- Most purchased product
- Most common shoe size
- Most common customer segment
- Most frequent error code
##### Limitations
May have:
- No mode
- One mode
- Multiple modes

### Measures of Dispersion: Variability
These tell you **how spread** out the data is. Two datasets may have the same mean but completely different variability.

#### Range

Difference between maximum and minimum. $$\text{Range} = \text{Max}-\text{Min}$$
-> 1, 3, 8, 10
-> Range = 9

##### Usefulness
Quick estimate of spread

##### Use Cases
- Temperature variation
- Price ranges
- Delivery times

##### Limitations
Depends only on two observations.

#### Variance
See [[Variance]].

##### Usefulness
Fundamental measure of variability.

##### Use Cases
- Risk analysis
- Quality control
- Machine learning
- Statistical modeling

##### Limitations
Units become squared. This makes interpretation difficult.

#### Standard Deviation
See [[Standard Deviation]]

##### Intuition

Represents the typical distance from the mean. **Example**:

- Average sales:
	-> $2,000
- Standard deviation:
	-> $500
- Interpretation:
	-> Most observations tend to lie around ±$500 from the average.

##### Usefulness
The most important measure of variability.

##### Use Cases
- Sales volatility
- Stock risk
- Manufacturing consistency
- Academic performance

#### Interquartile Range: IQR

Difference between: $$ IQR=Q 3-Q 1$$
Contains the middle 50% of observations.
##### Usefulness
Measures spread while ignoring outliers.

##### Use Cases
- Income analysis
- Sales analysis
- Outlier detection

### Measures of Position
These indicate where an observation lies relative to others.

#### Minimum
Smallest observation.

#### Maximum
Largest observation.

#### Quartiles
Divide data into four equal parts.
- Q1 = 25th percentile
- Q2 = Median
- Q3 = 75th percentile

##### Usefulness
Describe how values are distributed.

##### Use Cases
- Salary analysis
- Exam scores
- Customer spending

#### Percentiles
Divide data into 100 parts.

-> 90 th percentile:
\>\> A value larger than 90% of observations.

