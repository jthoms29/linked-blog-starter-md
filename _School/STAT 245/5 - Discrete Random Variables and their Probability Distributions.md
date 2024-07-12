TARGET DECK
School::STAT 245::05 - Discrete Random Variables and their Probability Distributions

# Random Variables

## Random Variable <!--fc-->
A variable who's outcome is determined by the outcome of a random experiment

## Discrete Random Variable <!--fc-->
A random variable that assumes countable values

## Continuous Random Variable <!--fc-->
A random variable that can assume any value contained in one or more intervals.

# Probability Distribution of a Discrete Random Variable

## Probability Distribution of Discrete Rand Var <!--fc-->
The probability distribution of a discrete random variable lists all the possible values that the random variable can assume and their corresponding probabilities
	The Requirements for a discrete probability distribution are:
	1:
	$$
0 \leq p(x) \leq 1
$$
	2:
	$$
\sum_{i=1}^{n}p(x_{i})=1
$$


### ==\*\*==Example
- Die, Coin
	In tossing a fair die, there is
	![[Pasted image 20240712094135.png]]
	In tossing a fair coin, there is
	![[Pasted image 20240712094152.png]]

	In tossing and unfair die:
	![[Pasted image 20240712094212.png]]
	![[Pasted image 20240712094225.png]]


# Mean and Standard Deviation of a Discrete Random Variable

## Mean or expected value of discrete random variable <!--fc-->
Let $x$ be a discrete random variable with probability distribution $p(x)$.
The *mean or expected value of $x$ is:*
$$
\mu=E(x)=\sum_{i=1}^{n}x_{i}p(x_{i})
$$
where the elements are summed over all values of the random variable $x$

## Variance of discrete random variable <!--fc-->
Let $x$ be a discrete random variable with probability distribution $p(x)$.
The *variance of $x$ is:*
![[Pasted image 20240712103551.png]]

# The Binomial Probability Distribution

## Binomial Experiment <!--fc-->
A *Binomial Experiment* is an experiment that has these five characteristics:
- The experiment consists of $n$ identical trials
- Each trial results in one of two outcomes (e.g.: success, fail)
- The probability of success on a single trial is equal to $p$ and remains the same from trial to trial. The probability of failure is equal to $q = (1-p)$
- The trials are independent
- We are interested in $x$, the number of successes observed during the $n$ trials, for $x = 0,1,2,\dots,n$

### ==\*\*==Binomial Experiment Example:
![[Pasted image 20240712104241.png]]

## The probability of $k$ successes in a binomial experiment <!--fc-->
A binomial experiment consists of $n$ identical trials with probability of success $p$ on each trial. The probability of $k$ successes in $n$ trials is:
![[Pasted image 20240712104440.png]]
for all values of $k = 0,1,2,\dots,n$

