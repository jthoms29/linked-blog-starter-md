TARGET DECK
School::STAT 245::10 - Estimation and Hypothesis Testing - Two Populations


# Confidence Intervals for large samples

## Confidence interval between two large populations
If sample size $n_{1} > 30$ and $n_{2}>30$, then:
![[Pasted image 20240731112440.png]]
![[Pasted image 20240731112451.png]]


### General equation for confidence interval between two large populations <!--fc-->
$$
(\bar{x_{1}}-\bar{x_{2}}) \pm z\sqrt{ \left( \frac{s_{1}^{2}}{n_{1}} \right)+\left( \frac{s_{2}^{2}}{n_{2}} \right) }
$$
In which $z$ is the $z$ value of the desired confidence percentage.
**If 0 is in the confidence interval, they are similar. If not, they are different.**
<!--ID: 1722463622866-->



### ==\*\*== Confidence interval between two large populations example <!--fc-->
	![[Pasted image 20240731113202.png]]
	![[Pasted image 20240731113211.png]]
	Conclusion depends on inclusion of 0.
<!--ID: 1722463622873-->


# Confidence Intervals for Small Samples

## Confidence Interval Between two small populations
If sample size $n_{1} <- 30$ or $n_{2}\leq 30$ or both, then:
==**OR**==
![[Pasted image 20240731115709.png]]
![[Pasted image 20240731115719.png]]



### General Equation for confidence interval with one or more small populations <!--fc-->
![[Pasted image 20240731115944.png]]
<!--ID: 1722463622879-->


### Combined standard deviation <!--fc-->
Where $s_{p}$ is the combined standard deviation
![[Pasted image 20240731120136.png]]
<!--ID: 1722463622884-->


### ==\*\*== Confidence interval between small samples example
![[Pasted image 20240731121719.png]]
![[Pasted image 20240731121728.png]]


# Hypothesis Testing two Large Samples

## Statistical tests of hypotheses for $\mu_{1}-\mu_{2}$ <!--fc-->
![[Pasted image 20240801105645.png]]
Null hypothesis always $\mu_{1}-\mu_{2}=0$
The level of significance for a statistical test of hypothesis is:
![[Pasted image 20240801105733.png]]
<!--ID: 1722639780249-->



## Critical Value Testing for two large populations <!--fc-->
![[Pasted image 20240801105852.png]]
$$
\frac{\bar{x_{1}}-\bar{x_{2}}}{\sqrt{ \frac{s_{1}^2}{n_{1}}+\frac{s_{2}^2}{n_{2}} }}><z
$$
Do not divide $\alpha$ by 2 to get $z$ value if single-tailed.
<!--ID: 1722639780260-->



# Hypothesis Testing for one or two small samples

## Critical value testing for at least one small sample <!--fc-->
![[Pasted image 20240801113206.png]]
Do not divide $\alpha$ by 2 when finding $t$ value if single tailed.
<!--ID: 1722639780271-->



# Confidence Intervals for two Population Proportions

## Confidence intervals for two proportions <!--fc-->
![[Pasted image 20240801115400.png]]
![[Pasted image 20240801115408.png]]
<!--ID: 1722639780281-->



## ==\*\*== Confidence Interval for two proportions example <!--fc-->
![[Pasted image 20240801120500.png]]
![[Pasted image 20240801120510.png]]
<!--ID: 1722639780292-->



# Hypothesis Testing about two population proportions

## Hypothesis tests for population proportions <!--fc-->
![[Pasted image 20240801120750.png]]
<!--ID: 1722639780301-->



## Hypothesis tests for two population proportions equations <!--fc-->
![[Pasted image 20240801120913.png]]
<!--ID: 1722639780312-->


## General $\hat{p}$ for two proportions <!--fc-->
![[Pasted image 20240801120926.png]]
Will always be in between $\hat{p}_{1}$ and $\hat{p}_{2}$
Just use this:
$$
\frac{x_{1}+x_{2}}{n_{1}+n_{2}}
$$
<!--ID: 1722639780322-->



## Strong Rejection <!--fc-->
![[Pasted image 20240802110711.png]]
If the resulting p-value is smaller than $\alpha$ by a large amount, you can strongly reject the null hypothesis.
<!--ID: 1722639780332-->


