# TCS NQT TOMORROW

## FINAL HIGH-ROI MASTER

## PART 3 — TCS STORY → ALGORITHM

## EXACT PATTERN VARIATIONS + EXAM SURVIVAL

═══════════════════════════════════════════════════════════════
MOST IMPORTANT IDEA
═══════════════════════════════════════════════════════════════

TCS QUESTION

```
   ↓
```

LONG STORY

```
   ↓
```

REMOVE THE STORY

```
   ↓
```

IDENTIFY THE OPERATION

```
   ↓
```

MATCH PATTERN

```
   ↓
```

WRITE TEMPLATE

```
   ↓
```

TEST EDGE CASES

```
   ↓
```

SUBMIT

Do NOT think:

```
"This is a new TCS problem."
```

Think:

```
"Which known pattern is hiding inside it?"
```

═══════════════════════════════════════════════════════════════

# 1. STORY-BASED ARRAY FORMULA

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## ACTUAL RECENT EXAMPLE

A July 25, 2026 candidate reported Q1 as:

```
Take 4 numbers
sort descending
calculate:

a[0] * a[3] + a[1] * a[2]
```

This looks like a business/story problem.

But underneath:

```
SORT
  +
FIXED FORMULA
```

The candidate reported solving Q1 completely.

───────────────────────────────────────────────────────────────

## RECOGNITION

If question says:

```
rearrange numbers
sort
arrange highest/lowest
then calculate formula
```

Think:

```
SORT → APPLY FORMULA
```

───────────────────────────────────────────────────────────────

## TEMPLATE

```
sort(a.begin(), a.end());

// depending on required order

answer =
    formula(a);
```

───────────────────────────────────────────────────────────────

## TRICK

Don't overcomplicate it with:

```
DP
recursion
graph
hashmap
```

if the entire problem is:

```
SORT
   ↓
FORMULA
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Maximum product
Minimum product
Pairing values
Arrange largest with smallest
Custom arithmetic after sorting
```

═══════════════════════════════════════════════════════════════

# 2. MATRIX TRACE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED TCS QUESTION

On July 21, 2026, a candidate reported:

```
Given a square matrix
find its trace.
```

Input:

```
space-separated integers
```

Reported constraints:

```
0 < r == c < 10
```

The candidate reported this as Q1.

───────────────────────────────────────────────────────────────

## DEFINITION

TRACE:

```
sum of MAIN DIAGONAL
```

For:

```
1 2 3
4 5 6
7 8 9
```

Trace:

```
1 + 5 + 9
= 15
```

───────────────────────────────────────────────────────────────

## CODE

```
int sum = 0;

for(int i = 0; i < n; i++)
    sum += a[i][i];
```

───────────────────────────────────────────────────────────────

## SECONDARY DIAGONAL

```
a[i][n-1-i]
```

───────────────────────────────────────────────────────────────

## MASTER MEMORY

MAIN:

```
i
i
```

SECONDARY:

```
i
n-1-i
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
trace
principal diagonal
main diagonal

    ↓

a[i][i]
```

═══════════════════════════════════════════════════════════════

# 3. CUSTOM MERGE + SORT VARIANT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED EXAMPLE

A July 21 candidate reported Q2 as:

```
Two integer lists

1. Merge alternately
2. Append remaining elements
3. Sort ONLY the even numbers
4. Keep odd numbers in original positions
```

This is extremely useful because it demonstrates a key TCS style:

```
MULTIPLE SIMPLE OPERATIONS
COMBINED INTO ONE STORY
```

The candidate reported both solutions passed public tests but some
private tests failed, illustrating the importance of edge cases.

───────────────────────────────────────────────────────────────

## BREAK IT INTO SUBPROBLEMS

```
    QUESTION
       │
┌──────┼────────┐
▼      ▼        ▼
```

MERGE   FILTER   SORT
│
▼
EVEN
│
▼
PUT BACK IN
ORIGINAL EVEN
POSITIONS

───────────────────────────────────────────────────────────────

## KEY LESSON

Never try to solve the whole story at once.

Break:

```
STEP 1
  ↓
STEP 2
  ↓
STEP 3
  ↓
STEP 4
```

───────────────────────────────────────────────────────────────

## GENERAL PATTERN

