# TCS NQT CODING — HIGH ROI PYQ PATTERN MASTER

## PART 2 — STRING + NUMBER/DIGIT + SLIDING WINDOW

## C++17 | Last-Day Revision

═══════════════════════════════════════════════════════════════

# PART 2 — CORE IDEA

STRING
│
├── Character-by-character processing
│       ↓
│    Traversal
│
├── Need counts?
│       ↓
│    Frequency / HashMap
│
├── Same forward/backward?
│       ↓
│    Two Pointer
│
├── Compare character collections?
│       ↓
│    Frequency
│
├── Longest continuous substring?
│       ↓
│    Sliding Window
│
└── Transform characters?
↓
Traversal + condition

NUMBER
│
├── Need digits?
│       ↓
│    % 10
│
├── Remove last digit?
│       ↓
│    / 10
│
├── Reverse?
│       ↓
│    rev = rev*10 + digit
│
├── Prime?
│       ↓
│    Check divisors
│
├── GCD?
│       ↓
│    Euclidean Algorithm
│
└── Special number?
↓
Digit processing

SLIDING WINDOW
│
├── Fixed size
│       ↓
│    Exactly K elements
│
└── Variable size
↓
Longest / shortest valid segment

═══════════════════════════════════════════════════════════════

# 17. REVERSE A STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Given:

```
"hello"
```

return:

```
"olleh"
```

## INTUITION

Exactly the same as reversing an array.

Characters have indexes.

So:

```
first ↔ last
second ↔ second-last
```

Therefore:

```
TWO POINTER
```

## CODE

```
int l = 0;
int r = s.size() - 1;

while(l < r) {
    swap(s[l], s[r]);
    l++;
    r--;
}
```

## OR

```
reverse(s.begin(), s.end());
```

## WHAT TO REMEMBER

If the interviewer/TCS expects algorithmic thinking:

```
left + right
```

If only output matters:

```
reverse()
```

## RECOGNITION

Words:

```
reverse string
reverse characters
read backwards
```

Think:

```
TWO POINTER
```

## SIMILAR

```
Reverse array
Reverse words
Palindrome
Reverse number
```

═══════════════════════════════════════════════════════════════

# 18. COUNT VOWELS / CONSONANTS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Count:

```
vowels
consonants
digits
spaces
special characters
```

## INTUITION

Visit every character.

For each character:

```
What category does it belong to?
```

This is simply:

```
STRING TRAVERSAL
    +
CONDITION
```

## CODE

```
int vowels = 0;
int consonants = 0;

for(char c : s) {

    c = tolower(c);

    if(c == 'a' || c == 'e' ||
       c == 'i' || c == 'o' ||
       c == 'u') {

        vowels++;
    }

    else if(isalpha(c)) {
        consonants++;
    }
}
```

## CORE PATTERN

```
for(char c : s)
    condition
    ↓
    counter++
```

## IMPORTANT

Use:

```
isalpha(c)
```

to distinguish letters from spaces/digits.

## RECOGNITION

If the question asks:

```
count X characters
classify characters
count categories
```

Think:

```
TRAVERSAL + CONDITION
```

## SIMILAR

```
Count digits
Count spaces
Count uppercase
Count lowercase
Count special characters
```

═══════════════════════════════════════════════════════════════

# 19. REMOVE VOWELS / REMOVE SPACES / FILTER STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Remove:

```
vowels
spaces
digits
special characters
unwanted characters
```

## INTUITION

Don't actually "delete" characters repeatedly.

Build a new result.

For every character:

```
If useful
    keep it
```

## CODE

```
string ans = "";

for(char c : s) {

    if(!isVowel(c)) {
        ans += c;
    }
}
```

## BETTER GENERAL PATTERN

```
string ans;

for(char c : s) {

    if(condition) {
        ans.push_back(c);
    }
}
```

## THE MASTER IDEA

This is:

```
FILTERING
```

Input
↓
Check condition
↓
Keep / Reject
↓
Output

## RECOGNITION

Words:

```
remove
delete
exclude
ignore
keep only
retain
```

Think:

```
FILTER
```

## SIMILAR

```
Remove duplicates
Remove spaces
Remove vowels
Keep digits only
Keep alphabets only
Keep even numbers
```

═══════════════════════════════════════════════════════════════

# 20. CHARACTER FREQUENCY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Given:

```
"banana"
```

find:

```
b → 1
a → 3
n → 2
```

## INTUITION

Every character gets a counter.

Every time we see it:

```
count++
```

## CODE

```
int freq[256] = {};

for(char c : s) {
    freq[(unsigned char)c]++;
}
```

## MAP VERSION

```
unordered_map<char,int> freq;

for(char c : s)
    freq[c]++;
```

## WHY THIS IS HIGH ROI

This one pattern gives:

```
Frequency
   │
   ├── Duplicate characters
   ├── First unique
   ├── Most frequent
   ├── Least frequent
   ├── Anagram
   └── Character comparison
```

## RECOGNITION

Words:

```
frequency
occurrence
appears
repeated
count each character
```

Think:

```
FREQUENCY ARRAY / HASHMAP
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1) if fixed alphabet
```

═══════════════════════════════════════════════════════════════

# 21. FIRST NON-REPEATING CHARACTER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Example:

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

## INTUITION

This problem has TWO STEPS.

STEP 1:

```
Count everything.
```

STEP 2:

```
Scan again from left to right.
```

Why scan again?

Because the question says:

```
FIRST
```

Frequency alone doesn't preserve the required answer.

## CODE

```
int freq[256] = {};

for(char c : s)
    freq[(unsigned char)c]++;

for(char c : s) {

    if(freq[(unsigned char)c] == 1) {
        cout << c;
        return;
    }
}
```

## MASTER PATTERN

```
"FIRST + frequency"
```

usually means:

```
    COUNT FIRST
         ↓
    SCAN AGAIN
```

## RECOGNITION

Words:

```
first unique
first non-repeating
first character occurring once
```

Think:

```
FREQUENCY + SECOND PASS
```

## SIMILAR

```
First repeating
First duplicate
First character satisfying condition
```

═══════════════════════════════════════════════════════════════

# 22. ANAGRAM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Determine whether two strings contain exactly the same characters with the same frequencies.

Example:

```
listen
silent
```

YES

## INTUITION

Order doesn't matter.

Frequency DOES matter.

Therefore:

```
frequency(S1)
   ==
frequency(S2)
```

## CODE — 26 LOWERCASE LETTERS

```
int freq[26] = {};

for(char c : s1)
    freq[c - 'a']++;

for(char c : s2)
    freq[c - 'a']--;

for(int x : freq) {

    if(x != 0) {
        cout << "NO";
        return;
    }
}

cout << "YES";
```

## IMPORTANT

Before this:

```
if(s1.size() != s2.size())
```

they cannot be anagrams.

## RECOGNITION

Words:

```
anagram
same letters
rearrangement
same characters in different order
```

Think:

```
FREQUENCY
```

## DO NOT THINK

```
sorting is the only solution
```

Sorting works:

```
O(N log N)
```

Frequency works:

```
O(N)
```

## SIMILAR

```
Permutation comparison
Character multiset equality
Scrambled words
```

═══════════════════════════════════════════════════════════════

# 23. REVERSE WORDS IN STRING

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Input:

```
"I love coding"
```

Possible output:

```
"coding love I"
```

This is different from reversing every character.

## INTUITION

First understand what is being reversed.

Characters?

```
"gnidoc evol I"
```

Words?

```
"coding love I"
```

Always identify the UNIT being reversed.

## EASY C++ APPROACH

```
stringstream ss(s);

vector<string> words;

string word;

while(ss >> word)
    words.push_back(word);

reverse(words.begin(), words.end());

for(string w : words)
    cout << w << " ";
```

## RECOGNITION

If question says:

```
reverse words
```

NOT:

```
reverse string
```

Think:

```
TOKENIZE → REVERSE WORD ORDER
```

