# TCS NQT CODING — Q1 MASTER

## HIGH-ROI PYQ / PATTERN REVISION SYSTEM

## PART 3 — STRING + ARRAY TRANSFORMATION

## PROBLEMS 21–30

## C++17

═══════════════════════════════════════════════════════════════
Q1 MASTER — PART 3
═══════════════════════════════════════════════════════════════

21. Reverse String
22. Palindrome String
23. Character Frequency
24. Anagram
25. First Non-Repeating Character
26. Count Vowels / Consonants
27. Remove Duplicate Characters
28. Reverse Words in String
29. Leaders in Array
30. Prefix Sum / Equilibrium Index

CORE STRING FAMILY

```
    STRING
       │
┌──────┼────────┐
│      │        │
```

REVERSE  COUNT    COMPARE
│      │        │
│      │    ┌───┴────┐
│      │    │        │
PALINDROME FREQ ANAGRAM
│
├── FIRST UNIQUE
└── FIRST REPEATING

CORE ARRAY FAMILY

```
    ARRAY
       │
 ┌─────┴─────┐
 │           │
```

LOCAL       PREFIX
PROPERTY     SUM
│           │
LEADER       EQUILIBRIUM
INDEX

═══════════════════════════════════════════════════════════════

# 21. REVERSE STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"hello"
```

Output:

```
"olleh"
```

───────────────────────────────────────────────────────────────

## WHY HIGH ROI?

String reversal is repeatedly included in current TCS NQT coding banks and string preparation material.

It is also the foundation for:

```
palindrome
reverse words
character manipulation
```

───────────────────────────────────────────────────────────────

## INTUITION

Two ends:

```
left → beginning
right → end
```

Swap:

```
s[left]
   ↕
s[right]
```

Move inward.

───────────────────────────────────────────────────────────────

## CORE CODE

```
int left = 0;
int right = s.size() - 1;

while(left < right) {

    swap(s[left], s[right]);

    left++;
    right--;
}
```

───────────────────────────────────────────────────────────────

## MASTER PATTERN

```
TWO ENDS
   ↓
COMPARE / SWAP
   ↓
MOVE INWARD
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
reverse
backward
opposite order
```

Think:

```
TWO POINTER
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Reverse array
Palindrome
Reverse words
Reverse only vowels
Reverse part of string
```

───────────────────────────────────────────────────────────────

## CONNECTION

Array reverse:

```
[1 2 3 4]
 ↑     ↑
```

String reverse:

```
"ABCD"
 ↑   ↑
```

Same pattern:

```
LEFT ↔ RIGHT
```

═══════════════════════════════════════════════════════════════

# 22. PALINDROME STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

```
"madam"
```

reads:

```
m a d a m
```

from both directions.

Therefore:

```
PALINDROME
```

───────────────────────────────────────────────────────────────

## INTUITION

Compare:

```
first ↔ last
second ↔ second-last
...
```

If any mismatch:

```
NOT PALINDROME
```

───────────────────────────────────────────────────────────────

## CODE

```
int left = 0;
int right = s.size() - 1;

bool ok = true;

while(left < right) {

    if(s[left] != s[right]) {

        ok = false;
        break;
    }

    left++;
    right--;
}
```

───────────────────────────────────────────────────────────────

## MASTER LINE

```
if(s[left] != s[right])
    NOT PALINDROME
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
same forward and backward
reads same from both ends
palindrome
```

Think:

```
TWO POINTER
```

───────────────────────────────────────────────────────────────

## IMPORTANT VARIATION

Question may say:

```
ignore case
```

Then:

```
convert to lowercase
```

Question may say:

```
ignore spaces
```

Then:

```
skip spaces
```

Question may say:

```
ignore special characters
```

Then:

```
compare only valid characters
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Palindrome number
Reverse string
Symmetric string
Valid palindrome
```

═══════════════════════════════════════════════════════════════

# 23. CHARACTER FREQUENCY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"banana"
```

Frequency:

```
b → 1
a → 3
n → 2
```

───────────────────────────────────────────────────────────────