```
EXTRACT
   ↓
TRANSFORM
   ↓
SORT
   ↓
REINSERT
```

This pattern appears frequently in story-based coding.

───────────────────────────────────────────────────────────────

## SIMILAR

```
Sort only positive numbers
Sort only even numbers
Sort selected positions
Replace selected elements
Preserve other elements
```

═══════════════════════════════════════════════════════════════

# 4. GREEDY — FIXED PACKAGE / PLAN PROBLEM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED EXAMPLE

A 2026 TCS NQT question shared on LeetCode involved:

```
Gym membership plans

3 months
6 months
9 months
12 months
```

with a priority toward larger plans.

The reported solution category was:

```
GREEDY
```

and the condition included divisibility by 3.

───────────────────────────────────────────────────────────────

## FIRST RECOGNITION

Question says:

```
choose largest possible package
minimum number of packages
maximum value first
denominations/plans
repeat until amount is covered
```

Think:

```
GREEDY
```

BUT:

```
Don't blindly use greedy.
```

First check whether the choices have
a natural optimal ordering.

───────────────────────────────────────────────────────────────

## BASIC TEMPLATE

Suppose:

```
largest denomination first
```

Then:

```
take as many as possible

remaining =
    amount % denomination
```

Continue.

───────────────────────────────────────────────────────────────

## RECOGNITION

```
maximum possible
minimum number
largest first
choose best current option

    ↓

GREEDY CANDIDATE
```

═══════════════════════════════════════════════════════════════

# 5. HASHING — DUPLICATE RECORDS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED EXAMPLE

A 2026 TCS NQT problem shared on LeetCode described:

```
transactions
```

Two transactions are duplicates if:

```
sender same
receiver same
amount same
```

while:

```
timestamp differs
```

The reported concept:

```
HashMap / HashSet.
```

───────────────────────────────────────────────────────────────

## KEY IDEA

Ignore fields that do NOT define duplication.

Build a key from:

```
sender
receiver
amount
```

Then:

```
if key already exists
    duplicate
```

───────────────────────────────────────────────────────────────

## MASTER PATTERN

```
    RECORD
      │
      ▼
RELEVANT FIELDS
      │
      ▼
    KEY
      │
      ▼
   HASHSET
      │
 ┌────┴────┐
 │         │
```

EXISTS     NEW
│         │
DUPLICATE    INSERT

───────────────────────────────────────────────────────────────

## RECOGNITION

```
duplicate records
same attributes
repeated transaction
unique combination
detect duplicates

    ↓

HASHSET / HASHMAP
```

═══════════════════════════════════════════════════════════════

# 6. AP / NUMBER-SEQUENCE STORY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED EXAMPLE

July 6, 2026 Shift 2 reportedly included:

```
Fibonacci using recursion
```

and another medium problem involving:

```
(n-2)th term
(n,1)th term
nth term
```

of an arithmetic progression given:

```
a, n, d
```

Candidate reports are memory-based, but this demonstrates that
basic mathematical/recurrence problems remain relevant.

───────────────────────────────────────────────────────────────

## AP FORMULA

Nth term:

```
a + (n-1)d
```

───────────────────────────────────────────────────────────────

## (n-2)TH TERM

```
a + (n-3)d
```

───────────────────────────────────────────────────────────────

## SUM OF FIRST N TERMS

```
n/2 * [2a + (n-1)d]
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
arithmetic progression
common difference
nth term

    ↓

FORMULA
```

Do NOT use recursion unnecessarily.

═══════════════════════════════════════════════════════════════

# 7. FIBONACCI — RECURSION VARIANT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT REPORTED QUESTION

July 6, 2026 Shift 2 reportedly included:

```
Fibonacci using recursion.
```

───────────────────────────────────────────────────────────────

## RECURSIVE DEFINITION

```
fib(0) = 0
fib(1) = 1

fib(n) =
    fib(n-1)
    +
    fib(n-2)
```

───────────────────────────────────────────────────────────────

## RECURSIVE CODE

```
long long fib(int n) {

    if(n <= 1)
        return n;

    return fib(n-1)
         + fib(n-2);
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT EXAM POINT

If the question explicitly asks:

```
use recursion
```

then recursion may be required by the expected task.

Otherwise:

```
iterative Fibonacci
```

is more efficient.

───────────────────────────────────────────────────────────────

## RECOGNITION

```
previous two terms
Fibonacci
recurrence

    ↓