## SIMILAR

```
Reverse each word
Reverse complete sentence
Rearrange words
Remove extra spaces
```

═══════════════════════════════════════════════════════════════

# 24. LONGEST SUBSTRING WITHOUT REPEATING CHARACTERS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Example:

```
"abcabcbb"
```

Longest substring without repetition:

```
"abc"
```

Answer:

```
3
```

## WHY NORMAL NESTED LOOPS ARE BAD

Brute force:

```
Try every substring
Check duplicates
```

Can become:

```
O(N²) or O(N³)
```

## INTUITION

We need a CONTINUOUS section.

That immediately suggests:

```
SLIDING WINDOW
```

Maintain:

```
[left ........ right]
```

Inside the window:

```
no duplicates
```

When duplicate appears:

```
move left
```

## HASHMAP IDEA

Store:

```
last position of each character
```

Example:

```
a → 0
b → 1
c → 2
```

When 'a' appears again at 3:

```
left must move after previous a.
```

## CODE

```
unordered_map<char,int> last;

int left = 0;
int ans = 0;

for(int right = 0; right < s.size(); right++) {

    char c = s[right];

    if(last.count(c)) {
        left = max(left, last[c] + 1);
    }

    last[c] = right;

    ans = max(ans, right - left + 1);
}
```

## CORE LINE

```
left = max(left, last[c] + 1);
```

This prevents left from moving backwards.

## RECOGNITION

Words:

```
longest substring
continuous characters
without repetition
unique characters
```

Think:

```
SLIDING WINDOW + HASHMAP
```

## COMPLEXITY

```
Time  : O(N)
Space : O(K)
```

where K = character set size.

## SIMILAR

```
Longest substring with K distinct
Minimum window
Longest valid segment
At most K duplicates
```

═══════════════════════════════════════════════════════════════

# 25. NUMBER DIGIT EXTRACTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## THIS IS THE MOST IMPORTANT NUMBER PATTERN

Given:

```
12345
```

How do I process digits individually?

Use:

```
digit = n % 10
```

Then remove last digit:

```
n = n / 10
```

## VISUAL

```
12345
   │
   │ % 10
   ▼
   5

12345 / 10
   ↓
  1234
```

Repeat.

## TEMPLATE

```
while(n > 0) {

    int digit = n % 10;

    // process digit

    n /= 10;
}
```

## THIS ONE TEMPLATE SOLVES

```
Digit sum
Digit count
Digit product
Reverse number
Palindrome number
Armstrong
Digit frequency
Repeated digits
Even/odd digit count
Largest digit
Smallest digit
```

## RECOGNITION

If question asks:

```
"digits of a number"
```

Think:

```
%10
/10
```

IMMEDIATELY.

═══════════════════════════════════════════════════════════════

# 26. SUM OF DIGITS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## EXAMPLE

```
n = 1234
```

Answer:

```
1 + 2 + 3 + 4 = 10
```

## INTUITION

Extract each digit and add.

## CODE

```
int sum = 0;

while(n > 0) {

    int digit = n % 10;

    sum += digit;

    n /= 10;
}
```

## CORE PATTERN

```
digit = n % 10
sum += digit
n /= 10
```

## SIMILAR

```
Product of digits
Count digits
Sum of even digits
Sum of odd digits
```

═══════════════════════════════════════════════════════════════

# 27. REVERSE NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## EXAMPLE

```
1234
```

→

```
4321
```

## INTUITION

Extract last digit and append it to the answer.

If:

```
rev = 0
```

and digit = 4:

```
rev = 0*10 + 4
    = 4
```

Next digit = 3:

```
rev = 4*10 + 3
    = 43
```

## CODE

```
int rev = 0;

while(n > 0) {

    int digit = n % 10;

    rev = rev * 10 + digit;

    n /= 10;
}
```

## CORE LINE

```
rev = rev * 10 + digit;
```

MEMORIZE THIS.

## RECOGNITION

Words:

```
reverse digits
reverse number
digits in opposite order
```

