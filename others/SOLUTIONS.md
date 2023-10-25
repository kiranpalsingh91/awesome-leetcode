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
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode *p = head, *q = head;
        
        while(p && p->next) {
            p = p->next->next;
            q = q->next;
            
            if(p == q) return true;
        }
        
        return false;
        
    }
};
```

## 4. Container With Most Water

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        
        int N = height.size();
        int L = 0, R = N - 1;
        
        int ans = 0;
        
        while(L < R) {
            int area = min(height[L], height[R]) * (R - L);
            
            ans = max(ans, area);
            
            if(height[L] < height[R]) {
                L++;
            } else {
                R--;
            }
        }
        
        return ans;
    }
};
```

## 5. Remove Nth Node From End of List

```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode *p = head, *q = head;
        while (n--) q = q->next;
        if (!q) return head->next;
        while (q->next) {
            p = p->next;
            q = q->next;
        }
        ListNode* toDelete = p->next;
        p->next = p->next->next;
        delete toDelete;
        return head;
    }
};
```

## 6. Reverse Words in a String

```cpp
class Solution {
public:
    string reverseWords(string s) {
      stack<int> stk;
      string ans = "";

      for(int i = 0; i < s.size(); i++){
        if(s[i] != ' '){
          stk.push(s[i]);
        } else {
          while(!stk.empty()){
            ans += stk.top();
            stk.pop();
          }
          ans += " ";
        }
      }

      while(!stk.empty()){
        ans += stk.top();
        stk.pop();
      }

      return ans;
   }
};
```

## 7. Valid Parentheses

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> S;
        
        for(char c : s) {
            if(c == '(' || c == '[' || c == '{') {
                S.push(c);
            } else {
                if(S.size() && c == ')' && S.top() == '(') {
                    S.pop();
                } else if( S.size() && c == ']' && S.top() == '[') {
                    S.pop();
                } else if (S.size() && c == '}' && S.top() == '{') {
                    S.pop();
                } else {
                    return false;
                }
            }
        } 
        
        // Check the stack size.
        if(S.size() == 0) {
            return true;
        } else {
            return false;
        }
            
    }
};
```

## 8. Implement Queue using Stacks

```cpp
class MyQueue {
public:
    
    stack<int> S1, S2;
    
    void push(int x) {
        while (S1.size()) {
            S2.push(S1.top());
            S1.pop();
        }
        
        S2.push(x);
        
        while (S2.size()) {
            S1.push(S2.top());
            S2.pop();
        }
    }
    
    int pop() {
        int x = S1.top();
        S1.pop();
        return x;
    }
    
    int peek() {
        return S1.top();
    }
    
    bool empty() {
        return S1.empty();
    }
};
```

## 9. Next Greater Element - I

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        
        int N = nums2.size();
        stack<int> S;
        unordered_map<int, int> M;
        
        for(auto A : nums2) {
            
            while(S.size() && A > S.top()) {
                M[S.top()] = A;
                S.pop();
            }
            
            S.push(A);
        }
        
        vector<int> ans;
        
        for(auto A : nums1) {
            if(M.count(A)) {
                ans.push_back(M[A]);
            } else {
                ans.push_back(-1);
            }
        }
        
        return ans;
    }
};
```

## 10. Backspace String Compare

```cpp
class Solution {
public:
    bool backspaceCompare(string s, string t) {
        stack<int> S, T;
        
        for(char c : s) {
            if(c == '#' && S.size()) {
                S.pop();
            } else if(c != '#') {
                S.push(c);
            }
        }
        
        for(char c : t) {
            if(c == '#' && T.size()) {
                T.pop();
            } else if (c != '#') {
                T.push(c);
            }
        }
        
        return (S == T);
    }
};
```

## 11. Min Stack

```cpp
class MinStack {
public:
    
    stack<int> S1, S2;
    
    void push(int val) {
        S1.push(val);
        if(S2.empty() || S2.size() && S2.top() >= val) {
            S2.push(val);
        }
    }
    
    void pop() {
        int x = S1.top();
        S1.pop();
        
        if(x == S2.top()) {
            S2.pop();
        }
    }
    
    int top() {
        return S1.top();
    }
    
    int getMin() {
        return S2.top();
    }
};
```

