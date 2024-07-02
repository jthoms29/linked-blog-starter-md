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
**Find the mean of the dataset**:
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


# Mean, Median and Mode in Histograms: Skewness <!--fc-->
If the shape of a histogram isn't too bizarre, we may determine the *skewness* of the dataset's histogram by comparing the mean or median to the mode.
==**Always compare to the mode**==
- A left skewed distribution will have a negative skewness value
- A symmetric distribution will have a skewness of 0
- A right skewed distribution will have a positive skewness value
<!--ID: 1719789154060-->


## Right skewed histogram <!--fc-->
Generally has the mean and median to the right, positive side
![[Pasted image 20240630091807.png]]
<!--ID: 1719789154067-->


## Left skewed histogram <!--fc-->
Generally ;has the mean and median to the left, negative side
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



