# TCS NQT CODING — HIGH ROI PYQ PATTERN MASTER

## PART 1 — ARRAY + HASHING + TWO POINTER

## C++17 | Last-Day Revision

═══════════════════════════════════════════════════════════════

# HOW TO USE THIS NOTE

For every problem, remember:

QUESTION
↓
WHAT IS CHANGING?
↓
WHAT MUST I REMEMBER?
↓
WHICH PATTERN?
↓
CODE

Do NOT memorize the complete code.

Memorize the:

```
PATTERN
   ↓
INTUITION
   ↓
3–5 CORE LINES
```

If TCS changes the story, identify the same underlying pattern.

═══════════════════════════════════════════════════════════════

# 1. MAXIMUM / MINIMUM IN ARRAY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Given an array, find:

```
Maximum
Minimum
Largest
Smallest
Highest score
Lowest price
Maximum value satisfying condition
```

## INTUITION

I don't need to compare every element with every other element.

I only need to maintain:

```
currentBest
```

For maximum:

```
if current > maximum
    maximum = current
```

For minimum:

```
if current < minimum
    minimum = current
```

## RECOGNITION

If the question says:

```
"largest"
"smallest"
"maximum"
"minimum"
"highest"
"lowest"
```

Think:

```
    ONE PASS
      ↓
  maintain answer
```

## CORE CODE

```
int mx = a[0];

for(int x : a) {
    mx = max(mx, x);
}
```

Minimum:

```
int mn = a[0];

for(int x : a) {
    mn = min(mn, x);
}
```

## IMPORTANT TRICK

Do NOT initialize:

```
int mx = 0;
```

because the array may contain negative numbers.

Safer:

```
int mx = a[0];
```

or

```
int mx = INT_MIN;
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

## SIMILAR PROBLEMS

Maximum
↓
Minimum
↓
Maximum under condition
↓
Minimum under condition
↓
Maximum difference
↓
Best score
↓
Best price

## TCS TRANSFORMATION

"Find the student with highest marks"

is still:

```
MAXIMUM ARRAY
```

"Find the highest salary below 50,000"

is:

```
MAXIMUM + CONDITION
```

═══════════════════════════════════════════════════════════════

# 2. SECOND LARGEST ELEMENT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find:

```
second largest
second highest
runner-up
second maximum
```

## INTUITION

I need to remember TWO things:

```
largest
second largest
```

Whenever a new number arrives:

```
if x > largest

    second = largest
    largest = x

else if x > second
    second = x
```

## CORE IDEA

```
    x
    │
    ▼
x > largest ?
   /     \
 YES      NO
  │        │
  ▼        ▼
```

second=largest   x > second?
largest=x           │
▼
second=x

## CODE

```
int largest = INT_MIN;
int second = INT_MIN;

for(int x : a) {

    if(x > largest) {
        second = largest;
        largest = x;
    }
    else if(x > second && x != largest) {
        second = x;
    }
}
```

## IMPORTANT

If "second largest DISTINCT element" is required:

```
x != largest
```

is important.

Example:

```
5 5 4
```

Second largest distinct = 4

## COMMON MISTAKE

Wrong:

```
sort(a.begin(), a.end());

second = a[n-2];
```

This fails when duplicates exist.

## RECOGNITION

Question asks for:

```
top 2
largest + second largest
runner-up
```

Think:

```
MAINTAIN TWO VARIABLES
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

## SIMILAR

```
second smallest
third largest
kth largest
```

BUT:

For Kth largest, sorting or heap may be easier.

═══════════════════════════════════════════════════════════════

# 3. MOVE ALL ZEROS TO END

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Move:

```
zeros
empty values
invalid elements
```

to the end while preserving the order of other elements.

Example:

```
[0,1,0,3,12]
```

becomes:

```
[1,3,12,0,0]
```

## INTUITION

Don't think:

```
"How do I move every zero?"
```

Think:

```
"Where should the NEXT non-zero element go?"
```

Maintain:

```
pos = next position for useful element
```

## PATTERN

```
useful element
      ↓
   a[pos]
      ↓
   pos++
```

## CODE

