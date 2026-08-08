# TCS NQT CODING — Q1 MASTER

## HIGH-ROI PYQ / PATTERN REVISION SYSTEM

## PART 2 — PROBLEMS 11–20

## C++17

═══════════════════════════════════════════════════════════════
Q1 MASTER — PART 2
═══════════════════════════════════════════════════════════════

PROBLEMS

```
11. Missing Number
12. Move Zeroes to End
13. Find Duplicate
14. Frequency of Array Elements
15. First Repeating / First Unique
16. Merge Two Sorted Arrays
17. Rotate Array
18. Maximum Subarray Sum — Kadane
19. GCD + LCM
20. Palindrome Number
```

CORE PATTERNS COVERED

```
ARRAY
  │
  ├── Mathematical property
  ├── Two pointer
  ├── Hashing
  ├── Frequency
  ├── Merge
  ├── Rotation
  └── Greedy/state tracking

NUMBER
  │
  ├── GCD
  ├── LCM
  └── Digit processing
```

These are repeatedly represented in TCS-oriented PYQ/problem collections.

═══════════════════════════════════════════════════════════════

# 11. MISSING NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Given N-1 numbers from:

```
1 → N
```

one number is missing.

Example:

```
N = 5

[1, 2, 4, 5]
```

Missing:

```
3
```

───────────────────────────────────────────────────────────────

## WHY HIGH ROI?

"Missing number" is a recurring basic array archetype in TCS PYQ collections.

It is also valuable because one simple mathematical idea produces an O(N) solution.

───────────────────────────────────────────────────────────────

## INTUITION

If all numbers from:

```
1 → N
```

are present:

```
total = N(N+1)/2
```

But one is missing.

Therefore:

```
missing
  =
expected sum
  -
actual sum
```

───────────────────────────────────────────────────────────────

## CORE FORMULA

```
expected = n * (n + 1) / 2

missing = expected - actual
```

───────────────────────────────────────────────────────────────

## CODE

```
long long expected =
    1LL * n * (n + 1) / 2;

long long actual = 0;

for(int x : a)
    actual += x;

cout << expected - actual;
```

───────────────────────────────────────────────────────────────

## TRICK

Use:

```
long long
```

for:

```
n * (n + 1)
```

because multiplication can overflow int.

───────────────────────────────────────────────────────────────

## ALTERNATIVE — XOR

If numbers are:

```
1 → N
```

use:

```
xor all numbers
xor all array elements
```

Everything occurring twice cancels:

```
x ^ x = 0
```

Remaining:

```
missing number
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Question says:

```
one number missing
numbers 1 to N
N-1 elements
```

Think:

```
SUM DIFFERENCE
```

or:

```
XOR
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Missing number
Missing + duplicate
Find absent ID
Find missing roll number
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
COMPLETE RANGE
      ↓
ONE ELEMENT MISSING
      ↓
EXPECTED - ACTUAL
```

═══════════════════════════════════════════════════════════════

# 12. MOVE ZEROES TO END

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
[0,1,0,3,12]
```

Output:

```
[1,3,12,0,0]
```

Requirement:

```
non-zero order must remain unchanged.
```

───────────────────────────────────────────────────────────────

## WHY HIGH ROI?

Move-zeroes is explicitly included in current TCS-oriented problem banks and PYQ collections.

───────────────────────────────────────────────────────────────

## INTUITION

We want:

```
ALL NON-ZERO
      ↓
THEN ALL ZERO
```

But:

```
preserve original order
```

Therefore maintain a:

```
WRITE POSITION
```

───────────────────────────────────────────────────────────────

## TWO-POINTER IDEA

```
j = 0
```

For every:

```
a[i]
```

If non-zero:

```
a[j] = a[i]
j++
```

After processing:

```
fill remaining positions with 0
```

───────────────────────────────────────────────────────────────

## CODE

```
int j = 0;

for(int i = 0; i < n; i++) {

    if(a[i] != 0) {

        a[j] = a[i];

        j++;
    }
}

while(j < n) {

    a[j] = 0;

    j++;
}
```

───────────────────────────────────────────────────────────────

