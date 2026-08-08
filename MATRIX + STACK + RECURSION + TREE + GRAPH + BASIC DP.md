# TCS NQT CODING — HIGH ROI PYQ PATTERN MASTER

## PART 3 — MATRIX + STACK + RECURSION + TREE + GRAPH + BASIC DP

## C++17 | Last-Day Revision

═══════════════════════════════════════════════════════════════

# PART 3 — PRIORITY

These topics are NOT equal.

```
    HIGHER ROI
        │
        ├── Matrix
        ├── Stack
        └── Basic Recursion
                │
                ▼
          Q2 SURVIVAL
                │
                ├── Tree BFS/DFS
                ├── Basic DP
                └── MST recognition
                │
                ▼
             LOWEST
                │
                ├── Advanced Graph
                ├── Advanced DP
                └── Backtracking
```

The goal:

```
RECOGNIZE
   +
KNOW BASIC TEMPLATE
   +
DON'T PANIC
```

═══════════════════════════════════════════════════════════════

# 36. MATRIX — ROW SUM / COLUMN SUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Given:

```
N × M matrix
```

Find:

```
row sums
column sums
maximum row
maximum column
```

## INTUITION

A matrix is simply:

```
ARRAY OF ARRAYS
```

So:

```
matrix[i][j]
```

means:

```
row i
column j
```

## ROW SUM

Fix:

```
i
```

and move:

```
j

for(int i = 0; i < n; i++) {

    int sum = 0;

    for(int j = 0; j < m; j++) {
        sum += a[i][j];
    }

    cout << sum << " ";
}
```

## COLUMN SUM

Fix:

```
j
```

and move:

```
i

for(int j = 0; j < m; j++) {

    int sum = 0;

    for(int i = 0; i < n; i++) {
        sum += a[i][j];
    }

    cout << sum << " ";
}
```

## CORE IDEA

ROW:

```
outer → row
inner → columns
```

COLUMN:

```
outer → column
inner → rows
```

## RECOGNITION

Words:

```
row sum
column sum
row average
column average
highest row
```

Think:

```
2D ARRAY TRAVERSAL
```

## COMPLEXITY

```
Time: O(N*M)
Space: O(1)
```

═══════════════════════════════════════════════════════════════

# 37. MATRIX TRACE / DIAGONAL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

For a square matrix:

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
1 + 5 + 9 = 15
```

## INTUITION

Main diagonal has:

```
row == column
```

Therefore:

```
a[i][i]
```

## CODE

```
int trace = 0;

for(int i = 0; i < n; i++)
    trace += a[i][i];
```

## SECONDARY DIAGONAL

Positions:

```
a[0][n-1]
a[1][n-2]
a[2][n-3]
```

Pattern:

```
j = n - 1 - i
```

## CODE

```
int sum = 0;

for(int i = 0; i < n; i++)
    sum += a[i][n - 1 - i];
```

## RECOGNITION

"diagonal"

Think:

```
MAIN:
a[i][i]

SECONDARY:
a[i][n-1-i]
```

## RECENT TCS CONNECTION

Matrix trace has been reported in recent 2026 NQT candidate recalls.

Therefore this is worth knowing.

═══════════════════════════════════════════════════════════════

# 38. MATRIX TRANSPOSE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Transpose:

```
rows ↔ columns
```

Example:

```
1 2 3
4 5 6
```

becomes:

```
1 4
2 5
3 6
```

## INTUITION

Original:

```
a[i][j]
```

becomes:

```
a[j][i]
```

## CODE

For a new matrix:

```
vector<vector<int>> t(m,
                      vector<int>(n));

for(int i = 0; i < n; i++) {

    for(int j = 0; j < m; j++) {

        t[j][i] = a[i][j];
    }
}
```

## RECOGNITION

"transpose"

immediately:

```
row ↔ column

a[i][j]
   ↓
a[j][i]
```

## SIMILAR

```
Matrix reflection
Matrix rotation
Diagonal operations
```

═══════════════════════════════════════════════════════════════

# 39. MATRIX ROTATION — BASIC IDEA

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Rotate square matrix 90° clockwise.

## INTUITION

A very useful relationship:

```
90° clockwise
    =
TRANSPOSE
    +