DP / RECURSION
```

═══════════════════════════════════════════════════════════════

# 8. THE "COMBINATION PROBLEM" PATTERN

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This is perhaps the most important TCS lesson.

A question can combine:

```
ARRAY
  +
SORT
  +
CONDITION
  +
FORMULA
```

Example:

```
sort
  ↓
choose
  ↓
calculate
```

Another:

```
MERGE
  ↓
FILTER
  ↓
SORT SELECTED
  ↓
REINSERT
```

Another:

```
HASH
  ↓
DUPLICATE CHECK
  ↓
COUNT
```

Another:

```
STACK
  ↓
CONDITION
  ↓
REPEATED REMOVAL
```

Therefore:

```
Don't memorize only "questions".
```

Memorize:

```
PATTERN COMBINATIONS.
```

═══════════════════════════════════════════════════════════════

# 9. TCS COMBINATION LIBRARY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## COMBINATION 1

```
ARRAY
  +
SORT
  +
FORMULA
```

Examples:

```
max product
min product
pairing
custom arithmetic
```

───────────────────────────────────────────────────────────────

## COMBINATION 2

```
ARRAY
  +
HASHING
```

Examples:

```
Two Sum
duplicate
frequency
first unique
```

───────────────────────────────────────────────────────────────

## COMBINATION 3

```
ARRAY
  +
TWO POINTER
```

Examples:

```
sorted pair
merge
partition
reverse
```

───────────────────────────────────────────────────────────────

## COMBINATION 4

```
STRING
  +
HASHING
```

Examples:

```
anagram
frequency
unique character
duplicate character
```

───────────────────────────────────────────────────────────────

## COMBINATION 5

```
ARRAY
  +
PREFIX SUM
```

Examples:

```
equilibrium
range sum
subarray sum
```

───────────────────────────────────────────────────────────────

## COMBINATION 6

```
ARRAY
  +
STACK
```

Examples:

```
next greater
next smaller
stock span
repeated removal
```

───────────────────────────────────────────────────────────────

## COMBINATION 7

```
ARRAY
  +
HEAP
```

Examples:

```
K largest
K smallest
top K
```

───────────────────────────────────────────────────────────────

## COMBINATION 8

```
TREE
  +
DFS
```

Examples:

```
height
diameter
path
```

───────────────────────────────────────────────────────────────

## COMBINATION 9

```
BST
  +
INORDER
```

Examples:

```
kth smallest
sorted traversal
rank
```

───────────────────────────────────────────────────────────────

## COMBINATION 10

```
GRID
  +
BFS/DFS
```

Examples:

```
islands
components
shortest path
```

───────────────────────────────────────────────────────────────

## COMBINATION 11

```
CHOICE
  +
OPTIMIZATION
```

Examples:

```
house robber
knapsack
subset selection

    ↓

DP
```

═══════════════════════════════════════════════════════════════

# 10. INPUT HANDLING — THIS CAN KILL A CORRECT SOLUTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Recent candidates have specifically discussed TCS requiring full programs
rather than LeetCode-style function-only submissions. One July 2026
discussion reported that tree questions may give level-order input with
-1 representing NULL; another candidate reported space/comma-separated
integer inputs. Treat the exact statement's input specification as
authoritative.

───────────────────────────────────────────────────────────────

## BEFORE CODING

Read:

```
Is there T?

Is N given?

Is array on next line?

Is input comma-separated?

Are there multiple test cases?

Is string containing spaces?

Is matrix N × N?

Are -1 values special?
```

───────────────────────────────────────────────────────────────

## NEVER ASSUME

Don't blindly write:

```
cin >> n;
```

if the actual input starts with:

```
T
```

Don't blindly use:

```
cin >> s;
```

if the string can contain spaces.

Use:

```
getline
```

when appropriate.

───────────────────────────────────────────────────────────────

## MATRIX

If:

```
N × N
```

then:

```
for i
  for j
    cin >> a[i][j]
```

═══════════════════════════════════════════════════════════════

# 11. PRIVATE TEST CASE SURVIVAL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Recent candidates reported cases where:

```
public tests passed
```

but:

```
private tests failed.
```

This means:

```
SAMPLE PASS
    ≠
