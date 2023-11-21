#1. Two Sum (Easy)

Question 

	Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
	You may assume that each input would have exactly one solution, and you may not use the same element twice.
	You can return the answer in any order.
	
	Example 1:
		Input: nums = [2,7,11,15], target = 9
		Output: [0,1]
		Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
	
	Example 2:
		Input: nums = [3,2,4], target = 6
		Output: [1,2]
	
	Example 3:
		Input: nums = [3,3], target = 6
		Output: [0,1]
	 
	
	Constraints:
		2 <= nums.length <= 10^4
		−10^9  <= nums[i] <= 10^9
		−10^9  <= target <= 10^9
		Only one valid answer exists.

	Follow-up: Can you come up with an algorithm that is less than O(n^2) time complexity?

Solution

	create a hash table "dct"
 	Think abot the nums[u], each judgement the different, target substrat input, in dct. 
  if true, return the answer. Or not, the input is stored in dct.
  
	Example 2:
	Index 0, Input =3
	Target -Input  = 3 => Not exist in dct.
	dct = [3]
	Index 1, Input =2
	Target -Input  = 4 => Not exist in dct.
	dct = [3, 2]
	Index 2, Input =4
	Target -Input  = 2 => Exist in dct.
	Return [1, index]
	dct = [3, 2]


```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dct = {}
        for i,v in enumerate(nums):
            if target-v in dct :
                return [dct[target-v],i]
            dct[v]=i
```
Runtime: 71 ms 
Memory Usage: 17.67 MB


Time complexity O(n)
Space Complexity: O(N)

Brute Force
Time Complexity: O(N^2)
Space Complexity: O(1)

More information about Leetcode #1 solution
https://ithelp.ithome.com.tw/articles/10292023


#2.Add Two Numbers (Medium)
Question

	You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.	
	You may assume the two numbers do not contain any leading zero, except the number 0 itself.
	
	Example 1:
	Input: l1 = [2,4,3], l2 = [5,6,4]
	Output: [7,0,8]
	Explanation: 342 + 465 = 807.
	
	Example 2:
	Input: l1 = [0], l2 = [0]
	Output: [0]
	
	Example 3:
	Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
	Output: [8,9,9,9,0,0,0,1]
	
	Constraints:
	The number of nodes in each linked list is in the range [1, 100].
	0 <= Node.val <= 9
	It is guaranteed that the list represents a number that does not have leading zeros.


思維: 

	1. LinkedNode 
 ![image](https://github.com/RaleighGithub/LeetcodeNote/assets/74161529/b3c9d08a-2be3-4074-bb07-3232d370a66d)
 
	2. If l1 or l2 is None, and return another one. All are None, and return 0. It is a condition, thus the while-loop is better than for-loop. 
	3. A temp variable is stored l1 and l2 value, and check it whether to carry.
	
```python3
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        result = ListNode(0)
        node = result
        temp = 0
        while l1 is not None or l2 is not None or temp>0:
            if l1 is not None:
                temp += l1.val
                l1 = l1.next
            if l2 is not None:
                temp += l2.val
                l2 = l2.next
            node.next = ListNode(temp%10)   # 取個位數
            node = node.next
            temp = temp // 10    # 檢查是否要進位
        return result.next
```
Runtime: 51 ms 
Memory Usage: 13.26 MB
Time Complexity: O(N)
Space Complexity: O(N)