REVERSE EACH ROW
```

## STEPS

STEP 1:

```
Transpose
```

STEP 2:

```
Reverse every row
```

## CODE

```
// transpose

for(int i = 0; i < n; i++) {
    for(int j = i + 1; j < n; j++) {
        swap(a[i][j], a[j][i]);
    }
}

// reverse each row

for(int i = 0; i < n; i++) {
    reverse(a[i].begin(), a[i].end());
}
```

## MEMORY TRICK

CLOCKWISE:

```
TRANSPOSE
   ↓
REVERSE ROWS
```

COUNTER-CLOCKWISE:

```
REVERSE ROWS
   ↓
TRANSPOSE
```

## PRIORITY

Know the idea.

Don't spend a lot of time practicing variants tonight.

═══════════════════════════════════════════════════════════════

# MATRIX MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MATRIX
│
├── Every cell
│      └── Nested loops
│
├── Row operation
│      └── Fix i, vary j
│
├── Column operation
│      └── Fix j, vary i
│
├── Main diagonal
│      └── a[i][i]
│
├── Secondary diagonal
│      └── a[i][n-1-i]
│
├── Transpose
│      └── a[i][j] → a[j][i]
│
└── Rotate 90°
└── Transpose + Reverse rows

═══════════════════════════════════════════════════════════════

# 40. STACK — BASIC CONCEPT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## CORE IDEA

Stack:

```
LIFO
```

Last In:

```
First Out
```

Think:

```
pile of plates
```

Operations:

```
push()
pop()
top()
empty()
```

## C++

```
stack<int> st;

st.push(x);

st.top();

st.pop();

st.empty();
```

## RECOGNITION

Use stack when the question involves:

```
reverse processing
matching pairs
nested structures
most recent unfinished thing
previous greater/smaller
expression evaluation
```

═══════════════════════════════════════════════════════════════

# 41. BALANCED PARENTHESES

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Examples:

```
()
{}
[]
```

Valid:

```
({[]})
```

Invalid:

```
([)]
```

## INTUITION

When opening bracket appears:

```
remember it
```

When closing bracket appears:

```
it must match the MOST RECENT opening bracket
```

"MOST RECENT"

immediately suggests:

```
STACK
```

## CODE

```
stack<char> st;

for(char c : s) {

    if(c == '(' ||
       c == '{' ||
       c == '[') {

        st.push(c);
    }

    else {

        if(st.empty()) {
            cout << "NO";
            return;
        }

        char top = st.top();
        st.pop();

        if((c == ')' && top != '(') ||
           (c == '}' && top != '{') ||
           (c == ']' && top != '[')) {

            cout << "NO";
            return;
        }
    }
}

cout << (st.empty() ? "YES" : "NO");
```

## RECOGNITION

Words:

```
balanced
matching brackets
parentheses
nested brackets
```

Think:

```
STACK
```

## SIMILAR

```
HTML/XML matching
Nested expressions
Remove adjacent pairs
Expression parsing
```

═══════════════════════════════════════════════════════════════

# 42. POSTFIX / REVERSE POLISH NOTATION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Example:

```
2 3 + 4 *
```

means:

```
(2 + 3) * 4
```

Answer:

```
20
```

## INTUITION

When number:

```
PUSH
```

When operator:

```
POP TWO

b = top
pop

a = top
pop
```

Then:

```
a operator b
```

Push result.

## CODE

For tokenized input:

```
stack<int> st;

for(string token : tokens) {

    if(isNumber(token)) {

        st.push(stoi(token));
    }

    else {

        int b = st.top();
        st.pop();

        int a = st.top();
        st.pop();

        int result;

        if(token == "+")
            result = a + b;

        else if(token == "-")
            result = a - b;

        else if(token == "*")
            result = a * b;

        else
            result = a / b;

        st.push(result);
    }
}