```
int pos = 0;

for(int i = 0; i < n; i++) {

    if(a[i] != 0) {
        a[pos] = a[i];
        pos++;
    }
}

while(pos < n) {
    a[pos] = 0;
    pos++;
}
```

## CORE LINES TO REMEMBER

```
if(a[i] != 0)
    a[pos++] = a[i];
```

Then:

```
while(pos < n)
    a[pos++] = 0;
```

## RECOGNITION

Whenever the question says:

```
move X to end
move X to beginning
separate valid/invalid
preserve relative order
```

Think:

```
WRITE POINTER
```

## SIMILAR

```
Move negatives
Move even numbers
Move odd numbers
Partition array
Remove duplicates
Remove unwanted elements
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

═══════════════════════════════════════════════════════════════

# 4. MISSING NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Array contains numbers from:

```
1 to N
```

with one number missing.

Example:

```
1 2 4 5
```

Answer:

```
3
```

## INTUITION 1 — SUM

Expected sum:

```
1 + 2 + ... + N
```

Actual sum:

```
sum(array)
```

Missing:

```
expected - actual
```

## CODE

```
long long expected = 1LL * n * (n + 1) / 2;

long long actual = 0;

for(int x : a)
    actual += x;

cout << expected - actual;
```

## INTUITION 2 — XOR

Very useful trick:

```
x ^ x = 0
x ^ 0 = x
```

Therefore all matching numbers cancel.

```
1 ^ 2 ^ 3 ^ 4
^ array elements
```

leaves missing number.

## CODE

```
int ans = 0;

for(int i = 1; i <= n; i++)
    ans ^= i;

for(int x : a)
    ans ^= x;
```

## WHEN TO USE WHICH?

SUM:

```
Simple
Easy to remember
```

XOR:

```
Avoid overflow
Elegant
```

## RECOGNITION

Words:

```
missing
exactly one absent
numbers 1...N
```

Think:

```
SUM or XOR
```

## SIMILAR

```
Single number
Duplicate number
Odd occurring element
```

═══════════════════════════════════════════════════════════════

# 5. FIND DUPLICATE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find a repeated element.

Example:

```
1 3 4 2 2
```

Answer:

```
2
```

## INTUITION

Ask:

```
"Have I seen this before?"
```

That immediately suggests:

```
SET
```

## CODE

```
unordered_set<int> seen;

for(int x : a) {

    if(seen.count(x)) {
        cout << x;
        break;
    }

    seen.insert(x);
}
```

## CORE PATTERN

```
seen?
  │
YES → duplicate
  │
 NO
  ↓
insert
```

## HASHING VERSION

```
unordered_map<int,int> freq;

for(int x : a)
    freq[x]++;
```

Then:

```
if(freq[x] > 1)
```

x is duplicate.

## RECOGNITION

Words:

```
repeated
duplicate
already appeared
occurs more than once
```

Think:

```
HASH SET / HASH MAP
```

## COMPLEXITY

```
Average:
Time  : O(N)
Space : O(N)
```

## SIMILAR

```
First repeating element
First unique element
Frequency
Duplicate characters
```

═══════════════════════════════════════════════════════════════

# 6. FREQUENCY COUNTING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Count:

```
how many times each number occurs
frequency
repeated values
most frequent
least frequent
```

## INTUITION

Every time I see a value:

```
increase its count
```

That's it.

## CODE

```
unordered_map<int,int> freq;

for(int x : a)
    freq[x]++;
```

## CHARACTER FREQUENCY

```
unordered_map<char,int> freq;

for(char c : s)
    freq[c]++;
```

## ARRAY FREQUENCY — SMALL RANGE

If values are 0–255:

```
int freq[256] = {};

for(char c : s)
    freq[(unsigned char)c]++;
```

## RECOGNITION

Words:

```
count
frequency
occurrences
repeated
appears X times
```

Think:

```
    HASHMAP
```

## MASTER THIS CONNECTION

```
Frequency
   │
   ├── Duplicate
   ├── First unique
   ├── Anagram
   ├── Most frequent
   ├── Least frequent
   └── Pair problems
