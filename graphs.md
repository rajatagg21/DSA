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
```json
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

- https://leetcode.com/problems/detonate-the-maximum-bombs/description/
```json
{
"key_learning": [
"Chain reaction phrasing (one triggers others which further trigger) is a strong signal for modeling the system as a directed graph and computing reachability via DFS/BFS from each node.",
"Geometric range condition (point within circle) translates into directed edge construction using distance comparison; this preprocessing is O(n^2) and dominates complexity for n up to typical interview limits.",
"Problem reduces to finding the maximum reachable nodes from any single source in a directed graph (multi-source reachability maximization).",
"Tradeoff thinking: DFS/BFS per node gives O(n*(n+e)) which is acceptable for n ≤ few hundreds; no need for Dijkstra since edges are unweighted; Union-Find is unsuitable because reachability is directional, not symmetric connectivity.",
"Optimization awareness: precompute adjacency list once; avoid recomputing distances inside traversal; consider pruning if graph is sparse.",
"Edge cases include isolated bombs (answer = 1), fully mutually reachable bombs (answer = n), and directional asymmetry where A triggers B but not vice versa.",
"Follow-up signals: asking for minimum bombs to detonate all (minimum start nodes → strongly connected components condensation DAG), dynamic bomb insertion (incremental graph), or weighted radii constraints leading to geometric indexing optimizations."
]
}
```

- https://leetcode.com/problems/number-of-islands/description/
```json
{
"key_learning": [
"2D grid with adjacency constraints (horizontal/vertical) is an implicit graph; each land cell is a node and 4-directional neighbors define edges, reducing the problem to counting connected components.",
"Trigger phrases like 'number of islands' and 'connected adjacent lands' map directly to flood-fill / connected-component traversal using DFS/BFS, or Union-Find if dynamic merging is required.",
"Time complexity expectation is O(m*n) since every cell must be visited once; space tradeoff includes recursion stack vs explicit queue vs in-place mutation to eliminate auxiliary visited matrix.",
"Mutating the grid to mark visited cells is a valid O(1) space optimization when input modification is allowed, demonstrating interview-level space awareness.",
"Edge-case awareness includes empty grid, single cell, all water, all land, and handling boundary conditions without index overflow.",
"Reusable mental model: any grid-based region-counting problem (islands, regions, blobs, clusters) follows identical component-count template with configurable neighbor directions (4 vs 8).",
"Follow-up signals include largest island size, number of distinct shapes (shape normalization), dynamic addition of land (Union-Find incremental connectivity), or perimeter computation (boundary counting pattern)."
]
}
```

- https://leetcode.com/problems/flood-fill/description/
```json
{
"key_learning": [
"Implicit graph modeling: 2D grid with 4-directional adjacency forms an unweighted graph; flood fill is connected component traversal constrained by value equality.",
"Recognition trigger: "directly adjacent" + "shares same color" + "keep repeating" → region expansion via DFS/BFS; this is a same-value connected component problem.",
"State mutation vs visited tracking tradeoff: in-place recoloring can serve as visited marking if original color is cached; requires early exit when new color equals original.",
"Time complexity target O(m*n) since each cell is processed at most once; space O(m*n) worst-case due to recursion stack or BFS queue.",
"DFS vs BFS tradeoff: DFS is concise but risks stack overflow on large continuous regions; BFS provides controlled memory growth; iterative DFS avoids recursion limits.",
"Boundary validation pattern: robust neighbor generation with bounds checks is critical to avoid invalid memory access; treat grid dimensions as dynamic not constant.",
"Edge-case triggers: starting cell already has target color, single-cell grid, entire grid uniform, thin grids (1 x n or m x 1).",
"Mental model reuse: identical structural pattern to Number of Islands, Surrounded Regions, and other grid connected-component labeling tasks.",
"Follow-up signal: changing adjacency to 8 directions, introducing weights, distance limits, or multiple sources shifts traversal to multi-source BFS or Dijkstra.",
"Optimization insight: region growth is proportional to reachable component size; worst-case full-grid traversal but no superlinear behavior is acceptable in interviews."
]
}
```

- https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1
```json
{
"key_learning": [
"Core abstraction: undirected graph cycle detection → either DFS with parent tracking or Union-Find (Disjoint Set Union) for incremental edge processing.",
"Recognition trigger: "undirected" + "contains a cycle" → need to detect back-edge excluding immediate parent; parent-awareness is mandatory in DFS.",
"Pattern classification: cycle in undirected graph ≠ back-edge to any visited node; must ignore the edge to the parent to avoid false positives.",
"Alternative formulation: if during Union-Find processing two vertices of an edge already share the same root → cycle detected (connected components merging logic).",
"Multiple components trigger: traversal must iterate across all vertices; unvisited node → start new DFS/BFS.",
"Time complexity target: O(V + E) for DFS/BFS; O(E α(V)) for Union-Find with path compression and union by rank.",
"Tradeoff insight: DFS exposes structure and supports follow-ups (cycle path retrieval); Union-Find is simpler for pure detection and dynamic edge addition.",
"Edge-case awareness: self-loop immediately forms cycle; parallel edges between same vertices form cycle in undirected graph.",
"Mental model reuse: cycle detection in undirected graphs underpins tree validation (tree = connected + acyclic) and redundant connection problems.",
"Follow-up signal: if directed graph → shift to DFS with recursion stack or Kahn’s algorithm (topological sort) for cycle detection."
]
}
```