cout << st.top();
```

## CRITICAL TRICK

For:

```
a - b
```

ORDER MATTERS.

If you pop:

```
b first
a second
```

calculate:

```
a - b
```

NOT:

```
b - a
```

Same for division.

## RECENT TCS CONNECTION

Postfix / Reverse Polish Notation has been reported in recent 2026 candidate experiences.

Therefore know this pattern.

═══════════════════════════════════════════════════════════════

# 43. NEXT GREATER ELEMENT — BASIC STACK PATTERN

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION

For each element, find the first greater element to its right.

Example:

```
[4,5,2,10]
```

Answer:

```
[5,10,10,-1]
```

## BRUTE FORCE

For every element:

```
scan right
```

O(N²)

## OPTIMAL INTUITION

Maintain elements that haven't found their greater element.

When current x arrives:

```
While stack top < x
```

those stack elements have found their answer.

Therefore:

```
MONOTONIC STACK
```

## CODE

```
vector<int> ans(n, -1);

stack<int> st;

for(int i = n - 1; i >= 0; i--) {

    while(!st.empty() &&
          st.top() <= a[i]) {

        st.pop();
    }

    if(!st.empty())
        ans[i] = st.top();

    st.push(a[i]);
}
```

## RECOGNITION

Words:

```
next greater
next smaller
nearest greater
nearest smaller
```

Think:

```
MONOTONIC STACK
```

## PRIORITY

Understand the pattern.

Don't spend an hour on every monotonic-stack variant.

═══════════════════════════════════════════════════════════════

# STACK MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STACK
│
├── Matching brackets
│      └── Push opening / Pop matching
│
├── Postfix expression
│      └── Push operands / Pop two
│
├── Next greater
│      └── Monotonic stack
│
├── Next smaller
│      └── Monotonic stack
│
└── Nested processing
└── Most recent item first

═══════════════════════════════════════════════════════════════

# 44. RECURSION — BASIC IDEA

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHAT IS RECURSION?

A function calls itself.

Every recursive problem needs:

```
BASE CASE
    +
SMALLER SUBPROBLEM
```

## TEMPLATE

```
returnType solve(parameters) {

    if(baseCase)
        return answer;

    return solve(smallerProblem);
}
```

## TWO QUESTIONS

Whenever you see recursion:

```
1. When should I STOP?

2. How do I make the problem smaller?
```

If you cannot answer both:

```
recursion is not ready.
```

═══════════════════════════════════════════════════════════════

# 45. FACTORIAL — RECURSION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## DEFINITION

```
n! = n × (n-1)!
```

Base:

```
0! = 1
1! = 1
```

## CODE

```
long long fact(int n) {

    if(n <= 1)
        return 1;

    return n * fact(n - 1);
}
```

## STRUCTURE

```
fact(n)
   ↓
n * fact(n-1)
          ↓
       smaller
          ↓
        base
```

## RECOGNITION

If problem naturally says:

```
F(n) depends on F(n-1)
```

think:

```
RECURSION
```

═══════════════════════════════════════════════════════════════

# 46. FIBONACCI — RECURSION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## DEFINITION

```
F(n) = F(n-1) + F(n-2)
```

Base:

```
F(0) = 0
F(1) = 1
```

## CODE

```
int fib(int n) {

    if(n <= 1)
        return n;

    return fib(n-1) + fib(n-2);
}
```

## IMPORTANT

This naive recursion is:

```
O(2^N)
```

It is useful for understanding recursion.

For efficient solution:

```
DP / iterative
```

## ITERATIVE

```
int a = 0;
int b = 1;

for(int i = 2; i <= n; i++) {

    int c = a + b;

    a = b;
    b = c;
}
```

## TCS TRICK

If question simply asks:

```
print Fibonacci
```

don't unnecessarily use recursive exponential solution.

Use iterative.

═══════════════════════════════════════════════════════════════

# 47. TREE — BASIC REPRESENTATION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## NODE

Typical binary tree node:

```
struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int x) {
        data = x;
        left = right = nullptr;
    }
};
```

## TREE

```
         1
        / \
       2   3
      / \
     4   5
```

Every node can have:

```
left child
right child
```

## KEY IDEA

A tree is naturally recursive.

Every subtree is itself a tree.

Therefore:

```
RECURSION
    +