## 12. Next Greater Element - II

```cpp
class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        int N = nums.size();
        
        // Stores index.
        stack<int> S;
        
        // Stores element
        vector<int> ans(N, -1);
        
        for(int i = 0; i < 2 * N; i++) {
            
            int n = nums[i % N];
            
            while(S.size() && nums[S.top()] < n) {
                ans[S.top()] = n;
                S.pop();
            }
            
            S.push(i % N);
        }
        
        return ans;
    }
};
```

## 13. Course Schedule

```cpp
class Solution {
public:
    bool canFinish(int k, vector<vector<int>>& prerequisites) {
        
        // Creation of graph
        unordered_map<int, vector<int>> G;
        vector<int> indegree(k, 0);
        
        for (auto &e : prerequisites) {
            int u = e[0], v = e[1];
            G[v].push_back(u);
            indegree[u]++;
        }
        
        queue<int> q;
        
        for (int i = 0; i < k; i++) {
            if (indegree[i] == 0) {
                q.push(i);
            }
        }
        
        while (q.size()) {
            int cnt = q.size();
            
            while (cnt--) {
                int u = q.front();
                q.pop();
                
                k--;
                
                for (auto v : G[u]) {
                    if (--indegree[v] == 0) {
                        q.push(v);
                    }
                }
            }
        }
        
        return k == 0;
    }
};
```

## 14. Longest Increasing Path in Matrix

```cpp
class Solution {
public:
    int M, N;
    vector<vector<int>> cnt;
    
    int dirs[4][2] = { {1, 0}, {0, 1}, {-1, 0}, {0, -1}};
    
    int dfs(vector<vector<int>> &A, int i, int j) {
        
        if(cnt[i][j] != -1e9) {
            return cnt[i][j];
        }
        
        cnt[i][j] = 1;
        
        for(auto &dir : dirs) {
            int a = i + dir[0];
            int b = j + dir[1];
            
            if(a < 0 || b < 0 || a >= M || b >= N || A[a][b] <= A[i][j]) continue;
            
            cnt[i][j] = max(cnt[i][j] , 1 + dfs(A, a, b));
        }
        
        return cnt[i][j];
    }
    
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        M = matrix.size();
        N = matrix[0].size();
        
        cnt.assign(M, vector<int>(N, -1e9));
        
        int ans = 0;
        
        for(int i = 0; i < M; i++) {
            for(int j = 0; j < N; j++) {
                ans = max(ans, dfs(matrix, i, j));
            }
        }
        
        return ans;
    }
};
```

## 15. Number of Islands

```cpp
class Solution {
public:
    
    int M, N;
    
    int dirs[4][2] = { {0, 1}, {1, 0}, {-1, 0}, {0, -1}};
    
    void dfs(vector<vector<char>> &grid, int i, int j) {
        
        // This cell of grid has been visited.
        grid[i][j] = '2';
        
        // Go to the four sides of grid.
        for(auto &dir : dirs) {
            int a = i + dir[0];
            int b = j + dir[1];
            
            if(a < 0 || b < 0 || a >= M || b >= N || grid[a][b] != '1') continue;
            
            dfs(grid, a, b);
        }
    }
    
    int numIslands(vector<vector<char>>& grid) {
        M = grid.size();
        N = grid[0].size();
        
        int islandCnt = 0;
        
        for(int i = 0; i < M; i++) {
            for(int j = 0; j < N; j++) {
                if(grid[i][j] == '1') {
                    dfs(grid, i, j);
                    islandCnt++;
                }
            }
        }
        
        return islandCnt;
    }
};
```

## 16. Longest Consecutive Sequence