```

This is one of the highest-ROI patterns.

═══════════════════════════════════════════════════════════════

# 7. TWO SUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find two elements whose:

```
sum = target
```

Example:

```
[2,7,11,15]
target = 9
```

Answer:

```
2 + 7
```

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

## OPTIMAL INTUITION

For current value:

```
x
```

I need:

```
target - x
```

That is the key thought.

Example:

```
target = 9
x = 2
```

Need:

```
9 - 2 = 7
```

Ask:

```
"Have I already seen 7?"
```

Therefore:

```
HASHMAP
```

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

## THE ONE LINE TO REMEMBER

```
int need = target - a[i];
```

That line should trigger:

```
HASHMAP LOOKUP
```

## RECOGNITION

If question says:

```
two numbers
pair
target sum
combination of two
indices of two values
```

Think:

```
TWO SUM
```

Then ask:

```
Is array sorted?
```

If NOT:

```
HashMap
```

If YES:

```
Two pointers can work.
```

## COMPLEXITY

```
Time  : O(N) average
Space : O(N)
```

## SIMILAR

```
Pair with target difference
Pair with target product
Three Sum
Count pairs
```

═══════════════════════════════════════════════════════════════

# 8. MERGE TWO SORTED ARRAYS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Given:

```
sorted A
sorted B
```

merge them into:

```
sorted result
```

## INTUITION

Both arrays are already sorted.

So don't sort again.

Look at:

```
A[i]
B[j]
```

Take the smaller one.

## VISUAL

```
A: 1 4 7
   ↑

B: 2 3 8
   ↑
```

Compare:

```
1 vs 2 → take 1
```

Move A pointer.

## CODE

```
int i = 0, j = 0;

vector<int> ans;

while(i < n && j < m) {

    if(a[i] <= b[j])
        ans.push_back(a[i++]);
    else
        ans.push_back(b[j++]);
}

while(i < n)
    ans.push_back(a[i++]);

while(j < m)
    ans.push_back(b[j++]);
```

## CORE PATTERN

```
TWO SORTED THINGS
      ↓
TWO POINTERS
      ↓
TAKE SMALLER
```

## RECOGNITION

If both inputs are:

```
sorted
```

and question asks:

```
merge
combine
sorted result
```

Think:

```
TWO POINTER
```

## IMPORTANT

Don't do:

```
concatenate
sort
```

That gives:

```
O((N+M) log(N+M))
```

Two-pointer merge:

```
O(N+M)
```

## SIMILAR

```
Merge intervals
Merge linked lists
Intersection of sorted arrays
Union of sorted arrays
```

═══════════════════════════════════════════════════════════════

# 9. SORT 0s, 1s AND 2s

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Array contains only:

```
0
1
2
```

Sort it.

Example:

```
2 0 2 1 1 0
```

→

```
0 0 1 1 2 2
```

## EASY SOLUTION

```
sort(a.begin(), a.end());
```

But know the algorithmic pattern.

## DUTCH NATIONAL FLAG

Maintain:

```
low
mid
high
```

Meaning:

```
[0 ... low-1]   = 0
[low ... mid-1]  = 1
[mid ... high]   = unknown
[high+1 ...]     = 2
```

## RULES

If:

```
a[mid] == 0
```

swap:

```
a[low]
a[mid]
```

then:

```
low++
mid++
```

If:

```
a[mid] == 1
```

just:

```
mid++
```

If:

```
a[mid] == 2
```

swap:

```
a[mid]
a[high]
```

then:

```
high--
```

DO NOT increment mid here.

## CODE

```
int low = 0;
int mid = 0;
int high = n - 1;

while(mid <= high) {

    if(a[mid] == 0) {
        swap(a[low], a[mid]);
        low++;
        mid++;
    }

    else if(a[mid] == 1) {
        mid++;
    }

    else {
        swap(a[mid], a[high]);
        high--;
    }
}
```

## RECOGNITION

Words:

```
only 0,1,2
three categories
sort in one pass
```

Think:

```
DUTCH NATIONAL FLAG
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

═══════════════════════════════════════════════════════════════

# 10. KADANE — MAXIMUM SUBARRAY SUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find:

```
maximum sum of a contiguous subarray
```

Example:

```
[-2,1,-3,4,-1,2,1,-5,4]
```

Answer:

```
6
```

because:

```
4 + (-1) + 2 + 1 = 6
```

## INTUITION

At every element ask:

```
Should I continue the previous subarray?
```