## WHY THIS WORKS

Example:

```
0 1 0 3 12
  ↑
non-zero
```

Write:

```
1
```

Then:

```
3
```

Then:

```
12
```

Result:

```
1 3 12 _ _
```

Fill:

```
0 0
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
move zeros
push zeros to end
shift zeros
preserve order
```

Think:

```
WRITE POINTER
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Move negatives
Move positives
Remove a value
Remove duplicates
Partition array
Move even numbers
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
FILTER + PRESERVE ORDER
         ↓
    WRITE POINTER
```

═══════════════════════════════════════════════════════════════

# 13. FIND DUPLICATE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
[1,3,4,2,2]
```

Duplicate:

```
2
```

───────────────────────────────────────────────────────────────

## INTUITION

Ask:

```
Have I seen this before?
```

This is a HASHING question.

───────────────────────────────────────────────────────────────

## HASHSET

```
unordered_set<int> seen;

for(int x : a) {

    if(seen.count(x)) {

        cout << x;
        return;
    }

    seen.insert(x);
}
```

───────────────────────────────────────────────────────────────

## MASTER IDEA

```
current value
      ↓
already seen?
   /       \
 YES       NO
  ↓         ↓
answer    store
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
duplicate
repeated
occurs again
already present
```

Think:

```
HASHSET
```

───────────────────────────────────────────────────────────────

## IF QUESTION ASKS FREQUENCY

Use:

```
unordered_map<int,int>
```

instead of:

```
unordered_set<int>
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
First duplicate
Repeated element
Duplicate transaction
Duplicate ID
Repeated number
Unique elements
```

A recent 2026 TCS question report also described duplicate transaction detection using sender/receiver/amount identity, which is the same underlying hashing idea.

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
DUPLICATE
   ↓
"HAVE I SEEN IT?"
   ↓
HASHSET
```

═══════════════════════════════════════════════════════════════

# 14. FREQUENCY OF ARRAY ELEMENTS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
[1,2,2,3,1,1]
```

Output:

```
1 → 3
2 → 2
3 → 1
```

───────────────────────────────────────────────────────────────

## INTUITION

Every number needs a counter.

Whenever x appears:

```
freq[x]++
```

───────────────────────────────────────────────────────────────

## CODE

```
unordered_map<int,int> freq;

for(int x : a)
    freq[x]++;
```

───────────────────────────────────────────────────────────────

## IF VALUES ARE SMALL

Could use:

```
int freq[MAX];
```

But HashMap is safer for arbitrary values.

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
frequency
occurrence
count each number
number of times
```

Think:

```
HASHMAP
```

───────────────────────────────────────────────────────────────

## THIS PATTERN CONNECTS TO

```
Frequency
   │
   ├── Duplicate
   ├── First repeating
   ├── First unique
   ├── Majority element
   ├── Most frequent
   ├── Anagram
   └── Common elements
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
COUNT
  ↓
MAP / ARRAY
  ↓
freq[x]++
```

═══════════════════════════════════════════════════════════════

# 15. FIRST REPEATING / FIRST UNIQUE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## IMPORTANT

These look similar but are different.

───────────────────────────────────────────────────────────────

## FIRST REPEATING

Example:

```
[4,5,2,4,2]
```

First element that repeats:

```
4
```

Possible approach:

```
Scan from left.

If already seen:

    answer

Otherwise:

    insert
```

───────────────────────────────────────────────────────────────

## CODE

```
unordered_set<int> seen;

for(int x : a) {

    if(seen.count(x)) {

        cout << x;
        return;
    }

    seen.insert(x);
}
```

───────────────────────────────────────────────────────────────

## FIRST UNIQUE

Example:

```
[4,5,2,4,2,5,7]
```

Frequency:

```
4 → 2
5 → 2
2 → 2
7 → 1
```

Answer:

```
7
```

But if:

```
[7,4,5,4]
```

answer:

```
7
```

───────────────────────────────────────────────────────────────

## INTUITION

"FIRST UNIQUE" means:

```
frequency first
     ↓
second pass
     ↓
first freq == 1
```

───────────────────────────────────────────────────────────────