TREE
```

═══════════════════════════════════════════════════════════════

# 48. TREE DFS TRAVERSALS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PREORDER

Order:

```
ROOT
LEFT
RIGHT
```

Code:

```
void preorder(Node* root) {

    if(root == nullptr)
        return;

    cout << root->data << " ";

    preorder(root->left);

    preorder(root->right);
}
```

## INORDER

Order:

```
LEFT
ROOT
RIGHT
```

Code:

```
void inorder(Node* root) {

    if(root == nullptr)
        return;

    inorder(root->left);

    cout << root->data << " ";

    inorder(root->right);
}
```

## POSTORDER

Order:

```
LEFT
RIGHT
ROOT
```

Code:

```
void postorder(Node* root) {

    if(root == nullptr)
        return;

    postorder(root->left);

    postorder(root->right);

    cout << root->data << " ";
}
```

## MEMORY TRICK

PRE:

```
ROOT comes PREviously
```

IN:

```
ROOT comes IN the middle
```

POST:

```
ROOT comes POST
```

## RECOGNITION

Traversal question:

```
DFS + recursion
```

═══════════════════════════════════════════════════════════════

# 49. TREE BFS / LEVEL ORDER

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION PATTERN

Process tree:

```
level by level
```

Example:

```
         1
        / \
       2   3
      / \
     4   5
```

Output:

```
1 2 3 4 5
```

## INTUITION

Need to process the earliest discovered node first.

That's:

```
QUEUE
```

## CODE

```
queue<Node*> q;

q.push(root);

while(!q.empty()) {

    Node* node = q.front();
    q.pop();

    cout << node->data << " ";

    if(node->left)
        q.push(node->left);

    if(node->right)
        q.push(node->right);
}
```

## RECOGNITION

Words:

```
level order
level by level
minimum depth
shortest path in unweighted tree
```

Think:

```
BFS + QUEUE
```

## MINIMUM DEPTH

At each level:

```
if node has no children
```

return current depth.

BFS finds the first leaf level.

## RECENT TCS CONNECTION

Minimum depth of binary tree has been reported in recent 2026 NQT question recalls.

═══════════════════════════════════════════════════════════════

# 50. TREE HEIGHT / MAX DEPTH

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## INTUITION

Height of tree:

```
1 + max(
        left height,
        right height
      )
```

## CODE

```
int height(Node* root) {

    if(root == nullptr)
        return 0;

    return 1 +
        max(height(root->left),
            height(root->right));
}
```

## RECOGNITION

Words:

```
height
depth
longest root-to-leaf path
```

Think:

```
TREE RECURSION
```

## COMPLEXITY

```
Time: O(N)
```

because each node is visited once.

═══════════════════════════════════════════════════════════════

# TREE MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TREE
│
├── Traversal
│      │
│      ├── Preorder
│      │      └── ROOT LEFT RIGHT
│      │
│      ├── Inorder
│      │      └── LEFT ROOT RIGHT
│      │
│      └── Postorder
│             └── LEFT RIGHT ROOT
│
├── Level order
│      └── BFS + Queue
│
├── Height
│      └── 1 + max(left,right)
│
└── Minimum depth
└── BFS is natural

═══════════════════════════════════════════════════════════════

# 51. GRAPH — BASIC DFS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## GRAPH

Nodes:

```
vertices
```

Connections:

```
edges
```

Example:

```
1 — 2
|   |
3 — 4
```

## DFS INTUITION

Go as deep as possible.

Then backtrack.

## CODE

```
void dfs(int node,
        vector<vector<int>>& adj,
        vector<int>& vis) {

    vis[node] = 1;

    for(int next : adj[node]) {

        if(!vis[next]) {
            dfs(next, adj, vis);
        }
    }
}
```

## RECOGNITION

Words:

```
connected components
reachability
explore graph
path exists
visit all nodes
```

Think:

```
DFS / BFS
```

═══════════════════════════════════════════════════════════════

# 52. GRAPH — BFS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## INTUITION

Explore:

```
nearest nodes first
```

Use:

```
QUEUE
```

## CODE

```
queue<int> q;

vector<int> vis(n, 0);

q.push(start);

vis[start] = 1;

