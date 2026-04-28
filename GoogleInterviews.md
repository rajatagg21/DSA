## Extraction Prompt
```json
<post_start> ... <post_end>

Given the text taken from leetcode post. You have to extract leetcode problems out of it. and give most closest leetcode problems to a given problem. 

The output should strictly be in a format:

Problem:
Topic Tags: 
Close Leetcode Problems: 


Topic tags should include data structure or related algorithm. 
```

- https://leetcode.com/discuss/post/6251197/google-l4-interview-experience-by-anonym-thmi/
---

### Problem:

Evaluate a nested expression string like: `add(5, mul(2, pow(5,2)))`

### Topic Tags:

Stack, Recursion, String Parsing, Expression Evaluation, DFS

### Close Leetcode Problems:

* Basic Calculator II
* Basic Calculator III
* Evaluate Reverse Polish Notation
* Parse Lisp Expression

---

### Problem:

Design interval insertion and point query system:

* `InsertRange(start, end)` → add interval [start, end)
* `Query(point)` → check if point lies in any interval

### Topic Tags:

Intervals, Ordered Map / TreeMap, Sweep Line, Binary Search, Design

### Close Leetcode Problems:

* Range Module
* Insert Interval
* Merge Intervals
* Data Stream as Disjoint Intervals

---

### Problem:

Longest Increasing Subsequence (with variation)

### Topic Tags:

Dynamic Programming, Binary Search, LIS, Greedy

### Close Leetcode Problems:

* Longest Increasing Subsequence
* Number of Longest Increasing Subsequence
* Longest Arithmetic Subsequence
* Russian Doll Envelopes


- https://leetcode.com/discuss/post/6138690/google-l3-onsite-interview-question-by-a-w45z/

**Problem:**
Given a string `s`, count the number of triplets `(i, j, k)` such that the substring `s[i...j]` and `s[j+1...k]` have the same number of **distinct characters**.

---

**Topic Tags:**

* Prefix Sum
* Binary Search
* Sliding Window
* Hashing / Frequency Count
* Bitmasking (alternative approach)
* Two Pointers

---

**Close Leetcode Problems:**

* 992. Subarrays with K Different Integers
* 340. Longest Substring with At Most K Distinct Characters
* 159. Longest Substring with At Most Two Distinct Characters
* 1371. Find the Longest Substring Containing Vowels in Even Counts
* 1915. Number of Wonderful Substrings
* 1542. Find Longest Awesome Substring

---

### 💡 Insight (what interviewer was hinting)

You already explored:

* **Brute force + set** → O(n³) / O(n² log n)
* **Bitmask** → optimize distinct tracking

The **Binary Search angle** comes from this key idea:

Fix `j` (middle split point):

* For left side `[i...j]`, track distinct count as you move `i → 0`
* For right side `[j+1...k]`, you want **same distinct count**

Now:

* Precompute `rightDistinct[j][k]` OR more efficiently maintain a structure
* For a fixed `j` and a distinct count `d`, you want to count how many `k` exist such that:

  ```
  distinct(s[j+1...k]) == d
  ```

👉 This becomes a **range counting problem**, where:

* Distinct count is **monotonic non-decreasing** as `k` increases
* So you can:

  * Use **binary search to find first and last k** where distinct count == d
  * Count range size

---

### ⚡ Clean Optimized Approach (High Level)

1. Fix `j`
2. Move `i` backward → maintain left distinct count
3. For each distinct count `d`:

   * Use **binary search on right side** to count valid `k`
4. Sum all contributions

Time complexity:

* ~ **O(n² log n)** (better than brute, alternative to bitmask O(n²))

- 
