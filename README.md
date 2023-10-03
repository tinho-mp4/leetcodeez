# ALL EASY LeetCode Solutions (JAVA)

Welcome to my collection of easy-level LeetCode solutions implemented in Java. In this repository, you'll find solutions to various easy-level LeetCode problems to help you improve your algorithmic problem-solving skills.

## Table of Contents

1. [Two Sum](#two-sum)
2. [Add Two Numbers](#add-two-numbers)
3. [Problem Title 3](#)
4. [Problem Title 4](#problem-title-4)
5. [Problem Title 5](#problem-title-5)


# Two Sum

### Intuition
My initial intuition for solving this problem is to use a hash map to store the elements of the array as we iterate through it. We can calculate the complement of each element with respect to the target value and check if it exists in the hash map. If it does, we have found the pair of elements that add up to the target.

### Approach
My approach involves iterating through the array once. For each element, I calculate its complement by subtracting it from the target value. Then, I check if this complement exists in the hash map. If it does, I've found a pair of elements that sum up to the target, and I return their indices. If not, I add the current element and its index to the hash map for future reference.

### Complexity
- Time complexity:
The time complexity of my solution is O(n), where n is the number of elements in the input array. This is because we iterate through the array once, and each hash map operation (insertion and lookup) takes O(1) time on average.

- Space complexity:
The space complexity of my solution is O(n) as well. This is because, in the worst case, we may need to store all n elements of the input array in the hash map.

### Code
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if  (map.containsKey(complement)) {
                return new int[] { map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}

```

# Add Two Numbers

### Intuition
My initial intuition for solving this problem is to simulate the addition process that we do manually when adding two numbers. We can start from the head of both linked lists and iterate through them while keeping track of the carry value. We'll create a new linked list to store the result.

### Approach
My approach involves simulating the addition process by iterating through the two linked lists simultaneously. At each step, I add the values from both lists along with the carry from the previous step. If the sum is greater than 9, I update the carry. I create a new node with the digit in the units place of the sum and append it to the result linked list. I continue this process until I have processed both input linked lists.

### Complexity
- Time complexity:
The time complexity of my solution is O(max(n, m)), where n and m are the lengths of the two input linked lists. We iterate through both lists once, and the number of iterations depends on the longer of the two lists.

- Space complexity:
The space complexity of my solution is O(max(n, m)), where n and m are the lengths of the input linked lists. This is because we create a new linked list to store the result, and its length can be at most max(n, m) + 1.

### Code
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode dummyHead = new ListNode(0);
    ListNode current = dummyHead;
    int carry = 0;
    while (l1 != null || l2 != null) {
        int sum = carry;
        if (l1 != null) {
            sum += l1.val;
            l1 = l1.next;
        }
        if (l2 != null) {
            sum += l2.val;
            l2 = l2.next;
        }
        ListNode newNode = new ListNode(sum % 10);
        carry = sum / 10;
        current.next = newNode;
        current = newNode;
    }
    if (carry > 0) {
        ListNode newNode = new ListNode(carry);
        current.next = newNode;
    }
    return dummyHead.next;
}

}
```
