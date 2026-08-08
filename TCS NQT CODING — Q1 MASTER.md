# TCS NQT CODING — Q1 MASTER

## HIGH-ROI PYQ/PATTERN REVISION SYSTEM

## PART 1 — CORE Q1 PROBLEMS 1–10

## C++17

═══════════════════════════════════════════════════════════════
HOW TO USE THIS NOTE
═══════════════════════════════════════════════════════════════

DO NOT memorize 10 independent solutions.

Learn:

```
QUESTION
   ↓
STRUCTURE
   ↓
PATTERN
   ↓
CORE LINES
   ↓
VARIATIONS
```

The goal is:

```
NEW STORY
   ↓
REMOVE STORY
   ↓
RECOGNIZE OLD PATTERN
   ↓
CODE
```

═══════════════════════════════════════════════════════════════
Q1 PRIORITY MAP
═══════════════════════════════════════════════════════════════

TIER S — MUST MASTER
│
├── 1. Maximum + Minimum
├── 2. Binary Search
├── 3. Closest Element / Closest Value
├── 4. Two Sum
├── 5. Sort + Custom Formula
├── 6. Matrix Trace
└── 7. Fibonacci / Basic Series

TIER A — VERY HIGH ROI
│
├── 8. Second Largest
├── 9. Sum / Count / Process Digits
└── 10. Prime Number

TIER B — COMES NEXT
│
├── Missing Number
├── Duplicate
├── Move Zeroes
├── Frequency
├── Palindrome
└── Anagram

═══════════════════════════════════════════════════════════════

# 1. MAXIMUM AND MINIMUM IN ARRAY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #1?

This is not theoretical.

A July 6, 2026 reported TCS NQT Q1 was:

```
Maximum & Minimum
```

and it was explicitly described as the Easy question.

This is therefore a HIGH-CONFIDENCE Q1 pattern.

───────────────────────────────────────────────────────────────

## PROBLEM

Given an array:

```
[5, 2, 9, 1, 7]
```

find:

```
maximum = 9
minimum = 1
```

───────────────────────────────────────────────────────────────

## INTUITION

Walk through the array once.

Maintain:

```
smallest
largest
```

For every number:

```
if smaller → update minimum
if larger  → update maximum
```

───────────────────────────────────────────────────────────────

## CORE ALGORITHM

```
minVal = first element
maxVal = first element

for every x:

    minVal = min(minVal, x)
    maxVal = max(maxVal, x)
```

───────────────────────────────────────────────────────────────

## CODE

```
int mn = a[0];
int mx = a[0];

for(int x : a) {

    mn = min(mn, x);
    mx = max(mx, x);
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT TRICK

DO NOT initialize:

```
mn = 0
mx = 0
```

because the array may contain:

```
negative numbers
```

Correct:

```
mn = a[0]
mx = a[0]
```

───────────────────────────────────────────────────────────────

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Question says:

```
largest
smallest
maximum
minimum
highest
lowest
```

Think immediately:

```
ONE PASS
```

───────────────────────────────────────────────────────────────

## SIMILAR PROBLEMS

```
Maximum element
Minimum element
Range = max - min
Maximum absolute value
Largest + smallest
Difference between largest and smallest
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
MAX / MIN
   ↓
TRACK EXTREME
   ↓
ONE PASS
```

═══════════════════════════════════════════════════════════════

# 2. BINARY SEARCH

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #2?

Binary-search/closest-value questions were reported in recent July 2026 TCS NQT experiences.

It is also one of the most important "sorted array" recognition patterns.

───────────────────────────────────────────────────────────────

## PROBLEM

Given sorted:

```
[2, 5, 8, 12, 16, 20]
```

find whether:

```
target = 12
```

exists.

───────────────────────────────────────────────────────────────

## INTUITION

Because the array is SORTED:

Don't inspect every element.

Check middle.

```
target == middle
    ↓
   DONE

target < middle
    ↓
   LEFT

target > middle
    ↓
   RIGHT
```

Every step eliminates half the search space.

───────────────────────────────────────────────────────────────

## CORE STRUCTURE

```
low = 0
high = n - 1

while(low <= high):

    mid = low + (high-low)/2

    if a[mid] == target
        found

    else if a[mid] < target
        low = mid + 1

    else
        high = mid - 1