OR

```
Should I start a new subarray here?
```

Therefore:

```
current = max(a[i], current + a[i])
```

## CODE

```
long long current = a[0];
long long best = a[0];

for(int i = 1; i < n; i++) {

    current = max((long long)a[i],
                  current + a[i]);

    best = max(best, current);
}
```

## CORE LINE

```
current = max(a[i], current + a[i]);
```

This is Kadane.

## MENTAL STORY

Previous subarray is useful?

```
YES → extend
```

Not useful?

```
NO → start fresh
```

## RECOGNITION

Words:

```
maximum contiguous sum
largest subarray sum
best continuous segment
```

Think:

```
KADANE
```

## IMPORTANT

"Subarray" means:

```
CONTIGUOUS
```

"Subsequence" means:

```
NOT NECESSARILY CONTIGUOUS
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

## SIMILAR

```
Maximum product subarray
Maximum sum segment
Best continuous profit
```

═══════════════════════════════════════════════════════════════

# 11. REVERSE ARRAY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Reverse:

```
array
string
sequence
```

## INTUITION

Swap:

```
first ↔ last
second ↔ second-last
```

Use:

```
left
right
```

## CODE

```
int l = 0;
int r = n - 1;

while(l < r) {

    swap(a[l], a[r]);

    l++;
    r--;
}
```

## CORE PATTERN

```
LEFT →→
←← RIGHT
```

When:

```
l >= r
```

stop.

## RECOGNITION

Words:

```
reverse
from both ends
symmetric
opposite positions
```

Think:

```
TWO POINTER
```

## SIMILAR

```
Palindrome
Reverse string
Reverse words
Reverse linked list
```

═══════════════════════════════════════════════════════════════

# 12. PALINDROME — ARRAY / STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Determine whether:

```
forward == backward
```

Example:

```
madam → YES
```

## INTUITION

Compare symmetrical positions:

```
first ↔ last
second ↔ second-last
```

If ANY pair differs:

```
NOT palindrome
```

## CODE

```
int l = 0;
int r = s.size() - 1;

bool ok = true;

while(l < r) {

    if(s[l] != s[r]) {
        ok = false;
        break;
    }

    l++;
    r--;
}
```

## NUMBER PALINDROME

Same idea can be done using digits.

Example:

```
121
```

or:

```
reverse number
```

## RECOGNITION

Words:

```
same forward/backward
reads same both ways
palindrome
```

Think:

```
TWO POINTER
```

## TRICK

Palindrome is NOT a separate complicated algorithm.

It is simply:

```
TWO POINTER + COMPARISON
```

## SIMILAR

```
Palindrome number
Valid palindrome
Symmetric array
Reverse comparison
```

═══════════════════════════════════════════════════════════════

# 13. SEARCH — FIRST OCCURRENCE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find:

```
first index
first occurrence
position of target
```

Example:

```
[5,3,7,3,9]
```

target = 3

answer:

```
1
```

## INTUITION

Scan from left.

The FIRST time target appears:

```
immediately answer.
```

## CODE

```
int index = -1;

for(int i = 0; i < n; i++) {

    if(a[i] == target) {
        index = i;
        break;
    }
}
```

## IMPORTANT TRICK

Do NOT continue after finding the first occurrence.

Use:

```
break;
```

## RECOGNITION

"First occurrence"

does NOT automatically mean binary search.

If array isn't guaranteed sorted:

```
LINEAR SEARCH
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

## SIMILAR

```
Last occurrence
Count occurrences
Find all positions
Search target
```

═══════════════════════════════════════════════════════════════

# 14. BINARY SEARCH

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHEN?

ONLY use ordinary binary search when the search space is:

```
SORTED
```

## INTUITION

Instead of checking every element:

```
Check middle.
```

If target is smaller:

```
go left
```

If target is larger:

```
go right
```

Therefore each step removes HALF the search space.

## CODE

```
int l = 0;
int r = n - 1;

while(l <= r) {

    int mid = l + (r - l) / 2;

    if(a[mid] == target) {
        cout << mid;
        return;
    }

    else if(a[mid] < target) {
        l = mid + 1;
    }

    else {
        r = mid - 1;
    }
}

cout << -1;
```

## CORE DECISION

