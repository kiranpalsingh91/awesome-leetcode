- [Solutions](#solutions)
  - [1. Two Sum](#1-two-sum)
  - [2. Add Two Numbers](#2-add-two-numbers)
  - [3. Linked List Cycle](#3-linked-list-cycle)
  - [4. Container With Most Water](#4-container-with-most-water)
  - [5. Remove Nth Node From End of List](#5-remove-nth-node-from-end-of-list)
  - [6. Reverse Words in a String](#6-reverse-words-in-a-string)
  - [7. Valid Parentheses](#7-valid-parentheses)
  - [8. Implement Queue using Stacks](#8-implement-queue-using-stacks)
  - [9. Next Greater Element - I](#9-next-greater-element---i)
  - [10. Backspace String Compare](#10-backspace-string-compare)
  - [11. Min Stack](#11-min-stack)
  - [12. Next Greater Element - II](#12-next-greater-element---ii)
  - [13. Course Schedule](#13-course-schedule)
  - [14. Longest Increasing Path in Matrix](#14-longest-increasing-path-in-matrix)
  - [15. Number of Islands](#15-number-of-islands)
  - [16. Longest Consecutive Sequence](#16-longest-consecutive-sequence)
  - [17. Transpose Matrix](#17-transpose-matrix)
  - [18. Merge Two Sorted List](#18-merge-two-sorted-list)
  - [19. Remove Duplicates From Sorted List](#19-remove-duplicates-from-sorted-list)
  - [20. Palindrome Linked List](#20-palindrome-linked-list)
  - [21. Middle of Linked List](#21-middle-of-linked-list)
  - [22. Intersection of Two Linked Lists](#22-intersection-of-two-linked-lists)
  - [23. Maximum Population Year](#23-maximum-population-year)
  - [24. Merge Intervals](#24-merge-intervals)
  - [25. Insert Intervals](#25-insert-intervals)
  - [26. Non Overlapping Intervals](#26-non-overlapping-intervals)
  - [27. Sort Array By Increasing Frequency](#27-sort-array-by-increasing-frequency)
  - [28. Kth Largest Element in an Array](#28-kth-largest-element-in-an-array)
  - [29. Top K Frequent Elements](#29-top-k-frequent-elements)
  - [30. Sort Characters By Frequency](#30-sort-characters-by-frequency)
  - [31. Maximum Number of Events That Can Be Attended](#31-maximum-number-of-events-that-can-be-attended)
  - [32. Climbing Stairs](#32-climbing-stairs)
  - [33. Pascals Triangle](#33-pascals-triangle)
  - [34. Best Time To Buy and Sell Stock](#34-best-time-to-buy-and-sell-stock)
  - [35. Jump Game](#35-jump-game)
  - [36. Unique Paths](#36-unique-paths)
  - [37. Flood Fill](#37-flood-fill)
  - [38. Is Graph Bipartite?](#38-is-graph-bipartite)
  - [39. Sort The People](#39-sort-the-people)
  - [40. Sort Array By Parity](#40-sort-array-by-parity)
  - [41. Count Nice Pairs in an Array](#41-count-nice-pairs-in-an-array)
  - [42. Count Number of Bad Pairs](#42-count-number-of-bad-pairs)
  - [43. Fair Distribution of Cookies](#43-fair-distribution-of-cookies)
  - [44. Sum of Left Leaves](#44-sum-of-left-leaves)
  - [45. Construct String From Binary Tree](#45-construct-string-from-binary-tree)
  - [46. Average of Levels in Binary Tree](#46-average-of-levels-in-binary-tree)
  - [47. Balanced Binary Tree](#47-balanced-binary-tree)
  - [48. Permutation - II](#48-permutation---ii)
  - [49. Combination Sum - II](#49-combination-sum---ii)
  - [50. Word Search](#50-word-search)
  - [51. Combination Sum](#51-combination-sum)
  - [52. Generate Parentheses](#52-generate-parentheses)
  - [53. Permutations](#53-permutations)

# Solutions

## 1. Two Sum

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> M;
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            int required = target - nums[i];
            if (M.count(required)) {
                return { M[required], i};
            }
            M[nums[i]] = i;
        }
        return {};
    }
};
```

## 2. Add Two Numbers

```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int carry = 0;
        ListNode dummy, *tail = &dummy;
        while(l1 || l2 || carry) {
            if(l1) {
                carry += l1->val;
                l1 = l1->next;
            }
            if(l2) {
                carry += l2->val;
                l2 = l2->next;
            }
            
            tail->next = new ListNode(carry % 10);
            carry /= 10;
            tail = tail->next;
        }
        
        return dummy.next;
    }
};
```

## 3. Linked List Cycle

```cpp

```

## 4. Container With Most Water

```cpp

```

## 5. Remove Nth Node From End of List

```cpp

```

## 6. Reverse Words in a String

```cpp

```

## 7. Valid Parentheses

```cpp

```

## 8. Implement Queue using Stacks

```cpp

```

## 9. Next Greater Element - I

```cpp

```

## 10. Backspace String Compare

```cpp

```

## 11. Min Stack

```cpp

```

## 12. Next Greater Element - II

```cpp

```

## 13. Course Schedule

```cpp

```

## 14. Longest Increasing Path in Matrix

```cpp

```

## 15. Number of Islands

```cpp

```

## 16. Longest Consecutive Sequence

```cpp

```

## 17. Transpose Matrix

```cpp

```

## 18. Merge Two Sorted List

```cpp

```

## 19. Remove Duplicates From Sorted List

```cpp

```

## 20. Palindrome Linked List

```cpp

```

## 21. Middle of Linked List

```cpp

```

## 22. Intersection of Two Linked Lists

```cpp

```

## 23. Maximum Population Year

```cpp

```

## 24. Merge Intervals

```cpp

```

## 25. Insert Intervals

```cpp

```

## 26. Non Overlapping Intervals

```cpp

```

## 27. Sort Array By Increasing Frequency

```cpp

```

## 28. Kth Largest Element in an Array

```cpp

```

## 29. Top K Frequent Elements

```cpp

```

## 30. Sort Characters By Frequency

```cpp

```

## 31. Maximum Number of Events That Can Be Attended

```cpp

```

## 32. Climbing Stairs

```cpp

```

## 33. Pascals Triangle

```cpp

```

## 34. Best Time To Buy and Sell Stock

```cpp

```

## 35. Jump Game

```cpp

```

## 36. Unique Paths

```cpp

```

## 37. Flood Fill

```cpp

```

## 38. Is Graph Bipartite?

```cpp

```

## 39. Sort The People

```cpp

```

## 40. Sort Array By Parity

```cpp

```

## 41. Count Nice Pairs in an Array

```cpp

```

## 42. Count Number of Bad Pairs

```cpp

```

## 43. Fair Distribution of Cookies

```cpp

```

## 44. Sum of Left Leaves

```cpp

```

## 45. Construct String From Binary Tree

```cpp

```

## 46. Average of Levels in Binary Tree

```cpp

```

## 47. Balanced Binary Tree

```cpp

```

## 48. Permutation - II

```cpp

```

## 49. Combination Sum - II

```cpp

```

## 50. Word Search

```cpp

```

## 51. Combination Sum

```cpp

```

## 52. Generate Parentheses

```cpp

```

## 53. Permutations

```cpp

```