```cpp
// Union Find that also return the vector of size of components.
class UnionFind {
    vector<int> id, size;
public:
    UnionFind(int n) : id(n), size(n, 1) {
        for (int i = 0; i < n; ++i) id[i] = i;
    }
    void connect(int a, int b) {
        int x = find(a), y = find(b);
        if (x == y) return;
        id[x] = y;
        size[y] += size[x];
    }
    int find(int a) {
        return id[a] == a ? a : (id[a] = find(id[a]));
    }
    vector<int> &getSizes() {
        return size;
    }
};

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        
        int N = nums.size();
        
        if(N == 0) {
            return 0;
        }
        
        UnionFind uf(N);
        
        unordered_map<int, int> M;
        
        // We have to store indexes in UnionFind instead of integer values.
        
        for(int i = 0; i < N; i++) {
            int n = nums[i];
            
            if(M.count(n)) continue;
            
            M[n] = i;
            
            if(M.count(n - 1)) uf.connect(M[n], M[n - 1]);
            if(M.count(n + 1)) uf.connect(M[n], M[n + 1]);
        }
        
        // ans -> maximum component size
        vector<int> ans = uf.getSizes();
        return *max_element(ans.begin(), ans.end());
    }
};
```

## 17. Transpose Matrix

```cpp
class Solution {
public:
    vector<vector<int>> transpose(vector<vector<int>>& matrix) {
        int R = matrix.size();
        int C = matrix[0].size();
        
        vector<vector<int>> trans(C, vector<int>(R));
        
        for(int i = 0; i < R; i++) {
            for(int j = 0; j < C; j++) {
                trans[j][i] = matrix[i][j];
            }
        }
        
        return trans;
    }
};
```

## 18. Merge Two Sorted List

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode dummy, *tail = &dummy;
        
        while(list1 && list2) {
            if(list1->val < list2->val) {
                tail->next = list1;
                list1 = list1->next;
            } else {
                tail->next = list2;
                list2 = list2->next;
            }
            
            tail = tail->next;
        }
        
        if(list1) tail->next = list1;
        if(list2) tail->next = list2;
            
        
        return dummy.next;
    }
};
```

## 19. Remove Duplicates From Sorted List

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head) return NULL;
        
        ListNode *p = head;
        
        while(p) {
            ListNode *q = p->next;
            while(q && q->val == p->val) {
                p->next = q->next;
                delete q;
                q = p->next;
            }
            
            p = p->next;
        }
        
        return head;
    }
};
```

## 20. Palindrome Linked List

```cpp
class Solution {
public:
    
    bool isPalindrome(ListNode* head) {
        vector<int> ans;
        
        while(head) {
            ans.push_back(head->val);
            head = head->next;
        }
        
        auto reversed = ans;
        reverse(reversed.begin(), reversed.end());
        
        return ans == reversed;
    }
};
```

## 21. Middle of Linked List

```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        auto p = head, q = head;
        
        while (q && q->next) {
            p = p->next;
            q = q->next->next;
        }
        
        return p;
    }
};
```

## 22. Intersection of Two Linked Lists

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *p = headA, *q = headB;
        
        if(p == NULL || q == NULL) {
            return NULL;
        }
        
        while(p != NULL && q != NULL && p != q) {
            p = p->next;
            q = q->next;
            
            if(p == q) {
                return p;
            }
            
            if(p == NULL) {
                p = headB;
            }
            
            if(q == NULL) {
                q = headA;
            }
        }
        
        return p;
    }
};
```

## 23. Maximum Population Year

```cpp
class Solution {
public:
    int maximumPopulation(vector<vector<int>>& logs) {
        
        int N = 2100;
        vector<int> line(N, 0);
        
        for(auto &e : logs) {
            int birth = e[0], death = e[1];
            line[birth] += 1;
            line[death] -= 1;
        }
        
        for(int i = 1950; i < N; i++) {
            line[i] += line[i - 1];
        }
        
        int maxPopulation = *max_element(line.begin(), line.end());
        
        for(int i = 1950; i < N; i++) {
            if(line[i] == maxPopulation) {
                return i;
            }
        }
        
        return logs[0][0];
    }
};
```

## 24. Merge Intervals

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& A) {
        
        sort(A.begin(), A.end());
        vector<vector<int>> ans;
        
        for (auto &a : A) {
            if (ans.empty() || ans.back()[1] < a[0]) {
                ans.push_back(a);
            } else {
                ans.back()[1] = max(ans.back()[1], a[1]);
            }
        }
        
        return ans;
    }
};
```

## 25. Insert Intervals