Think:

```
digit extraction + rev*10
```

## SIMILAR

```
Palindrome number
Digit rotation
Reverse digits
```

═══════════════════════════════════════════════════════════════

# 28. PALINDROME NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## EXAMPLE

```
121
```

reverse:

```
121
```

Therefore:

```
PALINDROME
```

## INTUITION

Save original number.

Reverse a copy.

Compare:

```
original == reverse
```

## CODE

```
int original = n;

int rev = 0;

while(n > 0) {

    int digit = n % 10;

    rev = rev * 10 + digit;

    n /= 10;
}

if(original == rev)
    cout << "Palindrome";
else
    cout << "Not Palindrome";
```

## IMPORTANT

Don't lose the original.

Therefore:

```
int original = n;
```

before modifying n.

## CONNECTION

String palindrome:

```
TWO POINTER
```

Number palindrome:

```
DIGIT EXTRACTION
```

Same concept:

```
FORWARD == BACKWARD
```

Different implementation.

═══════════════════════════════════════════════════════════════

# 29. ARMSTRONG NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## EXAMPLE

For 3-digit number:

```
153

1³ + 5³ + 3³
= 153
```

Therefore Armstrong.

## IMPORTANT

Don't blindly assume cube.

General Armstrong:

For a number with D digits:

```
sum of each digit^D
```

must equal original number.

## INTUITION

STEP 1:

```
Count digits
```

STEP 2:

```
Extract each digit
```

STEP 3:

```
Add digit^D
```

STEP 4:

```
Compare with original
```

## CODE IDEA

```
int original = n;

int digits = 0;
int temp = n;

while(temp > 0) {
    digits++;
    temp /= 10;
}

int sum = 0;
temp = n;

while(temp > 0) {

    int digit = temp % 10;

    sum += pow(digit, digits);

    temp /= 10;
}

if(sum == original)
    cout << "Armstrong";
```

## TCS TRICK

If the question explicitly says:

```
"for 3 digit numbers"
```

then:

```
digit * digit * digit
```

is enough.

No need for generalization.

## RECOGNITION

Words:

```
Armstrong
narcissistic number
sum of powers of digits
```

Think:

```
DIGIT EXTRACTION
```

═══════════════════════════════════════════════════════════════

# 30. PRIME NUMBER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## DEFINITION

Prime:

```
exactly two positive divisors

1
itself
```

Examples:

```
2
3
5
7
```

## BRUTE FORCE

Try:

```
2 → n-1
```

## OPTIMAL OBSERVATION

If n has a divisor greater than sqrt(n),

there must be a corresponding divisor smaller than sqrt(n).

Therefore only check:

```
i * i <= n
```

## CODE

```
bool prime = true;

if(n < 2)
    prime = false;

for(int i = 2; i * i <= n; i++) {

    if(n % i == 0) {
        prime = false;
        break;
    }
}
```

## CORE LINE

```
i * i <= n
```

## RECOGNITION

Words:

```
prime
divisible only by 1 and itself
prime numbers in range
```

Think:

```
DIVISIBILITY + SQRT
```

## COMPLEXITY

```
O(sqrt(N))
```

## SIMILAR

```
Count primes
Sum primes
Prime factors
Nearest prime
```

═══════════════════════════════════════════════════════════════

# 31. GCD

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION

Find:

```
GCD(a,b)
```

## INTUITION

Use Euclidean algorithm.

Key observation:

```
gcd(a,b)
=
gcd(b, a%b)
```

Repeat until:

```
b = 0
```

Then:

```
a = GCD
```

## CODE

```
while(b != 0) {

    int r = a % b;

    a = b;
    b = r;
}

cout << a;
```

## EXAMPLE

```
gcd(48,18)

48 % 18 = 12

gcd(18,12)

18 % 12 = 6

gcd(12,6)

12 % 6 = 0
```

Answer:

```
6
```

## RECOGNITION

GCD / HCF

Think:

```
EUCLIDEAN ALGORITHM
```

## LCM

