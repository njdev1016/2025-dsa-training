# DSA Training Plan - Challenge-Focused (3 Weeks)

**Goal:** Master the fundamentals needed to solve all 10 challenges in `2025-hs-oct-challenge/`
**Source:** `./gkg-code-interview-patterns/` (Grokking the Coding Interview)
**Time Commitment:** 3 weeks, 5 hours/day (105 hours total)

---

## Challenge Analysis & Prerequisites

### Easy Challenges (Solve First):
- **Part 03 (Game Begins):** String manipulation, Hash Sets
- **Part 10 (Good Ending):** Character counting, Hash Maps
- **Part 02 (White Noise):** Modulo arithmetic, Array traversal

### Medium Challenges:
- **Part 01 (Wrong Return):** Frequency counting, Sorting
- **Part 04 (Kitchen Secret):** 2D grid navigation, Boundary checking
- **Part 06 (Runtime Warp):** Mathematical operations, Distance formulas
- **Part 07 (Phone Call):** Binary conversion, Bit manipulation, Overflow handling
- **Part 08 (Eldritch Horror):** Anagram detection, Hash Maps

### Hard Challenges:
- **Part 05 (Piano Puzzle):** Sliding window algorithm (variable size)
- **Part 09 (You Cannot Escape):** BFS shortest path, Graph traversal

---

## Week 1: Core Data Structures (35 hours)

### Day 1: Arrays & Strings Fundamentals (5 hours)

**Morning - Theory (2 hours):**
- Fixed vs Dynamic arrays
- Array traversal patterns (forward, backward, two-pointer)
- String fundamentals: immutability, common operations
- ASCII values and character manipulation
- Array indexing and bounds checking

**Afternoon - Practice (3 hours):**
**GKG Reference:** `03. Pattern Two Pointers/`
- Pair with Target Sum (easy)
- Remove Duplicates (easy)
- Squaring a Sorted Array (easy)

**Why these problems:**
- Learn array traversal
- Practice index manipulation
- Understand boundary conditions

**Evening Goal:** Be comfortable iterating through arrays and strings

---

### Day 2: Hash Maps & Frequency Counting (5 hours)

**Morning - Theory (2 hours):**
- Hash Map concepts: O(1) lookups, key-value pairs
- Collision handling basics
- When to use hash maps vs arrays
- Frequency counting pattern
- Building frequency maps from arrays/strings

**Afternoon - Practice (3 hours):**
**GKG Reference:** `14. Pattern Top _K_ Elements/`
- Top K Numbers (easy)
- Top K Frequent Numbers (medium)
- Frequency Sort (medium)

**Why these problems:**
- Master frequency counting
- Learn to sort by frequency
- Practice hash map operations

**Challenge Readiness:** After today, you can solve **Part 01 (Wrong Return)**

---

### Day 3: Hash Sets & Character Deduplication (5 hours)

**Morning - Theory (2 hours):**
- Set data structure: uniqueness checking
- Set vs Map: when to use each
- Character/element deduplication patterns
- Set operations: add, contains, remove
- Converting between sets and lists

**Afternoon - Practice (3 hours):**
**GKG Reference:** `02. Pattern Sliding Window/`
- No-repeat Substring (hard) - Focus on using sets for tracking

**Custom Practice:**
- Find all unique characters in a string
- Remove duplicates from an array
- Check if two strings have common characters

**Why these problems:**
- Master uniqueness checking
- Practice set operations
- Understand when sets are better than maps

**Challenge Readiness:** After today, you can solve **Part 03 (Game Begins)**

---

### Day 4: Sorting Algorithms & Custom Comparators (5 hours)

**Morning - Theory (2 hours):**
- Sorting algorithms overview (Quick, Merge, Heap sort)
- Time/space complexity: O(n log n) typical
- Built-in sort functions in your language
- Custom comparators: sorting by multiple criteria
- Sorting tuples/pairs (key-value sorting)
- Stable vs unstable sorts

**Afternoon - Practice (3 hours):**
**GKG Reference:** `14. Pattern Top _K_ Elements/`
- Kth Smallest Number (easy)
- K Closest Points to the Origin (easy)

**Custom Practice:**
- Sort array of integers descending
- Sort by frequency, then by value
- Sort strings by length, then alphabetically

**Why these problems:**
- Master sorting patterns
- Practice custom sort logic
- Combine sorting with other operations

---

### Day 5: Integration Day - Hash Maps + Sorting (5 hours)

