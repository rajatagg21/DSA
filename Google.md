## Google Past Interview Problems (Graphs)

- https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/description/

**Brute → Optimal approach summary**

**1. Brute Force Idea**

* Use **BFS** because every move has equal cost and we want the **shortest path**.
* State = **(x, y, remaining_k)**.
* From each cell explore **4 directions**.
* If the next cell is an obstacle, reduce `k`.

**Problem:**
A cell can be visited many times with different `k` values → state space becomes **O(m × n × k)**.
If we track visited as `visited[m][n][k]`, memory becomes large and exploration increases.

---

**2. Observation**
Reaching the same cell `(x, y)` with:

* **more remaining eliminations** is always **better**.
* **less or equal eliminations** is **useless**, because a better state already exists.

Example:

Cell `(2,3)`

* reached with `k = 3` → good
* reached later with `k = 1` → pointless (worse state)

---

**3. Optimization**
Instead of storing `visited[x][y][k]`, store:

`best[x][y] = maximum remaining k seen at this cell`

When exploring a neighbor:

* compute `new_k = k_remaining - grid[nx][ny]`
* if `new_k < 0` → cannot go
* if `best[nx][ny] >= new_k` → skip (we already reached with a better state)
* otherwise update `best` and push to BFS.

---

**4. Extra Optimization**
If:

`k >= m + n - 2`

Then we can always go straight to the destination by removing obstacles.

Return:

`m + n - 2`

---

**Final Complexity**

* **Time:** `O(m × n × k)`
* **Space:** `O(m × n)`

---

**Core intuition:**
We prune BFS states by **keeping only the best obstacle-elimination state per cell**, which removes redundant exploration and makes the solution memory efficient.

- https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/description/

### Problem

For each query `(u, v, limit)`:

> Is there a path between `u` and `v` where **all edges have weight < limit**?

---

# 1️⃣ Brute Force Idea

For **every query**:

1. Build graph using **only edges with weight < limit**
2. Run **BFS/DFS from u**
3. Check if `v` reachable

**Time**

```
O(Q * (V + E))
```

Too slow.

---

# 2️⃣ Observation

Queries differ **only by the edge limit**.

If limit increases → **more edges become usable**.

Graph is **monotonically growing**.

---

# 3️⃣ Key Insight

Instead of rebuilding graph each time:

* **Sort edges by weight**
* **Sort queries by limit**

Process queries **in increasing limit order**.

---

# 4️⃣ Optimized Approach (DSU)

Maintain connectivity using **Union Find**.

For each query:

```
while edge_weight < limit:
    union(edge)

check find(u) == find(v)
```

Edges are **added only once**.

---

# 5️⃣ Complexity

```
Sorting edges:   O(E log E)
Sorting queries: O(Q log Q)
Union/Find:      ~O(E + Q)
```

Overall:

```
O(E log E + Q log Q)
```

---

# 6️⃣ Core Intuition (1 line)

> As the **limit grows**, keep **adding edges** and track connectivity with **DSU** instead of recomputing paths.

---

If you're doing **DSU prep for interviews**, this problem teaches a **very important pattern**:

**“Offline queries + sorting + DSU incremental graph building.”**

This pattern appears in **many hard problems**.