Once GCD is known:

```
LCM(a,b)
  =
|a*b| / GCD(a,b)
```

Use long long for multiplication.

## SIMILAR

```
HCF
LCM
Common divisor
Simplifying fractions
```

═══════════════════════════════════════════════════════════════

# 32. FIXED SLIDING WINDOW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Find:

```
maximum sum of K consecutive elements
```

Example:

```
[2,1,5,1,3,2]
```

K = 3

Windows:

```
2+1+5 = 8
1+5+1 = 7
5+1+3 = 9
1+3+2 = 6
```

Answer:

```
9
```

## BRUTE FORCE

For every starting point:

```
calculate K elements
```

Complexity:

```
O(NK)
```

## INTUITION

Adjacent windows overlap heavily.

Example:

```
[2,1,5]
   ↓
```

next:

```
[1,5,1]
```

We don't need to recalculate 1 and 5.

Remove:

```
leftmost
```

Add:

```
new rightmost
```

## CODE

```
long long window = 0;

for(int i = 0; i < k; i++)
    window += a[i];

long long ans = window;

for(int i = k; i < n; i++) {

    window += a[i];
    window -= a[i-k];

    ans = max(ans, window);
}
```

## CORE LINES

```
window += a[i];
window -= a[i-k];
```

## RECOGNITION

Words:

```
exactly K consecutive
K elements
fixed-size subarray
maximum sum of K
minimum sum of K
```

Think:

```
FIXED SLIDING WINDOW
```

## COMPLEXITY

```
Time  : O(N)
Space : O(1)
```

═══════════════════════════════════════════════════════════════

# 33. VARIABLE SLIDING WINDOW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Examples:

```
Longest substring without repeating
Longest subarray with sum <= K
Longest segment satisfying condition
Smallest window satisfying condition
```

Window size is NOT fixed.

## INTUITION

Maintain:

```
[left ... right]
```

Expand:

```
right++
```

If condition becomes invalid:

```
left++
```

until valid again.

## GENERAL TEMPLATE

```
int left = 0;

for(int right = 0; right < n; right++) {

    // add a[right]

    while(condition_is_invalid) {

        // remove a[left]

        left++;
    }

    // current window is valid

    ans = max(ans, right - left + 1);
}
```

## MASTER IDEA

```
RIGHT → EXPAND

LEFT → SHRINK
```

## RECOGNITION

Words:

```
longest
shortest
continuous
substring
subarray
window
at most K
no duplicates
satisfies condition
```

Think:

```
SLIDING WINDOW
```

BUT:

Not every "subarray" is sliding window.

You must have a condition that can be maintained as the window expands/shrinks.

═══════════════════════════════════════════════════════════════

# 34. SUBARRAY WITH GIVEN SUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## IMPORTANT CAVEAT

For:

```
POSITIVE NUMBERS ONLY
```

sliding window is straightforward.

For negative numbers:

```
use prefix sum + hashmap
```

Don't confuse these.

## POSITIVE ARRAY — INTUITION

Maintain:

```
current sum
```

Expand right.

If:

```
sum > target
```

remove from left.

If:

```
sum == target
```

found.

## CODE

```
int left = 0;
long long sum = 0;

for(int right = 0; right < n; right++) {

    sum += a[right];

    while(sum > target && left <= right) {
        sum -= a[left];
        left++;
    }

    if(sum == target) {
        cout << left << " " << right;
        return;
    }
}
```

## RECOGNITION

If:

```
positive numbers
contiguous subarray
target sum
```

think:

```
SLIDING WINDOW
```

## IF NEGATIVE NUMBERS EXIST

Think:

```
PREFIX SUM + HASHMAP
```

That distinction is extremely important.

═══════════════════════════════════════════════════════════════

# 35. MAXIMUM PRODUCT SUBARRAY / PRODUCT LOGIC

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY IT IS TRICKY

For sum:

```
negative usually hurts.
```

For product:

```
negative × negative = positive
```

Therefore we must remember BOTH:

```
maximum product
minimum product
```