```
a[mid] < target
      ↓
  go RIGHT

a[mid] > target
      ↓
   go LEFT
```

## RECOGNITION

Question gives:

```
sorted array
find target
search efficiently
```

Think:

```
BINARY SEARCH
```

## COMPLEXITY

```
Time  : O(log N)
Space : O(1)
```

## IMPORTANT

If the array isn't sorted:

```
Don't blindly use binary search.
```

═══════════════════════════════════════════════════════════════

# 15. SORTING + CUSTOM CALCULATION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## RECENT TCS-STYLE PATTERN

Example structure:

Given 4 numbers.

Sort them.

Then calculate:

```
a[0] * a[3] + a[1] * a[2]
```

The story can change.

## INTUITION

The important part isn't the formula.

The pattern is:

```
INPUT
  ↓
SORT
  ↓
INDEX / SELECT
  ↓
CALCULATE
```

## CODE

```
sort(a.begin(), a.end());

long long ans =
    1LL * a[0] * a[3]
    +
    1LL * a[1] * a[2];
```

## RECOGNITION

If question says:

```
arrange numbers
smallest/largest positions
pair extremes
then calculate
```

Think:

```
SORT FIRST
```

## TRICK

Always separate the problem:

```
STEP 1 → arrange
STEP 2 → select
STEP 3 → calculate
```

Don't mix everything into one loop.

## SIMILAR

```
Minimum pair product
Maximum pair product
Extreme pairing
Kth selection
Difference between extremes
```

═══════════════════════════════════════════════════════════════

# 16. SORTING + PAIRS / CUSTOM ORDER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Input consists of pairs:

```
(a,b)
(c,d)
...
```

Sort by:

```
first value
```

and if equal:

```
second value
```

## INTUITION

This is:

```
CUSTOM COMPARATOR
```

## CODE

```
sort(v.begin(), v.end(),
    [](auto &x, auto &y) {

        if(x.first != y.first)
            return x.first < y.first;

        return x.second < y.second;
    });
```

## IF DESCENDING FIRST

```
return x.first > y.first;
```

## RECOGNITION

Words:

```
sort by first
if equal sort by second
priority
custom order
pair sorting
```

Think:

```
CUSTOM SORT
```

## TRICK

Default pair sorting already does:

```
first ascending
then second ascending
```

So:

```
sort(v.begin(), v.end());
```

may be enough.

Don't write a comparator unnecessarily.

## SIMILAR

```
Sort students by marks
Sort employees by salary
Sort pairs
Sort intervals
Sort objects by multiple fields
```

═══════════════════════════════════════════════════════════════

# MASTER CONNECTION MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

The most important thing to remember from Part 1:

ARRAY
│
├── Need largest/smallest
│       ↓
│    ONE PASS
│
├── Need top 2
│       ↓
│    TWO VARIABLES
│
├── Need repeated values
│       ↓
│    HASHMAP / HASHSET
│
├── Need pair with target
│       ↓
│    HASHMAP
│
├── Array already sorted
│       ↓
│    TWO POINTER
│
├── Need reverse
│       ↓
│    TWO POINTER
│
├── Need palindrome
│       ↓
│    TWO POINTER
│
├── Need merge sorted arrays
│       ↓
│    TWO POINTER
│
├── Need move elements
│       ↓
│    WRITE POINTER
│
├── Need missing number
│       ↓
│    SUM / XOR
│
├── Need maximum contiguous sum
│       ↓
│    KADANE
│
├── Need target in sorted array
│       ↓
│    BINARY SEARCH
│
└── Need arrange before calculation
↓
SORT FIRST

═══════════════════════════════════════════════════════════════

# TCS CODING — INSTANT RECOGNITION CHEAT SHEET

QUESTION WORDS
│
▼

"LARGEST / SMALLEST"
↓
ONE-PASS MIN/MAX

"SECOND LARGEST"
↓
TWO VARIABLES

"FREQUENCY / OCCURRENCE"
↓
HASHMAP

"DUPLICATE"
↓
HASHSET / HASHMAP

"TWO NUMBERS + TARGET"
↓
TWO SUM → HASHMAP

"SORTED + MERGE"
↓
TWO POINTER

"REVERSE"
↓
TWO POINTER

