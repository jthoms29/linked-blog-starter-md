TARGET DECK
School::STAT 245::03 - Descriptive Statistics - Central Tendency and Dispersion

# Central Tendency: Mean, Median, Mode

## Mean <!--fc-->
The mean is the average of the data.
<!--ID: 1719635239022-->


### Sample mean <!--fc-->
Denoted by $\bar{x}$
Formula:
$$
\bar{x}=\frac{\left( \sum_{i=i}^{n}x_{i} \right)}{n}
$$
where $n$ is the number of data points in the sample, the *sample size*.
<!--ID: 1719635239031-->


### Population mean <!--fc-->
Denoted by $\mu$
Formula:
$$
\mu=\frac{\left( \sum_{i=1}^{N}x_{i} \right)}{N}
$$
where $N$ is the size of the population.
<!--ID: 1719635239036-->

### Combined Mean <!--fc-->
$$
\text{ Combined Mean = } \frac{(n_{1}\bar{x_{1}}+n_{2}\bar{x_{2}})}{n_{1}+n_{2}}
$$
The mean of two separate groups given their respective means and sample sizes.
<!--ID: 1720148899057-->



### Mean for grouped data <!--fc-->
If you have the frequency table for a dataset but not the actual data, you can still compute the *approximate* mean of the dataset.
$$
\bar{x}=\sum_{i=1}^{G}\frac{f_{i}x_{m_{i}}}{n}
$$
Where 
- $f_{i}$ is the frequency of the group $i$, 
- $x_{m_{i}}$ is the *class center* of group $i$ and 
- $n$ is the number of data points in the original dataset.
	- Recall that $n = \sum_{}^{}f_{i}$ so we can write the formula as:
$$
\bar{x}=\frac{\sum_{i=1}^{G}f_{i}x_{m_{i}}}{\sum_{i=1}^{G}f_{i}}
$$
	which is a form that more closely matches with a generic weighted mean formula.
<!--ID: 1719635239041-->


#### Class center <!--fc-->
$x_{m_{i}}$: The midpoint of the class boundary
	*If a class boundary went from 5.5 - 10.5, the center would be 8*
<!--ID: 1719635239046-->


### ==Example==
- **Find the mean of the dataset**:
	![[Pasted image 20240629154841.png]]
	- The first step is to find the formula to cue you to what quantities you need to compute
$$
\bar{x}=\frac{\sum_{i}^{}f_{i}x_{m_{i}}}{n}
$$
	When subbing in the values from the table
$$
\frac{490}{20} = 24.5
$$


## Median <!--fc-->
The symbol we use for median is MD
It is the midpoint of the data set with the data put in order.
- If there are an odd number of points, MD is the middle number
- If there are an even number of points, MD is the average of the two data points
<!--ID: 1719721841825-->


## Mode <!--fc-->
In a given dataset the mode is the data value that occurs the most
- There may not be a mode
- There may be more than one node
![[Pasted image 20240629222253.png]]
<!--ID: 1719721841833-->


### Mode of frequency table <!--fc-->
The class with the highest frequency
<!--ID: 1719721841838-->


## Midrange <!--fc-->
The midrange, MR, is defined simply by
$$
MR = \frac{H+L}{2}
$$
Where *H* and *L* are the high and low data values.
<!--ID: 1719721841843-->


## Range of Dataset <!--fc-->
The *range* of a set of n measurements is the difference between the largest and smallest measurements
$$
2,3,4,6,10
$$
$$
max(x)-min(x) = 10 -2=8
$$
<!--ID: 1720307195644-->




# Mean, Median and Mode in Histograms: Skewness <!--fc-->
If the shape of a histogram isn't too bizarre, we may determine the *skewness* of the dataset's histogram by comparing the mean or median to the mode.
==**Always compare to the mode**==
- A left skewed distribution will have a negative skewness value
- A symmetric distribution will have a skewness of 0
- A right skewed distribution will have a positive skewness value
<!--ID: 1719789154060-->


## Right skewed histogram <!--fc-->
Generally has the mean and median to the right, positive side
**median in the middle**
![[Pasted image 20240630091807.png]]
<!--ID: 1719789154067-->


## Left skewed histogram <!--fc-->
Generally has the mean and median to the left, negative side
**median in the middle**
![[Pasted image 20240630091928.png]]
<!--ID: 1719789154072-->