## WHY HIGH ROI?

Character-frequency problems are repeatedly listed as core TCS string problems.

───────────────────────────────────────────────────────────────

## INTUITION

Every character gets a counter.

For:

```
c
```

do:

```
freq[c]++
```

───────────────────────────────────────────────────────────────

## SIMPLE ASCII VERSION

```
int freq[256] = {0};

for(char c : s)
    freq[c]++;
```

───────────────────────────────────────────────────────────────

## THEN

```
for(int i = 0; i < 256; i++) {

    if(freq[i] > 0)
        cout << char(i)
             << " "
             << freq[i];
}
```

───────────────────────────────────────────────────────────────

## HASHMAP VERSION

```
unordered_map<char,int> freq;

for(char c : s)
    freq[c]++;
```

───────────────────────────────────────────────────────────────

## WHICH ONE?

ASCII / lowercase English:

```
frequency array
```

Arbitrary characters:

```
hashmap
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
frequency
occurrence
count each character
how many times
```

Think:

```
HASHMAP / FREQUENCY ARRAY
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Character frequency
Most frequent character
Least frequent character
First unique character
First repeated character
Anagram
```

═══════════════════════════════════════════════════════════════

# 24. ANAGRAM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Are:

```
"listen"
```

and:

```
"silent"
```

anagrams?

YES.

They contain:

```
same characters
same frequencies
```

───────────────────────────────────────────────────────────────

## KEY IDEA

Anagram does NOT mean:

```
same order
```

It means:

```
same character counts
```

───────────────────────────────────────────────────────────────

## METHOD 1 — SORT

```
"listen"
    ↓
eilnst

"silent"
    ↓
eilnst
```

Same:

```
YES
```

───────────────────────────────────────────────────────────────

## CODE

```
sort(s1.begin(), s1.end());
sort(s2.begin(), s2.end());

if(s1 == s2)
    cout << "Anagram";
```

───────────────────────────────────────────────────────────────

## METHOD 2 — FREQUENCY

For lowercase English:

```
int freq[26] = {0};
```

For each:

```
freq[s1[i]]++;
```

For second:

```
freq[s2[i]]--;
```

At end:

```
every frequency must be 0.
```

───────────────────────────────────────────────────────────────

## BETTER PATTERN

```
SAME CHARACTERS
    +
SAME FREQUENCY
    ↓
  ANAGRAM
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
rearrangement
same letters
same characters
different order
```

Think:

```
FREQUENCY
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Group anagrams
Check permutation
Compare character multisets
```

───────────────────────────────────────────────────────────────

## IMPORTANT

If case-insensitive:

```
convert both to lowercase
```

If spaces ignored:

```
remove/ignore spaces
```

═══════════════════════════════════════════════════════════════

# 25. FIRST NON-REPEATING CHARACTER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"swiss"
```

Frequencies:

```
s → 3
w → 1
i → 1
```

First character with frequency 1:

```
w
```

───────────────────────────────────────────────────────────────

## MOST IMPORTANT IDEA

You need BOTH:

```
frequency
original order
```

Therefore:

```
TWO PASSES
```

───────────────────────────────────────────────────────────────

## PASS 1

Count:

```
freq[c]++
```

───────────────────────────────────────────────────────────────

## PASS 2

Scan original string:

```
if(freq[c] == 1)
    answer
```

───────────────────────────────────────────────────────────────

## CODE

```
int freq[256] = {0};

for(char c : s)
    freq[c]++;

for(char c : s) {

    if(freq[c] == 1) {

        cout << c;
        return;
    }
}
```

───────────────────────────────────────────────────────────────

## WHY NOT ONE PASS?

Because when you see:

```
s
```

you don't yet know whether another:

```
s
```

appears later.

Therefore:

```
COUNT FIRST
   ↓
FIND FIRST
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
first
   +
non-repeating
   ↓
FREQUENCY + ORIGINAL ORDER
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
First unique
First non-repeating number
First repeated character
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
FREQUENCY
    ↓
SECOND PASS
    ↓
