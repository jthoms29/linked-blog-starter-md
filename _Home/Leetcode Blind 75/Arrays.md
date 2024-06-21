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





