TARGET DECK
Leetcode Blind 75::Arrays
# Find two indexes in array such that the elements that add to given number <!--fc-->
To solve in O(n) time, put each element into a hashmap with the elements as keys and the indexes as values. Iterate through the array and check if the map has `number - element` in it. If it does and the value isn't the current index, return the index and the map's value.
<!--ID: 1718255201822-->

# Using an array with random values, find the largest area of water that can be held by two heights in the array. <!--fc-->
Use two pointers; `start` and `end` starting at the start and end of the array, finding the current area by min(start, end) * (start - end). If its greater than the current record, swap it out. Increment the pointer with the lowest value each time.
<!--ID: 1718295461478-->