```cpp
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) {
        
        int start = newInterval[0], end = newInterval[1];
        vector<vector<int>> ans;
        
        for (auto &a : intervals) {
            
            if (start > end) {
                ans.push_back(a);
            } else if (end < a[0]) {
                ans.push_back({start, end});
                start = end + 1;
                ans.push_back(a);
            } else if (start > a[1]) {
                ans.push_back(a);
            } else {
                start = min(start, a[0]);
                end = max(end, a[1]);
            }
        }
        
        if (start <= end) {
            ans.push_back({start, end});
        }
        
        return ans;
    }
};
```

## 26. Non Overlapping Intervals

```cpp
class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>>& A) {
        
        sort(A.begin(), A.end(), [](auto &a, auto &b) {
            return a[1] < b[1];
        });
        
        int end = INT_MIN, ans = 0;
        
        for (auto &a : A) {
            if (a[0] < end) {
                ans++;
            } else {
                end = max(end, a[1]);
            }
        }
        
        return ans;
    }
};
```

## 27. Sort Array By Increasing Frequency

```cpp
class Solution {
public:
    vector<int> frequencySort(vector<int>& nums) {
        
        unordered_map<int, int> cnt;
        for (int n : nums) cnt[n]++;
        
        auto cmp = [&](int a, int b) {
            if (cnt[a] == cnt[b]) {
                return a < b;
            }
            return cnt[a] > cnt[b];
        };
        
        priority_queue<int, vector<int>, decltype(cmp)> pq(cmp);
        
        for ( auto &[n, c] : cnt) {
            pq.push(n);
        }
        
        vector<int> ans;
        
        while (pq.size()) {
            int c = pq.top();
            pq.pop();
            
            while (cnt[c]--) {
                ans.push_back(c);
            }
        }
        
        return ans;
    }
};
```

## 28. Kth Largest Element in an Array

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        
        priority_queue<int, vector<int>> pq;
        
        for (int n : nums) {
            pq.push(n);
        }
        
        k--;
        
        while (k--) {
            pq.pop();
        }
        
        return pq.top();
    }
};
```

## 29. Top K Frequent Elements

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        
        unordered_map<int, int> cnt;
        for (int n : nums) cnt[n]++;
        
        auto cmp = [&](int a, int b) {
            return cnt[a] > cnt[b];
        };
        
        priority_queue<int, vector<int>, decltype(cmp)> pq(cmp);
        
        for (auto &[n, c] : cnt) {
            pq.push(n);
        }
        
        
        while (pq.size() > k) {
            pq.pop();
        }
        
        vector<int> ans;
        
        while (pq.size()) {
            int x = pq.top();
            pq.pop();
            ans.push_back(x);
        }
        
        return ans;
    }
};
```

## 30. Sort Characters By Frequency

```cpp
class Solution {
public:
    string frequencySort(string s) {
        
        unordered_map<char, int> cnt;
        for (char c : s) cnt[c]++;
        
        auto cmp = [&](char a, char b) {
            return cnt[a] < cnt[b];
        };
        
        priority_queue<char, vector<char>, decltype(cmp)> pq(cmp);
        
        for (auto &[n, c] : cnt) {
            pq.push(n);
        }
        
        string ans = "";
        
        while (pq.size()) {
            char c = pq.top();
            pq.pop();
            
            ans += string(cnt[c], c);
        }
        
        return ans;
    }
};
```

## 31. Maximum Number of Events That Can Be Attended

```cpp
class Solution {
public:
    // Greedy Scheduling
    int maxEvents(vector<vector<int>>& events) {
        
        sort(events.begin(), events.end());
        int N = events.size(), i = 0, day = events[0][0];
        int eventAttended = 0;
        
        priority_queue<int, vector<int>, greater<>> pq;
        
        while (i < N || pq.size()) {
            if (pq.empty()) day = events[i][0];
            
            while (i < N && events[i][0] == day) {
                pq.push(events[i++][1]);
            }
            
            pq.pop();
            eventAttended++;
            day++;
            
            while (pq.size() && pq.top() < day) {
                pq.pop();
            }
        }
        
        return eventAttended;
        
    }
};
```

## 32. Climbing Stairs

```cpp
class Solution {
public:
    int climbStairs(int n) {
        
        if(n == 1) return 1;
        
        vector<int> dp(n, 0);
        
        dp[0] = 1;
        dp[1] = 2;
        
        for(int i = 2; i < n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n - 1];
    }
};
```

