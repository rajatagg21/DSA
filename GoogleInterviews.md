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

- https://leetcode.com/discuss/post/6115417/google-swel3-india-dec-2024-reject-by-an-6t4a/

Here’s a structured extraction of the closest LeetCode-style problems from the interview experience:

---

### Problem:

Minimum cost required to remove all terminal (leaf) nodes from a tree starting from the root.

**Topic Tags:**
Tree, DFS, Dynamic Programming on Trees, Greedy

**Close Leetcode Problems:**

* Minimum Cost Tree From Leaf Values
* Binary Tree Cameras
* Sum of Distances in Tree

---

### Problem:

Determine the rank of players based on results of multiple matches between pairs.

**Topic Tags:**
Graph, Topological Sort, Directed Graph, DFS/BFS

**Close Leetcode Problems:**

* Course Schedule
* Course Schedule II
* Find Eventual Safe States
* Sequence Reconstruction

---

### Problem:

Line sweep based problem with follow-up using binary search (similar to zero array transformation).

**Topic Tags:**
Line Sweep, Prefix Sum, Binary Search, Interval Processing

**Close Leetcode Problems:**

* Meeting Rooms II
* Car Pooling
* Range Addition
* Capacity To Ship Packages Within D Days

---

### Problem:

Dice game — given dice with equal number of sides but different values, count how many times Player 1 wins.

**Topic Tags:**
Arrays, Sorting, Two Pointers, Binary Search, Probability/Counting

**Close Leetcode Problems:**

* Number of Pairs Satisfying Inequality
* Successful Pairs of Spells and Potions
* Count Number of Teams
* Advantage Shuffle

---

- https://leetcode.com/discuss/post/6084864/google-l4-interview-expereince-by-anonym-b142/

Here’s a clean mapping of each problem to core topics and closest LeetCode equivalents:

---

**Problem:**
Broadcast & Shut Down (routers reachability with range)

**Topic Tags:**
Graph, BFS/DFS, Geometry (distance), Connectivity

**Close Leetcode Problems:**

* Number of Provinces (LC 547)
* Keys and Rooms (LC 841)
* Network Delay Time (LC 743)
* Find if Path Exists in Graph (LC 1971)

---

**Problem:**
IP to City Mapping (range lookup)

**Topic Tags:**
Binary Search, Interval Search, Sorting, Hashing

**Close Leetcode Problems:**

* Find Right Interval (LC 436)
* Time Based Key-Value Store (LC 981)
* Range Module (LC 715)
* Search Insert Position (LC 35)

---

**Problem:**
Validate Organic Molecule (bond counting + connectivity)

**Topic Tags:**
Graph, Degree Counting, Validation, Connected Components

**Close Leetcode Problems:**

* Graph Valid Tree (LC 261)
* Number of Connected Components in an Undirected Graph (LC 323)
* Find Center of Star Graph (LC 1791)
* Possible Bipartition (LC 886)

---

**Problem:**
Largest K-digit subsequence

**Topic Tags:**
Greedy, Monotonic Stack, String

**Close Leetcode Problems:**

* Remove K Digits (LC 402) *(reverse logic)*
* Create Maximum Number (LC 321)
* Largest Number (LC 179)
* Monotonic Stack Pattern (general)

---

**Problem:**
Password generation from unordered key counts

**Topic Tags:**
Backtracking, Permutations, Combinatorics, Frequency Map

**Close Leetcode Problems:**

* Permutations II (LC 47)
* Letter Tile Possibilities (LC 1079)
* Generate Parentheses (LC 22) *(pattern reference)*
* Subsets II (LC 90)

---

- https://leetcode.com/discuss/post/6084576/google-l3-nov-2024-offer-by-anonymous_us-5z1a/

Here’s a clean extraction + mapping of the closest LeetCode problems based on patterns described in your text:

---

**Problem:** Binary search-based problem involving validation logic (unit test style correctness checks)
**Topic Tags:** Binary Search, Search Space Reduction, Predicate Function, Arrays
**Close Leetcode Problems:**

* Binary Search (Concept base)
* Capacity To Ship Packages Within D Days
* Koko Eating Bananas
* Find Minimum in Rotated Sorted Array

---

**Problem:** Top-K elements with real-world constraints (file input, regex parsing, dynamic updates, scaling)
**Topic Tags:** Heap (Priority Queue), HashMap, Sorting, Regex, File Processing, Distributed Systems (conceptual)
**Close Leetcode Problems:**

* Top K Frequent Elements
* Kth Largest Element in an Array
* Find K Pairs with Smallest Sums
* Top K Frequent Words

---

**Problem:** Autocomplete search system with prefix-based suggestions and popularity ranking
**Topic Tags:** Trie, Design, Heap, String Processing, System Design, Prefix Matching
**Close Leetcode Problems:**

* Design Search Autocomplete System
* Implement Trie (Prefix Tree)
* Search Suggestions System
* Top K Frequent Words

---