## CODE

```
unordered_map<int,int> freq;

for(int x : a)
    freq[x]++;

for(int x : a) {

    if(freq[x] == 1) {

        cout << x;
        return;
    }
}
```

───────────────────────────────────────────────────────────────

## HUGE RECOGNITION TRICK

```
FIRST REPEATING

    "Have I seen it?"

         ↓

      HASHSET


FIRST UNIQUE

    "Does it occur once?"

         ↓

   FREQUENCY + 2 PASSES
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
First duplicate
First unique
First repeated character
First non-repeating character
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
         FIRST
           │
   ┌───────┴────────┐
   │                │
REPEATING         UNIQUE
   │                │
seen before      freq == 1
   │                │
 SET            MAP + PASS
```

═══════════════════════════════════════════════════════════════

# 16. MERGE TWO SORTED ARRAYS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY HIGH ROI?

A June 2026 reported TCS NQT slot included a Two Sum variant and a merge-sorted-array type question.

This is an important two-pointer pattern.

───────────────────────────────────────────────────────────────

## PROBLEM

A:

```
[1,3,5]
```

B:

```
[2,4,6]
```

Output:

```
[1,2,3,4,5,6]
```

───────────────────────────────────────────────────────────────

## INTUITION

Both arrays are already sorted.

Use:

```
i → A
j → B
```

Compare:

```
A[i]
B[j]
```

Take the smaller one.

───────────────────────────────────────────────────────────────

## CORE CODE

```
int i = 0;
int j = 0;

vector<int> ans;

while(i < n && j < m) {

    if(a[i] <= b[j]) {

        ans.push_back(a[i]);
        i++;
    }

    else {

        ans.push_back(b[j]);
        j++;
    }
}

while(i < n)
    ans.push_back(a[i++]);

while(j < m)
    ans.push_back(b[j++]);
```

───────────────────────────────────────────────────────────────

## MASTER IDEA

```
TWO SORTED ARRAYS
      ↓
TWO POINTERS
      ↓
TAKE SMALLER
      ↓
MOVE THAT POINTER
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
merge sorted
combine sorted arrays
maintain sorted order
```

Think:

```
TWO POINTER
```

───────────────────────────────────────────────────────────────

## COMPLEXITY

```
O(N + M)
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Merge intervals
Intersection
Union
Two sorted lists
Merge two strings by order
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
SORTED + TWO SEQUENCES
        ↓
    TWO POINTER
```

═══════════════════════════════════════════════════════════════

# 17. ROTATE ARRAY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Rotate:

```
[1,2,3,4,5]
```

right by:

```
2
```

Output:

```
[4,5,1,2,3]
```

───────────────────────────────────────────────────────────────

## FIRST OBSERVATION

If:

```
k > n
```

reduce:

```
k = k % n
```

Example:

```
n = 5
k = 7
```

becomes:

```
k = 2
```

───────────────────────────────────────────────────────────────

## EASY APPROACH

Create another array.

For right rotation:

```
new[(i+k)%n] = a[i]
```

───────────────────────────────────────────────────────────────

## CODE

```
vector<int> ans(n);

k %= n;

for(int i = 0; i < n; i++) {

    ans[(i + k) % n] = a[i];
}
```

───────────────────────────────────────────────────────────────

## IN-PLACE TRICK

For right rotation:

```
reverse entire array
```

then:

```
reverse first k
```

then:

```
reverse remaining n-k
```

Example:

```
1 2 3 4 5
```

Reverse all:

```
5 4 3 2 1
```

Reverse first 2:

```
4 5 3 2 1
```

Reverse remaining:

```
4 5 1 2 3
```

───────────────────────────────────────────────────────────────

## CODE

```
k %= n;

reverse(a.begin(), a.end());

reverse(a.begin(), a.begin() + k);

reverse(a.begin() + k, a.end());
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
rotate
shift
circular shift
move elements by K
```

Think:

```
K % N
```

then:

```
ROTATION
```

───────────────────────────────────────────────────────────────

## TRAPS

```
k > n
k == 0
n == 1
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Rotate left
Rotate right
Circular array
Shift array
```