CORRECT SOLUTION
```

One July 21 report specifically described both coding solutions passing
public tests but failing some private tests.

───────────────────────────────────────────────────────────────

## ALWAYS TEST

### ARRAY

```
n = 1

all same

already sorted

reverse sorted

negative values

zeros
```

───────────────────────────────────────────────────────────────

### STRING

```
empty-like minimum input

one character

all same

all unique

uppercase/lowercase

spaces
```

───────────────────────────────────────────────────────────────

### STACK

```
empty stack

one element

invalid closing bracket

nested brackets

subtraction/division
```

───────────────────────────────────────────────────────────────

### HEAP

```
K = 1

K = N

duplicate values
```

───────────────────────────────────────────────────────────────

### TREE

```
NULL tree

one node

only left children

only right children
```

───────────────────────────────────────────────────────────────

### GRAPH

```
disconnected

no path

source = destination

boundary cell
```

═══════════════════════════════════════════════════════════════

# 12. IF YOU GET STUCK ON Q2

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DO NOT stare at the story.

Use this:

```
            Q2
             │
             ▼
      WHAT IS CHANGING?
             │
  ┌──────────┼───────────┐
  ▼          ▼           ▼
ORDER       COUNT       RELATION
  │          │           │
 SORT       HASH        STACK
  │          │           │
  ▼          ▼           ▼
SEARCH     DUPLICATE   GREATER/
                       SMALLER


             │
             ▼

      IS IT CONTIGUOUS?
             │
         YES ↓
      WINDOW / PREFIX


             │
             ▼

      IS IT TOP K?
             │
         YES ↓
          HEAP


             │
             ▼

      IS IT TREE?
             │
      ┌──────┴──────┐
      ▼             ▼
     BST           NORMAL
      │             │
   INORDER        DFS/BFS


             │
             ▼

      IS IT "CHOOSE"?
             │
         YES ↓
            DP