while(!q.empty()) {

    int node = q.front();
    q.pop();

    for(int next : adj[node]) {

        if(!vis[next]) {

            vis[next] = 1;

            q.push(next);
        }
    }
}
```

## RECOGNITION

If question asks:

```
shortest path in UNWEIGHTED graph
minimum number of edges
level-wise exploration
```

think:

```
BFS
```

═══════════════════════════════════════════════════════════════

# 53. CYCLE DETECTION — BASIC RECOGNITION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## UNDIRECTED GRAPH

Typical DFS idea:

For current node:

```
visit neighbor
```

If neighbor is already visited AND:

```
neighbor != parent
```

then:

```
cycle exists
```

## CORE CODE

```
bool dfs(int node,
         int parent,
         vector<vector<int>>& adj,
         vector<int>& vis) {

    vis[node] = 1;

    for(int next : adj[node]) {

        if(!vis[next]) {

            if(dfs(next,
                   node,
                   adj,
                   vis))
                return true;
        }

        else if(next != parent) {
            return true;
        }
    }

    return false;
}
```

## RECOGNITION

Words:

```
cycle
circular dependency
loop in undirected graph
```

Think:

```
DFS + parent
```

## PRIORITY

Know the idea.

Don't spend too much time on advanced graph variations tonight.

═══════════════════════════════════════════════════════════════

# 54. MST — KRUSKAL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHY KNOW THIS?

MST has appeared in reported TCS NQT coding experiences.

You don't need to become a graph expert tonight.

You need to recognize:

```
"minimum total edge cost connecting all vertices"
```

as:

```
MST
```

## KRUSKAL INTUITION

Sort edges by weight.

Then:

```
take smallest edge
```

BUT:

```
don't create cycle.
```

How do we detect whether two nodes are already connected?

```
DSU / Union-Find
```

## PROCESS

```
Sort edges
    ↓
smallest first
    ↓
same component?
   / \
 YES  NO
  │    │
skip  take
       │
     union
```

## CORE STRUCTURE

```
sort(edges.begin(), edges.end());

for(edge : edges) {

    if(find(u) != find(v)) {

        take edge;

        union(u, v);

        total += weight;
    }
}
```

## RECOGNITION

Words:

```
connect all cities
minimum cost
all nodes connected
minimum total wiring
minimum network cost
```

Think:

```
MST
```

## IMPORTANT

MST is NOT:

```
shortest path from one source
```

MST:

```
connect ALL vertices
minimum total cost
```

═══════════════════════════════════════════════════════════════

# 55. DP — THE ONLY BASIC IDEA YOU NEED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## WHAT IS DP?

Dynamic Programming is:

```
solve overlapping subproblems once
    +
store their answers
```

## TWO QUESTIONS

When considering DP:

```
1. What is my STATE?

2. What is my TRANSITION?
```

Example Fibonacci:

```
dp[i] = dp[i-1] + dp[i-2]
```

## DP STORY

Big problem
↓
Smaller problems
↓
Repeated work?
↓
Store answer
↓
Reuse

═══════════════════════════════════════════════════════════════

# 56. CLIMBING STAIRS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION

You can climb:

```
1 step
OR
2 steps
```

How many ways to reach step N?

## INTUITION

To reach step N:

You must come from:

```
N-1
```

or:

```
N-2
```

Therefore:

```
dp[n] =
    dp[n-1] +
    dp[n-2]
```

## BASE CASE

```
dp[0] = 1
dp[1] = 1
```

## CODE

```
int a = 1;
int b = 1;

for(int i = 2; i <= n; i++) {

    int c = a + b;

    a = b;
    b = c;
}

cout << b;
```

## RECOGNITION

Words:

```
number of ways
one or two steps
reach nth step
```

Think:

```
FIBONACCI-LIKE DP
```

═══════════════════════════════════════════════════════════════

# 57. HOUSE ROBBER — BASIC DP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION

Choose houses to maximize money.

BUT:

```
cannot choose adjacent houses.
```

## INTUITION

At every house:

```
TAKE
```

or:

```
SKIP
```

If take current:

```
previous house cannot be taken.
```

Therefore:

```
dp[i] =
    max(
        dp[i-1],
        dp[i-2] + a[i]
    )
```

## CODE

```
int prev2 = 0;
int prev1 = 0;

for(int x : a) {

    int take = prev2 + x;

    int skip = prev1;

    int cur = max(take, skip);

    prev2 = prev1;
    prev1 = cur;
}

cout << prev1;
```

## RECOGNITION

Words:

```
choose maximum
cannot take adjacent
select non-adjacent elements
```

Think:

```
TAKE / SKIP DP
```

## IMPORTANT

This pattern is more useful than memorizing "House Robber."

═══════════════════════════════════════════════════════════════

# 58. 0/1 KNAPSACK — RECOGNITION ONLY

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION STRUCTURE

You have:

```
items
weights
values
capacity
```

Each item:

```
TAKE once
OR
DON'T TAKE
```

## INTUITION

Every item gives two choices:

```
TAKE
   ↓