**Morning - Review (1 hour):**
- Review frequency counting pattern
- Review sorting with custom logic
- Combining hash maps and sorting

**Practice All Day (4 hours):**
**GKG Reference:** Mix of previous patterns
- Review: Top K Frequent Numbers
- Review: Frequency Sort
- Solve custom problems combining both

**Challenge Day:**
- Solve **Part 01 (Wrong Return)** - Find 4 most common digits
- Solve **Part 03 (Game Begins)** - Find unique letters
- Solve **Part 10 (Good Ending)** - Find unpaired characters

**Evening:** Document your solutions and edge cases handled

---

### Day 6: Mathematical Operations & Modulo Arithmetic (5 hours)

**Morning - Theory (2 hours):**
- Modulo operator: properties and uses
- Handling negative numbers with modulo
- Circular/cyclic calculations (degrees, clock arithmetic)
- Integer overflow considerations
- Rounding functions: floor, ceiling, round
- Common math formulas you need

**Afternoon - Practice (3 hours):**
**GKG Reference:** `13. Pattern Bitwise XOR/`
- Complement of Base 10 Number (medium)

**Custom Practice:**
- Calculate angles normalized to 0-359
- Handle positive and negative rotations
- Sum large arrays with modulo

**Why these problems:**
- Master modulo arithmetic
- Handle circular number systems
- Practice edge cases with negatives

**Challenge Readiness:** After today, you can solve **Part 02 (White Noise)**

---

### Day 7: Week 1 Review & Challenge Day (5 hours)

**Morning - Review (2 hours):**
- Arrays and strings: iteration patterns
- Hash maps: frequency counting
- Hash sets: uniqueness checking
- Sorting: custom comparators
- Math: modulo arithmetic

**Afternoon - Challenges (3 hours):**
- Solve **Part 02 (White Noise)** - Calculate total rotation
- Review all Week 1 challenges (Parts 1, 2, 3, 10)
- Refactor solutions for clarity
- Test edge cases thoroughly

**Week 1 Complete:** 4/10 challenges solved

---

## Week 2: Grids & Sliding Window (35 hours)

### Day 8: 2D Arrays & Matrix Fundamentals (5 hours)

**Morning - Theory (2 hours):**
- 2D array representation: rows and columns
- Row-major vs column-major ordering
- Accessing elements: array[row][col]
- Matrix dimensions: rows x cols
- Common traversal patterns:
  - Row-by-row iteration
  - Column-by-column iteration
  - Accessing neighbors
- Memory layout of 2D arrays

**Afternoon - Practice (3 hours):**
**Custom Practice:**
- Print 2D array row by row
- Print 2D array column by column
- Create a 2D array from input
- Find element at specific position
- Count elements in 2D array

**Why these problems:**
- Understand 2D indexing
- Practice nested loops
- Master row/col access

---

### Day 9: Grid Navigation & Direction Vectors (5 hours)

**Morning - Theory (2 hours):**
- Direction vectors: representing UP, DOWN, LEFT, RIGHT
- 4-directional movement: (row-1,col), (row+1,col), (row,col-1), (row,col+1)
- Boundary validation: staying within grid
- Grid traversal simulation
- Tracking current position
- Handling invalid moves (staying in place)

**Afternoon - Practice (3 hours):**
**Custom Practice:**
- Implement 4-directional movement
- Simulate movement with boundary checking
- Track path of movements
- Count valid vs invalid moves
- Return final position after movements

**Why these problems:**
- Master grid navigation
- Handle boundary conditions
- Simulate movement step-by-step

---

### Day 10: Challenge Day - Grid Navigation (5 hours)

**Morning - Review (1 hour):**
- Review 2D array indexing
- Review direction vectors
- Review boundary validation

**Challenge (4 hours):**
- Solve **Part 04 (Kitchen Secret)** - Navigate 4x4 keypad grid
- Test with multiple examples
- Handle edge cases (invalid moves)
- Optimize and refactor

**Week 2 Progress:** 5/10 challenges solved

---

### Day 11: Sliding Window - Concept & Fixed Size (5 hours)

**Morning - Theory (2 hours):**
- Sliding window technique: what and why
- When to use sliding window (substring/subarray problems)
- Fixed-size window pattern
- Window expansion and contraction
- Tracking window state
- O(n) time complexity benefit

**Afternoon - Practice (3 hours):**
**GKG Reference:** `02. Pattern Sliding Window/`
- Maximum Sum Subarray of Size K (easy)
- Smallest Subarray with a given sum (easy)

