# Development Log – The Torchbearer

**Student Name:** Aidan Baker
**Student ID:** 826601445


---

## Entry 1 – [May 8]: Initial Plan


I cloned the repsoitory and have it on VS Code now, I reviewed Assignment.md. This project seems to be based on finding the shortest path and visiting all relics, so Dijkstra's is my best bet to implement this. I need to backtrack also to try all diffrent scenarios. I am confused a bit on the torch and keeping it from burning out but I believe after reviewing the code more it shouldnt be that hard to understand. Hardest part is definetly the backtracking for me. For testing I will just use small cases with few relics and I can manually check to see if it is working properly.

*I was wrong about the torch burning out, it doesn't it represensts path cost

---

## Entry 2 – [May 10]: [Part 2 a-c Debugging]


A wrong assumption I had before reading and testing the code was with the torch fuel, I first assumed it was a meter that had a limit, I overthought it and it is just a way to track shortest path. A bug I actually ran into was in precompute_distances() I forgot to assign the result of run_dijkstra to dist_table[source], so I wasn't even storing the computed distance. I was storing nothing. There wasn't really anthing to resolve, I initially made my own simple tests to make sure I was storing all results, but I ignored the fact that I was storing no result and didn't realize till much later.

---

## Entry 3 – [May 12]: [Part 5-6 Debugging]

Part 6 was an extremely hard part for me to get down alot of put dowards the backtracking and the pattern of choosing a relic to explore its path and then which I didn't realize is undoing the choice to allow another order to be tested. I also struggled with understanding correct order of operations to do for _explore. I tried to just remove the relic from the list and add it back later and I had issues with how the recursion behaves. It really helped when I made a copy of the remaining relics after I appended the relic to the visisted path and then removed it. After testing I wans't skipping paths on some tests cases.

---

## Entry 4 – [May 13]: Post-Implementation Reflection


I would really like to see a visual interface be made for this to imporve upon it, I could use HTML, CSS, and maybe JavaScipt to display the graph we navigate on to a user. I think being able to see the torchbearer traverse the dungeon would be so cool and a great way to show this alogorithmn working. Also imporving the efficency would be needed im afraid with bigger test cases it could take to much time checking every possible path or even optimizing so less pruning or less paths needing to be explored to deem a sections not optimal. 

---

## Final Entry – [Date]: Time Estimate


| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | 0.5 hours |
| Part 2: Precomputation Design | 4 hours |
| Part 3: Algorithm Correctness | 1 hour |
| Part 4: Search Design | 1 hours |
| Part 5: State and Search Space | 1.5 hours |
| Part 6: Pruning | 3 hours |
| Part 7: Implementation | .5 hours |
| README and DEVLOG writing | 4 hours |
| **Total** | 15.5 hours |
