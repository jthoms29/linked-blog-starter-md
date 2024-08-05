TARGET DECK
School::STAT 245::11 - Chi-Square Tests

# Goodness-of-Fit Test

## Multinomial Experiment <!--fc-->
- Consists of $n$ identical trials
- The outcome of each trial falls into one of $k$ categories
- The probability that the outcome of a single trial falls into a particular category $i$ is $p_{i}$, and remains constant form trial to trial.
	*This probability must be between 0 and 1*
	$$
\sum_{i}^{k}p_{i}=1
$$
- Trials are independent
- The experimenter counts the observed number of outcomes in each category, written as
$$
O_{1} + O_{2} + \dots + O_{k} = n
$$
<!--ID: 1722639780159-->



## Multinomial Experiment Probability Equation <!--fc-->
Will not use.
![[Pasted image 20240802112655.png]]
<!--ID: 1722639780174-->



## Multinomial Hypothesis <!--fc-->
$$H_{0} : P_{1} = p_{1}, P_{2} = p_{2}, \dots P_{k} = p_{k}
$$
vs.
$$
H_{1} : \text{At least one probability is different}
$$
<!--ID: 1722639780184-->



### Chi-Square Test <!--fc-->
Used for multinomial hypothesis tests.
$$
\chi^2 = \sum_{i=1}^{k}\frac{(O_{i}-E_{i})^2}{E_{i}}
$$
Summed over $k$ cells with
$$
E_{i} = np_{i}
$$
	(expected Observation count) (will also all sum to 1)
\\
![[Pasted image 20240802113707.png]]
Always right tailed, since it is squared.
<!--ID: 1722639780194-->




### ==\*\*== Multinomial Hypothesis Example <!--fc-->
![[Pasted image 20240802114248.png]]
![[Pasted image 20240802114258.png]]
![[Pasted image 20240802114311.png]]
You have to give a more detailed explanation. More than simple rejection. Talk about preference.
<!--ID: 1722639780222-->


### No $\alpha$ for $\chi^2$ given <!--fc-->
Use 0.05 by default.
<!--ID: 1722639780237-->



