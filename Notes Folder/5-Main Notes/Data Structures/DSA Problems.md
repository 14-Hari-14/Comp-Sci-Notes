
2025-02-28 19:18

Tags: #dsa #leetcodeproblems

# DSA Problems

## Two Sum

Link: https://leetcode.com/problems/two-sum/description/?utm_source=instabyte.io&utm_medium=referral&utm_campaign=interview-master-100
### Approaches
- #### Brute Force
	- Time Complexity: O(n^2)
	- Space Complexity: O(1) (no extra space used)
	- Make 2 for loops and check each pair of numbers to see if they give the sum
- #### Using Hashmap
	- Time Complexity: O(n)
	- Space Complexity: O(n) (n elements stored in the hashmap)
	- Make an empty hashmap (fancy word for dictionary) iterate through the array if the element not in the hashmap add it and check if the complement of the element is present.
		- for example if the target is 9 and the element we have right now is 2 check the hashmap for a 7. If its there return the indexes of 2 and 7 stored as values in the hashmap. Else keep looking through the loop


## Valid Parenthesis

Link: https://leetcode.com/problems/valid-parentheses/description/?utm_source=instabyte.io&utm_medium=referral&utm_campaign=interview-master-100

### Approaches
- #### Make a stack
	- Add the opening parenthesis to the stack `(, [ , {
	- if the closing parenthesis appears compare it with the top of the stack if the match is correct pop the top else return false


##

# References
---


	