ORDER PRESERVED
```

═══════════════════════════════════════════════════════════════

# 26. COUNT VOWELS AND CONSONANTS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"education"
```

Count:

```
vowels
consonants
```

───────────────────────────────────────────────────────────────

## INTUITION

For each alphabetic character:

```
is it a vowel?
```

Vowels:

```
a e i o u
```

Otherwise:

```
consonant
```

───────────────────────────────────────────────────────────────

## CODE

```
int vowels = 0;
int consonants = 0;

for(char c : s) {

    c = tolower(c);

    if(c >= 'a' && c <= 'z') {

        if(c == 'a' ||
           c == 'e' ||
           c == 'i' ||
           c == 'o' ||
           c == 'u') {

            vowels++;
        }

        else {

            consonants++;
        }
    }
}
```

───────────────────────────────────────────────────────────────

## IMPORTANT

Don't classify:

```
space
digit
punctuation
```

as consonants.

First verify:

```
alphabetic
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
count
classify
characters
```

Think:

```
ONE PASS + CONDITION
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Count uppercase
Count lowercase
Count digits
Count special characters
Count vowels
Count consonants
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
CHARACTER
   ↓
CLASSIFY
   ↓
COUNTER
```

═══════════════════════════════════════════════════════════════

# 27. REMOVE DUPLICATE CHARACTERS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"programming"
```

Remove repeated characters while preserving first occurrence.

Possible output:

```
"progamin"
```

───────────────────────────────────────────────────────────────

## INTUITION

For every character:

```
Have I already added it?
```

If NO:

```
add it
```

If YES:

```
skip
```

───────────────────────────────────────────────────────────────

## CODE

```
bool seen[256] = {false};

string ans = "";

for(char c : s) {

    if(!seen[(unsigned char)c]) {

        ans += c;

        seen[(unsigned char)c] = true;
    }
}
```

───────────────────────────────────────────────────────────────

## CORE IDEA

```
FILTER
   +
PRESERVE FIRST OCCURRENCE
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
remove duplicates
unique characters
retain first occurrence
```

Think:

```
SET / SEEN ARRAY
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Remove duplicate numbers
Unique elements
First occurrence only
Distinct characters
```

───────────────────────────────────────────────────────────────

## CONNECTION

Array duplicate:

```
seen[x]
```

String duplicate:

```
seen[c]
```

Same pattern.

Only data type changes.

═══════════════════════════════════════════════════════════════

# 28. REVERSE WORDS IN A STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Input:

```
"I love coding"
```

Output:

```
"coding love I"
```

───────────────────────────────────────────────────────────────

## FIRST THINK

This is NOT:

```
reverse every character
```

It is:

```
reverse ORDER OF WORDS
```

───────────────────────────────────────────────────────────────

## INTUITION

Break:

```
I
love
coding
```

Then output:

```
coding
love
I
```

───────────────────────────────────────────────────────────────

## SIMPLE C++ APPROACH

```
stringstream ss(s);

vector<string> words;

string word;

while(ss >> word)
    words.push_back(word);

reverse(words.begin(), words.end());

for(int i = 0; i < words.size(); i++) {

    if(i > 0)
        cout << " ";

    cout << words[i];
}
```

───────────────────────────────────────────────────────────────

## RECOGNITION

```
reverse words
   ≠
reverse characters
```

Think:

```
TOKENIZE
   ↓
REVERSE TOKENS
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Reverse sentence
Reverse word order
Arrange words backwards
Remove extra spaces
```

───────────────────────────────────────────────────────────────

## TRICK

If input contains multiple spaces:

```
stringstream
```

automatically handles whitespace separation.

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
SENTENCE
   ↓
WORDS
   ↓
VECTOR
   ↓
REVERSE
```

═══════════════════════════════════════════════════════════════

# 29. LEADERS IN ARRAY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

An element is a leader if:

```
every element to its RIGHT
is smaller than it.
```

Example:

```
[16,17,4,3,5,2]
```

Leaders:

```
17
5
2
```

───────────────────────────────────────────────────────────────

## NAIVE APPROACH

For each element:

```
scan everything right
```

Complexity:

```
O(N²)
```

───────────────────────────────────────────────────────────────

## KEY OBSERVATION

Start from the RIGHT.

The last element is automatically a leader.

Maintain:

```
maximumSeenFromRight
```

───────────────────────────────────────────────────────────────

## ALGORITHM

```
maxRight = a[n-1]

answer = {a[n-1]}
```

Move:

```
right → left
```

If:

```
a[i] > maxRight
```

then:

```
a[i] is leader
```

Update:

```
maxRight = a[i]
```

───────────────────────────────────────────────────────────────

## CODE

```
vector<int> leaders;

int maxRight = a[n-1];

leaders.push_back(a[n-1]);

for(int i = n-2; i >= 0; i--) {

    if(a[i] > maxRight) {

        leaders.push_back(a[i]);

        maxRight = a[i];
    }
}

reverse(leaders.begin(), leaders.end());
```

───────────────────────────────────────────────────────────────

## DEEP INTUITION

Question asks:

```
"Is everything to my RIGHT smaller?"
```

Instead of repeatedly scanning right:

```
PRECOMPUTE RIGHT INFORMATION
```

Maintain:

```
maximum on right
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
greater than all elements to right
leader
maximum on right
```

Think:

```
RIGHT → LEFT
MAXIMUM SO FAR
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Right-side maximum
Suffix maximum
Next greater
Stock-like right-side comparison
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
PROPERTY OF RIGHT SIDE
        ↓
   SCAN FROM RIGHT
```

═══════════════════════════════════════════════════════════════

# 30. PREFIX SUM / EQUILIBRIUM INDEX

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PROBLEM

Find an index where:

```
sum of elements LEFT
       =
sum of elements RIGHT
```

Example:

```
[-7,1,5,2,-4,3,0]
```

At index 3:

Left:

```
-7 + 1 + 5 = -1
```

Right:

```
-4 + 3 + 0 = -1
```

Therefore:

```
index = 3
```

───────────────────────────────────────────────────────────────

## NAIVE

For every index:

```
calculate left sum
calculate right sum
```

This can become:

```
O(N²)
```

───────────────────────────────────────────────────────────────

## KEY OBSERVATION

Calculate:

```
totalSum
```

Then maintain:

```
leftSum
```

For current:

```
rightSum =
    totalSum
    - leftSum
    - a[i]
```

───────────────────────────────────────────────────────────────

## CORE CONDITION

```
leftSum
  ==
totalSum - leftSum - a[i]
```

───────────────────────────────────────────────────────────────

## CODE

```
long long total = 0;

for(int x : a)
    total += x;

long long left = 0;

for(int i = 0; i < n; i++) {

    long long right =
        total - left - a[i];

    if(left == right) {

        cout << i;
        return;
    }

    left += a[i];
}

cout << -1;
```

───────────────────────────────────────────────────────────────

## MASTER IDEA

Instead of repeatedly calculating:

```
LEFT
RIGHT
```

maintain:

```
TOTAL
LEFT
```

Then:

```
RIGHT = TOTAL - LEFT - CURRENT
```

───────────────────────────────────────────────────────────────

## RECOGNITION

Words:

```
equilibrium
equal left and right sum
balance index
pivot index
sum before = sum after
```

Think:

```
PREFIX SUM
```

───────────────────────────────────────────────────────────────

## SIMILAR

```
Prefix sum
Running sum
Range sum
Equilibrium index
Pivot index
Subarray sum
```

───────────────────────────────────────────────────────────────

## MASTER CONNECTION

```
             TOTAL
               │
      ┌────────┴────────┐
      ▼                 ▼
   LEFT             CURRENT
      │                 │
      └────────┬────────┘
               ▼
    RIGHT = TOTAL - LEFT - CURRENT
```

═══════════════════════════════════════════════════════════════

# STRING PATTERN MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                STRING
                   │
    ┌──────────────┼──────────────┐
    │              │              │
  ORDER          COUNT          COMPARE
    │              │              │
    ▼              ▼              ▼
 REVERSE       FREQUENCY       ANAGRAM
    │              │
    ▼              ├── FIRST UNIQUE