═══════════════════════════════════════════════════════════════

# 18. MAXIMUM SUBARRAY SUM — KADANE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Find maximum sum of a contiguous subarray.

Example:

```
[-2,1,-3,4,-1,2,1,-5,4]
```

Best:

```
[4,-1,2,1]
```

sum:

```
6
```

───────────────────────────────────────────────────────────────

## WHY HIGH ROI?

Maximum subarray is a recurring TCS array archetype in current TCS-oriented problem collections and is a core linear-time array pattern.

───────────────────────────────────────────────────────────────

## THE KEY QUESTION

At every element:

```
Should I continue the current subarray?
```

OR:

```
Should I start a new subarray here?
```

───────────────────────────────────────────────────────────────

## CORE STATE

```
currentSum

bestSum
```

───────────────────────────────────────────────────────────────

## TRANSITION

```
currentSum =
    max(a[i],
        currentSum + a[i])
```

Then:

```
bestSum =
    max(bestSum,
        currentSum)
```

───────────────────────────────────────────────────────────────

## CODE

```
long long current = a[0];

long long best = a[0];

for(int i = 1; i < n; i++) {

    current =
        max((long long)a[i],
            current + a[i]);

    best =
        max(best, current);
}

cout << best;
```

───────────────────────────────────────────────────────────────

## DEEP INTUITION

If current sum becomes very bad:

```
current + a[i]
```

may be worse than:

```
starting fresh at a[i]
```

Therefore:

```
discard bad prefix
```

───────────────────────────────────────────────────────────────

## MASTER LINE

```
current = max(x, current + x)
```

MEMORIZE.

───────────────────────────────────────────────────────────────

## IMPORTANT EDGE CASE

All numbers negative:

```
[-5,-2,-8]
```

Correct answer:

```
-2
```

NOT:

```
0
```

Therefore:

```
initialize from a[0]
```

NOT:

```
current = 0
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
maximum contiguous sum
maximum subarray
largest sum segment
best continuous segment
```

Think:

```
KADANE
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Minimum subarray
Maximum circular subarray
Maximum product subarray
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
CONTIGUOUS
   +
MAX SUM
   ↓
KADANE
```

═══════════════════════════════════════════════════════════════

# 19. GCD + LCM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Given:

```
a = 12
b = 18
```

GCD:

```
6
```

LCM:

```
36
```

───────────────────────────────────────────────────────────────

## GCD INTUITION

Use:

```
gcd(a,b)
  =
gcd(b, a%b)
```

Repeat until:

```
b == 0
```

───────────────────────────────────────────────────────────────

## CODE

```
int a, b;

while(b != 0) {

    int r = a % b;

    a = b;

    b = r;
}

int gcd = a;
```

───────────────────────────────────────────────────────────────

## LCM

Once GCD is known:

```
LCM =
(a / GCD) * b
```

Prefer this ordering to reduce overflow risk.

───────────────────────────────────────────────────────────────

## CODE

```
long long lcm =
    1LL * (originalA / gcd) * originalB;
```

───────────────────────────────────────────────────────────────

## WHY DIVIDE FIRST?

Instead of:

```
a*b/gcd
```

use:

```
(a/gcd)*b
```

because:

```
a*b
```

could overflow before division.

───────────────────────────────────────────────────────────────

## RECOGNITION

```
HCF
GCD
LCM
common divisor
common multiple
```

Think:

```
EUCLIDEAN ALGORITHM
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Fraction simplification
Ratio reduction
Common denominator
Coprime numbers
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
GCD
 ↓
a % b
 ↓
b % remainder
 ↓
repeat
 ↓
0
 ↓
GCD
```

═══════════════════════════════════════════════════════════════

# 20. PALINDROME NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Check:

```
121
```

Reverse:

```
121
```

Therefore:

```
PALINDROME
```

Example:

```
123
```

reverse:

```
321
```

Therefore:

```
NOT PALINDROME
```

───────────────────────────────────────────────────────────────

## INTUITION

Save original.

Reverse a copy.

Compare:

```
original == reverse
```