## INTUITION

At every element:

```
current maximum
current minimum
```

Because a negative number can turn:

```
minimum → maximum
```

## CORE IDEA

```
maxHere
minHere
```

If x is negative:

```
swap(maxHere, minHere)
```

Then:

```
maxHere = max(x, maxHere*x)
minHere = min(x, minHere*x)
```

## CODE

```
long long mx = a[0];
long long mn = a[0];
long long ans = a[0];

for(int i = 1; i < n; i++) {

    if(a[i] < 0)
        swap(mx, mn);

    mx = max((long long)a[i], mx * a[i]);
    mn = min((long long)a[i], mn * a[i]);

    ans = max(ans, mx);
}
```

## RECOGNITION

Words:

```
maximum product
contiguous product
negative numbers
```

Think:

```
MAX + MIN STATE
```

## SIMILAR

```
Maximum product subset
Product segment
DP-style state tracking
```

═══════════════════════════════════════════════════════════════

# MASTER STRING CONNECTION MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STRING
│
├── Reverse
│      ↓
│   Two Pointer
│
├── Palindrome
│      ↓
│   Two Pointer
│
├── Count characters
│      ↓
│   Frequency
│
├── First unique
│      ↓
│   Frequency + Second Pass
│
├── Anagram
│      ↓
│   Frequency comparison
│
├── Remove characters
│      ↓
│   Filtering
│
├── Count vowels/consonants
│      ↓
│   Traversal + condition
│
├── Reverse words
│      ↓
│   Tokenization + reverse
│
└── Longest unique substring
↓
Sliding Window + HashMap

═══════════════════════════════════════════════════════════════

# MASTER NUMBER CONNECTION MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

NUMBER
│
├── Need individual digits?
│      ↓
│   n % 10
│   n /= 10
│
├── Sum digits?
│      ↓
│   sum += digit
│
├── Reverse?
│      ↓
│   rev = rev*10 + digit
│
├── Palindrome?
│      ↓
│   original == reverse
│
├── Armstrong?
│      ↓
│   digit^numberOfDigits
│
├── Prime?
│      ↓
│   divisibility up to sqrt(n)
│
├── GCD?
│      ↓
│   Euclidean algorithm
│
└── LCM?
↓
a*b/GCD

═══════════════════════════════════════════════════════════════

# MASTER SLIDING WINDOW MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CONTIGUOUS
│
▼
Do I have a FIXED SIZE K?
│
├── YES
│     ↓
│  FIXED WINDOW
│
│  Example:
│  max sum of K
│
└── NO
↓
VARIABLE WINDOW
│
├── Longest valid
├── Shortest valid
├── At most K
├── No duplicates
└── Sum constraint

═══════════════════════════════════════════════════════════════

# TCS INSTANT RECOGNITION — PART 2

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

"REVERSE STRING"
↓
TWO POINTER

"PALINDROME STRING"
↓
TWO POINTER

"COUNT CHARACTERS"
↓
FREQUENCY

"FIRST NON-REPEATING"
↓
FREQUENCY + SECOND PASS

"ANAGRAM"
↓
FREQUENCY COMPARISON

"REMOVE VOWELS / SPACES"
↓
FILTERING

"REVERSE WORDS"
↓
TOKENIZE + REVERSE

"LONGEST SUBSTRING WITHOUT REPEAT"
↓
SLIDING WINDOW + HASHMAP

"CONSECUTIVE K ELEMENTS"
↓
FIXED SLIDING WINDOW

"LONGEST CONTINUOUS VALID SEGMENT"
↓
VARIABLE SLIDING WINDOW

"SUBARRAY TARGET SUM"
↓
POSITIVE → SLIDING WINDOW
NEGATIVE → PREFIX SUM + HASHMAP

"DIGITS OF NUMBER"
↓
%10 + /10

"REVERSE NUMBER"
↓
rev = rev*10 + digit

"PALINDROME NUMBER"
↓
ORIGINAL == REVERSE

"ARMSTRONG"
↓
DIGIT POWERS