**Why these problems:**
- Understand window movement
- Practice maintaining window state
- Learn fixed-size patterns

---

### Day 12: Sliding Window - Variable Size (5 hours)

**Morning - Theory (2 hours):**
- Variable-size window technique
- Expanding window: when to grow
- Contracting window: when to shrink
- Two-pointer approach with windows
- Using hash map/set with sliding window
- Tracking elements in current window

**Afternoon - Practice (3 hours):**
**GKG Reference:** `02. Pattern Sliding Window/`
- Longest Substring with K Distinct Characters (medium)
- Fruits into Baskets (medium)

**Why these problems:**
- Master variable window size
- Practice expand/contract logic
- Use hash maps with windows

---

### Day 13: Sliding Window - Advanced (Minimum Window) (5 hours)

**Morning - Theory (2 hours):**
- Minimum window substring pattern
- Finding shortest window with all required elements
- Using frequency maps with windows
- Validating window completeness
- Optimizing window search

**Afternoon - Practice (3 hours):**
**GKG Reference:** `02. Pattern Sliding Window/`
- Study minimum window substring approach
- Practice with hash map tracking

**Custom Practice:**
- Find shortest substring with all vowels
- Find shortest subarray with sum >= target
- Practice tracking required vs found elements

**Why these problems:**
- Master minimum window pattern
- Prepare for Part 05 challenge
- Handle complex window validation

---

### Day 14: Challenge Day - Sliding Window (5 hours)

**Morning - Review (1 hour):**
- Review variable window technique
- Review minimum window pattern
- Review hash map usage with windows

**Challenge (4 hours):**
- Solve **Part 05 (Piano Puzzle)** - Find shortest substring with all 7 notes
- Test with various inputs
- Handle edge cases (not all notes present)
- Optimize for large inputs

**Week 2 Complete:** 6/10 challenges solved

---

## Week 3: Advanced Topics & Graph Algorithms (35 hours)

### Day 15: Distance Formulas & Mathematical Operations (5 hours)

**Morning - Theory (2 hours):**
- Euclidean distance formula (2D, 3D, 4D, N-D)
- Distance = sqrt((x2-x1)^2 + (y2-y1)^2 + ...)
- Square root calculations
- Rounding functions:
  - floor: round down
  - ceiling: round up (needed for Part 06)
  - round: round to nearest
- Working with floating-point numbers
- Precision considerations

**Afternoon - Practice (3 hours):**
**GKG Reference:** `14. Pattern Top _K_ Elements/`
- K Closest Points to the Origin (easy)

**Custom Practice:**
- Calculate 2D Euclidean distances
- Calculate 3D Euclidean distances
- Calculate 4D Euclidean distances
- Practice ceiling function
- Sum distances between consecutive points

**Challenge Readiness:** After today, you can solve **Part 06 (Runtime Warp)**

---

### Day 16: Number Systems & Binary Conversion (5 hours)

**Morning - Theory (2 hours):**
- Number systems: decimal, binary, hexadecimal
- Binary number system: base-2
- Decimal to binary conversion algorithm
- Binary to decimal conversion
- Bit representation and positions
- 32-bit unsigned integers
- Maximum value: 2^32 - 1 = 4294967295
- Overflow handling: what happens when number > max
- Leading zeros in binary

**Afternoon - Practice (3 hours):**
**GKG Reference:** `13. Pattern Bitwise XOR/`
- Complement of Base 10 Number (medium)

**Custom Practice:**
- Convert decimal to binary (manual implementation)
- Convert binary to decimal
- Handle 32-bit overflow
- Remove leading zeros
- Calculate number of overflows needed

**Challenge Readiness:** After today, you can solve **Part 07 (Phone Call)**

---

### Day 17: Bit Manipulation Basics (5 hours)

**Morning - Theory (2 hours):**
- Bitwise operators: AND, OR, XOR, NOT
- Left shift (<<) and right shift (>>)
- Bit masking techniques
- Checking if bit is set
- Setting and clearing bits
- XOR properties: a XOR a = 0, a XOR 0 = a
- Common bit manipulation tricks

**Afternoon - Practice (3 hours):**
**GKG Reference:** `13. Pattern Bitwise XOR/`
- Single Number (easy)
- Two Single Numbers (medium)

**Why these problems:**
- Understand XOR properties
- Practice bit manipulation
- Learn clever bit tricks