```

───────────────────────────────────────────────────────────────

## CODE

```
int low = 0;
int high = n - 1;

while(low <= high) {

    int mid = low + (high - low) / 2;

    if(a[mid] == target) {
        cout << mid;
        return;
    }

    else if(a[mid] < target) {
        low = mid + 1;
    }

    else {
        high = mid - 1;
    }
}

cout << -1;
```

───────────────────────────────────────────────────────────────

## MOST IMPORTANT RECOGNITION

```
SORTED
   +
SEARCH
   ↓
BINARY SEARCH
```

───────────────────────────────────────────────────────────────

## TRICK

Never write:

```
mid = (low + high) / 2
```

Prefer:

```
mid = low + (high-low)/2
```

because it avoids integer overflow.

───────────────────────────────────────────────────────────────

## SIMILAR PROBLEMS

```
Search target
First occurrence
Last occurrence
Lower bound
Upper bound
Closest element
Count occurrences
Insert position
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
SORTED ARRAY
      ↓
   SEARCH
      ↓
BINARY SEARCH
```

═══════════════════════════════════════════════════════════════

# 3. CLOSEST ELEMENT / CLOSEST VALUE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #3?

Recent July 2026 candidate reports include a binary-search/closest-value style Q1.

This is extremely valuable because it teaches you how TCS modifies a basic pattern.

───────────────────────────────────────────────────────────────

## PROBLEM

Given sorted:

```
[2, 5, 8, 12, 16]
```

target:

```
10
```

closest value:

```
8
or 12
```

Depending on the question's tie rule.

───────────────────────────────────────────────────────────────

## FIRST QUESTION

Ask:

```
Is array sorted?
```

If YES:

```
BINARY SEARCH
```

───────────────────────────────────────────────────────────────

## INTUITION

Find where target would be inserted.

Two candidates matter:

```
element immediately before target
element immediately after target
```

Compare:

```
|candidate - target|
```

Pick smaller.

───────────────────────────────────────────────────────────────

## CORE IDEA

After binary search:

```
left
right
```

represent the insertion boundary.

Check valid candidates.

───────────────────────────────────────────────────────────────

## SIMPLE APPROACH

```
int best = a[0];

for(int x : a) {

    if(abs(x-target) < abs(best-target))
        best = x;
}
```

This is O(N).

For a small TCS constraint, this may be completely acceptable.

───────────────────────────────────────────────────────────────

## IMPORTANT TCS LESSON

Do NOT automatically over-engineer.

First read:

```
constraints
```

If:

```
N <= 1000
```

O(N) may be perfectly fine.

If:

```
N <= 10^6
```

then optimize.

───────────────────────────────────────────────────────────────

## BINARY-SEARCH VERSION

Think:

```
lower_bound(target)
```

Then compare:

```
a[pos]
a[pos-1]
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
sorted
   +
closest
   ↓
BINARY SEARCH + NEIGHBOURS
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Closest number
Floor
Ceiling
Lower bound
Upper bound
Nearest index
```

═══════════════════════════════════════════════════════════════

# 4. TWO SUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #4?

A June 5, 2026 reported TCS NQT question was a "Coin Pair Indices" problem — a Two Sum variant.

This is an excellent example of TCS changing the STORY while retaining the same algorithm.

───────────────────────────────────────────────────────────────

## PROBLEM

Given:

```
[2, 7, 11, 15]
```

target:

```
9
```

find two elements whose sum is:

```
9
```

Answer:

```
2 + 7
```

───────────────────────────────────────────────────────────────

## BRUTE FORCE

Try every pair:

```
i
  j
```

Complexity:

```
O(N²)
```

───────────────────────────────────────────────────────────────

## BETTER INTUITION

For current:

```
x
```

we need:

```
target - x
```

So instead of asking:

```
"Which pair?"
```

ask:

```
"Have I already seen the number I need?"
```

Use:

```
HASHMAP
```

───────────────────────────────────────────────────────────────

## CORE LINE

```
need = target - x
```

Then:

```
if(mp.count(need))
    answer found
```

───────────────────────────────────────────────────────────────

## CODE

```
unordered_map<int,int> mp;