```

═══════════════════════════════════════════════════════════════

# 13. THE 25 PATTERN TRIGGERS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. maximum/minimum
   ↓
   ONE PASS

2. second largest
   ↓
   TWO EXTREMES

3. sorted search
   ↓
   BINARY SEARCH

4. pair target
   ↓
   HASHMAP / TWO POINTER

5. duplicate
   ↓
   SET

6. frequency
   ↓
   HASHMAP

7. first unique
   ↓
   FREQUENCY + SECOND PASS

8. reverse
   ↓
   TWO POINTER

9. palindrome
   ↓
   TWO POINTER

10. same letters
    ↓
    ANAGRAM / FREQUENCY

11. exactly K consecutive
    ↓
    FIXED WINDOW

12. longest valid substring
    ↓
    VARIABLE WINDOW

13. subarray sum
    ↓
    WINDOW / PREFIX

14. next greater
    ↓
    MONOTONIC STACK

15. postfix
    ↓
    STACK

16. balanced brackets
    ↓
    STACK

17. top K
    ↓
    HEAP

18. range sum
    ↓
    PREFIX SUM

19. trace
    ↓
    MAIN DIAGONAL

20. greater than everything right
    ↓
    LEADERS

21. tree height
    ↓
    DFS

22. BST kth smallest
    ↓
    INORDER

23. level order
    ↓
    BFS

24. shortest unweighted path
    ↓
    BFS

25. cannot take adjacent
    ↓
    TAKE/SKIP DP

═══════════════════════════════════════════════════════════════

# 14. FINAL 15-MINUTE PATTERN TEST

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Don't code these.

Only identify the pattern.

───────────────────────────────────────────────────────────────

Q1:

"Find the first employee ID that occurs only once."

ANSWER:

```
FREQUENCY + SECOND PASS
```

───────────────────────────────────────────────────────────────

Q2:

"Find the maximum sum of 7 consecutive days."

ANSWER:

```
FIXED SLIDING WINDOW
```

───────────────────────────────────────────────────────────────

Q3:

"Find the first greater temperature to the right."

ANSWER:

```
MONOTONIC STACK
```

───────────────────────────────────────────────────────────────

Q4:

"Evaluate 5 4 2 * +."

ANSWER:

```
POSTFIX STACK
```

───────────────────────────────────────────────────────────────

Q5:

"Find 4 largest values."

ANSWER:

```
MIN HEAP SIZE 4
```

───────────────────────────────────────────────────────────────

Q6:

"Find sum between L and R for many queries."

ANSWER:

```
PREFIX SUM
```

───────────────────────────────────────────────────────────────

Q7:

"Find kth smallest element in BST."

ANSWER:

```
INORDER
```

───────────────────────────────────────────────────────────────

Q8:

"Find number of connected groups in grid."

ANSWER:

```
DFS/BFS
```

───────────────────────────────────────────────────────────────

Q9:

"Find minimum moves in an unweighted grid."

ANSWER:

```
BFS
```

───────────────────────────────────────────────────────────────

Q10:

"Cannot choose two adjacent houses."

ANSWER:

```
TAKE/SKIP DP
```

───────────────────────────────────────────────────────────────

Q11:

"Take four numbers, arrange descending, then apply a formula."

ANSWER:

```
SORT + FORMULA
```

───────────────────────────────────────────────────────────────

Q12:

"Sort only even numbers while odd positions remain fixed."

ANSWER:

```
EXTRACT → SORT → REINSERT
```

───────────────────────────────────────────────────────────────

Q13:

"Transactions are duplicate if three fields match."

ANSWER:

```
HASH KEY
```

───────────────────────────────────────────────────────────────

Q14:

"Find trace of square matrix."

ANSWER:

```
SUM a[i][i]
```

───────────────────────────────────────────────────────────────

Q15:

"Repeatedly remove elements based on their neighbour."

ANSWER:

```
MONOTONIC STACK / STATE
```

═══════════════════════════════════════════════════════════════

# 15. FINAL HIGH-ROI PROBLEM LIST

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Q1 — FIRST PRIORITY

```
1. Maximum + Minimum
2. Second Largest
3. Two Sum
4. Frequency
5. First Unique
6. Missing Number
7. Move Zeroes
8. Binary Search
9. Closest Element
10. Reverse Number
11. Palindrome Number
12. Prime
13. GCD / LCM
14. Fibonacci
15. Matrix Trace
16. Matrix Diagonal
17. Sort + Formula
18. Merge Sorted Arrays
19. Rotate Array
20. Kadane
21. Reverse String
22. Palindrome String
23. Character Frequency
24. Anagram
25. First Non-Repeating
26. Vowels / Consonants
27. Remove Duplicates
28. Reverse Words
29. Leaders
30. Equilibrium / Prefix Sum
```

═══════════════════════════════════════════════════════════════

# Q2 — FIRST PRIORITY

```
1. Postfix Expression
2. Fixed Sliding Window
3. Longest Unique Substring
4. Subarray Sum
5. Next Greater Element
6. Balanced Parentheses
7. K Largest — Min Heap
8. Prefix Sum
9. Monotonic Stack
10. BST Kth Smallest
11. BST Kth Largest
12. Tree Height
13. Level Order
14. BFS / DFS Components
15. Grid Shortest Path
16. House Robber
17. Climbing Stairs
18. 0/1 Knapsack
19. Greedy Package Problem
20. Hash-Key Duplicate Detection
```

═══════════════════════════════════════════════════════════════

# 16. THE ACTUAL ROI HIERARCHY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                TOMORROW
                   │
                   ▼
          ┌─────────────────┐
          │   Q1 SECURITY   │
          └────────┬────────┘
                   │
                   ▼
         ARRAY + STRING
                   │
                   ▼
          HASH / SORT / BASIC
                   │
                   ▼
         MATRIX / NUMBER
                   │
                   ▼
          ┌─────────────────┐
          │   Q2 ATTACK     │
          └────────┬────────┘
                   │
      ┌────────────┼────────────┐
      ▼            ▼            ▼
    STACK        WINDOW        HEAP
      │            │            │
  postfix/NGE    K-window      Top K
      │            │
      └────────────┼────────────┘
                   ▼
                BST/TREE
                   │
                   ▼
              GRAPH/BFS
                   │
                   ▼
                 DP
```

═══════════════════════════════════════════════════════════════

# 17. WHAT NOT TO DO TONIGHT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DO NOT START:

```
❌ Advanced DP
❌ Trie
❌ Segment Tree
❌ Fenwick Tree
❌ Advanced Graph
❌ Complex Backtracking
❌ Advanced String Algorithms
❌ Random LeetCode Hard
❌ 100 unrelated TCS questions
```

