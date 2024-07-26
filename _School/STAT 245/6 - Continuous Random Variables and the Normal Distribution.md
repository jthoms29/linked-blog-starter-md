TARGET DECK
School::STAT 245::06 - Continuous Random Variables and the Normal Distribution

# The Normal Probability Distribution

## Probability density function of normal distribution <!--fc-->
The probability density of the normal distribution is
![[Pasted image 20240716093111.png]]
where
$$
\begin{gather}
\text{mean = expected value of x = }E(x) = \mu \\
\text{standard deviation = }\sigma = \sqrt{ \sigma^2 }
\end{gather}
$$
<!--ID: 1721308758246-->



## Normal probability distribution curve properties <!--fc-->
A normal probability distribution, when plotted, gives a bell-shaped curve such that
1. The total area under the curve is 1.0
2. The curve is symmetric about the mean
3. The two tails of the curve extend indefinitely
<!--ID: 1721308758259-->



## Standard normal distribution <!--fc-->
A normal distribution with $\mu =0$ and $\sigma =1$
![[Pasted image 20240716103803.png]]
<!--ID: 1721308758266-->



## What determines the shape of the normal distribution? <!--fc-->
The shape of the distribution is determined by $\sigma$, the population standard deviation.
- Large values of $\sigma$ reduce the height of the curve and increase the spread
- Small values of $\sigma$ increase the height of the curve and reduce the spread
![[Pasted image 20240716104037.png]]
<!--ID: 1721308758272-->




## Finding probability of variable lying within interval of normal curve <!--fc-->
To find the probability that a normal random variable $x$ lies in the interval $a$ to $b$, we need to find the area under the normal curve between the points $a$ and $b$.
![[Pasted image 20240716104330.png]]
<!--ID: 1721308758277-->



## Finding area under curve <!--fc-->
Split x value into 2 values
$$
1.63 = 1.6 + 0.03
$$
Find where these values intersect on the table.
<!--ID: 1721308758284-->


## Decimal Places Needed <!--fc-->
4
<!--ID: 1721308758289-->



## Finding probability of absolute value less than value <!--fc-->
$$
P(|z| \leq 1.41) = P(-1.41 \leq z \leq 1.41)
$$
<!--ID: 1721308758293-->



## Finding Probability of absolute value greater than value <!--fc-->
$$
P(|z| \geq 2.13) = P(z \geq 2.13) + P(z \leq -2.13)
$$
<!--ID: 1721308758298-->



## Finding z values given probability <!--fc-->
$$
P(Z \leq z) = 0.0119
$$
*find z*
If less than, look on chart
If greater than, subtract probability from 1 and then look on chart
<!--ID: 1721308758307-->



## Finding z values given probability with absolute value less than <!--fc-->
Get the compliment of the probability and divide it by 2. Find the value with probability and take the absolute value of it.
<!--ID: 1721308758315-->



## Finding z values give probability with absolute value greater than <!--fc-->
Divide the given probability by 2 and find the value with this probability. Take the absolute value of it.
<!--ID: 1721308758321-->




# Standardizing a Normal Distribution <!--fc-->
Most of the time, the probabilities involve $x$, a normal random variable with mean $\mu$ and standard deviation $\sigma$. The normal random variable is **standardized** be computing the $z$ value.
<!--ID: 1721308758326-->



## ==Finding $z$ value when standardizing normal distribution <!--fc-->
The standardized normal random variable, $z$, is defined as
$$
z = \frac{x-\mu}{\sigma}
$$
<!--ID: 1721308758330-->


## Properties of $z$ <!--fc-->
1. When $x$ is less than $\mu$, then $z$ is negative
2. When x is greater than $\mu$, $z$ is positive
3. When $x = \mu$, then $z = 0$
<!--ID: 1721308758335-->

## ==\*\*==Standardizing Normal Distribution Example <!--fc-->
- Example
	Let $x$ be a normally distributed random variable with a mean of 10 and a standard deviation of 2. Find $P(11\leq x\leq 13.6)$
	![[Pasted image 20240719105841.png]]
	![[Pasted image 20240719105848.png]]
<!--ID: 1721593271494-->



## Value outside of range after normalizing <!--fc-->
This will have a probability of either 0 or 1 as the graph extends infinitely +/-.
<!--ID: 1721593271504-->



## Finding missing $x$ value with un-normalized values
Work backwards. Find the value on the table that gives probability, and algebraically manipulate the formula to find the $x$ that gives $z$
*Remember, the normal table gives you the area to the left*
- Example:
	![[Pasted image 20240719115702.png]]


