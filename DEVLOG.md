# Development Log – The Torchbearer

**Student Name:** Aidan Baker
**Student ID:** 826601445

> Instructions: Write at least four dated entries. Required entry types are marked below.
> Two to five sentences per entry is sufficient. Write entries as you go, not all in one
> sitting. Graders check that entries reflect genuine work across multiple sessions.
> Delete all blockquotes before submitting.

---

## Entry 1 – [May 8-9]: Initial Plan

> Required. Write this before writing any code. Describe your plan: what you will
> implement first, what parts you expect to be difficult, and how you plan to test.

I cloned the repsoitory and have it on VS Code now, I reviewed Assignment.md. This project seems to be based on finding the shortest path and visiting all relics, so Dijkstra's is my best bet to implement this. I need to backtrack also to try all diffrent scenarios. I am confused a bit on the torch and keeping it from burning out but I believe after reviewing the code more it shouldnt be that hard to understand. Hardest part is definetly the backtracking for me. For testing I will just use small cases with few relics and I can manually check to see if it is working properly.

*I was wrong about the torch burning out, it doesn't it represensts path cost

---

## Entry 2 – [May 10]: [Short description]

> Required. At least one entry must describe a bug, wrong assumption, or design change
> you encountered. Describe what went wrong and how you resolved it.

A wrong assumption I had before reading and testing the code was with the torch fuel, I first assumed it was a meter that had a limit, I overthought it and it is just a way to track shortest path. A bug I actually ran into was in precompute_distances() I forgot to assign the result of run_dijkstra to dist_table[source], so I wasn't even storing the computed distance. I was storing nothing. There wasn't really anthing to resolve, I initially made my own simple tests to make sure I was storing all results, but I ignored the fact that I was storing no result and didn't realize till much later.

---

## Entry 3 – [Date]: [Short description]

_Your entry here._

---

## Entry 4 – [Date]: Post-Implementation Reflection

> Required. Written after your implementation is complete. Describe what you would
> change or improve given more time.

_Your entry here._

---

## Final Entry – [Date]: Time Estimate

> Required. Estimate minutes spent per part. Honesty is expected; accuracy is not graded.

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | 0.5 hours |
| Part 2: Precomputation Design | 3.5 hours |
| Part 3: Algorithm Correctness | 1 hour |
| Part 4: Search Design | .5 hours |
| Part 5: State and Search Space | |
| Part 6: Pruning | |
| Part 7: Implementation | |
| README and DEVLOG writing | 1.5 hours |
| **Total** | |