**Challenge Day:**
- Solve **Part 06 (Runtime Warp)** - Calculate 4D Euclidean distances
- Solve **Part 07 (Phone Call)** - Binary conversion with overflow

---

### Day 18: Anagram Detection & String Sorting (5 hours)

**Morning - Theory (2 hours):**
- What is an anagram: same letters, different order
- Anagram detection methods:
  1. Sort both strings and compare
  2. Use frequency map and compare
- Sorting characters in a string
- Using sorted string as hash key
- Finding all anagrams in a dataset
- Grouping anagrams together

**Afternoon - Practice (3 hours):**
**Custom Practice:**
- Check if two words are anagrams
- Group anagrams from a list
- Find words without anagrams
- Use hash maps with sorted strings as keys

**Why these problems:**
- Master anagram detection
- Practice string sorting
- Use hash maps creatively

**Challenge Readiness:** After today, you can solve **Part 08 (Eldritch Horror)**

---

### Day 19: Challenge Day - Anagrams (5 hours)

**Morning - Review (1 hour):**
- Review anagram detection methods
- Review hash map with sorted keys
- Review finding unique elements

**Challenge (4 hours):**
- Solve **Part 08 (Eldritch Horror)** - Find word with no anagram
- Test with various datasets
- Optimize for large word lists
- Handle edge cases

**Week 3 Progress:** 8/10 challenges solved

---

### Day 20: Graph Theory Fundamentals (5 hours)

**Morning - Theory (2.5 hours):**
- Graph representations:
  - Adjacency matrix (2D array)
  - Adjacency list (hash map of lists)
  - Implicit graphs (grids as graphs)
- Graph vs Tree differences
- Directed vs undirected graphs
- Graph terminology:
  - Vertex/Node
  - Edge/Connection
  - Neighbor/Adjacent node
  - Path
  - Cycle
- Grid as implicit graph:
  - Each cell is a node
  - Edges connect adjacent cells
  - Walls are non-existent nodes

**Afternoon - Practice (2.5 hours):**
**Custom Practice:**
- Represent a grid as a graph
- Find neighbors of a cell (4-directional)
- Check if a cell is valid (not wall, in bounds)
- Convert grid coordinates to graph nodes

**Why these problems:**
- Understand graphs conceptually
- Learn grid-to-graph mapping
- Prepare for BFS

---

### Day 21: BFS Algorithm - Theory & Implementation (5 hours)

**Morning - Theory (2.5 hours):**
- BFS (Breadth-First Search) algorithm
- Queue data structure: FIFO (First In, First Out)
- BFS traversal: level-by-level exploration
- Why BFS finds shortest path in unweighted graphs
- BFS template/pseudocode:
  1. Initialize queue with start node
  2. Mark start as visited
  3. While queue not empty:
     - Dequeue current node
     - For each neighbor:
       - If not visited and valid:
         - Mark visited
         - Enqueue neighbor
         - Track parent/path
- Visited tracking: set or boolean array
- Path reconstruction

**Afternoon - Practice (2.5 hours):**
**GKG Reference:** `08. Pattern Tree Breadth First Search/`
- Binary Tree Level Order Traversal (easy)
- Reverse Level Order Traversal (easy)

**Why these problems:**
- Understand BFS mechanics
- Practice queue operations
- Learn level-by-level traversal

---

### Day 22: BFS on Grids - Shortest Path (5 hours)

**Morning - Theory (2 hours):**
- BFS on grid graphs
- 4-directional movement in BFS
- Handling obstacles/walls
- Tracking visited cells (2D boolean array or set)
- Path reconstruction: storing parent/direction
- Output format: sequence of moves (UDLR)
- Multiple shortest paths: any valid answer

**Afternoon - Practice (3 hours):**
**GKG Reference:** `08. Pattern Tree Breadth First Search/`
- Minimum Depth of a Binary Tree (easy) - Understand shortest path concept

**Custom Practice:**
- Implement BFS on a small grid
- Find shortest path from A to B
- Handle walls and boundaries
- Reconstruct path from parent tracking

**Why these problems:**
- Master BFS on grids
- Practice path reconstruction
- Handle complex state tracking

**Challenge Readiness:** After today, you can solve **Part 09 (You Cannot Escape)**

---

### Day 23: Challenge Day - BFS Shortest Path (5 hours)

**Morning - Review (1 hour):**
- Review BFS algorithm
- Review grid traversal
- Review path reconstruction