───────────────────────────────────────────────────────────────

## CORE DIGIT TEMPLATE

```
digit = n % 10

reverse =
    reverse * 10 + digit

n /= 10
```

───────────────────────────────────────────────────────────────

## CODE

```
int original = n;

long long rev = 0;

while(n > 0) {

    int digit = n % 10;

    rev = rev * 10 + digit;

    n /= 10;
}

if(rev == original)
    cout << "Palindrome";
else
    cout << "Not Palindrome";
```

───────────────────────────────────────────────────────────────

## MOST IMPORTANT LINE

```
rev = rev * 10 + digit;
```

This is the master reverse-number formula.

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
reads same backwards
same from both directions
palindrome number
reverse equals original
```

Think:

```
DIGIT EXTRACTION + REVERSE
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Palindrome string
Reverse number
Reverse string
Symmetric number
```

───────────────────────────────────────────────────────────────

## CONNECTION

PALINDROME STRING:

```
left ↔ right
```

PALINDROME NUMBER:

```
reverse digits
   ↓
compare original
```

Same mathematical idea:

```
FORWARD == BACKWARD
```

═══════════════════════════════════════════════════════════════

# Q1 MASTER CONNECTION — PART 2

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                ARRAY
                  │
    ┌─────────────┼─────────────┐
    │             │             │
  RANGE         SEARCH       ORDER
    │             │             │
    ▼             ▼             ▼
```

Missing         Binary          Rotate
Max/Min         Search           Sort
Second Largest  Closest          Merge
│
▼
Two Pointer

```
                ARRAY
                  │
         ┌────────┴────────┐
         │                 │
       REPEAT             COUNT
         │                 │
      HashSet           HashMap
         │                 │
   Duplicate          Frequency
   First Repeat       First Unique


                ARRAY
                  │
                  ▼
            CONTIGUOUS
                  │
                  ▼
               MAX SUM
                  │
                  ▼
                KADANE


                NUMBER
                  │
      ┌───────────┼────────────┐
      │           │            │
    DIGITS       PRIME        GCD
      │           │            │
  %10 /10       sqrt(n)     Euclidean
      │
 ┌────┼────┐
 │    │    │
Sum Reverse Palindrome
```

═══════════════════════════════════════════════════════════════

# THE 20-PROBLEM Q1 MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PROBLEM                     CORE PATTERN

1. Maximum + Minimum         ONE-PASS TRACKING

2. Binary Search             SORTED SEARCH

3. Closest Element           BINARY SEARCH + NEIGHBOURS

4. Two Sum                   HASHMAP

5. Sort + Formula            SORT + CALCULATE

6. Matrix Trace              DIAGONAL

7. Fibonacci                 RECURRENCE / SERIES

8. Second Largest            TWO EXTREMES

9. Digit Processing          %10 /10

10. Prime                    DIVISIBILITY

11. Missing Number           SUM / XOR

12. Move Zeroes              WRITE POINTER

13. Find Duplicate           HASHSET

14. Frequency                HASHMAP

15. First Repeat / Unique    SET / FREQUENCY

16. Merge Sorted Arrays      TWO POINTER

17. Rotate Array             MODULO + REVERSAL

18. Maximum Subarray         KADANE

19. GCD / LCM                EUCLIDEAN

20. Palindrome Number        DIGIT REVERSE

═══════════════════════════════════════════════════════════════

# MOST IMPORTANT SIMILARITY GROUPS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## GROUP A — HASHING

```
Two Sum
   │
   ├── Find Duplicate
   ├── Frequency
   ├── First Repeating
   ├── First Unique
   └── Pair Difference
```

MASTER QUESTION:

```
"Do I need to remember
 something I've already seen?"
```

If YES:

```
HASHMAP / HASHSET
```

═══════════════════════════════════════════════════════════════

## GROUP B — TWO POINTER

```
Merge Sorted Arrays
   │
   ├── Two Sum sorted
   ├── Move Zeroes
   ├── Remove Duplicates
   └── Partitioning
```

MASTER QUESTION:

```
"Can I process the array
 from two moving positions?"
```

If YES:

```
TWO POINTER
```