PALINDROME         ├── FIRST REPEAT
                   └── DUPLICATE
                   │
                   ▼
                FILTER
                   │
                   ├── Remove duplicate
                   ├── Vowels
                   ├── Digits
                   └── Spaces
```

═══════════════════════════════════════════════════════════════

# ARRAY PATTERN MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                  ARRAY
                    │
    ┌───────────────┼────────────────┐
    │               │                │
  EXTREME         ORDER            SUM
    │               │                │
max/min          sorting          prefix
second max       merge            Kadane
                   │                │
                 rotate         equilibrium
                   │
                   ▼
              TWO POINTER
                   │
              ┌────┴────┐
              │         │
           merge      move zero


                    ARRAY
                      │
                RIGHT-SIDE PROPERTY
                      │
                      ▼
                 LEADERS
                      │
                      ▼
             RIGHT → LEFT
             MAXIMUM SO FAR
```

═══════════════════════════════════════════════════════════════

# THE MOST IMPORTANT SIMILARITIES

## 1. PALINDROME NUMBER vs PALINDROME STRING

NUMBER:

```
%10
 ↓
reverse
 ↓
compare
```

STRING:

```
left
  ↕
right
  ↓
compare
```

UNDERLYING PATTERN:

```
FORWARD == BACKWARD
```

═══════════════════════════════════════════════════════════════

## 2. ARRAY DUPLICATE vs STRING DUPLICATE

ARRAY:

```
seen[x]
```

STRING:

```
seen[c]
```

UNDERLYING PATTERN:

```
HAVE I SEEN THIS?
```

═══════════════════════════════════════════════════════════════

## 3. ARRAY FREQUENCY vs STRING FREQUENCY

ARRAY:

```
freq[number]++
```

STRING:

```
freq[character]++
```

UNDERLYING PATTERN:

```
COUNT OCCURRENCES
```

═══════════════════════════════════════════════════════════════

## 4. FIRST UNIQUE NUMBER vs FIRST UNIQUE CHARACTER

NUMBER:

```
freq[x]
```

CHARACTER:

```
freq[c]
```

Then:

```
second pass
   ↓
first frequency == 1
```

UNDERLYING PATTERN:

```
FREQUENCY + ORIGINAL ORDER
```

═══════════════════════════════════════════════════════════════

## 5. MOVE ZEROES vs REMOVE DUPLICATE CHARACTERS

MOVE ZEROES:

```
keep desired elements
write them forward
```

REMOVE DUPLICATES:

```
keep first unseen elements
write them forward
```

UNDERLYING PATTERN:

```
FILTER
   ↓
PRESERVE ORDER
```

═══════════════════════════════════════════════════════════════

## 6. LEADERS vs PREFIX SUM

LEADER:

```
Need information from RIGHT

↓

Scan right → left
```

EQUILIBRIUM:

```
Need information from LEFT + RIGHT

↓

TOTAL + LEFT SUM
```

UNDERLYING PATTERN:

```
PRECOMPUTE INFORMATION
INSTEAD OF REPEATEDLY SCANNING
```

═══════════════════════════════════════════════════════════════

# Q1 STORY → PATTERN TRANSLATOR

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

"Read backwards"
↓
REVERSE

"Same forwards and backwards"
↓
PALINDROME

"How many times does each character occur?"
↓
FREQUENCY

"First character that occurs once"
↓
FREQUENCY + SECOND PASS

"Same letters in different order"
↓
ANAGRAM

"Remove repeated characters"
↓
SEEN / SET

"Count vowels"
↓
CHARACTER CLASSIFICATION

"Reverse sentence word order"
↓
TOKENIZE + REVERSE

"Greater than every element on right"
↓
LEADERS
↓
RIGHT → LEFT MAX

"Left sum equals right sum"
↓
PREFIX SUM / RUNNING SUM

═══════════════════════════════════════════════════════════════

# Q1 MASTER — 30 PROBLEMS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ARRAY / SEARCH / NUMBER