"PALINDROME"
↓
TWO POINTER

"MISSING NUMBER"
↓
SUM / XOR

"MAXIMUM CONTIGUOUS SUM"
↓
KADANE

"FIRST OCCURRENCE"
↓
LINEAR SEARCH

"SORTED + SEARCH"
↓
BINARY SEARCH

"MOVE X TO END"
↓
WRITE POINTER

"SORT THEN CALCULATE"
↓
SORT + INDEX

"SORT BY FIRST, THEN SECOND"
↓
CUSTOM COMPARATOR

═══════════════════════════════════════════════════════════════

# THE BIGGEST TCS TRICK

Do NOT ask:

```
"Have I seen this exact question?"
```

Ask:

```
"What operation is the question secretly asking me to perform?"
```

Example:

```
"A shopkeeper has packets with different weights.
 Find two packets whose total weight is X."
```

Don't think:

```
"I haven't seen packets."
```

Think:

```
PACKETS
   ↓
TWO VALUES
   ↓
TARGET SUM
   ↓
TWO SUM
   ↓
HASHMAP
```

Another:

```
"Arrange students according to their marks."
```

Think:

```
SORTING
```

Another:

```
"Find the first position where ID appears."
```

Think:

```
LINEAR SEARCH
```

Another:

```
"Find the longest continuous section..."
```

Think:

```
SUBARRAY / SLIDING WINDOW / KADANE
```

The STORY is irrelevant.

The OPERATION is what matters.

═══════════════════════════════════════════════════════════════

# PART 1 — MINIMUM CODE TEMPLATES TO MEMORIZE

## Traversal

```
for(int i = 0; i < n; i++) {
    // process a[i]
}
```

## Range loop

```
for(int x : a) {
    // process x
}
```

## HashMap

```
unordered_map<int,int> mp;

mp[x]++;
```

## HashSet

```
unordered_set<int> st;

if(st.count(x)) { }

st.insert(x);
```

## Sort

```
sort(a.begin(), a.end());
```

## Two Pointer

```
int l = 0;
int r = n - 1;

while(l < r) {
    // process
    l++;
    r--;
}
```

## Binary Search

```
int l = 0, r = n - 1;

while(l <= r) {

    int mid = l + (r-l)/2;

}
```

## Digit Extraction

```
int digit = n % 10;
n /= 10;
```

## Maximum

```
int mx = a[0];

for(int x : a)
    mx = max(mx, x);
```

## Minimum

```
int mn = a[0];

for(int x : a)
    mn = min(mn, x);
```

## Frequency

```
unordered_map<int,int> freq;

for(int x : a)
    freq[x]++;
```

## Swap

```
swap(a[i], a[j]);
```

═══════════════════════════════════════════════════════════════

# PART 1 — FINAL MEMORY TREE

ARRAY
│
├── MAX/MIN
│      └── One Pass
│
├── SECOND LARGEST
│      └── Two Variables
│
├── FREQUENCY
│      └── HashMap
│
├── DUPLICATE
│      └── HashSet
│
├── TWO SUM
│      └── HashMap
│
├── MOVE ZERO
│      └── Write Pointer
│
├── REVERSE
│      └── Two Pointer
│
├── PALINDROME
│      └── Two Pointer
│
├── MERGE SORTED
│      └── Two Pointer
│
├── 0/1/2 SORT
│      └── Dutch National Flag
│
├── MISSING
│      └── Sum / XOR
│
├── MAX SUBARRAY
│      └── Kadane
│
├── SEARCH
│      ├── Unsorted → Linear
│      └── Sorted → Binary
│
└── SORT + CALCULATE
└── Sort → Select → Calculate

═══════════════════════════════════════════════════════════════

# LAST-DAY RULE

If you can look at a new TCS question and classify it within:

```
    30–60 seconds
```

into one of:

```
Traversal
Hashing
Sorting
Two Pointer
Searching
Sliding Window
Number/Digit
Stack
Tree/Graph
DP
```

then you have already solved a large part of the problem.

The coding is only the second half.

PATTERN RECOGNITION
+
IMPLEMENTATION
+
EDGE CASES
=
TCS CODING SUCCESS
═══════════════════════════════════════════════════════════════