═══════════════════════════════════════════════════════════════

## GROUP C — DIGIT PROCESSING

```
Digit Sum
   │
   ├── Reverse
   ├── Palindrome
   ├── Armstrong
   ├── Digit Count
   └── Digit Product
```

MASTER:

```
n % 10
   ↓
process
   ↓
n / 10
```

═══════════════════════════════════════════════════════════════

## GROUP D — SORTING

```
Sort + Formula
   │
   ├── Second Largest
   ├── Merge
   ├── Pair problems
   └── Rank transformation
```

MASTER QUESTION:

```
"Would ordering the data
 make the problem simpler?"
```

If YES:

```
SORT
```

═══════════════════════════════════════════════════════════════

## GROUP E — CONTIGUOUS ARRAY

```
Maximum Subarray
   │
   ├── Minimum Subarray
   ├── Maximum Product
   ├── Sliding Window
   └── Subarray Sum
```

MASTER QUESTION:

```
"Does the question care
 about a continuous segment?"
```

If YES:

```
KADANE / SLIDING WINDOW /
PREFIX SUM
```

depending on the exact condition.

═══════════════════════════════════════════════════════════════

# TCS Q1 STORY → PATTERN TRANSLATOR

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

"One number missing from 1 to N"
↓
MISSING NUMBER

"Move all empty slots/zeros to end"
↓
WRITE POINTER

"Find repeated ID"
↓
HASHSET

"How many times each ID appears?"
↓
HASHMAP

"First ID that occurs once"
↓
FREQUENCY + SECOND PASS

"Combine two already sorted lists"
↓
TWO POINTER

"Shift array by K"
↓
ROTATION

"Highest sum of consecutive elements"
↓
KADANE

"Highest common divisor"
↓
EUCLIDEAN

"Smallest common multiple"
↓
GCD → LCM

"Same backwards"
↓
PALINDROME

"Two numbers add to X"
↓
HASHMAP / TWO POINTER

"Sorted + find value"
↓
BINARY SEARCH

"Sorted + closest value"
↓
BINARY SEARCH + NEIGHBOURS

═══════════════════════════════════════════════════════════════

# Q1 EDGE-CASE CHECKLIST

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MISSING NUMBER

```
N = 1?
Missing = N?
Missing = 1?
```

───────────────────────────────────────────────────────────────

MOVE ZEROES

```
All zero?
No zero?
Zero at beginning?
Zero at end?
```

───────────────────────────────────────────────────────────────

DUPLICATE

```
Duplicate appears twice?
Multiple duplicates?
All values same?
```

───────────────────────────────────────────────────────────────

FREQUENCY

```
Negative values?
Large values?
Preserve order?
```

───────────────────────────────────────────────────────────────

MERGE

```
One array empty?
Different sizes?
Duplicate values?
```

───────────────────────────────────────────────────────────────

ROTATION

```
k > n?
k = 0?
n = 1?
```

───────────────────────────────────────────────────────────────

KADANE

```
All negative?
One element?
All positive?
```

───────────────────────────────────────────────────────────────

GCD

```
One value = 0?
Equal values?
Negative input?
```

───────────────────────────────────────────────────────────────

PALINDROME

```
Single digit?
Ends in zero?
Negative number?
Clarify whether negative sign counts.
```

═══════════════════════════════════════════════════════════════

# Q1 — CORE CODE LINES TO MEMORIZE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## MISSING

```
expected = 1LL*n*(n+1)/2;
missing = expected - actual;
```

## MOVE ZEROES

```
if(a[i] != 0)
    a[j++] = a[i];
```

## DUPLICATE

```
if(seen.count(x))
    // duplicate
```

## FREQUENCY

```
freq[x]++;
```

## MERGE

```
if(a[i] <= b[j])
    take a[i];
else
    take b[j];
```

## ROTATION

```
k %= n;
```

## KADANE

```
current = max(x, current + x);
best = max(best, current);
```

## GCD

```
while(b != 0) {
    int r = a % b;
    a = b;
    b = r;
}
```

## REVERSE NUMBER