for(int i = 0; i < n; i++) {

    int need = target - a[i];

    if(mp.count(need)) {

        cout << mp[need] << " " << i;
        return;
    }

    mp[a[i]] = i;
}
```

───────────────────────────────────────────────────────────────

## WHY STORE AFTER CHECK?

Suppose:

```
target = 10
current = 5
```

Don't accidentally use the same element twice.

So:

```
CHECK need first
```

then:

```
STORE current
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
pair
  +
target sum
  ↓
TWO SUM
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Two numbers sum X
Two students total X
Two coins total X
Pair with difference K
Pair with target product
Count pairs
```

───────────────────────────────────────────────────────────────

## VARIATION

If array is SORTED:

```
left = 0
right = n-1

if sum < target
    left++

if sum > target
    right--
```

This gives:

```
TWO POINTER
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
PAIR + TARGET
     ↓
HASHMAP
```

SORTED:

```
PAIR + TARGET
     ↓
TWO POINTER
```

═══════════════════════════════════════════════════════════════

# 5. SORT 4 NUMBERS + CUSTOM FORMULA

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #5?

This is an actual reported July 25, 2026 TCS NQT Q1:

```
Take 4 numbers
sort descending
calculate

res = a[0]*a[3] + a[1]*a[2]
```

The candidate reported solving Q1 completely.

This is extremely important because it shows TCS Q1 may be a very simple transformation problem rather than a classic DSA problem.

───────────────────────────────────────────────────────────────

## PROBLEM

Input:

```
4 numbers
```

Example:

```
1 4 2 3
```

Sort descending:

```
4 3 2 1
```

Then:

```
result
=
a[0]*a[3]
+
a[1]*a[2]
```

Therefore:

```
4*1 + 3*2
= 10
```

───────────────────────────────────────────────────────────────

## INTUITION

Don't overthink the story.

Break it into:

```
INPUT
  ↓
SORT
  ↓
APPLY FORMULA
  ↓
OUTPUT
```

───────────────────────────────────────────────────────────────

## CODE

```
sort(a, a+4, greater<int>());

long long ans =
    1LL*a[0]*a[3]
    +
    1LL*a[1]*a[2];
```

───────────────────────────────────────────────────────────────

## MASTER LESSON

Many TCS questions are:

```
BASIC OPERATION
   +
CUSTOM FORMULA
```

Don't search for a complicated DSA pattern when the problem is simply:

```
SORT + CALCULATE
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
arrange
sort
then calculate
based on positions
apply formula
```

Think:

```
SORT → INDEX → CALCULATE
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Sort 3 numbers
Sort descending
Sort ascending
Find product after sorting
Median after sorting
Pair smallest/largest
Difference after sorting
```

───────────────────────────────────────────────────────────────

## TRICK

If multiplication can be large:

```
1LL * a * b
```

Don't rely on:

```
int * int
```

═══════════════════════════════════════════════════════════════

# 6. MATRIX TRACE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #6?

A July 21, 2026 reported TCS NQT Q1 was exactly:

```
Given a square matrix,
find its trace.
```

The reported constraint was:

```
0 < r == c < 10
```

and the input was space-separated integers.

This is direct evidence for matrix traversal as a Q1 pattern.

───────────────────────────────────────────────────────────────

## PROBLEM

Matrix:

```
1 2 3
4 5 6
7 8 9
```

Main diagonal:

```
1
   5
      9
```

Trace:

```
1 + 5 + 9
= 15
```

───────────────────────────────────────────────────────────────

## INTUITION

Main diagonal means:

```
row == column
```

Therefore:

```
a[i][i]
```

───────────────────────────────────────────────────────────────

## CODE

```
int trace = 0;

for(int i = 0; i < n; i++) {

    trace += a[i][i];
}
```

───────────────────────────────────────────────────────────────

## SECONDARY DIAGONAL

If question asks secondary diagonal:

```
a[i][n-1-i]
```

Example:

```
1 2 3
4 5 6
7 8 9
```

secondary:

```
3
   5
      7
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
diagonal
   ↓
i == j
```

Other diagonal:

```
j = n-1-i
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Trace
Diagonal sum
Secondary diagonal
Difference of diagonals
Matrix transpose
Matrix row/column sums
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
MATRIX
  ↓