capacity decreases
```

OR

```
SKIP
   ↓
capacity unchanged
```

## STATE

```
dp[i][capacity]
```

means:

```
best answer using first i items
with this capacity
```

## TRANSITION

```
skip = dp[i-1][w]

take =
    value[i] +
    dp[i-1][w-weight[i]]
```

Then:

```
max(take, skip)
```

## RECOGNITION

Words:

```
choose items
weight
value
capacity
each item at most once
```

Think:

```
0/1 KNAPSACK
```

## PRIORITY

For tonight:

```
RECOGNIZE
```

Don't spend excessive time on all knapsack variants.

═══════════════════════════════════════════════════════════════

# 59. SUBSET SUM — RECOGNITION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QUESTION

Can some subset of numbers produce:

```
target?
```

## INTUITION

For every number:

```
TAKE
OR
SKIP
```

Therefore DP.

## STATE

```
dp[i][sum]
```

means:

```
Can we make sum
using first i elements?
```

## TRANSITION

```
skip
```

OR

```
take
```

## RECOGNITION

Words:

```
subset
target sum
choose some elements
possible or impossible
```

Think:

```
SUBSET SUM DP
```

═══════════════════════════════════════════════════════════════

# DP MASTER MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DP
│
├── Fibonacci
│      └── Previous 2 states
│
├── Climbing Stairs
│      └── dp[i-1] + dp[i-2]
│
├── House Robber
│      └── TAKE / SKIP
│
├── Knapsack
│      └── TAKE / SKIP + CAPACITY
│
└── Subset Sum
└── TAKE / SKIP + TARGET

═══════════════════════════════════════════════════════════════

# 60. TCS Q2 EMERGENCY RECOGNITION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If Q2 looks unfamiliar, DON'T PANIC.

Read the question and look for these keywords.

───────────────────────────────────────────────────────────────

"MATRIX"

```
↓
```

2D ARRAY

```
↓
```

Nested loops
row / column / diagonal

───────────────────────────────────────────────────────────────

"BALANCED BRACKETS"

```
↓
```

STACK

───────────────────────────────────────────────────────────────

"POSTFIX / RPN"

```
↓
```

STACK

───────────────────────────────────────────────────────────────

"NEXT GREATER"

```
↓
```

MONOTONIC STACK

───────────────────────────────────────────────────────────────

"TREE LEVEL BY LEVEL"

```
↓
```

BFS + QUEUE

───────────────────────────────────────────────────────────────

"TREE HEIGHT"

```
↓
```

DFS / RECURSION

───────────────────────────────────────────────────────────────

"SHORTEST PATH — UNWEIGHTED"

```
↓
```

BFS

───────────────────────────────────────────────────────────────

"CONNECTED COMPONENTS"

```
↓
```

DFS / BFS

───────────────────────────────────────────────────────────────

"MINIMUM COST TO CONNECT EVERYTHING"

```
↓
```

MST

───────────────────────────────────────────────────────────────

"NUMBER OF WAYS"

```
↓
```

DP POSSIBILITY

───────────────────────────────────────────────────────────────

"TAKE OR SKIP"

```
↓
```

DP

───────────────────────────────────────────────────────────────

"WEIGHT + VALUE + CAPACITY"

```
↓
```

KNAPSACK

───────────────────────────────────────────────────────────────

# 61. WHAT NOT TO STUDY TONIGHT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DO NOT go deep into:

```
❌ Dijkstra
❌ Bellman-Ford
❌ Floyd-Warshall
❌ Topological sort variants
❌ Segment tree
❌ Fenwick tree
❌ Trie
❌ Advanced graph algorithms
❌ Advanced DP optimization
❌ Digit DP
❌ Bitmask DP
❌ Advanced backtracking
❌ Complex tree DP
❌ Heavy-light decomposition
❌ Advanced linked-list tricks
```

Why?

Because:

```
TIME LEFT IS LIMITED
```

Your objective is:

```
EXPECTED SCORE
```

not:

```
COMPLETE DSA MASTERY
```

═══════════════════════════════════════════════════════════════

# COMPLETE TCS NQT PATTERN MAP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                     TCS CODING
                          │
    ┌─────────────────────┼─────────────────────┐
    │                     │                     │
  ARRAY                 STRING                NUMBER
    │                     │                     │
    ├── Traversal         ├── Traversal         ├── Digits
    ├── Sorting           ├── Frequency         ├── Prime
    ├── Hashing           ├── Palindrome        ├── GCD
    ├── Two Pointer       ├── Anagram           └── LCM
    ├── Kadane            ├── Sliding Window
    ├── Search            └── Filtering
    └── Matrix
    │
    └─────────────────────────────────────────────
                          │
                     CORE PATTERNS
                          │
    ┌──────────┬──────────┼──────────┬─────────────┐
    │          │          │          │             │
  SORT       HASH       TWO PTR   WINDOW        SEARCH
    │          │          │          │             │
    └──────────┴──────────┴──────────┴─────────────┘
                          │
                          ▼
                     Q2 PATTERNS
                          │
         ┌────────────────┼────────────────┐
         │                │                │
       STACK            TREE             DP
         │                │                │
      Brackets         BFS/DFS         Take/Skip
      RPN              Height          Knapsack
      NGE              Depth           Subset
         │                │                │
         └────────────────┼────────────────┘
                          │
                          ▼
                     GRAPH
                          │
                     BFS / DFS
                          │
                         MST
```