```
digit = n % 10;
rev = rev * 10 + digit;
n /= 10;
```

═══════════════════════════════════════════════════════════════

# Q1 FINAL REVISION ORDER — 20 PROBLEMS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

FIRST MASTER THESE:

```
1. Maximum + Minimum
2. Binary Search
3. Closest Element
4. Two Sum
5. Sort + Formula
6. Matrix Trace
7. Fibonacci
8. Second Largest
9. Digit Processing
10. Prime
```

THEN:

```
11. Missing Number
12. Move Zeroes
13. Find Duplicate
14. Frequency
15. First Repeat / First Unique
16. Merge Sorted Arrays
17. Rotate Array
18. Kadane
19. GCD / LCM
20. Palindrome Number
```

═══════════════════════════════════════════════════════════════

# THE REAL REVISION METHOD

DO NOT:

```
Read solution
   ↓
Say "I know this"
   ↓
Move on
```

Instead:

```
Read problem
    ↓
CLOSE NOTES
    ↓
Say PATTERN
    ↓
Explain INTUITION
    ↓
Write CORE LINE
    ↓
Code
    ↓
Test EDGE CASE
    ↓
State COMPLEXITY
```

Example:

```
"Move all zeros to the end."
```

Immediately say:

```
ARRAY
  ↓
PRESERVE ORDER
  ↓
WRITE POINTER
```

Example:

```
"Find first employee whose ID
 occurs exactly once."
```

Immediately say:

```
FREQUENCY
   ↓
HASHMAP
   ↓
SECOND PASS
```

Example:

```
"Find maximum total salary
 from consecutive employees."
```

Immediately say:

```
CONTIGUOUS
   ↓
MAXIMUM SUM
   ↓
KADANE
```

Example:

```
"Combine two sorted lists."
```

Immediately say:

```
SORTED
   +
TWO ARRAYS
   ↓
TWO POINTER
```

═══════════════════════════════════════════════════════════════

# Q1 MASTER BRAIN

```
                     QUESTION
                        │
                        ▼
                 WHAT IS ASKED?
                        │
        ┌───────────────┼────────────────┐
        │               │                │
      EXTREME         SEARCH           PAIR
        │               │                │
    max/min          sorted?          target?
        │               │                │
   one pass       binary search      hashmap
                                        │
                                  sorted → 2 ptr

                        │
                        ▼

                     ARRAY
                        │
   ┌────────────────────┼─────────────────────┐
   │                    │                     │
 REPEAT               ORDER               SEGMENT
   │                    │                     │
Hashing              Sorting               Continuous
   │                    │                     │
```

duplicate             merge                max sum
frequency             rotate                ↓
unique                rank                 KADANE

```
                        │
                        ▼

                     NUMBER
                        │
         ┌──────────────┼──────────────┐
         │              │              │
       DIGITS          PRIME          GCD
         │              │              │
      %10 /10        sqrt check      Euclid
         │
     reverse
     palindrome
```

═══════════════════════════════════════════════════════════════

# END OF Q1 MASTER PART 2

20 HIGH-ROI PROBLEMS COMPLETE.

The important point:

```
20 PROBLEMS
    ↓
~10 CORE PATTERNS

    ARRAY TRAVERSAL
    SORTING
    BINARY SEARCH
    HASHING
    TWO POINTER
    MATRIX
    DIGIT PROCESSING
    NUMBER THEORY
    KADANE
    RECURSION / SERIES
```

NEXT:

```
Q1 MASTER PART 3

STRING + ARRAY TRANSFORMATION
│
├── Reverse String
├── Palindrome String
├── Character Frequency
├── Anagram
├── First Non-Repeating Character
├── Remove Duplicates
├── Vowels / Consonants
├── Reverse Words
├── Leader Elements
└── Equilibrium / Prefix Sum
```

Then:

```
FINAL Q1 MASTER REVISION SHEET
```

before moving to:

```
Q2 HIGH-ROI
│
├── Postfix
├── Sliding Window
├── Stack
├── Heap
├── Prefix Sum
├── Tree/BST
├── Graph
└── DP
```

═══════════════════════════════════════════════════════════════