NESTED LOOP
```

Special diagonal:

```
i == j
   ↓
a[i][i]
```

═══════════════════════════════════════════════════════════════

# 7. FIBONACCI / BASIC SERIES

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY #7?

A July 6, 2026 reported TCS NQT Q1 was:

```
Fibonacci using recursion
```

in another shift.

This demonstrates that TCS can directly test basic recurrence/series logic as Q1.

───────────────────────────────────────────────────────────────

## PROBLEM

Fibonacci:

```
0 1 1 2 3 5 8 13 ...
```

Relationship:

```
F(n)
  =
F(n-1) + F(n-2)
```

───────────────────────────────────────────────────────────────

## RECURSIVE INTUITION

Every Fibonacci number depends on:

```
previous 2 numbers
```

Base:

```
F(0) = 0
F(1) = 1
```

───────────────────────────────────────────────────────────────

## RECURSIVE CODE

```
int fib(int n) {

    if(n <= 1)
        return n;

    return fib(n-1) + fib(n-2);
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT

Naive recursion:

```
O(2^N)
```

So if the question asks for an efficient solution:

```
ITERATIVE
```

───────────────────────────────────────────────────────────────

## ITERATIVE CODE

```
long long a = 0;
long long b = 1;

for(int i = 2; i <= n; i++) {

    long long c = a + b;

    a = b;
    b = c;
}
```

───────────────────────────────────────────────────────────────

## MASTER IDEA

```
SERIES
   ↓
FIND RELATION
   ↓
PREVIOUS TERMS
   ↓
CURRENT TERM
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Fibonacci
Tribonacci
Arithmetic progression
Geometric progression
nth term
recursive series
```

───────────────────────────────────────────────────────────────

## IMPORTANT TCS CONNECTION

A July 6 Shift 2 report also described an arithmetic-progression question involving:

```
(n-2)th term
(n,1)th term
nth term
```

given:

```
a, n, d
```

So knowing the basic series/formula family is useful.

═══════════════════════════════════════════════════════════════

# 8. SECOND LARGEST ELEMENT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY?

Second-largest is a classic TCS array transformation and is explicitly used in broader TCS pattern analyses.

───────────────────────────────────────────────────────────────

## PROBLEM

```
[10, 5, 8, 20, 15]
```

Largest:

```
20
```

Second largest:

```
15
```

───────────────────────────────────────────────────────────────

## WRONG INSTINCT

Sort:

```
O(N log N)
```

Then pick second-last.

It works, but isn't necessary.

───────────────────────────────────────────────────────────────

## BETTER INTUITION

Maintain:

```
largest
secondLargest
```

When x arrives:

```
if x > largest:

    second = largest
    largest = x

else if x > second
     AND x != largest:

    second = x
```

───────────────────────────────────────────────────────────────

## CODE

```
long long largest = LLONG_MIN;
long long second = LLONG_MIN;

for(long long x : a) {

    if(x > largest) {

        second = largest;
        largest = x;
    }

    else if(x > second && x != largest) {

        second = x;
    }
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT

Question may mean:

```
second largest DISTINCT
```

or:

```
second element after sorting
```

Read wording carefully.

Example:

```
[10,10,8]
```

Second largest DISTINCT:

```
8
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
second largest
   ↓
TWO VARIABLES
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Second smallest
Third largest
Largest + second largest
Top two values
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
K-th extreme
   ↓
TRACK EXTREMES
```

For small fixed K:

```
variables
```

For general K:

```
heap
```

═══════════════════════════════════════════════════════════════

# 9. DIGIT PROCESSING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## THIS IS A FAMILY, NOT ONE QUESTION

TCS frequently rotates simple number/digit problems. The broader 2024–26 analysis assigns a substantial share to number theory/digit problems.

Mastering one template gives many problems.

───────────────────────────────────────────────────────────────

## THE MASTER TEMPLATE

Given:

```
n = 12345
```

Extract last digit:

```
digit = n % 10
```

Remove last digit:

```
n = n / 10
```

───────────────────────────────────────────────────────────────

## TEMPLATE

```
while(n > 0) {

    int digit = n % 10;

    // process digit

    n /= 10;
}
```

───────────────────────────────────────────────────────────────

## THIS SOLVES

```
Digit sum
Digit count
Digit product
Reverse number
Palindrome number
Armstrong
Even digit count
Odd digit count
Largest digit
Smallest digit
Digit frequency
```

───────────────────────────────────────────────────────────────

## 9A. SUM OF DIGITS

```
int sum = 0;

while(n > 0) {

    int digit = n % 10;

    sum += digit;

    n /= 10;
}
```

───────────────────────────────────────────────────────────────

## 9B. COUNT DIGITS

```
int count = 0;

while(n > 0) {

    count++;

    n /= 10;
}
```

───────────────────────────────────────────────────────────────

## 9C. PRODUCT OF DIGITS

```
int product = 1;

while(n > 0) {

    int digit = n % 10;

    product *= digit;

    n /= 10;
}
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Question says:

```
digits
each digit
sum of digits
reverse digits
digit count
```

Think:

```
%10
/10
```

───────────────────────────────────────────────────────────────

## MASTER MEMORY

```
    NUMBER
      │
      ▼
   % 10
      │
      ▼
  LAST DIGIT
      │
      ▼
    / 10
      │
      ▼
  REMOVE DIGIT
```

═══════════════════════════════════════════════════════════════

# 10. PRIME NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY?

Prime/number-theory questions appear repeatedly in TCS reports and pattern analyses; a July 2026 slot also reportedly used a sum-of-primes problem.

───────────────────────────────────────────────────────────────

## PROBLEM

Determine whether:

```
17
```

is prime.

A prime number has exactly:

```
2 positive divisors

1
itself
```

───────────────────────────────────────────────────────────────

## WRONG APPROACH

Check:

```
2 → n-1
```

This is:

```
O(N)
```

───────────────────────────────────────────────────────────────

## KEY OBSERVATION

If n has a factor greater than:

```
sqrt(n)
```

there must be a corresponding factor smaller than:

```
sqrt(n)
```

Therefore:

```
only check i*i <= n
```

───────────────────────────────────────────────────────────────

## CODE

```
bool prime = true;

if(n < 2)
    prime = false;

for(int i = 2;
    i * i <= n;
    i++) {

    if(n % i == 0) {

        prime = false;
        break;
    }
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT EDGE CASES

```
0 → not prime
1 → not prime
2 → prime
3 → prime
4 → not prime
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
prime
divisor
divisible
prime numbers up to N
```

Think:

```
DIVISIBILITY
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Count primes
Sum primes
Prime factors
Largest prime
Nearest prime
```

───────────────────────────────────────────────────────────────

## PRIME RANGE

If N is small:

```
check every number
```

If N is large:

```
SIEVE OF ERATOSTHENES
```

This distinction matters.

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
PRIME
  ↓
DIVISORS
  ↓
CHECK UP TO SQRT(N)
```

═══════════════════════════════════════════════════════════════

# Q1 PATTERN CONNECTION MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
            TCS Q1
               │
   ┌───────────┼────────────┐
   │           │            │
  ARRAY       SEARCH       NUMBER
   │           │            │
   │           │            │
```

┌───┼───┐       │       ┌────┼─────┐
│   │   │       │       │    │     │
Max Second Sort  Binary  Digits Prime Series
Min Largest      Search
│           │
│           └── Closest
│
└── Custom Formula

```
               │
               ▼

            MATRIX
               │
               └── Trace


               │
               ▼

             HASH
               │
               └── Two Sum
```

═══════════════════════════════════════════════════════════════

# THE BIGGEST Q1 LESSON

These 10 questions are NOT 10 unrelated problems.

They collapse into:

```
1. ONE-PASS TRACKING
   ├── Max
   ├── Min
   └── Second Largest

2. SORTING
   ├── Sort 4 numbers
   └── Sort + formula

3. BINARY SEARCH
   ├── Search
   └── Closest value

4. HASHING
   └── Two Sum

5. MATRIX
   └── Trace

6. NUMBER PROCESSING
   ├── Digits
   ├── Prime
   └── Series
```

So:

```
   10 QUESTIONS
        ↓
   6 CORE PATTERNS
```

═══════════════════════════════════════════════════════════════

# Q1 INSTANT RECOGNITION TABLE

QUESTION WORDING
│
▼
PATTERN

"largest"
↓
MAX TRACKING

"smallest"
↓
MIN TRACKING

"second largest"
↓
TWO VARIABLES

"sorted + search"
↓
BINARY SEARCH

"closest in sorted array"
↓
BINARY SEARCH + NEIGHBOURS

"two values sum to X"
↓
HASHMAP / TWO POINTER

"sort then calculate"
↓
SORT + FORMULA

"trace"
↓
a[i][i]

"diagonal"
↓
a[i][i]
OR
a[i][n-1-i]

"digits"
↓
%10 /10

"prime"
↓
DIVISIBILITY UP TO SQRT

"series"
↓
RECURRENCE / FORMULA

═══════════════════════════════════════════════════════════════

# Q1 CODING TRAPS

1.

Don't initialize max/min to zero.

Use:

```
a[0]
```

───────────────────────────────────────────────────────────────

2.

Binary search only when the data permits it.

```
SORTED
   ↓
BINARY SEARCH
```

───────────────────────────────────────────────────────────────

3.

Two Sum:

Check complement BEFORE storing current element.

───────────────────────────────────────────────────────────────

4.

Multiplication:

```
1LL * a * b
```

───────────────────────────────────────────────────────────────

5.

Matrix trace:

```
square matrix
```

Main diagonal:

```
a[i][i]
```

───────────────────────────────────────────────────────────────

6.

Prime:

```
0 and 1 are NOT prime.
```

───────────────────────────────────────────────────────────────

7.

Digit extraction:

```
n % 10
    ↓
last digit

n / 10
    ↓
remove last digit
```

───────────────────────────────────────────────────────────────

8.

Fibonacci:

Don't use naive recursion for huge N.

───────────────────────────────────────────────────────────────

9.

Second largest:

Clarify whether "distinct" is required.

───────────────────────────────────────────────────────────────

10.

Custom formula:

Follow the exact ordering requested.

Don't assume ascending if the question says descending.

═══════════════════════════════════════════════════════════════

# Q1 REVISION LOOP

For each problem:

```
STEP 1
Read question only.

    ↓

STEP 2
Say pattern aloud.

    ↓

STEP 3
Explain algorithm in 2–3 sentences.

    ↓

STEP 4
Write core lines WITHOUT LOOKING.

    ↓

STEP 5
Test:

    normal case
    smallest case
    duplicate case
    negative case if applicable
    impossible case

    ↓

STEP 6
State complexity.

    ↓

STEP 7
Ask:

"What other TCS story could use
 this same algorithm?"
```

═══════════════════════════════════════════════════════════════

# Q1 MASTER STORY

```
          TCS QUESTION
                │
                ▼
          REMOVE STORY
                │
                ▼
         IDENTIFY DATA
                │
    ┌───────────┼────────────┐
    ▼           ▼            ▼
  ARRAY       STRING       NUMBER
    │           │            │
    ▼           ▼            ▼
 OPERATION    OPERATION    OPERATION
    │           │            │
    └───────────┼────────────┘
                ▼
             PATTERN
                │
                ▼
             TEMPLATE
                │
                ▼
             EDGE CASE
                │
                ▼
              CODE
                │
                ▼
            TEST CASES
                │
                ▼
             SUBMIT
```

═══════════════════════════════════════════════════════════════

# END PART 1

PROBLEMS MASTERED:

```
1. Maximum + Minimum
2. Binary Search
3. Closest Element
4. Two Sum
5. Sort + Custom Formula
6. Matrix Trace
7. Fibonacci / Series
8. Second Largest
9. Digit Processing
10. Prime
```

NEXT PART:

```
11. Missing Number
12. Find Duplicate
13. Move Zeroes
14. Frequency Counting
15. First Non-Repeating Character
16. Anagram
17. Reverse String
18. Palindrome
19. Maximum Subarray / Kadane
20. GCD + LCM
```

Then we will build the final:

```
Q1 → Q2 transition set
```

using the recent TCS Q2 patterns:
Postfix
Sliding Window
Stack
Heap
Prefix Sum
Tree/BST
Graph
DP

═══════════════════════════════════════════════════════════════
