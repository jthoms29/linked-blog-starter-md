TARGET DECK
School::STAT 245::02 - Descriptive Statistics - Frequency Data (Counting)

# Relative Frequency <!--fc-->
$$
\frac{\text{frequency of category}}{\text{sum of all frequencies}}
$$
*2 or 3 significant figures*.
- All relative frequencies should sum to 1.
<!--ID: 1719942261261-->

# Frequency Tables

## Steps for Constructing a Frequency Table <!--fc-->
The construction of a frequency table proceeds in two steps:
**Step 1:**
Determine the classes. Either the classes are *pre-defined* or you have to define the classes based on the number of groups you want
**Step 2:** 
Construct the frequency table and fill it in
<!--ID: 1719286673922-->


## Defining Classes for Frequency Tables <!--fc-->
**Steps**:
- Determine high data limit $H$, and the low data limit $L$.
- Compute the range:
$$
R = H - L
$$
- Compute the class width:
$$
W = \frac{R+1}{G}
$$
*Where $G$ is the number of groups (or classes) you want.*
- Begin the frequency table's first two columns:
![[Pasted image 20240624203948.png]]
*If the classes are given, you wont have or need the second column*
<!--ID: 1719286673933-->


### Class Range <!--fc-->
$$
R = H-L
$$
(limits, not boundaries)
<!--ID: 1719958144960-->


### Class Width <!--fc-->
Upper boundary - Lower Boundary
*i.e. the .5 values*
*or*
$$
\frac{\text{Range + 1}}{\text{number of classes}}
$$
<!--ID: 1719958078872-->


### Class Midpoint <!--fc-->
$$
\frac{\text{Upper limit + Lower limit}}{2}
$$
*i.e. NOT the .5 values, not boundaries
<!--ID: 1719958078877-->


### Class Boundary <!--fc-->
The midpoint of the upper limit of one class and the lower limit of the next class
![[Pasted image 20240702120124.png]]
<!--ID: 1719958078882-->

### Class Limits <!--fc-->
The standard upper and lower values of the class
<!--ID: 1719958078849-->


The columns feature a specific way of labelling classes. This is to make the class names useful for seeing that the classes are uniquely defined - there will be no data points on the boundaries of the classes

## Constructing a frequency table <!--fc-->
- Class
- Class Boundaries
- Tally$^*$
- Frequency
- Cumulative Frequency
- Relative Frequency
![[Pasted image 20240624205858.png]]
*$^*$The tally column is optional*
<!--ID: 1719286673942-->


## $n$ in relative frequency column <!--fc-->
The last number in the cumulative frequency column, $n$, should equal number of data points as a check since it is the sum of the frequencies. The sum of the relative frequencies will be 1.
<!--ID: 1719286673951-->

## What columns use limits or boundaries <!--fc-->
- Range - limit
- Midpoint - limit
- Width - boundaries
Width is the only calculation that uses the boundaries i.e. the .5 values
<!--ID: 1719958446500-->


## ==Examples @@@@@@@@@@@@@@@@@@@@@@==

-  FREQUENCY TABLE CONSTRUCTION EXAMPLE 1:
	25 army inductees were tested for blood type. The data are:

	![[Pasted image 20240624210605.png]]
	**Step 1**: Classes given: A B O AB
	**Step 2**: Construct frequency table:
	![[Pasted image 20240624210658.png]]


- FREQUENCY TABLE CONSTRUCTION EXAMPLE 2:
	Given the high temperature data for each of the 50 states for the month of July, construct a frequency table using 7 classes:

	![[Pasted image 20240625112409.png]]

	**Step 1**:
	(a)
	- High limit, H = 134
	- Low limit, L = 100
	(b)
	- Range: 
	$$R = H - L = 34$$
	(c)
	- Class width:
	$$
	W = \frac{R+1}{G} = \frac{34+1}{7}=5
	$$
	**Step 2**:
	![[Pasted image 20240625112937.png]]

==@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@==

# Plotting Frequency Data <!--fc-->
After constructing a frequency table, there are multiple different graphical ways that you can represent the data
- Histogram - plot of frequency data using steps
- Frequency polygon - plot of frequency data using straight lines
- Cumulative frequency graph
- Pie charts, Pareto charts, Stem & Leaf Plots
<!--ID: 1719351462270-->


## Histograms <!--fc-->
A bar graph plotting the frequency column in the frequency table
![[Pasted image 20240625114522.png]]
<!--ID: 1719351462275-->

### frequency value of bar graph <!--fc-->
The base value, no other calculations
<!--ID: 1719958078888-->



### Relative Frequency Histogram <!--fc-->
A bar graph plotting the relative frequency column of the frequency table
![[Pasted image 20240625132317.png]]
*This is not the correct graph, not in the textbook*
Define the width of each class to be 1, and the sum of each area will sum to one
$$
(0.2*1) + (0.28 * 1) + (0.36 * 1) + (0.16 * 1) = 1.00
$$
So, relative frequencies may be interpreted this way
![[Pasted image 20240625132609.png]]
<!--ID: 1719351462280-->


## Frequency Polygons <!--fc-->
Another form of histogram. Has a smoother curve than a traditional histogram
![[Pasted image 20240625133414.png]]
*Relative frequency of blood-types example*
<!--ID: 1719351462284-->


## Cumulative Frequency Graph <!--fc-->
Plotting the cumulative frequencies from the frequency table results in a cumulative frequency graph. It represents the probability of having a value equal to or less than the given value f that quantity is pulled at random from the population
![[Pasted image 20240625133559.png]]
<!--ID: 1719351462293-->


## Pie Chart <!--fc-->
A round histogram. The angles in the pie chart are computated using:
$$
Angle = \text{Relative Frequency} \times 360^{ o }
$$
![[Pasted image 20240625134011.png]]
![[Pasted image 20240625134019.png]]
<!--ID: 1719351462301-->


## Pareto Chart <!--fc-->
An ordered histogram with classes ordered from highest to lowest frequencies. The classes need to be qualitative for this to make sense.
![[Pasted image 20240625134133.png]]
<!--ID: 1719351462307-->


## Stem and Leaf Plots <!--fc-->
A fancy kind of histogram that lets you see all data instead of just class frequency information
The steps for making a stem and leaf plot are:
- Order the data
- Divide into classes of 10's or 5's (low decade and high decade)
- Use "leading" and "trailing" digits of the data values to make the plot
The first number of each data point is the **stem**, the trailing digit is the **leaf**.
![[Pasted image 20240625153455.png]]
This way you can visualize frequency information *and* see values of the individual data points as well.
<!--ID: 1719351491555-->


### Leading and Trailing Digits <!--fc-->
Given classes: 50-54, 55-59, 60-64, 65-69, 70-74, 75-78
Divide the classes into 5's and the data *in order*
$$
|50,51,51,52,53,53,|55,55,56,57,57,58,59,|62,63,|65,65,66,66,67,67,69,69,
|72,73,|75,75,77,78,79|
$$
Where bars illustrate the division of the data into low and high decades.
<!--ID: 1719351462314-->