## 33. Pascals Triangle

```cpp
class Solution {
public:
    vector<vector<int>> generate(int N) {
        vector<vector<int>> ans(N);
        
        for(int i = 0; i < N; i++) {
            ans[i] = vector<int>(i + 1, 1);
            
            for(int j = 1; j < i; j++) {
                ans[i][j] = ans[i - 1][j] + ans[i - 1][j - 1];
            }
        }
        
        return ans;
        
    }
};
```

## 34. Best Time To Buy and Sell Stock

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min = 1e5;
        int profit = 0;

        for (int n : prices) {
            if (n < min) {
                // Update the minimum
                min = n;
            }
            profit = max(profit, n - min);
        }
        return profit;
    }
};
```

## 35. Jump Game

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        
        int N = nums.size();
        int maxEnd = 0;
        
        for(int i = 0; i < N && maxEnd >= i; i++) {
            maxEnd = max(maxEnd, i + nums[i]);
        }
        
        return maxEnd >= N - 1;
    }
};
```

## 36. Unique Paths

```cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<int> dp(n + 1, 0);
        dp[n - 1] = 1;
        
        for(int i = m - 1; i >= 0; i--) {
            for(int j = n - 1; j >= 0; j--){
                dp[j] += dp[j + 1];
            }
        }
        
        return dp[0];
    }
};
```

## 37. Flood Fill

```cpp
class Solution {
public:
    int M, N;
    int dirs[4][2] = {{0, 1}, {1, 0}, {-1, 0}, {0, -1}};
    int startingColor;
    
    void dfs(vector<vector<int>>& image, int x, int y, int newColor) { 
        image[x][y] = newColor;
        
        for(auto &dir : dirs) {
            int a = x + dir[0];
            int b = y + dir[1];
            
            if(a < 0 || b < 0 || a >= M || b >= N || image[a][b] != startingColor) continue;
            
            dfs(image, a, b, newColor);
        }
    }
    
    
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        M = image.size();
        N = image[0].size();
        
        startingColor = image[sr][sc];
        
        if(startingColor == newColor) {
            return image;
        }
        
        dfs(image, sr, sc, newColor);
        
        return image;
    }
};
```

## 38. Is Graph Bipartite?

```cpp
class Solution {
public:
    bool isBipartite(vector<vector<int>>& graph) {
        
        int N = graph.size();
        
        vector<int> id(N, 0);
        
        function<bool(int, int)> dfs = [&](int u, int color) {
            // When to return false.
            if(id[u]) return (id[u] == color);
            
            id[u] = color;
            
            // Traverse all neighbours of graph, give the opposite color of current color.
            for(int v : graph[u]) {
                if (!dfs(v, -color)) return false;
            }
            
            return true;
        };
        
        for(int i = 0; i < N; i++) {
            if(!id[i] && !dfs(i, 1)) {
                return false;
            }
        }
        
        return true;
    }
};
```

## 39. Sort The People

```cpp
class Solution {
public:
    vector<string> sortPeople(vector<string>& names, vector<int>& heights) {
        int N = names.size();
        
        vector<int> idx(N, 0);
        iota(idx.begin(), idx.end(), 0);
        
        sort(idx.begin(), idx.end(), [&](int a, int b) {
            return heights[a] > heights[b];
        });
        
        vector<string> ans;
        
        for (auto a : idx) {
            ans.push_back(names[a]);
        }
        
        return ans;
    }
};
```

## 40. Sort Array By Parity

```cpp
class Solution {
public:
    vector<int> sortArrayByParity(vector<int>& nums) {
        sort(nums.begin(), nums.end(), [&](int a, int b) {
            return a % 2 < b % 2;
        });
        
        return nums;
    }
};
```

## 41. Count Nice Pairs in an Array

```cpp
class Solution {
public:
    
    int rev(int n) {
      string s = to_string(n);
      reverse(s.begin(), s.end());

      return stoi(s);
    }
    
    int countNicePairs(vector<int>& nums) {
        
        int N = nums.size();
        int MOD = 1e9 + 7;
        
        unordered_map<int, int> M;
        int ans = 0;
        
        for(int i = 0; i < N; i++) {
            ans = (ans + (M[nums[i] - rev(nums[i])]) % MOD) % MOD;
            M[nums[i] - rev(nums[i])]++;
        }
        
        return ans;
    }
};
```

