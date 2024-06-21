TARGET DECK
Home::Leetcode Blind 75::Binary
# Missing Number: Given an array that should contain numbers in the range 0 - array length, find the number that is missing <!--fc-->
You can create an array with the expected range and xor all of the values together, and then xor that value with all of the values in the actual array. All of the similar numbers will eventually cancel out leaving you with the missing one. Alternatively, you could add up the two arrays and subtract the actual from the range.
<!--ID: 1718928237039-->



