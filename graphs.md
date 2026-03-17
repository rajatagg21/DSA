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
- https://leetcode.com/problems/detect-cycles-in-2d-grid/ (based on cycle detection only)
- https://leetcode.com/problems/surrounded-regions/
```json
{
"key_learning": [
"Grid-as-graph abstraction: model each cell as a node with 4-directional edges; this reduces the problem to connected components classification with boundary constraints.",
"Recognition trigger: 'connected horizontally or vertically' + 'region' → connected components; 'none on edge' → boundary reachability; invert thinking to mark boundary-connected components instead of checking enclosure per region.",
"Core pattern: multi-source flood fill from boundary nodes; classify safe components first, then transform remaining nodes in-place; this avoids per-component enclosure validation.",
"Tradeoff model: DFS (simpler, recursion depth risk) vs BFS (heap-backed queue, production-safe) vs Union-Find (explicit component tracking, higher constant factor); choose based on stack safety and memory constraints.",
"Time-space expectation: O(mn) time with single traversal; O(1) extra space preferred via in-place marking; recursive stack O(mn) worst-case must be justified or avoided.",
"Edge-case awareness: empty grid, single row/column, all 'O's, no 'O's, thin snake-like regions causing deep recursion, duplicate boundary processing.",
"Reusable mental model: classify nodes by reachability from forbidden/privileged boundary set, then mutate the complement set; applicable to island counting, enclave detection, and percolation-style problems.",
"Follow-up signals: diagonal connectivity variation (8-direction graph), weighted cells (requires Dijkstra), dynamic updates (Union-Find), count regions instead of mutate, or return region sizes (component aggregation)."
]
}
```
- https://leetcode.com/problems/number-of-enclaves/description/
- https://www.geeksforgeeks.org/problems/number-of-distinct-islands/1
```json
{
"key_learning": [
"Core abstraction: 2D grid interpreted as an implicit unweighted graph; islands correspond to connected components under 4-directional adjacency.",
"Recognition trigger: "connected 1s" → connected component discovery; "distinct" → canonical shape representation problem.",
"Pattern classification: component traversal (DFS/BFS) + structural normalization (relative coordinate encoding or traversal signature).",
"Key insight: translation invariance required (shift-invariant representation), but rotation/reflection are NOT considered equivalent → no need for geometric normalization beyond translation.",
"Canonicalization mental model: store each island as coordinates relative to its starting cell or origin anchor to remove positional bias.",
"Shape equivalence requires deterministic traversal order or post-processing normalization (e.g., sorted coordinate list) to avoid ordering artifacts.",
"Time complexity target: O(n*m) traversal; additional O(K log K) per island for canonical sorting (K = island size); overall bounded by O(n*m log(n*m)).",
"Space complexity expectation: O(n*m) for visited tracking plus storage of island shapes.",
"Tradeoff thinking: DFS simpler for shape capture; BFS equivalent; Union-Find insufficient alone since structure (not just connectivity) must be recorded.",
"Edge-case awareness: single-cell islands, entire grid one island, thin grids, checkerboard patterns, repeated identical shapes at different locations.",
"Reusable pattern: this is "connected component labeling + canonical hashing" — similar to distinct subtrees, duplicate subtree detection, or shape fingerprinting problems.",
"Follow-up signals: if rotations/reflections are considered identical → must generate all 8 transformations and choose minimal canonical form; if diagonal connectivity allowed → adjacency model changes to 8-direction graph."
]
}
```
- https://leetcode.com/problems/is-graph-bipartite/description/
```json
{
"key_learning": [
"Core abstraction: undirected graph property verification; bipartiteness reduces to 2-coloring problem under adjacency constraints.",
"Recognition trigger: "partition into two sets" + "every edge connects across sets" → graph coloring with 2 colors; equivalent to checking absence of odd-length cycles.",
"Pattern classification: BFS/DFS level-order traversal with parity assignment; conflict detection when adjacent nodes share same color.",
"Disconnected graph signal: must iterate across all nodes and initiate traversal for unvisited components.",
"Time complexity target: O(V + E) mandatory; any superlinear approach unacceptable for interview-level graph problems.",
"Space complexity expectation: O(V) for color/visited tracking and traversal queue/stack.",
"Tradeoff thinking: BFS naturally enforces level parity (clean for bipartite); DFS equivalent but requires careful parent/color handling; Union-Find with parity useful for dynamic edge addition follow-ups.",
"Key invariant: if during traversal an edge connects nodes of identical color → odd cycle detected → not bipartite.",
"Edge-case awareness: isolated nodes are trivially bipartite; single-node graph valid; disconnected components must not short-circuit incorrectly.",
"Reusable mental model: bipartite check = parity layering on graph; same reasoning applies to scheduling constraints, possible grouping, and constraint satisfaction with binary states.",
"Follow-up signal: if directed graph → bipartite definition changes; if edges added dynamically → use Union-Find with parity tracking; if need to return partitions → store color groups explicitly."
]
}
```
## 5. Bridges and Cut Vertex
- https://leetcode.com/problems/critical-connections-in-a-network/

```json
{
"key_learning": [
"Recognize 'removal disconnects graph' → bridge detection in an undirected graph → maps to Tarjan’s low-link algorithm",
"Core abstraction: undirected graph + DFS traversal with discovery time (tin) and lowest reachable ancestor (low)",
"Bridge condition pattern: edge (u,v) is critical if low[v] > tin[u] → no back-edge from subtree of v to u or above",
"Pattern classification: articulation/bridge problems → subset of connectivity + cycle detection using DFS tree properties",
"Key signal: 'directly or indirectly reachable' → connected components + transitive connectivity → graph modeling",
"Avoid brute-force edge removal (O(E*(V+E))) → optimized linear time O(V+E) using single DFS pass",
"Tradeoff: DFS-based Tarjan vs Union-Find → Union-Find cannot detect bridges in a single pass without offline tricks",
"Maintain parent tracking in DFS to avoid falsely treating bidirectional edge as back-edge",
"Edge-case awareness: disconnected graph → run DFS from all unvisited nodes; single node or no edges → no bridges",
"Graph size expectations: up to ~10^5 nodes/edges → must use adjacency list + O(V+E) solution",
"Low-link mental model: captures earliest reachable ancestor via back-edges → reusable for SCCs, articulation points, bridges",
"Follow-up signals: 'remove node disconnects graph' → articulation points; 'strongly connected' → SCC (directed graph variant)"
]
}
```

