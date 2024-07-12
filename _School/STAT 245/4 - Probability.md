TARGET DECK
School::STAT 245::04 - Probability

# Experiment, Outcome, and Sample Space

## Experiment <!--fc-->
A process that, when performed, results in one and only one of many observations. The observations are called the outcomes, and the collection of outcomes for an experiment is called a sample space.

## Outcomes <!--fc-->
The observations made during an experiment
![[Pasted image 20240710195900.png]]

## Sample Space <!--fc-->
The collection of outcomes for an experiment
Denoted by $S = \{\}$
![[Pasted image 20240710195932.png]]

## Event <!--fc-->
A collection of one or more outcomes of an experiment

## Simple Event <!--fc-->
An event that includes one and only one of the final outcomes for an experiment, denoted by $E_{i}$

## Compound Event <!--fc-->
A collection of more than one outcomes for and experiment, denoted by $A$

# Calculating Probability

## Probability <!--fc-->
A numerical measure of the likelihood that a specific event will occur

## First Property of Probability <!--fc-->
The probability of any particular outcome occurring is between 0 and 1 (inclusive)
![[Pasted image 20240710223709.png]]
*$E_{i}$ is a single event*
*A is a compound event*

## Second Property of Probability <!--fc-->
The sum of probabilities for all simple events in an experiment is equal to 1.
![[Pasted image 20240710224301.png]]

## Equally likely outcomes <!--fc-->
Refer to two or more outcomes that have the same probability of occurrence

## The Classical Probability Rule <!--fc-->
Given that $E_{i}$ is a simple event and $A$ is a compound event, then
![[Pasted image 20240710230542.png]]

### ==\*\*==Example: Coin experiment
	![[Pasted image 20240710230633.png]]

### ==\*\*==Example: Die experiment
	![[Pasted image 20240710230717.png]]
	![[Pasted image 20240710230738.png]]

## Calculating Probability of Event from Chart <!--fc-->
![[Pasted image 20240710231205.png]]
A : Observer similar faces
	A = {$E_{1}$, $E_{4}$}
	Probability:
$$
P(A) = P(\text{HH}) + P(\text{TT}) = P(E_{1}) + P(E_{4}) = \frac{1}{4} + \frac{1}{4} = \frac{2}{4}
$$

# Marginal Probability, Conditional Probability, Related Probability Concepts

## Marginal/Simple Probability <!--fc-->
The probability of a single event without consideration of any other event.
*Example:*
	![[Pasted image 20240711152318.png]]
	The only consideration made is 'Male'

## Conditional Probability <!--fc-->
The probability that an event will occur given that another event has already occurred. If $A$ and $B$ are two evens, the conditional probability of $A$ given $B$ is written as:
![[Pasted image 20240711161145.png]]
*Example:*
	![[Pasted image 20240711161744.png]]
	Outcomes need to be both 'In favor' and 'Male' to be considered, and it is compared to number of males
	**Order matters, A given B, B is denominator**
	![[Pasted image 20240711162502.png]]

## Mutually Exclusive Events <!--fc-->
Events that can not occur together.
![[Pasted image 20240711162859.png]]

## Compliment of an Event <!--fc-->
The compliment of event $A$ denoted by $\bar{A}$ or $A^c$ is the event that included all outcomes for an experiment that are not in $A$\
![[Pasted image 20240711163218.png]]

## ==\*\*==Example: Complimentary events
	![[Pasted image 20240711164355.png]]

# Intersection of Events and the Multiplication Rule

## Intersection of Events <!--fc-->
Let $A$ and $B$ be two events defined in a sample space. The *intersection* of the events, denoted by $A \cap B$, represents the collection of outcomes that are common to both $A$ and $B$.
![[Pasted image 20240711165549.png]]
*Example*
![[Pasted image 20240711165737.png]]
*Denominator is total*

## Calculating Conditional Probability <!--fc-->
To calculate *conditional probability* for $A$ and $B$, then
1. The conditional probability of even $A$, given that event $B$ has occurred is:
	![[Pasted image 20240711175256.png]]
2. The conditional probability of event $B$, given that event $A$ has occurred is:
	![[Pasted image 20240711175337.png]]

## Independent Events <!--fc-->
The idea that one event does not affect the probability of the next event.
$A$ and $B$ are independent iff:
![[Pasted image 20240711175951.png]]
\*\***You can also check this using conditional probabilities in both orders**
*Example:*
	![[Pasted image 20240711195328.png]]


## Mutually Exclusive Events <!--fc-->
Two events $A$ and $B$ are *mutually exclusive* iff:
![[Pasted image 20240711183001.png]]


## ==\*\*==Example: Intersections and conditional probability
	![[Pasted image 20240711185714.png]]
	![[Pasted image 20240711185724.png]]
	![[Pasted image 20240711185754.png]]

# Union of Events and the Addition Rule

## Union <!--fc-->
The *union* of events $A$ and $B$, denoted by $A \cap B$, is the collection of events that belong either to $A$ or $B$ or both.
![[Pasted image 20240711193904.png]]

## Calculating the probability of a union <!--fc-->
The probability of the union of two events $A$ and $B$ is
![[Pasted image 20240711194414.png]]

# Counting Rule, Factorials, Combinations, Permutations

## Finding Total Outcomes <!--fc-->
Consider an experiment that is performed on two stages. If the first stage can be accomplished is $m$ ways and for each of those ways the second can be accomplished $n$ ways, the total number of ways to accomplish the experiment is $mn$
*Example:*
	![[Pasted image 20240711201502.png]]
If there is $k$ stages with $n_{1}$ ways to accomplish, then $n_{2}$ ways, etc., then the number of ways to accomplish the experiment is $n_{1}n_{2}n_{3}\dots n_{k}$
*Example:*
	![[Pasted image 20240711210034.png]]

## Calculating Combinations <!--fc-->
The number of $n$ distinct objects that can be formed, taking them $r$ at a time, is
![[Pasted image 20240711210512.png]]
**Order does not matter: ABC, CAB <- 1 combination**
*Example:*
	![[Pasted image 20240711210529.png]]


## Calculating Permutations <!--fc-->
The number of ways we can arrange $n$ distinct objects, taking them $r$ at a time is:
![[Pasted image 20240711211652.png]]
**Order matters: ABC, CBA <- 2 permutations
*Example:*
	![[Pasted image 20240711211707.png]]

## Number of ways to arrange entire set <!--fc-->
The number of ways to arrange an entire set of $n$ distinct items is
![[Pasted image 20240712074305.png]]
*Example:*
	![[Pasted image 20240712074330.png]]
			