═══════════════════════════════════════════════════════════════

# THE 10 PATTERNS THAT MATTER MOST

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If you forget everything else, remember these:

```
1. ARRAY TRAVERSAL
   ↓
   one pass / maintain answer

2. HASHING
   ↓
   frequency / lookup / duplicate

3. SORTING
   ↓
   arrange first, then solve

4. TWO POINTER
   ↓
   left + right

5. SEARCH
   ↓
   unsorted = linear
   sorted = binary

6. SLIDING WINDOW
   ↓
   continuous segment

7. DIGIT PROCESSING
   ↓
   %10 and /10

8. STACK
   ↓
   most recent unfinished thing

9. BFS / DFS
   ↓
   graph/tree traversal

10. DP
    ↓
    state + transition
```

═══════════════════════════════════════════════════════════════

# ULTIMATE TCS QUESTION → PATTERN TRANSLATOR

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

"Find largest"
↓
MAX

"Find second largest"
↓
TWO VARIABLES

"Find duplicate"
↓
HASHSET

"Count occurrences"
↓
HASHMAP

"Two numbers add to X"
↓
TWO SUM

"Array is sorted + find target"
↓
BINARY SEARCH

"Array is sorted + merge"
↓
TWO POINTER

"Reverse"
↓
TWO POINTER

"Palindrome"
↓
TWO POINTER

"Maximum contiguous sum"
↓
KADANE

"Exactly K consecutive"
↓
FIXED WINDOW

"Longest valid continuous"
↓
VARIABLE WINDOW

"First occurrence"
↓
LINEAR SEARCH

"Digits"
↓
%10 /10

"Prime"
↓
SQRT DIVISIBILITY

"GCD"
↓
EUCLIDEAN

"Matrix"
↓
NESTED LOOPS

"Diagonal"
↓
i,i OR i,n-1-i

"Balanced brackets"
↓
STACK

"Postfix"
↓
STACK

"Next greater"
↓
MONOTONIC STACK

"Tree level order"
↓
BFS

"Tree height"
↓
DFS

"Shortest unweighted path"
↓
BFS

"Connected components"
↓
DFS/BFS

"Minimum cost connect all"
↓
MST

"Number of ways"
↓
DP

"Take or skip"
↓
DP

"Weight + value + capacity"
↓
KNAPSACK

═══════════════════════════════════════════════════════════════

# FINAL EXAM-DAY CODING DECISION TREE

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

```
                READ QUESTION
                     │
                     ▼
            WHAT IS THE DATA?
                     │
    ┌────────────────┼────────────────┐
    │                │                │
  ARRAY            STRING           NUMBER
    │                │                │
    ▼                ▼                ▼
 What word?       What word?       Digits?
    │                │                │
```