# Mean, Median, Mode in Distributions: Geometric Aspects
To understand the geometric aspects of histograms we make the abstraction of letting the class widths shrink to zero, so that the histogram curve becomes smooth.

## Geometric Aspects of Mode <!--fc-->
The mode is the *x* value where the frequency *f(x)* is maximum. The mode is a "local maximum" of the histogram (if there are multiple modes, they don't all have to have the same maximum value)
![[Pasted image 20240630153147.png]]
<!--ID: 1719789154076-->


## Geometric Aspects of Median <!--fc-->
The area under the curve is equal on either side of the median
![[Pasted image 20240630154736.png]]
<!--ID: 1719789154081-->


## Geometric Aspects of Mean <!--fc-->
The mean is the balance point of the histogram/distribution
![[Pasted image 20240630154824.png]]
<!--ID: 1719789154086-->

# Measures of Dispersion for Ungrouped Data

## Variance/Standard Deviation definition <!--fc-->
Variance and its square root; standard deviation, measure how 'wide' or 'spread out' a data distribution is.
<!--ID: 1720148899061-->


## Variance of a population formula <!--fc-->
The **variance of a population** of $N$ measurements, about their given mean $\mu$, is given by:
$$
\sigma^2=\frac{\left( \sum_{i=1}^{N}(x_{i}-\mu)^2 \right)}{N}
$$
<!--ID: 1720148899065-->


## Variance of a sample formula <!--fc-->
The **variance of a sample** of $n$ measurements about their given average $\bar{x}$ is given by:
![[Pasted image 20240704202058.png]]
<!--ID: 1720148899069-->


## Standard deviation of a sample formula <!--fc-->
The **standard deviation** of a set of measurements is equal to the positive square root of the variance:
![[Pasted image 20240704202241.png]]
<!--ID: 1720148899081-->


## Large $S$ value meaning <!--fc-->
The larger the variance, the greater the variability of the dataset
<!--ID: 1720148899087-->

==--*quiz 1 until here*==

## Coefficient of Variation <!--fc-->
CVar: a normalized measure of data spread
*For samples:*
$$
\text{CVar} = \frac{s}{\bar{x}}*100\%
$$
*For populations:*
$$
\text{CVar}= \frac{\sigma}{\mu}*100\%
$$
<!--ID: 1720148899096-->

# Variance of a grouped sample <!--fc-->
The **Variance of a grouped sample**:
![[Pasted image 20240705073423.png]]
where $n = \sum_{i=1}^{n}f_{i}$.
<!--ID: 1720307195651-->



# Measures of Position

## Quartiles <!--fc-->
Three summary measures that divide a ranked data set into four equal parts
<!--ID: 1720307195655-->


## First Quartile <!--fc-->
$Q_{1}$
The median of all values less than the median
<!--ID: 1720307195660-->


## Third Quartile <!--fc-->
$Q_{3}$
The median of all values greater than the median
<!--ID: 1720307195665-->


## Second Quartile <!--fc-->
$m$
The median
<!--ID: 1720307195669-->


## Interquartile Range <!--fc-->
$$
\text{IQR} = Q_{3} - Q_{1}
$$
<!--ID: 1720307195673-->


## Five-Number Summary <!--fc-->
The *five-number summary* of a dataset consists of the
- Smallest number
- First quartile
- Median
- Third quartile
- Largest
$$
\text{Min }Q_{1}\text{ Median }Q_{3}\text{ Max}
$$ 
<!--ID: 1720543134998-->


## Box-and-Whisker Plot <!--fc-->
The *lower and upper inner fences* of a dataset are
$$
\begin{gather}
\text{Lower inner fence} = Q_{1} -(1.5)\text{IQR} \\
\text{Upper inner fence}=Q_{3}+(1.5)\text{IQR}
\end{gather}
$$
<!--ID: 1720543135013-->



### Outliers <!--fc-->
If a data point lies outside the fences, it is considered an *outlier*
<!--ID: 1720543135027-->



# Percentiles
## Calculating Percentiles 
To calculate percentiles, $P_{i}$, let $i$ be the ordered position of a data set of $n$ data points, then let the percentile position of $x_{i}$ to be
![[Pasted image 20240708104623.png]]
where $n$ represents sample sizes

## Calculate position from percentile 
If you want to find the position, $i$ of the data point corresponding to a given percentile $P$, then compute
![[Pasted image 20240708104800.png]]



