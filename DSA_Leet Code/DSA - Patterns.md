# DSA Patterns — Complete Reference

> 30+ topics · 100+ patterns · Recognition clues · Complexity tags

---

## Table of Contents

- [[#Arrays]]
- [[#Strings]]
- [[#Sliding Window]]
- [[#Prefix Sum]]
- [[#Two Pointers]]
- [[#Bit Manipulation]]
- [[#Hash Tables]]
- [[#Stacks]]
- [[#Queues & Monotonic Queue]]
- [[#Linked List]]
- [[#Binary Search]]
- [[#Sorting]]
- [[#Recursion & Backtracking]]
- [[#Trees — Traversal]]
- [[#BST]]
- [[#Tries]]
- [[#Heaps]]
- [[#Intervals]]
- [[#Greedy]]
- [[#Graph — DFS]]
- [[#Graph — BFS]]
- [[#Topological Sort]]
- [[#Union Find]]
- [[#Shortest Path]]
- [[#Minimum Spanning Tree]]
- [[#1-D Dynamic Programming]]
- [[#Knapsack DP]]
- [[#Longest Increasing Subsequence]]
- [[#2D Grid DP]]
- [[#String DP]]
- [[#Tree — Graph DP]]
- [[#Bitmask DP]]
- [[#Segment Tree & BIT]]
- [[#Math & Geometry]]

---

## Arrays

### Two Pointers (Opposite Ends)
> **When to use:** Sorted array, find pair with target sum/difference, or check palindrome.

**Steps:**
1. Set `left = 0`, `right = n - 1`
2. Move `left++` if sum too small, `right--` if too large
3. Stop when pointers cross

**Recognition clue:** `sorted`, `pair`, `target sum`
**Complexity:** `O(n)` time · `O(1)` space · in-place

---

### Two Pointers (Same Direction)
> **When to use:** Remove duplicates, partition array, or merge two sorted arrays in-place.

**Steps:**
1. `slow` pointer tracks the "write" position
2. `fast` pointer scans forward
3. Copy `fast → slow` only when condition is met

**Recognition clue:** `remove`, `deduplicate`, `partition`
**Complexity:** `O(n)` time · `O(1)` space · in-place

---

### Prefix Product Trick
> **When to use:** Product of every subarray except self, or range queries without division.

**Steps:**
1. Build left-product array left to right
2. Build right-product array right to left
3. Multiply `left[i] * right[i]` for the answer

**Recognition clue:** `except self`, `range product`
**Complexity:** `O(n)` time · `O(n)` space · no division needed

---

### Cycle Sort / Index Mapping
> **When to use:** Find missing or duplicate numbers in range `[1..n]`.

**Steps:**
1. Place each number at index `num - 1`
2. Re-scan: index where `arr[i] != i + 1` is missing/duplicate

**Recognition clue:** `missing positive`, `1..n range`
**Complexity:** `O(n)` time · `O(1)` space

---

## Strings

### Two-Pointer Palindrome Check
> **When to use:** Check or build palindromes, reverse words.

**Steps:**
1. `left` from start, `right` from end
2. Skip non-alphanumeric characters if needed
3. Compare chars, advance inward

**Recognition clue:** `palindrome`, `reverse`
**Complexity:** `O(n)` time

---

### Character Frequency Map
> **When to use:** Anagram check, ransom note, isomorphic strings.

**Steps:**
1. Count chars of string A into a map
2. Subtract counts using string B
3. All zeros = valid match

**Recognition clue:** `anagram`, `contains`, `frequency`
**Complexity:** `O(n)` time · `O(26)` space

---

### KMP / Z-Algorithm
> **When to use:** Find all occurrences of a pattern in text efficiently.

**Steps:**
1. Build failure function (prefix = suffix lengths)
2. Slide pattern using failure array to avoid re-comparison

**Recognition clue:** `repeated match`, `substring search`
**Complexity:** `O(n + m)` time

---

### Simulation / Row-by-Row
> **When to use:** Zigzag, spiral, or encoded string construction.

**Steps:**
1. Simulate the pattern step by step
2. Append characters to appropriate buckets
3. Concatenate buckets for final result

**Recognition clue:** `zigzag`, `encode`, `pattern layout`
**Complexity:** `O(n)` time

---

## Sliding Window

### Fixed-Size Window
> **When to use:** Max/min/avg of every subarray of exactly length k.

**Steps:**
1. Compute sum of first window
2. Slide: add `arr[right]`, remove `arr[right - k]`
3. Track max/min as you go

**Recognition clue:** `length k`, `every window`, `subarray of size k`
**Complexity:** `O(n)` time · `O(1)` space

---

### Dynamic Window (Expand / Shrink)
> **When to use:** Longest or shortest subarray satisfying a condition.

**Steps:**
1. Expand `right` pointer until condition breaks
2. Shrink `left` pointer to restore the condition
3. Record window size at each valid state

**Recognition clue:** `longest/shortest subarray`, `at most k distinct`
**Complexity:** `O(n)` time

---

### Frequency Map Window
> **When to use:** Permutation in string, find all anagrams.

**Steps:**
1. Build frequency map of the pattern
2. Maintain window frequency map
3. Match when window map equals pattern map

**Recognition clue:** `permutation in string`, `anagram in string`
**Complexity:** `O(n)` time · `O(26)` space

---

## Prefix Sum

### Prefix Sum Array
> **When to use:** Multiple range sum queries on a static array.

**Steps:**
1. Build `prefix[i] = prefix[i-1] + arr[i]`
2. Answer `query(l, r) = prefix[r] - prefix[l-1]`

**Recognition clue:** `range sum`, `immutable array`
**Complexity:** `O(1)` query · `O(n)` build

---

### HashMap of Prefix Sums
> **When to use:** Count subarrays with exact sum k, or divisible by k.

**Steps:**
1. Walk array, maintain running sum
2. Check if `(sum - k)` exists in map → subarray found
3. Store `sum → count` in map

**Recognition clue:** `subarray sum equals k`, `count subarrays`
**Complexity:** `O(n)` time · `O(n)` space

---

### Prefix XOR
> **When to use:** Count subarrays with XOR equal to target.

**Steps:**
1. Same as prefix sum but with XOR operator
2. Use map to store prefix XOR frequencies

**Recognition clue:** `subarray XOR`, `XOR equals target`
**Complexity:** `O(n)` time

---

## Two Pointers

### Opposite-End Pointers on Sorted Array
> **When to use:** 2Sum, 3Sum, Container With Most Water.

**Steps:**
1. Sort if not already sorted
2. `left = 0`, `right = n - 1`
3. Adjust based on comparison with target

**Recognition clue:** `sorted`, `two numbers`, `target sum`
**Complexity:** `O(n)` after sort

---

### Merge Two Sorted Arrays
> **When to use:** Merge in-place or find intersection.

**Steps:**
1. Start from ends to avoid overwriting
2. Place larger element at the back
3. Advance the respective pointer

**Recognition clue:** `merge sorted`, `in-place`
**Complexity:** `O(n + m)` time

---

### Trapping Water / Histogram
> **When to use:** Trap rain water, largest rectangle.

**Steps:**
1. Precompute `maxLeft` and `maxRight` arrays
2. Water at `i = min(maxL, maxR) - height[i]`
3. Or use two-pointer to avoid precompute arrays

**Recognition clue:** `trap`, `water`, `bounded by walls`
**Complexity:** `O(n)` time · `O(1)` space (two-pointer version)

---

## Bit Manipulation

### XOR Cancellation
> **When to use:** Find single number, missing number when everything else appears twice.

**Steps:**
1. XOR all numbers together
2. Pairs cancel to `0`, lone number remains

**Recognition clue:** `single number`, `appears once`
**Complexity:** `O(n)` time · `O(1)` space

---

### Bit Counting Tricks
> **When to use:** Count set bits, reverse bits, check power of 2.

**Steps:**
1. `n & (n-1)` clears the lowest set bit
2. `n & (-n)` isolates the lowest set bit
3. Iterate or use lookup table

**Recognition clue:** `number of 1s`, `power of 2`
**Complexity:** `O(log n)` time

---

### XOR to Find Two Uniques
> **When to use:** Two numbers appear once, rest appear twice.

**Steps:**
1. XOR all → XOR of the two unique numbers
2. Find any set bit position (the separating bit)
3. XOR elements in each group separately

**Recognition clue:** `two single numbers`
**Complexity:** `O(n)` time · `O(1)` space

---

### Bitmask Enumeration
> **When to use:** Enumerate all subsets of a set.

**Steps:**
1. Iterate `mask` from `0` to `(1 << n) - 1`
2. For each mask, check which bits are set

**Recognition clue:** `all subsets`, `enumerate combinations`
**Complexity:** `O(2^n)` time

---

## Hash Tables

### Frequency Counting
> **When to use:** Majority element, top-k frequent, group by property.

**Steps:**
1. Insert all elements into a frequency map
2. Query or sort by frequency

**Recognition clue:** `most frequent`, `majority`, `count occurrences`
**Complexity:** `O(n)` time

---

### Two-Sum Pattern
> **When to use:** Find pair with target, or check if complement exists.

**Steps:**
1. For each element, check if `complement (target - x)` is in map
2. If yes → found pair; else insert `x`

**Recognition clue:** `two numbers sum to target`
**Complexity:** `O(n)` time

---

### Grouping by Key
> **When to use:** Group anagrams, isomorphic strings, pattern matching.

**Steps:**
1. Derive canonical key (sorted word, freq tuple)
2. Group all elements sharing the same key

**Recognition clue:** `group`, `same pattern`, `anagram group`
**Complexity:** `O(n log n)` time

---

### Sliding Window + Hash Map
> **When to use:** Longest subarray with k distinct, minimum window substring.

**Steps:**
1. Expand `right`, add to map
2. Shrink `left` when constraint is broken
3. Track answer at each valid window

**Recognition clue:** `k distinct`, `minimum window`
**Complexity:** `O(n)` time

---

## Stacks

### Matching Brackets / Validity
> **When to use:** Valid parentheses, decode nested strings.

**Steps:**
1. Push open brackets onto stack
2. On closing bracket, pop and check match
3. Stack empty at end = valid

**Recognition clue:** `valid`, `balanced`, `brackets`
**Complexity:** `O(n)` time

---

### Monotonic Stack (Increasing)
> **When to use:** Next greater element, daily temperatures, online stock span.

**Steps:**
1. Maintain stack of indices in increasing value order
2. When current > stack top, pop and record answer
3. Push current index

**Recognition clue:** `next greater`, `next smaller`, `waiting for answer`
**Complexity:** `O(n)` time

---

### Monotonic Stack (Decreasing)
> **When to use:** Largest rectangle in histogram, trapping rain water.

**Steps:**
1. Maintain stack where top is always the largest
2. Pop when current element breaks monotonicity
3. Compute area/span on each pop

**Recognition clue:** `largest rectangle`, `span`, `boundaries`
**Complexity:** `O(n)` time

---

### Expression Evaluation
> **When to use:** Evaluate Reverse Polish Notation, basic calculator.

**Steps:**
1. Push operands onto stack
2. On operator, pop two operands, compute, push result

**Recognition clue:** `evaluate`, `calculator`, `RPN`
**Complexity:** `O(n)` time

---

## Queues & Monotonic Queue

### BFS Level Traversal
> **When to use:** Level-order tree traversal, shortest path in unweighted graph.

**Steps:**
1. Enqueue root/source node
2. For each level, process all nodes and enqueue children
3. Track level count for distance

**Recognition clue:** `level order`, `shortest unweighted path`
**Complexity:** `O(V + E)` time

---

### Sliding Window Maximum (Deque)
> **When to use:** Maximum in every window of size k.

**Steps:**
1. Maintain deque of indices, front = current max
2. Remove indices outside window from front
3. Remove smaller elements from back before adding new

**Recognition clue:** `max in window`, `sliding max`
**Complexity:** `O(n)` time

---

### Monotonic Deque for DP
> **When to use:** Jump Game VI — maximize `dp[i]` using window max.

**Steps:**
1. `dp[i] = arr[i] + max(dp[i-k..i-1])`
2. Use deque to maintain window max of dp values

**Recognition clue:** `jump with window`, `max subarray DP`
**Complexity:** `O(n)` time

---

## Linked List

### Fast & Slow Pointers
> **When to use:** Detect cycle, find middle, find cycle start.

**Steps:**
1. `slow` moves 1 step, `fast` moves 2 steps
2. If they meet → cycle exists
3. For cycle start: reset one pointer to head, move both 1 step at a time

**Recognition clue:** `cycle`, `middle of list`
**Complexity:** `O(n)` time · `O(1)` space

---

### In-Place Reversal
> **When to use:** Reverse entire list, reverse sublist `[m..n]`, reverse k-groups.

**Steps:**
1. `prev = null`, `curr = head`
2. Save `next`, point `curr.next = prev`, advance both
3. Reconnect segments for partial reversal

**Recognition clue:** `reverse`, `k-group`
**Complexity:** `O(n)` time · `O(1)` space

---

### Dummy Head Trick
> **When to use:** Remove nth from end, merge lists, partition list.

**Steps:**
1. Create dummy node pointing to head
2. Manipulate `.next` pointers freely
3. Return `dummy.next`

**Recognition clue:** `remove node`, `merge`, `avoid edge cases`
**Complexity:** `O(n)` time

---

### Two-Pointer for Kth from End
> **When to use:** Remove Nth node from end.

**Steps:**
1. Move `fast` pointer `k` steps ahead
2. Move both until `fast` reaches end
3. `slow` is now at the target node

**Recognition clue:** `kth from end`
**Complexity:** `O(n)` time · one pass

---

## Binary Search

### Classic Binary Search
> **When to use:** Search in sorted array, search insert position.

**Steps:**
1. `lo = 0`, `hi = n - 1`
2. `mid = (lo + hi) // 2`
3. Adjust `lo` or `hi` based on comparison

**Recognition clue:** `sorted array`, `find target`
**Complexity:** `O(log n)` time

---

### Binary Search on Answer
> **When to use:** Koko eating bananas, capacity to ship, minimum max.

**Steps:**
1. Define search space `[min_possible, max_possible]`
2. Write `isValid(mid)` predicate function
3. Binary search to find smallest valid answer

**Recognition clue:** `minimum maximum`, `feasibility check`, `at least k`
**Complexity:** `O(n log n)` time

---

### Search in Rotated Array
> **When to use:** Search in rotated sorted array, find minimum.

**Steps:**
1. Find which half is sorted
2. Check if target lies in the sorted half
3. Search that half; else search the other

**Recognition clue:** `rotated`, `pivot point`
**Complexity:** `O(log n)` time

---

### Find Boundary (First/Last Occurrence)
> **When to use:** Find first/last position of element, leftmost condition.

**Steps:**
1. Standard binary search, but on match continue (don't stop)
2. Track last valid position seen
3. Use `lo`/`hi` carefully for left vs right boundary

**Recognition clue:** `first occurrence`, `leftmost`, `boundary`
**Complexity:** `O(log n)` time

---

## Sorting

### Merge Sort (Divide & Conquer)
> **When to use:** Sort linked list, count inversions, reverse pairs.

**Steps:**
1. Split in half recursively
2. Merge two sorted halves
3. Count during merge for inversions

**Recognition clue:** `inversions`, `sort linked list`, `stable sort`
**Complexity:** `O(n log n)` time · `O(n)` space

---

### QuickSelect (Partition)
> **When to use:** Kth largest/smallest in unsorted array.

**Steps:**
1. Partition around pivot (like one step of quicksort)
2. Recurse only on the side containing kth element

**Recognition clue:** `kth largest`, `kth smallest`
**Complexity:** `O(n)` avg · `O(n²)` worst

---

### Counting / Bucket Sort
> **When to use:** Sort by frequency, limited value range, maximum gap.

**Steps:**
1. Create buckets indexed by value or frequency
2. Place elements in buckets
3. Read out in order

**Recognition clue:** `frequency sort`, `limited range`
**Complexity:** `O(n)` time · `O(k)` space

---

### Custom Comparator Sort
> **When to use:** Sort by custom rule (intervals, task scheduler).

**Steps:**
1. Define comparison function
2. Use sort with custom lambda
3. Apply greedy logic after sorting

**Recognition clue:** `sort by`, `order by rule`
**Complexity:** `O(n log n)` time

---

## Recursion & Backtracking

### Generate All Subsets
> **When to use:** Subsets, power set, combination sum.

**Steps:**
1. At each element: branch include vs exclude
2. Recurse with remaining elements
3. Add to result at each node (subsets) or at leaves (combinations)

**Recognition clue:** `all subsets`, `power set`, `combinations`
**Complexity:** `O(2^n)` time

---

### Generate Permutations
> **When to use:** All permutations, next permutation.

**Steps:**
1. At each position, try placing each unused element
2. Swap element in, recurse, swap back (backtrack)

**Recognition clue:** `permutations`, `arrangements`, `all orderings`
**Complexity:** `O(n! * n)` time

---

### Constraint-Based Pruning
> **When to use:** N-Queens, Sudoku solver, palindrome partitioning.

**Steps:**
1. At each choice point, check constraint before recursing
2. If invalid, skip (prune the branch)
3. If at leaf and all constraints met, record solution

**Recognition clue:** `valid placement`, `constraint`, `N-Queens`
**Complexity:** Pruned exponential

---

### Partition / Split String
> **When to use:** Palindrome partitioning, word break.

**Steps:**
1. At each index, try all possible splits
2. Check validity of left part
3. Recurse on right part

**Recognition clue:** `partition string`, `split into valid parts`
**Complexity:** `O(2^n)` worst case

---

## Trees — Traversal

### DFS Preorder (Root First)
> **When to use:** Clone tree, serialize, path problems, construct tree.

**Steps:**
1. Visit root → recurse left → recurse right
2. Process node before its children

**Recognition clue:** `serialize`, `copy`, `root-first`, `construct`
**Complexity:** `O(n)` time

---

### DFS Inorder (Left → Root → Right)
> **When to use:** BST validation, kth smallest, sorted output from BST.

**Steps:**
1. Recurse left → visit root → recurse right
2. Inorder of BST gives sorted sequence

**Recognition clue:** `BST sorted`, `kth smallest`, `validate BST`
**Complexity:** `O(n)` time

---

### DFS Postorder (Children First)
> **When to use:** Delete tree, compute subtree values (diameter, path sum).

**Steps:**
1. Recurse left → recurse right → visit root
2. Subtree results available before parent is processed

**Recognition clue:** `height`, `diameter`, `delete`, `bottom-up`
**Complexity:** `O(n)` time

---

### BFS Level Order
> **When to use:** Level-by-level traversal, right side view, zigzag.

**Steps:**
1. Queue starts with root
2. Dequeue node, enqueue children
3. Process all nodes of one level before moving to next

**Recognition clue:** `level order`, `depth`, `by layer`, `right side view`
**Complexity:** `O(n)` time

---

### Return Value Up the Tree
> **When to use:** Diameter, max path sum, balanced check.

**Steps:**
1. Each call returns a value representing its subtree
2. Parent combines children's return values
3. Update global answer along the way

**Recognition clue:** `diameter`, `max path through node`, `global max`
**Complexity:** `O(n)` time

---

## BST

### BST Property Traversal
> **When to use:** Validate BST, find kth smallest, find successor.

**Steps:**
1. Use min/max bounds: every node must satisfy bounds
2. Pass `(minVal, maxVal)` down recursion
3. Inorder gives sorted order — count to kth

**Recognition clue:** `validate BST`, `kth in BST`
**Complexity:** `O(n)` time

---

### BST Search / Insert / Delete
> **When to use:** Design BST, trim BST, find floor/ceiling.

**Steps:**
1. Compare target with current node
2. Go left if smaller, right if larger
3. On delete, replace with inorder successor

**Recognition clue:** `BST insert`, `delete`, `find`, `trim`
**Complexity:** `O(h) = O(log n)` average

---

### Augmented BST / Ordered Set
> **When to use:** Calendar problems, range queries, rank queries.

**Steps:**
1. Use `TreeMap` / `SortedList` as BST proxy
2. `floorKey()`, `ceilingKey()` for range queries
3. Insert and check overlap

**Recognition clue:** `calendar`, `no overlap`, `range query`
**Complexity:** `O(log n)` per operation

---

## Tries

### Trie Insert & Search
> **When to use:** Autocomplete, spell check, prefix search.

**Steps:**
1. Each node has children map + `isEnd` flag
2. Insert: follow/create nodes per character
3. Search: follow nodes, check `isEnd` at end

**Recognition clue:** `prefix`, `autocomplete`, `starts with`
**Complexity:** `O(L)` per operation (L = word length)

---

### Trie + DFS for Word Search
> **When to use:** Word Search II, add-and-search words.

**Steps:**
1. Build trie from word list
2. DFS on grid, navigate trie simultaneously
3. Mark visited cells; when `isEnd`, record word

**Recognition clue:** `word search`, `find words in grid`
**Complexity:** `O(M * N * 4^L)` time

---

### XOR Trie (Maximize XOR)
> **When to use:** Maximum XOR of two numbers.

**Steps:**
1. Insert numbers bit by bit (MSB first) into trie
2. For each number, greedily go to opposite bit to maximize XOR

**Recognition clue:** `maximum XOR`, `bitwise maximize`
**Complexity:** `O(n * 32)` time

---

## Heaps

### Top-K with Min-Heap
> **When to use:** Top k frequent elements, k closest points, kth largest.

**Steps:**
1. Maintain min-heap of size k
2. If heap size > k, pop the smallest
3. Remaining heap = top k largest elements

**Recognition clue:** `top k`, `k closest`, `kth largest`
**Complexity:** `O(n log k)` time

---

### Two Heaps (Median)
> **When to use:** Find median from data stream, sliding window median.

**Steps:**
1. Max-heap for lower half, min-heap for upper half
2. Balance sizes so difference ≤ 1
3. Median = top of larger heap or avg of both tops

**Recognition clue:** `running median`, `data stream`, `median`
**Complexity:** `O(log n)` insert · `O(1)` median query

---

### Heap for Scheduling / Greedy
> **When to use:** Task scheduler, single-threaded CPU, meeting rooms.

**Steps:**
1. Push `(priority, task)` into heap
2. Poll minimum/maximum at each time step
3. Re-add with updated time/count if not done

**Recognition clue:** `schedule`, `earliest deadline`, `CPU tasks`
**Complexity:** `O(n log n)` time

---

## Intervals

### Merge Overlapping Intervals
> **When to use:** Merge intervals, insert interval.

**Steps:**
1. Sort by start time
2. If `current.start <= last.end` → merge (extend end)
3. Else append new interval

**Recognition clue:** `merge`, `overlapping intervals`
**Complexity:** `O(n log n)` time

---

### Greedy Interval Selection
> **When to use:** Non-overlapping intervals (minimum removals), activity selection.

**Steps:**
1. Sort by end time
2. Greedily pick interval with earliest end
3. Skip any interval that overlaps last picked

**Recognition clue:** `minimum removal`, `max non-overlapping`
**Complexity:** `O(n log n)` time

---

### Sweep Line / Event Points
> **When to use:** Meeting rooms II, skyline problem, minimum intervals.

**Steps:**
1. Create events: `+1` at start, `-1` at end
2. Sort events by time (break ties: end before start)
3. Scan and track current active count

**Recognition clue:** `concurrent`, `overlap count`, `skyline`
**Complexity:** `O(n log n)` time

---

## Greedy

### Sort and Greedily Pick
> **When to use:** Jump game, candy, gas station, meeting rooms.

**Steps:**
1. Sort or process in a specific order
2. At each step make the locally optimal choice
3. Prove greedy works via exchange argument

**Recognition clue:** `minimum steps`, `minimum cost`, `feasibility`
**Complexity:** `O(n log n)` time

---

### Greedy with Priority Queue
> **When to use:** Hire K workers, task scheduler, Huffman coding.

**Steps:**
1. Sort candidates
2. Maintain heap for best current choice
3. Pop best, compute, re-insert if reusable

**Recognition clue:** `minimum cost with constraint`, `hire k`
**Complexity:** `O(n log n)` time

---

### Two-Pointer Greedy
> **When to use:** Trapping water, container with most water.

**Steps:**
1. Start from both ends
2. Move pointer on the side with smaller height
3. Accumulate answer as you move inward

**Recognition clue:** `maximize area`, `maximize water`
**Complexity:** `O(n)` time

---

## Graph — DFS

### DFS Flood Fill / Island Counting
> **When to use:** Number of islands, surrounded regions, pacific atlantic.

**Steps:**
1. Iterate all cells; on target cell, DFS to mark entire region
2. Mark visited to avoid re-visit
3. Count DFS calls = number of components

**Recognition clue:** `islands`, `connected regions`, `flood fill`
**Complexity:** `O(V + E)` time

---

### DFS Cycle Detection
> **When to use:** Course schedule, find eventual safe states.

**Steps:**
1. Track visited: `0 = unvisited`, `1 = in-stack`, `2 = done`
2. If you reach a node in-stack → cycle found
3. Mark done after all neighbors processed

**Recognition clue:** `cycle in graph`, `safe states`, `prerequisite`
**Complexity:** `O(V + E)` time

---

### DFS Path Finding
> **When to use:** All paths source to target, clone graph.

**Steps:**
1. Maintain current path in recursion
2. On reaching target, save a copy of path
3. Backtrack: remove last node from path

**Recognition clue:** `all paths`, `enumerate paths`
**Complexity:** `O(2^V * V)` time

---

## Graph — BFS

### Multi-Source BFS
> **When to use:** Rotting oranges, 01-matrix (distance to nearest 0).

**Steps:**
1. Enqueue all sources simultaneously at level 0
2. BFS outward — distance fills like spreading water
3. Level at which cell is first reached = shortest distance

**Recognition clue:** `nearest`, `distance from multiple sources`
**Complexity:** `O(V + E)` time

---

### BFS on Implicit Graph
> **When to use:** Open the lock, word ladder, sliding puzzle.

**Steps:**
1. State = node, one move = one edge
2. Enqueue initial state, use visited set
3. Each BFS level = one move; return level when goal found

**Recognition clue:** `minimum moves`, `transformations`, `word ladder`
**Complexity:** `O(V + E)` time

---

### BFS with Constraints (State BFS)
> **When to use:** Shortest path with k obstacle removals, bus routes.

**Steps:**
1. State includes position AND remaining resource (e.g., k removals)
2. Visited = `(position, resource)` pair
3. Standard BFS on expanded state space

**Recognition clue:** `shortest path with k removals`, `constrained BFS`
**Complexity:** `O(V * k)` time

---

## Topological Sort

### Kahn's Algorithm (BFS Topo Sort)
> **When to use:** Course schedule, task ordering, build order.

**Steps:**
1. Compute in-degree of all nodes
2. Enqueue all nodes with in-degree 0
3. Process: decrement neighbors' in-degree, enqueue when 0

**Recognition clue:** `prerequisite`, `ordering`, `dependencies`
**Complexity:** `O(V + E)` time

---

### DFS-Based Topo Sort
> **When to use:** Dependency ordering, find SCCs.

**Steps:**
1. DFS; after all neighbors processed, push node to stack
2. Stack read in reverse = topological order

**Recognition clue:** `dependency order`, `post-order stack`
**Complexity:** `O(V + E)` time

---

### Cycle Detection via Topo Sort
> **When to use:** Detect if valid ordering exists.

**Steps:**
1. Run Kahn's algorithm
2. If final order has fewer than V nodes → cycle exists

**Recognition clue:** `detect cycle`, `valid schedule possible`
**Complexity:** `O(V + E)` time

---

## Union Find

### Union-Find with Path Compression
> **When to use:** Connected components, number of provinces, accounts merge.

**Steps:**
1. `find(x)`: recursively find root with path compression
2. `union(x, y)`: merge smaller rank into larger (union by rank)
3. Count components by counting unique roots

**Recognition clue:** `connected components`, `merge groups`
**Complexity:** `O(α(n)) ≈ O(1)` per operation

---

### Union-Find for Cycle Detection
> **When to use:** Redundant connection, cycle in undirected graph.

**Steps:**
1. For each edge `(u, v)`: find roots of u and v
2. If same root → adding this edge creates a cycle
3. Else union them

**Recognition clue:** `redundant edge`, `cycle in undirected graph`
**Complexity:** `O(E * α(n))` time

---

## Shortest Path

### Dijkstra's Algorithm
> **When to use:** Shortest path with non-negative weights.

**Steps:**
1. Min-heap of `(dist, node)`
2. Relax neighbors: if `dist + w < known` → update heap
3. Skip if already processed with shorter distance

**Recognition clue:** `shortest path`, `non-negative weights`
**Complexity:** `O((V + E) log V)` time

---

### Bellman-Ford
> **When to use:** Shortest path with negative weights, cheapest flights within K stops.

**Steps:**
1. Relax all edges `V - 1` times
2. Each relaxation: `dist[v] = min(dist[v], dist[u] + w)`
3. K stops = `K + 1` relaxation rounds

**Recognition clue:** `negative weights`, `at most k stops`
**Complexity:** `O(V * E)` time

---

### 0-1 BFS (Deque)
> **When to use:** 0-1 weighted graph, grid shortest path with binary weights.

**Steps:**
1. Use double-ended queue
2. Weight-0 edge → push front; weight-1 edge → push back
3. Equivalent to Dijkstra but in `O(V + E)`

**Recognition clue:** `0-1 weights`, `binary edge weights`
**Complexity:** `O(V + E)` time

---

### Floyd-Warshall
> **When to use:** All-pairs shortest path, small dense graph.

**Steps:**
1. `dp[i][j]` = shortest path from `i` to `j`
2. For each intermediate node `k`: `dp[i][j] = min(dp[i][j], dp[i][k] + dp[k][j])`

**Recognition clue:** `all pairs`, `small graph (V ≤ 500)`
**Complexity:** `O(V³)` time

---

## Minimum Spanning Tree

### Kruskal's Algorithm (Sort + Union-Find)
> **When to use:** Min cost to connect all points, MST of weighted graph.

**Steps:**
1. Sort all edges by weight
2. For each edge, union nodes if not already connected
3. Stop when `V - 1` edges are added

**Recognition clue:** `min cost connect`, `MST`, `minimum total weight`
**Complexity:** `O(E log E)` time

---

### Prim's Algorithm (Greedy + Min-Heap)
> **When to use:** Dense graph MST (similar approach to Dijkstra).

**Steps:**
1. Start from any node
2. Always expand the cheapest edge crossing the cut
3. Use min-heap of `(weight, neighbor)`

**Recognition clue:** `dense graph`, `MST`, `greedy tree growth`
**Complexity:** `O(E log V)` time

---

## 1-D Dynamic Programming

### Linear DP (Bottom-Up)
> **When to use:** Climbing stairs, house robber, Fibonacci-style problems.

**Steps:**
1. Define `dp[i]` = answer for prefix of size `i`
2. Write recurrence: `dp[i] = f(dp[i-1], dp[i-2], ...)`
3. Initialize base cases, iterate forward

**Recognition clue:** `number of ways`, `min/max cost`, `staircase`
**Complexity:** `O(n)` time · `O(1)` space (with rolling variables)

---

### DP on Choices (Include / Exclude)
> **When to use:** House robber (can't take adjacent), decode ways.

**Steps:**
1. At each index, two choices: take or skip
2. `dp[i] = max(take: val[i] + dp[i-2], skip: dp[i-1])`

**Recognition clue:** `non-adjacent`, `conditional include/exclude`
**Complexity:** `O(n)` time

---

## Knapsack DP

### 0/1 Knapsack
> **When to use:** Partition equal subset sum, target sum, last stone weight II.

**Steps:**
1. `dp[i][w]` = can we achieve weight `w` using first `i` items
2. Iterate items outer, weights inner (backward for 1D)
3. `dp[i][w] = dp[i-1][w] OR dp[i-1][w - item]`

**Recognition clue:** `subset sum`, `partition`, `target weight`
**Complexity:** `O(n * W)` time

---

### Unbounded Knapsack
> **When to use:** Coin change, coin change II, perfect squares.

**Steps:**
1. Same as 0/1 but item can be reused
2. `dp[w] = min(dp[w], dp[w - coin] + 1)`
3. Iterate amounts in increasing order (forward)

**Recognition clue:** `unlimited coins`, `fewest items`, `reuse allowed`
**Complexity:** `O(n * W)` time

---

### Bounded Subset DP
> **When to use:** Target sum with +/- signs (Target Sum problem).

**Steps:**
1. Model as subset sum: `sum(P) - sum(N) = target`
2. Find subset summing to `(total + target) / 2`

**Recognition clue:** `assign + or -`, `count ways to reach target`
**Complexity:** `O(n * sum)` time

---

## Longest Increasing Subsequence

### DP O(n²) LIS
> **When to use:** Basic LIS, number of LIS.

**Steps:**
1. `dp[i]` = LIS ending at index `i`
2. For each `i`, scan all `j < i`: if `arr[j] < arr[i]`, `dp[i] = max(dp[i], dp[j] + 1)`

**Recognition clue:** `longest increasing subsequence`
**Complexity:** `O(n²)` time

---

### Binary Search O(n log n) LIS
> **When to use:** LIS length only (no reconstruction needed).

**Steps:**
1. Maintain `tails` array (patience sorting)
2. For each element, binary search position in `tails`
3. Replace or extend; length of `tails` = LIS length

**Recognition clue:** `LIS length`, `large n`
**Complexity:** `O(n log n)` time

---

### 2D LIS (Envelopes, Nesting)
> **When to use:** Russian doll envelopes, 2D nesting problems.

**Steps:**
1. Sort by first dimension ascending, second dimension descending
2. Run LIS on second dimension only
3. Descending sort prevents double-counting same first dimension

**Recognition clue:** `nested`, `2D increasing`, `envelopes`
**Complexity:** `O(n log n)` time

---

## 2D Grid DP

### Grid Path DP
> **When to use:** Unique paths II, minimum path sum, triangle.

**Steps:**
1. `dp[i][j]` = best value to reach cell `(i, j)`
2. Transition from `dp[i-1][j]` and `dp[i][j-1]`
3. Handle obstacles by setting `dp = infinity` or `0`

**Recognition clue:** `grid paths`, `obstacles`, `min path`
**Complexity:** `O(m * n)` time

---

### Interval DP on 2D
> **When to use:** Burst balloons, stone merge.

**Steps:**
1. `dp[i][j]` = optimal answer for subarray/subgrid `[i..j]`
2. Try all split points `k` in range
3. `dp[i][j] = max/min over dp[i][k] + dp[k+1][j] + cost`

**Recognition clue:** `burst`, `merge`, `split range optimally`
**Complexity:** `O(n³)` time

---

### DP with Multiple Passes
> **When to use:** Cherry pickup, dungeon game (reverse DP).

**Steps:**
1. Sometimes fill DP backward (from target to source)
2. For collecting max twice: run two agents simultaneously in one DP state

**Recognition clue:** `two trips`, `minimum from bottom-right`
**Complexity:** `O(n³)` time

---

## String DP

### LCS (Longest Common Subsequence)
> **When to use:** LCS, edit distance, shortest common supersequence.

**Steps:**
1. `dp[i][j]` = LCS of `s1[0..i]` and `s2[0..j]`
2. If chars match: `dp[i][j] = dp[i-1][j-1] + 1`
3. Else: `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`

**Recognition clue:** `common subsequence`, `edit distance`
**Complexity:** `O(m * n)` time

---

### Palindrome DP
> **When to use:** Longest palindromic subsequence, palindrome partitioning II.

**Steps:**
1. `dp[i][j]` = LPS of `s[i..j]`
2. If `s[i] == s[j]`: `dp[i][j] = dp[i+1][j-1] + 2`
3. Else: `dp[i][j] = max(dp[i+1][j], dp[i][j-1])`

**Recognition clue:** `palindromic subsequence`, `min cuts palindrome`
**Complexity:** `O(n²)` time

---

### Sequence Matching DP
> **When to use:** Wildcard matching, regex, interleaving string.

**Steps:**
1. `dp[i][j]` = can `s1[0..i]` and `pattern[0..j]` match
2. Handle `*` specially: can match zero or more chars
3. Fill table row by row

**Recognition clue:** `wildcard`, `regex`, `interleave`
**Complexity:** `O(m * n)` time

---

### Decoding / Counting Ways
> **When to use:** Decode ways, distinct subsequences.

**Steps:**
1. `dp[i]` = number of ways to decode/match up to index `i`
2. Check validity of 1-char and 2-char substrings
3. Accumulate counts

**Recognition clue:** `number of decodings`, `count ways`
**Complexity:** `O(n)` time

---

## Tree — Graph DP

### Tree DP (Bottom-Up on Tree)
> **When to use:** House robber III, binary tree cameras, diameter.

**Steps:**
1. Each node returns tuple of states (e.g., robbed/not, covered/not)
2. Parent combines children's states
3. Update global answer during DFS

**Recognition clue:** `tree`, `rob/skip`, `camera coverage`, `tree path`
**Complexity:** `O(n)` time

---

### Rerooting Technique
> **When to use:** Sum of distances in tree.

**Steps:**
1. First DFS: compute answers assuming root is the root
2. Second DFS: propagate answer to each child using parent's answer
3. Answer for child = adjust parent answer by ± subtree sizes

**Recognition clue:** `sum of distances`, `all-node answers`
**Complexity:** `O(n)` time

---

## Bitmask DP

### DP over Subsets
> **When to use:** Shortest path visiting all nodes, assign tasks to workers.

**Steps:**
1. `dp[mask]` = min cost/time when `mask` is the set of visited/assigned nodes
2. Transition: try adding each unset bit
3. Final answer: `dp[(1 << n) - 1]`

**Recognition clue:** `visit all`, `assign all`, `TSP-like`
**Complexity:** `O(2^n * n)` time

---

### Profile DP
> **When to use:** Tiling problems, broken profile DP.

**Steps:**
1. State = current column profile (bitmask)
2. Transition = place dominoes fitting the profile

**Recognition clue:** `tiling`, `domino placement`
**Complexity:** `O(2^n * n)` time

---

## Segment Tree & BIT

### Binary Indexed Tree (Fenwick Tree)
> **When to use:** Prefix sum with point updates, count of smaller numbers.

**Steps:**
1. BIT supports `O(log n)` update and prefix query
2. `update(i, delta)`: propagate to parent indices with `i += i & (-i)`
3. `query(i)`: sum from `1..i` with `i -= i & (-i)`

**Recognition clue:** `range sum with updates`, `count inversions`
**Complexity:** `O(log n)` per operation

---

### Segment Tree Range Query
> **When to use:** Range min/max/sum with point or range updates.

**Steps:**
1. Build tree over array (bottom-up)
2. Update: change leaf, propagate up
3. Query: split range into `O(log n)` nodes, combine results

**Recognition clue:** `range query`, `point update`, `range update`
**Complexity:** `O(log n)` per operation

---

## Math & Geometry

### Modular Arithmetic
> **When to use:** Large number computations, combinations mod p.

**Steps:**
1. Use `(a + b) % m`, `(a * b) % m` throughout
2. For division: use modular inverse (Fermat's little theorem)
3. Precompute factorials and inverse factorials

**Recognition clue:** `mod 10^9+7`, `large numbers`, `count mod`
**Complexity:** `O(n)` precompute

---

### Digit DP
> **When to use:** Count numbers with a property up to N.

**Steps:**
1. Process digits left to right
2. State: `(position, tight constraint, accumulated property)`
3. `tight = true` means digits so far match N exactly

**Recognition clue:** `count numbers up to N`, `digit property`
**Complexity:** `O(digits * states)` time

---

### Geometry (Cross Product / Collinearity)
> **When to use:** Max points on a line, valid square, minimum area rectangle.

**Steps:**
1. Cross product to check collinearity or turn direction
2. Sort points; use cross product to filter convex hull
3. For 4-point shapes: check distances and diagonals

**Recognition clue:** `collinear`, `convex hull`, `rectangle`, `max points on line`
**Complexity:** `O(n log n)` time

---

## Quick Pattern Recognition Guide

| Clue in Problem | Pattern to Try |
|---|---|
| Sorted array + pair/target | Two Pointers (opposite ends) |
| Subarray of size k | Fixed Sliding Window |
| Longest/shortest subarray with condition | Dynamic Sliding Window |
| Subarray sum equals k | Prefix Sum + HashMap |
| Find single/missing in 1..n | XOR or Cycle Sort |
| Appears once, rest twice | XOR Cancellation |
| Next greater / smaller element | Monotonic Stack |
| Cycle in linked list | Fast & Slow Pointers |
| Kth largest / smallest | QuickSelect or Min-Heap |
| Top K frequent | Min-Heap of size K |
| Running median | Two Heaps |
| Prefix search / autocomplete | Trie |
| Merge overlapping intervals | Sort by start + greedy |
| Islands / connected regions | DFS Flood Fill |
| Shortest path (unweighted) | BFS |
| Shortest path (weighted, positive) | Dijkstra |
| Shortest path (negative weights) | Bellman-Ford |
| Prerequisites / task order | Topological Sort |
| Connected components / merge groups | Union Find |
| Min cost to connect all | Kruskal / Prim MST |
| Number of ways (small n) | Backtracking |
| Number of ways (overlapping sub-problems) | Dynamic Programming |
| Subset sum / partition | 0/1 Knapsack DP |
| Unlimited reuse / coin change | Unbounded Knapsack DP |
| Longest increasing subsequence | LIS DP / Patience Sort |
| Visit all nodes (TSP-like) | Bitmask DP |
| Range queries with updates | Segment Tree / BIT |
| Count numbers up to N with property | Digit DP |
| Maximum XOR | XOR Trie |