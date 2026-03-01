## 1. Dijkstra
Identification: Single source shortest paths (quite easy to identify)
- https://leetcode.com/problems/network-delay-time/
- https://leetcode.com/problems/cheapest-flights-within-k-stops/description/
- https://leetcode.com/problems/path-with-minimum-effort/
- https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/description/
- https://leetcode.com/problems/minimum-obstacle-removal-to-reach-corner/description/
- https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/description/

## 2. Toposort
Identification: Toposort applies if and only if: We need to order things such that dependencies are satisfied.
Formally:
- Directed graph
- No cycles allowed
- Precedence constraints
- https://leetcode.com/problems/course-schedule/description/ (Kahns Algorithm - Toposort - DAG cycle detection)
- https://leetcode.com/problems/course-schedule-ii/description/
- https://leetcode.com/problems/find-eventual-safe-states/description/
- https://www.geeksforgeeks.org/problems/alien-dictionary/1 (super imp)
- 


## 3. Multi-source BFS
- https://leetcode.com/problems/as-far-from-land-as-possible/description/ (Google Phone Screen L4)
- https://leetcode.com/problems/rotting-oranges/description/

## 4. DFS/BFS
- https://leetcode.com/problems/number-of-provinces/description/
  ```
  {
"key_learning": [
"Transitive connectivity language (directly + indirectly connected) is a strong trigger for modeling the problem as an undirected graph and reducing it to counting connected components.",
"An adjacency matrix representation implies O(n^2) traversal; for dense graphs DFS/BFS over the matrix is optimal, while Union-Find provides a clean abstraction when thinking in terms of dynamic merging or follow-up edge additions.",
"Counting disjoint groups is equivalent to counting traversal initiations from unvisited nodes; this mental model generalizes to islands, friend circles, network clusters, and generic component-count problems.",
"Symmetric matrix with self-connections signals undirected graph properties; avoid redundant work by leveraging visited tracking and iterating only necessary indices.",
"Interview tradeoff thinking: DFS/BFS is simpler and space O(n), Union-Find offers near O(1) amortized merges (alpha(n)) and scales better when edges are streamed or modified.",
"Edge-case awareness includes n=1, fully disconnected graph (answer = n), fully connected graph (answer = 1), and ensuring no double-counting due to matrix symmetry.",
"Follow-up signals include: dynamically adding connections, detecting largest component size, checking if graph is fully connected, or converting adjacency matrix to adjacency list for sparse optimization."
]
}

  ```
