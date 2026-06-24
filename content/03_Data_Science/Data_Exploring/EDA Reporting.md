---
tags:
  - data-science
  - concept
created: 2026-05-19
---

A **good** exploratory data analysis report usually follows this workflow:

## Understand the Objective

Start by asking:
- What question am I trying to answer?
- What business problem am I solving?

Example:
> Understand sales performance and identify trends, patterns and opportunities for improvement

## Understand the Dataset

Describe what the data contains.

Example:
- Orders
- Customers
- Products
- Sales
- Discounts
- Profit
- Dates

#### Identify
- Number of rows and columns
- Types of variables:
	- Numerical (Sales, Profit, Quantity)
	- Categorical (Category, Region, Customer Segment)
	- Dates (Order Date, Ship Date)

## Assess Data Quality

Check for potential issues:
- Missing values
- Duplicate records
- Incorrect data types
- Impossible values
- Outliers

Document what you would do to clean the data, even if you don't actually modify it.

## Generate Descriptive Statistics

For important numerical variables:
- Mean
- Median
- Standard Deviation
- Minimum
- Maximum

#### Ask
- What is a typical sale?
- How much variability exists?
- Are there extreme values?

## Explore Relationships

Use visualizations to answer questions. 

### Bar Charts
Compare categories using [[Bar Charts]].
#### Questions
- Which categories sell the most?
- Which product has the best margins?

### Line Charts
Analyze changes over time using [[Line Charts]].
#### Questions
- Are sales increasing/decreasing?
- Is there [[Seasonality|seasonality]]?
- Are there unusual spikes?

### Histograms
Study data distribution using [[Histograms]].
#### Questions
- Are sales concentrated in a certain range?
- Are there outliers?
- Is the distribution [[Skew Data|skewed]]?

## Interpret Findings

Most important step.

Don't just say: 
> "Sales reached 500000".

**Explain** instead:
> "Sales peaked in November and December, suggesting seasonal demand that could be leveraged through targeted marketing campaigns."

Always move from:
<center>Observation -> Possible explanation -> Business implication</center>

#### Example
**Observation**
- High discounts often produce negative profits

**Possible Explanation**
- Some product are being discounted too aggressively

**Business implication**
- The company should review its discount policies to prevent selling at a loss

## Summary Key Insights

A good report usually ends with 3-5 major findings.

#### Example
- Most daily sales are relatively small, with a few exceptionally high-sales days.
- Sales exhibit seasonal peaks during certain months.
- A small number of products generate a large share of revenue.
- Large discounts are associated with negative profits.
- Sales performance differs across categories and regions.

## Provide Recommendations

Translate findings into actions.

#### Example
- Investigate causes of high-sales periods and replicate them.
- Monitor discount strategies.
- Focus marketing on top-performing categories.
- Analyze underperforming products and regions.

## Report Structure

1. Introduction: **Objective** of the analysis
2. Dataset Description: columns and data types
3. Data Quality Assessment: Missing values, duplicates, **assumptions**
4. [[Descriptive Statistics]]: Mean, Median, Std Dev
5. Visual Analysis
	- Bar Chart
	- Line Chart
	- Histogram
6. Key Findings: Patterns, trends, outliers
7. Business Implications and Recommendations
8. Conclusion: main takeaways and next steps