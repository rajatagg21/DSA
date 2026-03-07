## Google Past Interview Problems (Graphs)

- https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/description/

```markdown
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
```
