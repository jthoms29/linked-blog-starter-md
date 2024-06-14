TARGET DECK
Leetcode Blind 75::String

# Find the length of the longest substring of a string that doesn't have repeating characters <!--fc-->
Loop through the string with two pointers `start` and `end`, moving `end` up and adding each character to a hashset. If the character is already in there, keep removing the character at `start` and incrementing its pointer. At the end of each loop, check if the current substring length is greater than the record, use it as the record.
<!--ID: 1718294613776-->


# Find the longest palindromic substring of a given string <!--fc-->
There are two cases, even and odd.
For odd strings, loop through the string using two pointers each set to the current index, decrementing left and incrementing right in an inner while loop. Make sure they aren't out of bounds and contain the same character. Check if the current substring length is greater than the record each time. 
For even strings, just make the second pointer i+1. Do odd even one after another, the blocks will be  very similar
<!--ID: 1718294613791-->

# Find the number of palindromic substrings in a given string <!--fc-->
There are two cases, even and odd.
For odd strings, loop through using two pointers setting each to the current index, decrementing left and incrementing right in an inner while loop. Each time the pointers aren't out of bounds and have the same character, increment the the total palindrome count.
For even strings, do the same but set the `end` pointer to `i+1`
<!--ID: 1718295161832-->



