TARGET DECK
Home::Leetcode Blind 75::Arrays
# Two Sum: Find two indexes in array such that the elements that add to given number <!--fc-->
To solve in O(n) time, put each element into a hashmap with the elements as keys and the indexes as values. Iterate through the array and check if the map has `number - element` in it. If it does and the value isn't the current index, return the index and the map's value.
<!--ID: 1718928213464-->


# Container With Most Water: Using an array with random values, find the largest area of water that can be held by two heights in the array. <!--fc-->
Use two pointers; `start` and `end` starting at the start and end of the array, finding the current area by min(start, end) * (start - end). If its greater than the current record, swap it out. Increment the pointer with the lowest value each time.
<!--ID: 1718928213490-->


# 3Sum: Given an array of integers, find each unique set of three numbers that add up to 0 <!--fc-->
Sort the array, and loop through the numbers. For each number, use two pointers set to i+1 and length-1, and if they aren't equal to -number, either increment the left or decrement the right depending on if it's greater or less. Each time they are equal, add it to the solution list. Stop when left !< right
<!--ID: 1718928213503-->

# Maximum Product Subarray: Given an array, find the maximum product that can be computed from a contiguous subarray <!--fc-->
Set result to first element of array, and make variables for current (the current element) min and max.
For each new element in the array, check if the current max is:
- current max * n
- current min * n (because of negative * negative)
- or just n
Do the same thing for the minimum (for min * n calculation)
At the end of each loop check if the current max is larger than the result. If so, swap them.
<!--ID: 1721593271511-->

# Maximum Subarray: Given an array, find the maximum sum that can be computed from a contiguous subarray <!--fc-->
Set result to first element of the array. Make a variable the curMax set to 0.
Iterate linearly through the array, checking to see if the maximum current value is curMax + n or just n. Then check to see if curMax is greater than the result, and swap it out if true.
<!--ID: 1721655481320-->