**Challenge (4 hours):**
- Solve **Part 09 (You Cannot Escape)** - BFS shortest path in mansion
- Test with multiple grid layouts
- Verify shortest path length
- Handle edge cases (no path, already at goal)

**All Challenges Complete:** 10/10 solved

---

### Day 24-25: Competition Preparation (10 hours)

**Day 24: Review & Optimization (5 hours)**
- Review all 10 challenge solutions
- Optimize time complexity where possible
- Refactor for code clarity
- Add comprehensive comments
- Test all edge cases:
  - Empty inputs
  - Single element
  - Maximum constraints
  - Invalid inputs

**Day 25: Speed Practice (5 hours)**
- Re-solve 5 random challenges from scratch
- Time yourself: aim for < 30 minutes each
- Focus on implementation speed
- Practice debugging quickly
- Simulate competition environment

---

### Day 26: Mock Competition (5 hours)

**Mock Competition Setup:**
- Pick 3 random challenges (1 easy, 1 medium, 1 hard)
- Time limit: 90 minutes total
- No looking at previous solutions
- Implement from scratch
- Test thoroughly

**Example Set:**
- Easy: Part 03 or Part 10 (15 min)
- Medium: Part 04 or Part 08 (30 min)
- Hard: Part 05 or Part 09 (45 min)

**After Competition:**
- Review mistakes
- Identify knowledge gaps
- Practice weak areas

---

### Day 27: Final Review & Documentation (5 hours)

**Morning (3 hours):**
- Create solution documentation
- Write approach explanations
- Document time/space complexity
- List edge cases for each problem

**Afternoon (2 hours):**
- Final confidence building
- Quick solve familiar problems
- Mental preparation
- Rest and relax

---

## Pattern-to-Challenge Mapping

### From GKG Patterns to Challenges:

**Pattern 2: Sliding Window**
- Directly needed for: Part 05 (Piano Puzzle)
- Problems: Maximum Sum Subarray, Longest Substring with K Distinct

**Pattern 3: Two Pointers**
- Foundation for: Array manipulation, Part 01
- Problems: Remove Duplicates, Squaring Sorted Array

**Pattern 8: Tree BFS**
- Concept needed for: Part 09 (Grid BFS)
- Problems: Level Order Traversal, Minimum Depth

**Pattern 13: Bitwise XOR**
- Directly needed for: Part 07 (Binary conversion)
- Problems: Complement of Base 10 Number

**Pattern 14: Top K Elements**
- Directly needed for: Part 01 (Most common digits)
- Problems: Top K Frequent Numbers, Frequency Sort

---

## Daily Schedule Template (5 hours/day)

### Morning Session (2-2.5 hours):
- **Hour 1-2:** Theory and Concepts
  - Read explanations
  - Watch videos if available
  - Take notes on key patterns
- **30 min:** Break

### Afternoon Session (2.5-3 hours):
- **Hour 3-4:** Practice Problems
  - Solve GKG reference problems
  - Implement from scratch
  - Test with examples
- **15 min:** Break
- **Hour 5:** Review and Consolidation
  - Review solutions
  - Optimize code
  - Document learnings

---

## Problem-Solving Approach (Use for Every Challenge)

### Step 1: Understand (10 min)
- Read problem carefully 2-3 times
- Identify inputs and outputs
- List constraints and edge cases
- Work through example manually

### Step 2: Plan (10 min)
- Identify the pattern/algorithm needed
- Sketch out approach on paper
- Consider time/space complexity
- Check for edge cases

### Step 3: Implement (20-40 min)
- Write code step by step
- Use meaningful variable names
- Add comments for complex logic
- Handle edge cases

### Step 4: Test (10 min)
- Test with provided examples
- Test edge cases:
  - Empty input
  - Single element
  - Maximum size
  - Invalid input
- Verify output format

### Step 5: Optimize (10 min)
- Review time complexity
- Check for unnecessary operations
- Simplify logic if possible
- Refactor for clarity

---

## Progress Tracking Checklist

### Week 1: Core Data Structures
- [ ] Day 1: Arrays & Strings fundamentals
- [ ] Day 2: Hash Maps & Frequency counting
- [ ] Day 3: Hash Sets & Deduplication
- [ ] Day 4: Sorting & Custom comparators
- [ ] Day 5: Solve Parts 01, 03, 10
- [ ] Day 6: Mathematical operations & Modulo
- [ ] Day 7: Solve Part 02, Review week

**Week 1 Milestones:** 4/10 challenges complete

