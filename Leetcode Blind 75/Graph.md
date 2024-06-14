TARGET DECK
Leetcode Blind 75::Graph
# Find the longest consecutive Sequence of numbers in a random array of numbers <!--fc-->
For O(1) time put the elements in a hash set, loop through the array until you find a number where n-1 doesn't exist. Then keep checking if n+1 exists in the set. Alternatively, O(nlogn) sorting and counting through normally may actually be faster
<!--ID: 1718293972029-->

# Make a deep clone of a given connected graph <!--fc-->
Make a new node with the same value as the given one and recursively loop through its neighbors cloning them as well. Add each clone to a hash map with the real node as a key and the clone as a value. Check before creating the clones to avoid getting stuck in an infinite loop of making the same clones over and over. If the cloned node is already exists, return it immediately.
<!--ID: 1718295161846-->

# See if there is a cycle in a linked list <!--fc-->
Use two pointers `fast` and `slow`, starting slow at the first node and fast at the second node. Each time, increment slow by one and fast by two. If fast is null or fast.next is null, return false. If fast is slow, return true. If there is a loop, they will meet each other eventually.
<!--ID: 1718295461471-->