```
1. Maximum + Minimum
2. Binary Search
3. Closest Element
4. Two Sum
5. Sort + Custom Formula
6. Matrix Trace
7. Fibonacci
8. Second Largest
9. Digit Processing
10. Prime
```

ARRAY TRANSFORMATION

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

STRING

```
21. Reverse String
22. Palindrome String
23. Character Frequency
24. Anagram
25. First Non-Repeating Character
26. Vowels / Consonants
27. Remove Duplicate Characters
28. Reverse Words
```

ARRAY ADVANCED-Q1

```
29. Leaders
30. Prefix Sum / Equilibrium Index
```

═══════════════════════════════════════════════════════════════

# 30 PROBLEMS → CORE PATTERNS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

30 PROBLEMS

```
   ↓

ONE-PASS
   │
   ├── Max/Min
   ├── Second Largest
   └── Classification

SORTING
   │
   ├── Sort + Formula
   └── Merge

BINARY SEARCH
   │
   └── Closest

HASHING
   │
   ├── Two Sum
   ├── Duplicate
   ├── Frequency
   ├── First Unique
   └── Anagram

TWO POINTER
   │
   ├── Reverse
   ├── Palindrome
   ├── Move Zeroes
   └── Merge

DIGITS
   │
   ├── Sum
   ├── Reverse
   └── Palindrome

NUMBER THEORY
   │
   ├── Prime
   └── GCD/LCM

MATRIX
   │
   └── Trace

CONTIGUOUS ARRAY
   │
   └── Kadane

PREFIX / SUFFIX
   │
   ├── Equilibrium
   └── Leaders

STRING
   │
   ├── Reverse
   ├── Frequency
   ├── Anagram
   ├── Palindrome
   └── Word manipulation
```

═══════════════════════════════════════════════════════════════

# Q1 INSTANT RECOGNITION — FINAL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

QUESTION:

"largest / smallest"
↓
ONE PASS

"second largest"
↓
TWO EXTREMES

"sorted + search"
↓
BINARY SEARCH

"sorted + closest"
↓
BINARY SEARCH + NEIGHBOURS

"pair + target"
↓
HASHMAP
│
└── sorted → TWO POINTER

"duplicate"
↓
HASHSET

"frequency"
↓
HASHMAP / FREQUENCY ARRAY

"first unique"
↓
FREQUENCY + SECOND PASS

"same characters, different order"
↓
ANAGRAM

"same forward/backward"
↓
PALINDROME

"reverse"
↓
TWO POINTER

"move/remove while preserving order"
↓
WRITE POINTER / FILTER

"contiguous maximum sum"
↓
KADANE

"greater than everything on right"
↓
RIGHT → LEFT MAX

"left sum = right sum"
↓
PREFIX SUM

"digits"
↓
%10 /10

"prime"
↓
DIVISIBILITY / SQRT

"GCD"
↓
EUCLIDEAN

"LCM"
↓
GCD

"trace"
↓
a[i][i]

"diagonal"
↓
a[i][i]
OR
a[i][n-1-i]

"rotate by K"
↓
K % N

═══════════════════════════════════════════════════════════════

# Q1 CODING TRICKS — LAST-MINUTE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1.

For max/min:

```
initialize from a[0]
```

NOT zero.

───────────────────────────────────────────────────────────────

2.

For Kadane:

```
initialize from a[0]
```

NOT zero.

Otherwise all-negative arrays break.

───────────────────────────────────────────────────────────────

3.

For rotation:

```
k %= n
```

───────────────────────────────────────────────────────────────

4.

For binary search:

```
mid = low + (high-low)/2
```

───────────────────────────────────────────────────────────────

5.

For Two Sum:

```
check complement
BEFORE storing current
```

───────────────────────────────────────────────────────────────

6.

For frequency:

```
COUNT FIRST
THEN answer questions about order.
```

───────────────────────────────────────────────────────────────

7.

For first unique:

```
frequency → second pass
```

───────────────────────────────────────────────────────────────

8.

For leaders:

```
scan RIGHT → LEFT
```

───────────────────────────────────────────────────────────────

9.