### Week 2: Grids & Sliding Window
- [ ] Day 8: 2D Arrays & Matrix basics
- [ ] Day 9: Grid navigation & Directions
- [ ] Day 10: Solve Part 04
- [ ] Day 11: Sliding Window - Fixed size
- [ ] Day 12: Sliding Window - Variable size
- [ ] Day 13: Sliding Window - Minimum window
- [ ] Day 14: Solve Part 05

**Week 2 Milestones:** 6/10 challenges complete

### Week 3: Advanced Topics & Graphs
- [ ] Day 15: Distance formulas & Math
- [ ] Day 16: Number systems & Binary
- [ ] Day 17: Solve Parts 06, 07
- [ ] Day 18: Anagram detection
- [ ] Day 19: Solve Part 08
- [ ] Day 20: Graph theory fundamentals
- [ ] Day 21: BFS algorithm & Implementation
- [ ] Day 22: BFS on grids
- [ ] Day 23: Solve Part 09
- [ ] Day 24-25: Competition prep
- [ ] Day 26: Mock competition
- [ ] Day 27: Final review

**Week 3 Milestones:** 10/10 challenges complete

---

## Challenge Difficulty Progression

### Recommended Solving Order:

**Week 1 (Easy):**
1. Part 03 - Game Begins (Day 5)
2. Part 10 - Good Ending (Day 5)
3. Part 01 - Wrong Return (Day 5)
4. Part 02 - White Noise (Day 7)

**Week 2 (Medium):**
5. Part 04 - Kitchen Secret (Day 10)
6. Part 06 - Runtime Warp (Day 17)
7. Part 07 - Phone Call (Day 17)
8. Part 08 - Eldritch Horror (Day 19)

**Week 3 (Hard):**
9. Part 05 - Piano Puzzle (Day 14)
10. Part 09 - You Cannot Escape (Day 23)

---

## Key Success Strategies

### Learning Tips:
1. **Understand before memorizing** - Know why algorithms work
2. **Practice consistently** - 5 hours daily, no skipping
3. **Code from scratch** - Don't just read solutions
4. **Test thoroughly** - Always test edge cases
5. **Review regularly** - Spend 30 min daily reviewing previous concepts

### Debugging Tips:
1. **Print intermediate values** - See what's happening
2. **Test with simple examples** - Start small
3. **Check boundary conditions** - Off-by-one errors common
4. **Verify data types** - Integer overflow, float precision
5. **Read error messages carefully** - They tell you what's wrong

### Time Management:
1. **Don't get stuck** - Max 20 min before seeking help
2. **Start with easy parts** - Build confidence
3. **Leave time for testing** - At least 10 minutes
4. **Practice under time pressure** - Simulate competition
5. **Rest properly** - 8 hours sleep crucial

---

## Resource Summary

### GKG Patterns Used:
- Pattern 2: Sliding Window (Week 2)
- Pattern 3: Two Pointers (Week 1)
- Pattern 8: Tree BFS (Week 3)
- Pattern 13: Bitwise XOR (Week 3)
- Pattern 14: Top K Elements (Week 1)

### Challenge Files:
Location: `./2025-hs-oct-challenge/part##-name/`
- Instructions: `part##-instructions.txt`
- Sample input: Check folder for sample files
- Test your solutions thoroughly before final submission

### Additional Resources:
- Language documentation for your chosen language
- Built-in data structure references (maps, sets, queues)
- Math library documentation (sqrt, ceil, floor)
- Debugging tools in your IDE

---

## After Completion - Competition Day

### Pre-Competition:
- [ ] Get good sleep (8 hours)
- [ ] Eat a proper meal
- [ ] Have water nearby
- [ ] Test your development environment
- [ ] Review key patterns (30 min)

### During Competition:
- [ ] Read all problems first (10 min)
- [ ] Solve easiest first
- [ ] Skip if stuck > 20 min
- [ ] Test before final submission
- [ ] Track time remaining

### Post-Competition:
- [ ] Review your solutions
- [ ] Learn from mistakes
- [ ] Celebrate your achievement

---

**Training Duration:** 21 days (3 weeks)
**Total Hours:** 105 hours (5 hours/day)
**Total Challenges:** 10
**Prerequisite Topics:** 10+ fundamental concepts

**Last Updated:** 2025-11-20
**Challenge Folder:** `./2025-hs-oct-challenge/`
**Reference Folder:** `./gkg-code-interview-patterns/`

---

Good luck with your training! Remember: Master the fundamentals, practice consistently, and test thoroughly. You've got this!