## 42. Count Number of Bad Pairs

```cpp
class Solution {
public:
    long long countBadPairs(vector<int>& nums) {
        
        long long pairsCnt = 0;
        int N = nums.size();
        unordered_map<int, int> M;
        
        for(int i = 0; i < N; i++) {
            pairsCnt += i - M[i - nums[i]];
            M[i - nums[i]]++;
        }
        
        return pairsCnt;
    }
};
```

## 43. Fair Distribution of Cookies

```cpp
class Solution {
public:
    int dp[9][1 << 9], sum[1 << 9];
    
    int distributeCookies(vector<int>& cookies, int k) {
        
        memset(dp, 0x3f, sizeof(dp));
        memset(sum, 0, sizeof(sum));
        
        int N = cookies.size();
        
        for(int i = 0; i < N; i++) {
            dp[i][0] = 0;
        }
        
        for (int mask = 0; mask < (1 << N); mask++) {
            for (int i = 0; i < N; i++) {
                if (mask >> i & 1) {
                    sum[mask] += cookies[i];
                }
            }
        }
        
        for(int i = 0; i < k; i++) {
            for(int mask = 0; mask < (1 << N); mask++) {
                for(int sub = mask; sub; sub = (sub - 1) & mask) {
                    dp[i + 1][mask] = min(dp[i + 1][mask], max(dp[i][mask ^ sub], sum[sub]));
                }
            }
        }
        
        return dp[k][(1 << N) - 1];
    }
};
```

## 44. Sum of Left Leaves

```cpp
class Solution {
public:
    int sum = 0;
    
    void dfs(TreeNode* root, bool lefty) {
        if (!root) return;
        
        if (!root->left && !root->right) {
            if (lefty) sum += root->val;
        } 
        
        dfs(root->left, true);
        dfs(root->right, false);
    }
    int sumOfLeftLeaves(TreeNode* root) {
        dfs(root, false);
        return sum;
    }
};
```

## 45. Construct String From Binary Tree

```cpp
class Solution {
public:
    
    string ans;
    void preorder(TreeNode* root) {
        
        ans += (to_string)(root->val);
        
        if(root->left) {
            ans += "(";
            preorder(root->left);
            ans += ")";
        } else if(!root->left && root->right) {
            ans += "()";
        }
        
        if(root->right) {
            ans += "(";
            preorder(root->right);
            ans += ")";
        }
        
    }
    
    string tree2str(TreeNode* root) {
        preorder(root);
        return ans;
    }
};
```

## 46. Average of Levels in Binary Tree

```cpp
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        
        vector<double> ans;
        
        queue<TreeNode*> q;
        q.push(root);
        
        while(q.size()) {
            
            int cnt = q.size();
            double levelAverage = 0.0;
            int nodesInLevel = cnt;
            
            while(cnt--) {
                auto node = q.front();
                q.pop();
                
                levelAverage += double(node->val);
                
                if(node->left) {
                    q.push(node->left);
                }
                
                if(node->right) {
                    q.push(node->right);
                }
            }
            
            ans.push_back(levelAverage / nodesInLevel);
        }
        
        return ans;
    }
};
```

## 47. Balanced Binary Tree

```cpp
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if (root == NULL)  return true;
		if (Height(root) == -1)  return false;
		return true;
	}
	int Height(TreeNode* root) {
		if (root == NULL)  return 0;
		int leftHeight = Height(root->left);
		int rightHight = Height(root->right);
		if (leftHeight == -1 || rightHight == -1 || abs(leftHeight - rightHight) > 1)  return -1;
		return max(leftHeight, rightHight) + 1;
    }
};
```

## 48. Permutation - II

```cpp
class Solution {
public:
    
    vector<vector<int>> ans;
    
    void permute(vector<int>& nums, int start) {
        
        if (start == nums.size()) {
            ans.push_back(nums);
        }
        
        for(int i = start; i < nums.size(); i++) {
            if(i != start && nums[i] == nums[start]) continue;
            
            swap(nums[i], nums[start]);
            permute(nums, start + 1);
        }
    }
    
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        
        sort(nums.begin(), nums.end());
        permute(nums, 0);
        return ans;
    }
};
```