For equilibrium:

```
right =
total - left - current
```

───────────────────────────────────────────────────────────────

10.

For palindrome:

```
compare two ends
```

───────────────────────────────────────────────────────────────

11.

For digit problems:

```
digit = n % 10
n /= 10
```

───────────────────────────────────────────────────────────────

12.

For LCM:

```
(a / gcd) * b
```

NOT blindly:

```
a*b/gcd
```

───────────────────────────────────────────────────────────────

13.

For multiplication:

```
1LL * a * b
```

───────────────────────────────────────────────────────────────

14.

For strings:

```
clarify whether:
case matters
spaces matter
punctuation matters
```

───────────────────────────────────────────────────────────────

15.

For TCS input:

```
Don't assume the statement's formatting
is identical to normal LeetCode.
```

Read exactly:

```
number of test cases?
N?
next line?
arrays on separate lines?
target at end?
```

Recent July candidates specifically reported losing time on input handling despite knowing the algorithm.

═══════════════════════════════════════════════════════════════

# Q1 — FINAL MASTER REVISION FLOW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
            READ QUESTION
                   │
                   ▼
           UNDERSTAND INPUT
                   │
                   ▼
          WHAT IS THE OUTPUT?
                   │
                   ▼
         REMOVE THE STORY
                   │
                   ▼
           FIND KEYWORD
                   │
   ┌───────────────┼────────────────┐
   ▼               ▼                ▼
 EXTREME         SEARCH           COUNT
   │               │                │
max/min         sorted?          frequency?
   │               │                │
one pass       binary search      hashmap
                                   │
                                   ▼
                              unique/repeat

   ┌───────────────┼────────────────┐
   ▼               ▼                ▼
  ORDER          SEGMENT          STRING
   │               │                │
 sorting         contiguous       reverse?
 rotate          max sum          palindrome?
 merge           prefix           anagram?
   │               │                │
   ▼               ▼                ▼
```

two pointer       Kadane          string pattern

```
                   │
                   ▼
              WRITE TEMPLATE
                   │
                   ▼
              EDGE CASES
                   │
                   ▼
               COMPLEXITY
                   │
                   ▼
                SUBMIT
```

═══════════════════════════════════════════════════════════════

# FINAL Q1 CHECK

Before moving to Q2, I should be able to look at:

```
"A company has a list of employee IDs.
 Find the first ID which occurs only once."
```

and immediately say:

```
FREQUENCY
   ↓
HASHMAP
   ↓
SECOND PASS
```

I should see:

```
"Two sorted arrays must be combined."
```

and immediately say:

```
TWO POINTER
   ↓
TAKE SMALLER
```

I should see:

```
"Find the maximum sum of consecutive elements."
```

and immediately say:

```
KADANE
```

I should see:

```
"Find an element greater than every
 element to its right."
```

and immediately say:

```
LEADER
   ↓
RIGHT → LEFT
```

I should see:

```
"Find an index where left sum
 equals right sum."
```

and immediately say:

```
PREFIX SUM
   ↓
TOTAL - LEFT - CURRENT
```

I should see:

```
"Check whether the string
 reads the same backward."
```

and immediately say:

```
PALINDROME
   ↓
TWO POINTER
```

I should see:

```
"Two strings contain exactly
 the same letters."
```

and immediately say:

```
ANAGRAM
   ↓
FREQUENCY
```

═══════════════════════════════════════════════════════════════

# END — Q1 MASTER 30

NEXT TARGET:

```
Q2 HIGH-ROI MASTER

NOT 30 MORE RANDOM QUESTIONS.

We will target the harder second-question
patterns actually reported in recent TCS slots:

    ├── Postfix Expression
    ├── Stack / Monotonic Stack
    ├── Sliding Window
    ├── Heap / K Largest
    ├── Prefix Sum variants
    ├── BST / Tree
    ├── BFS / Graph
    └── Basic DP
```

The objective:

```
Q1 → make automatic
Q2 → maximize pattern coverage
Q2 → partial-credit survival if unfamiliar
```

═══════════════════════════════════════════════════════════════