"PRIME"
↓
DIVISIBILITY UP TO SQRT(N)

"GCD"
↓
EUCLIDEAN ALGORITHM

"LCM"
↓
a*b/GCD

═══════════════════════════════════════════════════════════════

# THE MOST IMPORTANT SIMILARITY NETWORK

These problems are NOT separate.

They are the same ideas wearing different clothes.

## FAMILY 1

```
Reverse Array
      │
      ├── Reverse String
      ├── Palindrome
      └── Reverse Number
```

Core:

```
MOVE FROM BOTH ENDS
OR
PROCESS DIGITS
```

───────────────────────────────────────────────────────────────

## FAMILY 2

```
Character Frequency
      │
      ├── First Non-Repeating
      ├── Anagram
      ├── Duplicate Characters
      ├── Most Frequent
      └── Common Characters
```

Core:

```
FREQUENCY MAP
```

───────────────────────────────────────────────────────────────

## FAMILY 3

```
Maximum K-Window Sum
      │
      ├── Minimum K-Window
      ├── Longest Valid Window
      ├── Longest Unique Substring
      └── Subarray Condition
```

Core:

```
SLIDING WINDOW
```

───────────────────────────────────────────────────────────────

## FAMILY 4

```
Digit Sum
      │
      ├── Reverse Number
      ├── Palindrome Number
      ├── Armstrong
      ├── Digit Product
      └── Digit Frequency
```

Core:

```
%10
/10
```

───────────────────────────────────────────────────────────────

## FAMILY 5

```
Prime
      │
      ├── Prime in Range
      ├── Count Primes
      ├── Sum Primes
      └── Prime Factors
```

Core:

```
DIVISIBILITY
```

───────────────────────────────────────────────────────────────

# EDGE-CASE CHECKLIST

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Before submitting any TCS coding question, mentally ask:

```
1. N = 1?

2. Empty string?

3. Duplicate values?

4. All values same?

5. Negative numbers?

6. Zero present?

7. Target absent?

8. Target at first position?

9. Target at last position?

10. Answer is impossible?

11. Integer overflow?

12. Is the array actually sorted?

13. Does "first" mean I should break?

14. Does "subarray" mean CONTIGUOUS?

15. Does the problem allow negative values?
```

These small checks prevent many hidden-test failures.

═══════════════════════════════════════════════════════════════

# INTEGER OVERFLOW — TCS TRAP

If:

```
a[i] * a[j]
```

can become large:

Use:

```
long long
```

Example:

```
long long ans =
    1LL * a[0] * a[3];
```

Why?

Because:

```
int * int
```

may overflow BEFORE being assigned to long long.

Therefore:

```
1LL * a * b
```

forces long long multiplication.

═══════════════════════════════════════════════════════════════

# STRING INPUT — IMPORTANT TCS TRICK

If input is ONE WORD:

```
cin >> s;
```

If input contains SPACES:

```
getline(cin, s);
```

Example:

```
"I love coding"
```

requires:

```
getline(cin, s);
```

If you used:

```
cin >> s;
```

you would only get:

```
"I"
```

═══════════════════════════════════════════════════════════════

# CHARACTER CONVERSION TRICKS

Lowercase:

```
c = tolower(c);
```

Uppercase:

```
c = toupper(c);
```

Alphabet:

```
isalpha(c)
```

Digit:

```
isdigit(c)
```

Lowercase letter:

```
c >= 'a' && c <= 'z'
```

Uppercase letter:

```
c >= 'A' && c <= 'Z'
```

Convert digit character to number:

```
int x = c - '0';
```

Convert number 0–9 to character:

```
char c = x + '0';
```

═══════════════════════════════════════════════════════════════

# LAST-DAY CODING MENTAL FLOW

When TCS gives a question:

