TARGET DECK
School::STAT 245::08 - Estimation of the Mean and Proportion

# Estimation, Point Estimate, and Interval Estimate

## Estimation <!--fc-->
The assignment of value(s) to a population parameter based in a value of the corresponding sample statistic
<!--ID: 1721952266821-->


## An estimate <!--fc-->
The value(s) assigned to a population parameter based on the value of a sample statistic
<!--ID: 1721952266829-->


## An estimator <!--fc-->
The sample statistic used to estimate a population parameter
<!--ID: 1721952266834-->


### Point estimator <!--fc-->
A single number calculated to estimate the population parameter, based on the sample data
<!--ID: 1721952266838-->


### Interval estimator <!--fc-->
Two numbers are calculated (based on the sample data) to form an interval within which the parameter is expected to lie.
<!--ID: 1721952266843-->


## ==\*\*==Point estimation Example
![[Pasted image 20240725110133.png]]

# Estimation of a Population Mean: $\sigma$ unknown

## Margin of error <!--fc-->
The *margin or error* for the estimate $\mu$, denoted by $E$, is the quantity that is subtracted from and added to the values of $\bar{x}$ to obtain a confidence interval for $\mu$. Thus:
![[Pasted image 20240725110518.png]]
![[Pasted image 20240725110527.png]]
*margin of error $E$ is not the percentage, it's the value you want to be within*
<!--ID: 1721952266847-->


## General Margin of Error equation <!--fc-->
$$
E = z\left( \frac{s}{\sqrt{ n }} \right)
$$
<!--ID: 1722011943628-->



## Find constants in margin of error calculation <!--fc-->
Find the absolute $< z$ value that corresponds to the wanted margin of error percentage
<!--ID: 1721952266851-->


## Determining sample size for an estimation of $\mu$ <!--fc-->
To determine the sample size of an estimation for a particular margin of error, reshape the equation
![[Pasted image 20240725111721.png]]
![[Pasted image 20240725111729.png]]![[Pasted image 20240725111737.png]]
<!--ID: 1721952266856-->


### Rounding sample size calculation <!--fc-->
Always round up to the next integer value.
<!--ID: 1721952266861-->



## ==\*\*==Mean estimation example <!--fc-->
![[Pasted image 20240725115121.png]]
![[Pasted image 20240725115200.png]]
When margin of error is not given, go with 95%
<!--ID: 1721952266868-->



## Interval Estimation for a normal population mean <!--fc-->
![[Pasted image 20240725115843.png]]
*YOU NEED TO INCLUDE THIS*
![[Pasted image 20240725120800.png]]
<!--ID: 1721952266874-->


## Interval size for greater confidence <!--fc-->
Greater confidence percentages cause wider intervals. Smaller ones will be fully contained in larger ones.
<!--ID: 1721952266880-->


## Confidence Coefficient <!--fc-->
The probability that a confidence interval will contain the estimated parameter.
<!--ID: 1721952266886-->


# Confidence Intervals For Small Samples

## t-statistic
Used for small samples ($n\leq30$), we use the t-statistic approach where
![[Pasted image 20240725121156.png]]


## Confidence intervals for small samples <!--fc-->
![[Pasted image 20240726110517.png]]
<!--ID: 1722043380711-->


## General Equation - Confidence interval for small sample <!--fc-->
$$
\bar{x} \pm t_{n-1, \frac{\alpha}{2}}\left( \frac{s}{\sqrt{ n }} \right)
$$
<!--ID: 1722043380715-->



## Using t-table <!--fc-->
$$
t_{n-1, \frac{\alpha}{2} }
$$
$n-1$ : total - 1   
	*row*
$\frac{\alpha}{2}$ : (1 - confidence percent) / 2      
	*column*
<!--ID: 1722043380719-->



## ==\*\*==Example: Small sample size <!--fc-->
![[Pasted image 20240726111348.png]]
![[Pasted image 20240726111400.png]]
<!--ID: 1722043380723-->



# Estimation of a Population Proportion: Large Samples

## Point estimator for proportion $p$ in large binomial population <!--fc-->
$$
\hat{p} = \frac{x}{n}
$$
<!--ID: 1722043380727-->


## Margin of error for proportion $p$ in large binomial population <!--fc-->
$$
E = z\sqrt{ \frac{\hat{p}(1-\hat{p})}{n} }
$$
<!--ID: 1722043380737-->



## ==\*\*==Example: Margin of error for proportion <!--fc-->
![[Pasted image 20240726115117.png]]![[Pasted image 20240726115126.png]]
$$
\hat{p}\pm z\sqrt{ \frac{\hat{p}(1-\hat{p})}{n} }
$$
![[Pasted image 20240726121604.png]]
<!--ID: 1722043380744-->





## Determining Sample size for the estimation of $p$ in proportion based on confidence level <!--fc-->
![[Pasted image 20240726115529.png]]
<!--ID: 1722043380749-->





