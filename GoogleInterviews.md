<pre>
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

- https://leetcode.com/discuss/post/6033289/google-l3-interview-experience-oct-2024-0xzt8/

Here’s a clean mapping of each problem to closest LeetCode-style problems and relevant topics:

---

### **Problem 1: Router Message Propagation (BFS within distance d)**

**Topic Tags:** Graph, BFS, Shortest Path, Weighted Graph

**Close Leetcode Problems:**

* 1334. Find the City With the Smallest Number of Neighbors at a Threshold Distance
* 743. Network Delay Time
* 787. Cheapest Flights Within K Stops
* 542. 01 Matrix

---

### **Problem 1 (Follow-up): Only Nearest Router Propagation**

**Topic Tags:** Graph, BFS, Greedy, Dijkstra-like Traversal

**Close Leetcode Problems:**

* 1631. Path With Minimum Effort
* 1514. Path with Maximum Probability
* 778. Swim in Rising Water

---

### **Problem 2: Minimum Cost to Disconnect All Leaf Nodes in Tree**

**Topic Tags:** Tree, DFS, DP on Trees, Greedy, Minimum Cut

**Close Leetcode Problems:**

* 968. Binary Tree Cameras
* 979. Distribute Coins in Binary Tree
* 1245. Tree Diameter
* 2313. Minimum Flips in Binary Tree to Get Result

---

### **Problem 3: Expression Evaluation (add, sub, mul, pow)**

**Topic Tags:** Stack, Expression Parsing, Recursion

**Close Leetcode Problems:**

* 224. Basic Calculator
* 227. Basic Calculator II
* 772. Basic Calculator III
* 150. Evaluate Reverse Polish Notation

---

### **Problem 4: Find Indexes of '1' Using query(L, R)**

**Topic Tags:** Binary Search, Divide and Conquer, Interactive Problem, Segment Tree Concept

**Close Leetcode Problems:**

* 374. Guess Number Higher or Lower
* 278. First Bad Version
* 1533. Find the Index of the Large Integer
* 1095. Find in Mountain Array

---

### **Problem 4 (Follow-up): Partition Array into Subarrays with k Ones**

**Topic Tags:** Prefix Sum, Binary Search, Sliding Window

**Close Leetcode Problems:**

* 930. Binary Subarrays With Sum
* 1248. Count Number of Nice Subarrays
* 560. Subarray Sum Equals K
* 209. Minimum Size Subarray Sum

---

- https://leetcode.com/discuss/post/5979952/google-london-l4-aug-oct-24-offer-accept-vb8y/

Here’s a clean extraction + mapping of the problems described in the post to closest LeetCode problems:

---

**Problem:**
Design a data structure to find the average of the last *n* elements in a stream, with a follow-up to ignore the highest values.

**Topic Tags:**
Queue, Sliding Window, Heap (Priority Queue), Design

**Close Leetcode Problems:**

* Moving Average from Data Stream (LC 346)
* Find Median from Data Stream (LC 295) *(for heap-based thinking)*
* Sliding Window Maximum (LC 239) *(conceptual overlap for window maintenance)*

---

**Problem:**
Graph shortest path problem with BFS; includes follow-up requiring multiple BFS runs.

**Topic Tags:**
Graph, BFS, Shortest Path

**Close Leetcode Problems:**

* Shortest Path in Binary Matrix (LC 1091)
* Word Ladder (LC 127)
* Rotting Oranges (LC 994) *(multi-source BFS pattern)*
* 01 Matrix (LC 542) *(multiple BFS optimization)*

---

**Problem:**
Graph problem involving topological sorting (initially not identified directly).

**Topic Tags:**
Graph, Topological Sort, DFS, BFS (Kahn’s Algorithm), DAG

**Close Leetcode Problems:**

* Course Schedule (LC 207)
* Course Schedule II (LC 210)
* Alien Dictionary (LC 269)
* Parallel Courses (LC 1136)

---

- https://leetcode.com/discuss/post/5807042/google-l4-india-rejected-by-anonymous_us-37up/

Here’s a structured extraction from your post, mapping each mentioned/implicit problem to the closest LeetCode problems:

---

### Problem:

Single-threaded CPU scheduling (process tasks based on enqueue time + processing time)

**Topic Tags:** Heap (Priority Queue), Sorting, Simulation

**Close Leetcode Problems:**

* Single-Threaded CPU
* Task Scheduler (variation with scheduling constraints)

---

### Problem:

Placing minimum cameras in a binary tree to monitor all nodes

**Topic Tags:** Binary Tree, DFS, Greedy

**Close Leetcode Problems:**

* Binary Tree Cameras
* Binary Tree Maximum Path Sum (similar DFS tree-state propagation pattern)

---

### Problem:

Removing maximum stones using row/column connectivity (connected components)

**Topic Tags:** Disjoint Set Union (DSU), Graph, Connected Components

**Close Leetcode Problems:**

* Most Stones Removed with Same Row or Column
* Number of Provinces (classic DSU)
* Accounts Merge (DSU with mapping)

---

### Problem:

Unknown string problem (brute force solved, optimization missing)

**Topic Tags:** Strings, Sliding Window / Hashing / DP (likely), Optimization

**Close Leetcode Problems (most probable patterns based on interview trends):**

* Longest Substring Without Repeating Characters (sliding window optimization jump from brute force)
* Minimum Window Substring (classic optimization-heavy string problem)
* Longest Repeating Character Replacement (two-pointer optimization)

---

- https://leetcode.com/discuss/post/5741664/google-l4-backened-bangalore-or-hyderaba-dard/

Here’s a structured extraction + mapping of the problems described, with closest LeetCode equivalents and proper topic tagging.

---

### Problem:

Initial BFS question → Modified to shortest path with obstacles (Dijkstra)

Topic Tags:
Graph, BFS, Dijkstra, Shortest Path, Priority Queue, Grid

Close Leetcode Problems:

* 1091. Shortest Path in Binary Matrix
* 1631. Path With Minimum Effort
* 743. Network Delay Time
* 778. Swim in Rising Water

---

### Problem:

Two-source BFS (two diseases spreading), one dominates and blocks the other; check if weaker one reaches destination

Topic Tags:
Graph, Multi-source BFS, Simulation, Grid Traversal, Competition/Blocking

Close Leetcode Problems:

* 994. Rotting Oranges
* 2258. Escape the Spreading Fire
* 542. 01 Matrix
* 1926. Nearest Exit from Entrance in Maze

---

### Problem:

Given employee arrival & departure times, print active employees in each time interval

Topic Tags:
Sweep Line, Intervals, Sorting, Events, Simulation

Close Leetcode Problems:

* 253. Meeting Rooms II
* 759. Employee Free Time
* 56. Merge Intervals
* 732. My Calendar III

---

### Problem:

Find peak element in mountain array with duplicates

Topic Tags:
Binary Search, Arrays, Peak Finding, Edge Cases

Close Leetcode Problems:

* 162. Find Peak Element
* 852. Peak Index in a Mountain Array
* 1095. Find in Mountain Array

---

### Problem:

(Extra coding round – Array question, unspecified but likely pattern-based)

Topic Tags:
Array, Two Pointers / Prefix / Sliding Window (context-dependent)

Close Leetcode Problems:

* 53. Maximum Subarray
* 238. Product of Array Except Self
* 560. Subarray Sum Equals K
* 11. Container With Most Water

---
</pre>