┌────┼────┐      ┌────┼────┐          ▼
│    │    │      │    │    │       %10 /10
max  pair sort   freq reverse longest
│    │    │      │      │      │
MAX  HASH SORT   HASH  TWO PTR WINDOW
│
└──────────────┐
▼
SEARCH?
/       
sorted     unsorted
│           │
▼           ▼
BINARY       LINEAR

If ARRAY/STRING/NUMBER doesn't fit:

```
                     ▼

                  MATRIX?
                     │
                     ▼
                NESTED LOOPS

                     ↓

                   STACK?
                     │
              ┌──────┼──────┐
              │      │      │
           bracket  RPN     NGE

                     ↓

                   TREE?
                     │
              ┌──────┴──────┐
              │             │
            level         depth
              │             │
             BFS           DFS

                     ↓

                   GRAPH?
                     │
          ┌──────────┼──────────┐
          │          │          │
         BFS        DFS        MST

                     ↓

                    DP?
                     │
              ┌──────┼──────┐
              │      │      │
            ways   take/skip  capacity
```

═══════════════════════════════════════════════════════════════

# FINAL "DON'T GET FOOLED" RULES

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. "SUBARRAY"

   means CONTIGUOUS.

2. "SUBSEQUENCE"

   does NOT necessarily mean contiguous.

3. "SORTED ARRAY"

   immediately consider:

   ```
    Binary Search
    Two Pointer
   ```

4. "FREQUENCY"

   immediately consider:

   ```
    HashMap / frequency array
   ```

5. "FIRST"

   often means:

   ```
    scan from left
    stop at first valid answer
   ```

6. "LONGEST CONTINUOUS"

   consider:

   ```
    Sliding Window
   ```

7. "MAXIMUM CONTIGUOUS SUM"

   consider:

   ```
    Kadane
   ```

8. "DIGITS"

   think:

   ```
    %10
    /10
   ```

9. "BALANCED"

   consider:

   ```
    Stack
   ```

10. "LEVEL ORDER"

    think:

    ```
    BFS
    ```

11. "MINIMUM COST TO CONNECT ALL"

    think:

    ```
    MST
    ```

12. "TAKE OR SKIP"

    think:

    ```
    DP
    ```

═══════════════════════════════════════════════════════════════

# FINAL MASTER REVISION ORDER FOR TONIGHT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DO NOT revise in random order.

Use this exact order:

```
    1
    │
    ▼
ARRAY TRAVERSAL
    │
    ▼
HASHING
    │
    ▼
SORTING
    │
    ▼
TWO POINTER
    │
    ▼
STRING
    │
    ▼
NUMBER / DIGITS
    │
    ▼
SEARCH
    │
    ▼
SLIDING WINDOW
    │
    ▼
MATRIX
    │
    ▼
STACK
    │
    ▼
TREE BFS/DFS
    │
    ▼
BASIC DP
    │
    ▼
GRAPH / MST RECOGNITION
```

═══════════════════════════════════════════════════════════════

# THE REAL GOAL

Tomorrow, TCS may change:

```
story
variable names
input format
constraints
examples
wording
```

But underneath, the problem will still often be:

```
ARRAY
   +
SORT
```

or:

```
STRING
   +
HASHMAP
```

or:

```
ARRAY
   +
TWO POINTER
```

or:

```
STRING
   +
SLIDING WINDOW
```

or:

```
NUMBER
   +
DIGITS
```

or:

```
STACK
   +
EXPRESSION
```

or:

```
TREE
   +
BFS/DFS
```

or:

```
DP
   +
TAKE/SKIP
```

Therefore:

```
         DON'T MEMORIZE QUESTIONS.

                 MEMORIZE:

              THE STRUCTURE.

                     ↓

                QUESTION
                     ↓
              REMOVE STORY
                     ↓
               FIND OPERATION
                     ↓
               IDENTIFY PATTERN
                     ↓
              APPLY TEMPLATE
                     ↓
                EDGE CASES
                     ↓
                   CODE
                     ↓
                  TEST
```

═══════════════════════════════════════════════════════════════

# END OF COMPLETE PATTERN NOTE

PART 1:
Array + Hashing + Two Pointer

PART 2:
String + Number/Digit + Sliding Window

PART 3:
Matrix + Stack + Recursion + Tree + Graph + DP

═══════════════════════════════════════════════════════════════
