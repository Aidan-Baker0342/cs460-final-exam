# The Torchbearer

**Student Name:** Aidan Baker
**Student ID:** 826601445
**Course:** CS 460 – Algorithms | Spring 2026

> This README is your project documentation. Write it the way a developer would document
> their design decisions , bullet points, brief justifications, and concrete examples where
> required. You are not writing an essay. You are explaining what you built and why you built
> it that way. Delete all blockquotes like this one before submitting.

---

## Part 1: Problem Analysis

> Document why this problem is not just a shortest-path problem. Three bullet points, one
> per question. Each bullet should be 1-2 sentences max.

- **Why a single shortest-path run from S is not enough:**
  This doesn't work since running this would lead to relics being missed since the problem require visiting all relic nodes not just reach the end in the shortest path. 

- **What decision remains after all inter-location costs are known:**
  The decision left is what order the relics should be visits to result in the shortest route.

- **Why this requires a search over orders (one sentence):**
  It requires search over orders since we compare all possible routes and choose the shortest path for minimal cost.

---

## Part 2: Precomputation Design

### Part 2a: Source Selection

> List the source node types as a bullet list. For each, one-line reason.

| Source Node Type | Why it is a source |
|---|---|
| Spawn | We start here and shortest path to all relics |
| Relics | Shortest path from relic to relic and relics to exit |

### Part 2b: Distance Storage

> Fill in the table. No prose required.

| Property | Your answer |
|---|---|
| Data structure name | Dictionary |
| What the keys represent | GRaph nodes |
| What the values represent | Min cost from starting node to other nodes |
| Lookup time complexity | O(1) |
| Why O(1) lookup is possible | Python dictionaries use hashing |

### Part 2c: Precomputation Complexity

> State the total complexity and show the arithmetic. Two to three lines max.

- **Number of Dijkstra runs:** k + 1
- **Cost per run:** O(m log n)
- **Total complexity:** O((k + 1) * (m log n))
- **Justification (one line):** We run it once at the start and again for each k relic.

---

## Part 3: Algorithm Correctness

> Document your understanding of why Dijkstra produces correct distances.
> Bullet points and short sentences throughout. No paragraphs.

### Part 3a: What the Invariant Means

> Two bullets: one for finalized nodes, one for non-finalized nodes.
> Do not copy the invariant text from the spec.

- **For nodes already finalized (in S):**
  - The distnaces are finished and optimized, for the nodes found the shortest min cost is found.

- **For nodes not yet finalized (not in S):**
  - Nodes that have not yet been optimized for their route, Dijkstra's hasn't fully optimized.

### Part 3b: Why Each Phase Holds

> One to two bullets per phase. Maintenance must mention nonnegative edge weights.

- **Initialization : why the invariant holds before iteration 1:**
  - At the start the source dist is 0 and every node is set to infinity, so no other paths have been discovered.

- **Maintenance : why finalizing the min-dist node is always correct:**
  - The node with smallest curr_distance cannot be imporved on since all edge weights are nonnegative. 
  - Later path to a past node would only increase the weight not lessen.

- **Termination : what the invariant guarantees when the algorithm ends:**
  - At finish every reachable node has its shortest path from the source.

### Part 3c: Why This Matters for the Route Planner

> One sentence connecting correct distances to correct routing decisions.

The correct shortest path distances means the algorithmn can compare and choice the optimal route with the lowest total cost.

---

## Part 4: Search Design

### Why Greedy Fails

> State the failure mode. Then give a concrete counter-example using specific node names
> or costs (you may use the illustration example from the spec). Three to five bullets.

- **The failure mode:** Greedy strategy always fails since it always chooses shortest path to the next relic, but this can lead to a less optimial total final cost since it doesn't see future path costs. 
- **Counter-example setup:** Start at S the cost to A is 1 and to B is 2, from A to B costs 4, and from B to A cost 1.
- **What greedy picks:** Greedy strategy chooses A first since it has a smaller cost, then picks A to B with a cost of 4 ending in a total final cost of 5.
- **What optimal picks:** The optimal strategy chooses B first at cost of 2 then from B to A at cost 1, total final cost is 3.
- **Why greedy loses:** Since Greedy chooses the most optimal path each step it can lead to a less optimal final path, shown by Greedy chooses A first at 1 but ending with a final cost of 5 with a more optimal final path with B leading to a final cost of 3.

### What the Algorithm Must Explore

> One bullet. Must use the word "order."

- The algorithmn must explore all possible orders of relic nodes to determine path has the minimum total cost.

---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---|---|---|---|
| Current location | current_loc | node | The node that we are currently searching |
| Relics already collected | relics_visited_order | list[node] | The collected relics so far stored as a list in the order visited|
| Fuel cost so far | cost_so_far | float | The total fuel cost so far |

### Part 5b: Data Structure for Visited Relics

> Fill in the table.

| Property | Your answer |
|---|---|
| Data structure chosen | List |
| Operation: check if relic already collected | Time complexity: O(1)|
| Operation: mark a relic as collected | Time complexity: O(1)|
| Operation: unmark a relic (backtrack) | Time complexity: O(1)|
| Why this structure fits | A list hold the relics visited order which allows for backtracking|

### Part 5c: Worst-Case Search Space

> Two bullets.

- **Worst-case number of orders considered:** k!
- **Why:** Since the algorithmn has to try all possible order of relics.

---

## Part 6: Pruning

### Part 6a: Best-So-Far Tracking

> Three bullets.

- **What is tracked:** The best complete route with its total fuel cost and relic order.
- **When it is used:** Checked before continue deeper.
- **What it allows the algorithm to skip:** It skips paths whose current cost is already greater than or equal to the best route.

### Part 6b: Lower Bound Estimation

> Three bullets.

- **What information is available at the current state:** The current location, remainig relics, and total fuel cost so far.
- **What the lower bound accounts for:** It uses the current cost as the min for possible routes to continue.
- **Why it never overestimates:** since all edge weights are nonnegtive, so more movements only increase cost.

### Part 6c: Pruning Correctness

> One to two bullets. Explain why pruning is safe.

-  Its safe since the current cost is already greater than or equal to the best route known
-  Continueing cannot be more optimized

---

## References

> Bullet list. If none beyond lecture notes, write that.

- CS 460 lecture notes on Dijkstra’s algorithm and backtracking
- Python documentation for heapq
- GeeksforGeeks – Dijkstra’s Algorithm explanation and examples