Why?

Because your remaining time is better spent converting:

```
KNOWN PATTERNS
    ↓
AUTOMATIC RECOGNITION
    ↓
FAST IMPLEMENTATION
```

═══════════════════════════════════════════════════════════════

# 18. FINAL EXAM ALGORITHM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                    START
                      │
                      ▼
              READ BOTH QUESTIONS
                      │
                      ▼
            IDENTIFY EASIER Q1
                      │
                      ▼
                SOLVE Q1 FIRST
                      │
                      ▼
             TEST EDGE CASES
                      │
                      ▼
                   SUBMIT
                      │
                      ▼
                 MOVE Q2
                      │
                      ▼
           IDENTIFY STRUCTURE
                      │
    ┌─────────────────┼──────────────────┐
    ▼                 ▼                  ▼
  STACK             WINDOW              HEAP
    │                 │                  │
    ▼                 ▼                  ▼
 postfix            fixed K            top K
 NGE                 unique             kth
 bracket             subarray
    │                 │
    └─────────────────┼──────────────────┘
                      ▼
                 TREE / GRAPH
                      │
                      ▼
                     DP
                      │
                      ▼
               IF UNKNOWN:
               SIMPLIFY
                      │
                      ▼
            WRITE CORRECT VERSION
                      │
                      ▼
             OPTIMIZE IF NEEDED
                      │
                      ▼
                   SUBMIT
```

═══════════════════════════════════════════════════════════════

# FINAL MEMORY PALACE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ARRAY

```
max/min        → ONE PASS
pair target    → HASH
sorted pair    → TWO POINTER
sorted search  → BINARY SEARCH
contiguous max → KADANE
range sum      → PREFIX
right property → SUFFIX / RIGHT→LEFT
```

STRING

```
reverse        → TWO POINTER
palindrome     → TWO POINTER
frequency      → HASH
anagram        → FREQUENCY
unique         → FREQUENCY + SECOND PASS
unique window  → SLIDING WINDOW
```

STACK

```
postfix        → STACK
bracket        → STACK
next greater   → MONOTONIC STACK
repeated remove→ MONOTONIC STACK
```

HEAP

```
K largest      → MIN HEAP
K smallest     → MAX HEAP
```

TREE

```
height         → DFS
preorder       → ROOT LEFT RIGHT
inorder        → LEFT ROOT RIGHT
postorder      → LEFT RIGHT ROOT
level          → BFS
```

BST

```
search         → PROPERTY
kth smallest   → INORDER
kth largest    → REVERSE INORDER
```

GRAPH

```
components     → DFS/BFS
islands        → DFS/BFS
shortest       → BFS if unweighted
```

DP

```
ways           → PREVIOUS STATES
adjacent limit → TAKE/SKIP
capacity       → KNAPSACK
```

STORY

```
long story     → IGNORE
identify nouns → STRUCTURE
identify verb  → OPERATION
map pattern    → TEMPLATE
```

═══════════════════════════════════════════════════════════════

# THE ONE SENTENCE FOR TOMORROW

```
"I don't need to know every problem;
 I need to recognize the algorithm hiding
 inside the problem."
```

═══════════════════════════════════════════════════════════════

# DATA CONFIDENCE NOTE

The exact future questions cannot be known from PYQs.

TCS does not publish an official future-question list,
and current 2026 question lists are primarily
candidate-reported / memory-based.

What IS supported by the recent evidence:

```
• 2 coding problems are being reported in the current format.
• Q1 has repeatedly been Easy / Low-Medium.
• Q2 is generally harder.
• Recent shifts have varied considerably.
• Arrays, strings, hashing, stacks, heaps,
  trees/BST, greedy and basic DP all appear
  in the current preparation/question ecosystem.
• Exact question repetition is NOT guaranteed.
• Pattern repetition is the safer preparation strategy.
```

Therefore:

```
DO NOT BET ON ONE EXACT QUESTION.
```

BET ON:

```
PATTERN
   +
VARIANT
   +
IMPLEMENTATION
```

═══════════════════════════════════════════════════════════════
END — FINAL TCS NQT CODING MASTER
═══════════════════════════════════════════════════════════════