```
    READ
      │
      ▼
What is the OUTPUT?
      │
      ▼
What is changing?
      │
      ▼
Is it ARRAY / STRING / NUMBER?
      │
      ▼
What special word appears?
      │
      ├── frequency
      │      ↓
      │   HASHMAP
      │
      ├── sorted
      │      ↓
      │   BINARY SEARCH / TWO POINTER
      │
      ├── pair + target
      │      ↓
      │   HASHMAP / TWO POINTER
      │
      ├── reverse/palindrome
      │      ↓
      │   TWO POINTER
      │
      ├── longest/shortest continuous
      │      ↓
      │   SLIDING WINDOW
      │
      ├── digits
      │      ↓
      │   %10 /10
      │
      ├── maximum contiguous sum
      │      ↓
      │   KADANE
      │
      └── prime/GCD
             ↓
         NUMBER THEORY
```

═══════════════════════════════════════════════════════════════

# PART 2 — MINIMUM CODE TEMPLATES TO MEMORIZE

## Reverse string/array

```
int l = 0, r = n - 1;

while(l < r) {
    swap(a[l], a[r]);
    l++;
    r--;
}
```

## Frequency

```
int freq[256] = {};

for(char c : s)
    freq[(unsigned char)c]++;
```

## HashMap

```
unordered_map<int,int> mp;

mp[x]++;
```

## Digit extraction

```
int digit = n % 10;
n /= 10;
```

## Reverse number

```
rev = rev * 10 + digit;
```

## Fixed window

```
window += a[i];
window -= a[i-k];
```

## Variable window

```
for(int right = 0; right < n; right++) {

    // add right

    while(invalid) {
        // remove left
        left++;
    }

    // process window
}
```

## Prime

```
for(int i = 2; i * i <= n; i++) {
    if(n % i == 0)
        // not prime
}
```

## GCD

```
while(b != 0) {
    int r = a % b;
    a = b;
    b = r;
}
```

═══════════════════════════════════════════════════════════════

# PART 2 — FINAL MEMORY TREE

STRING
│
├── Reverse
│      └── Two Pointer
│
├── Palindrome
│      └── Two Pointer
│
├── Frequency
│      └── HashMap
│
├── First Unique
│      └── Frequency + Second Pass
│
├── Anagram
│      └── Frequency Comparison
│
├── Remove Characters
│      └── Filtering
│
├── Reverse Words
│      └── Tokenization
│
└── Longest Unique Substring
└── Sliding Window + HashMap

NUMBER
│
├── Digit Sum
│      └── %10 + /10
│
├── Reverse
│      └── rev*10 + digit
│
├── Palindrome
│      └── Original == Reverse
│
├── Armstrong
│      └── Digit Powers
│
├── Prime
│      └── sqrt(n) divisibility
│
└── GCD/LCM
└── Euclidean Algorithm

SLIDING WINDOW
│
├── Fixed
│      └── Exactly K
│
├── Variable
│      └── Longest/Shortest
│
├── String
│      └── Frequency/HashMap
│
└── Subarray
└── Sum / Constraint

═══════════════════════════════════════════════════════════════

# MASTER RULE

When you see a NEW question:

DON'T ASK:

```
"Have I solved this exact problem?"
```

ASK:

```
"Which old problem does this behave like?"
```

Examples:

```
"Longest section of customers without repeating IDs"
                ↓
Longest substring without repeating
                ↓
Sliding Window + HashMap


"Two students whose combined marks equal X"
                ↓
Two Sum
                ↓
HashMap


"Check whether ID reads same backwards"
                ↓
Palindrome
                ↓
Two Pointer


"Find special property of every digit"
                ↓
Digit Extraction
                ↓
%10 + /10


"Maximum total of K consecutive houses"
                ↓
Fixed Sliding Window


"Highest sum of a continuous segment"
                ↓
Kadane
```

THIS IS THE SKILL WE ARE BUILDING:

```
    NEW STORY
       ↓
  REMOVE STORY
       ↓
 FIND STRUCTURE
       ↓
   RECOGNIZE
       ↓
  APPLY PATTERN
       ↓
     CODE
```

═══════════════════════════════════════════════════════════════
END OF PART 2
═══════════════════════════════════════════════════════════════