## 49. Combination Sum - II

```cpp
class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& A, int target) {
        
        int N = A.size();
        sort(A.begin(), A.end());
        vector<vector<int>> ans;
        vector<int> temp;
        
        function<void(int, int)> dfs = [&](int start, int goal) {
            if(goal == 0) {
                ans.push_back(temp);
                return;
            }
            
            for(int i = start; i < N && goal - A[i] >= 0 ; i++) {
                if(i != start && A[i] == A[i - 1]) continue;
                temp.push_back(A[i]);
                dfs(i + 1, goal - A[i]);
                temp.pop_back();
            }
        };
        
        dfs(0, target);
        
        return ans;
    }
};
```

## 50. Word Search

```cpp
class Solution {
public:
    int M, N;
    int dirs[4][2] = { {0, 1}, {1, 0}, {-1, 0}, {0, -1}};
    bool dfs(vector<vector<char>>& board, string word, int x, int y, int i) {
        
        if(board[x][y] != word[i]) {
            return false;
        }
        
        // Return condition -> when to return true, when string is found
        if(i + 1 == word.size()) {
            return true;
        }
        
        char c = board[x][y];
        board[x][y] = 0;
        
        for(auto &dir: dirs) {
            int a = x + dir[0];
            int b = y + dir[1];
            // Check validity of next cell in grid
            if(a < 0 || a >= M || b < 0 || b >= N || board[a][b] != word[i + 1]) continue;
            if(dfs(board, word, a, b, i + 1)) {
                return true;
            }
        }
        
        board[x][y] = c;
        return false;
    }
    
    bool exist(vector<vector<char>>& board, string word) {
        M = board.size();
        N = board[0].size();
        
        for(int i = 0; i < M; i++) {
            for(int j = 0; j < N; j++) {
                if(dfs(board, word, i, j, 0)) {
                    return true;
                }
            }
        }
        
        return false;
    }
};
```

## 51. Combination Sum

```cpp
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& A, int target) {
        
        vector<vector<int>> ans;
        vector<int> temp;
        
        sort(A.begin(), A.end());
        
        function<void(int, int)> dfs = [&](int start, int goal) {
            
            // Base case
            if(goal == 0) {
                ans.push_back(temp);
                return;
            }
            
            // Two choices. - Include or exclude.
            for (int i = start; i < A.size() && goal - A[i] >= 0; i++) {
                temp.push_back(A[i]);
                dfs(i, goal - A[i]);
                temp.pop_back();
            }
        };
        
        dfs(0, target);
        return ans;
    }
};
```

## 52. Generate Parentheses

```cpp
class Solution {
public:
    
    vector<string> ans;
    
    void backtracking(string &temp, int leftCnt, int rightCnt) {
        
        // We found a valid parentheses.
        if(leftCnt == 0 && rightCnt == 0) {
            ans.push_back(temp);
            return;
        }
        
        // Include left parentheses
        
        if(leftCnt) {
            temp += "(";
            backtracking(temp, leftCnt - 1, rightCnt);
            temp.pop_back();
        }
        
        // Include right parentheses
        
        if(rightCnt > leftCnt) {
            temp += ")";
            backtracking(temp, leftCnt, rightCnt - 1);
            temp.pop_back();
        }
        
    }
    
    vector<string> generateParenthesis(int n) {
        string temp = "";
        backtracking(temp, n, n);
        
        return ans;
    }
};
```

## 53. Permutations

```cpp
class Solution {
public:
    
    vector<vector<int>> ans;
    
    void permute(vector<int> &nums, int start) {
        // Base case
        if(start == nums.size()) {
            ans.push_back(nums);
            return;
        }
        
        for(int i = start; i < nums.size(); i++) {
            swap(nums[start], nums[i]);
            permute(nums, start + 1);
            swap(nums[start], nums[i]);
        }
        
    }
    
    vector<vector<int>> permute(vector<int>& nums) {
        permute(nums, 0);
        return ans;
    }
};
```