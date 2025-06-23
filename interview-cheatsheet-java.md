## Coding Interview Cheatsheet - Java

### ✅ Datatypes and Variables

```java
// Integer types
byte a = 10;                // -128 to 127
short b = 1000;             // -32,768 to 32,767
int c = 100000;             // -2^31 to 2^31-1
long d = 10000000000L;      // -2^63 to 2^63-1

// Floating point types
float e = 5.75f;            // ~±3.4e−38 to ±3.4e+38
double f = 19.99;           // ~±1.7e−308 to ±1.7e+308

// Character and Boolean
char g = 'A';               // Unicode: 0 to 65,535
boolean isJavaFun = true;   // true or false
```

---

### ✅ Conditionals

```java
if (x > 0) {
    System.out.println("positive");
} else if (x == 0) {
    System.out.println("zero");
} else {
    System.out.println("negative");
}

switch (day) {
    case 1: System.out.println("Mon"); break;
    default: System.out.println("Other");
}

int max = (a > b) ? a : b; // ternary

// Logical operators
if (a > 0 && b > 0) {
    System.out.println("Both positive");
} else if (a > 0 || b > 0) {
    System.out.println("At least one is positive");
} else if (!(a > 0)) {
    System.out.println("a is not positive");
}
```

---

### ✅ Loops

```java
for (int i = 0; i < 5; i++) {}
for (int n : array) {}
while (condition) {}
do {} while (condition);
```

---

### ✅ Arrays

```java
int[] nums = new int[5];
int[] fixed = {1, 2, 3};
int[][] grid = new int[3][3];

Arrays.fill(nums, 7); // nums = [7, 7, 7, 7, 7]
Arrays.sort(fixed);   // fixed = [1, 2, 3]
int idx = Arrays.binarySearch(fixed, 2); // idx = 1
String str = Arrays.toString(fixed);     // "[1, 2, 3]"

for (int i = 0; i < nums.length; i++) { System.out.print(nums[i] + " "); }
for (int num : nums) { System.out.print(num + " "); }
```

---

### ✅ List/ArrayList

```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
names.add("Charlie");
System.out.println(names);                // [Alice, Bob, Charlie]

names.remove("Bob");
System.out.println(names);                // [Alice, Charlie]

System.out.println(names.get(0));         // Alice
System.out.println(names.contains("Bob")); // false
System.out.println(names.size());         // 2

// Iteration using for-each
for (String name : names) {
    System.out.print(name + " ");         // Alice Charlie
}
```

---

### ✅ Strings

```java
String s = "hello world";
s.length();                 // 11
s.charAt(0);                // h
s.substring(1, 5);          // ello
s.toLowerCase();            // hello world
s.toUpperCase();            // HELLO WORLD
s.equals("hello");          // false
s.contains("world");        // true
s.startsWith("he");         // true
s.endsWith("ld");           // true
s.indexOf("l");             // 2
s.lastIndexOf("l");         // 9
s.replace("l", "L");        // heLLo worLd
s.isEmpty();                // false
String[] parts = s.split(" ");  // ["hello", "world"]
String joined = String.join("-", parts);
System.out.println(joined); // hello-world

StringBuilder sb = new StringBuilder();
sb.append("hi");
sb.append(" there");
System.out.println(sb.toString());  // hi there
```

---

### ✅ LinkedList

```java
LinkedList<Integer> list = new LinkedList<>();
list.addFirst(10);       // [10]
list.addLast(20);        // [10, 20]
list.add(15);            // [10, 20, 15]
list.removeFirst();      // [20, 15]
list.removeLast();       // [20]
System.out.println(list.get(0));       // 20
System.out.println(list.contains(20)); // true
System.out.println(list.size());       // 1

// Using for-each loop
for (int val : list) {
    System.out.print(val + " ");
}

// Using index-based loop
for (int i = 0; i < list.size(); i++) {
    System.out.print(list.get(i) + " ");
}

// Using iterator with while loop
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    System.out.print(it.next() + " ");
}

class ListNode {
    int val;
    ListNode next;

    ListNode(int x) {
        val = x;
    }
}

ListNode head = new ListNode(1) {
    next = new ListNode(2) {
        next = new ListNode(3)
    }
};

while (head != null) {
    System.out.print(head.val + " -> ");
    head = head.next;
}
```

---

### ✅ Stack

```java
Stack<Integer> stack = new Stack<>();
stack.push(10); // [10]
stack.push(20); // [10, 20]
stack.push(30); // [10, 20, 30]
System.out.println(stack.peek());       // 30
System.out.println(stack.pop());        // 30 => [10, 20]
System.out.println(stack.isEmpty());    // false

while (!stack.isEmpty()) {
    System.out.print(stack.pop() + " ");  // 20 10
}
```

---

### ✅ Queue / ArrayDeque

```java
Queue<String> q = new ArrayDeque<>();
q.offer("A");             // [A]
q.offer("B");             // [A, B]
q.offer("C");             // [A, B, C]
System.out.println(q.peek()); // A
System.out.println(q.poll()); // A => [B, C]
System.out.println(q.isEmpty()); // false

while (!q.isEmpty()) {
    System.out.print(q.poll() + " ");  // B C
}
```

---

### ✅ Set / HashSet

```java
Set<String> set = new HashSet<>();
set.add("apple");       // [apple]
set.add("banana");      // [apple, banana]
set.contains("apple");  // true
set.remove("banana");   // [apple]
System.out.println(set.size()); // 1

for (String s : set) {
    System.out.print(s + " ");
}
```

---

### ✅ TreeSet

```java
TreeSet<Integer> ts = new TreeSet<>();
ts.add(10);                // [10]
ts.add(5);                 // [5, 10]
ts.add(20);                // [5, 10, 20]
System.out.println(ts.first());     // 5
System.out.println(ts.last());      // 20
System.out.println(ts.floor(15));   // 10
System.out.println(ts.ceiling(15)); // 20

for (int val : ts) {
    System.out.print(val + " ");
}

TreeSet<Integer> desc = new TreeSet<>((a,b) -> b - a);
desc.add(5);
desc.add(10);
desc.add(1);
System.out.println(desc); // [10, 5, 1]
```

---

### ✅ Map / HashMap

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);    // {a=1}
map.put("b", 2);    // {a=1, b=2}
System.out.println(map.get("a"));           // 1
System.out.println(map.containsKey("b"));   // true
map.remove("b");    // {a=1}
System.out.println(map.size()); // 1

for (Map.Entry<String, Integer> e : map.entrySet()) {
    System.out.println(e.getKey() + " -> " + e.getValue());
}
```

---

### ✅ PriorityQueue

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.add(3);    // [3]
minHeap.add(1);    // [1, 3]
minHeap.add(2);    // [1, 3, 2]
System.out.println(minHeap.poll()); // 1 => [2, 3]

while (!minHeap.isEmpty()) {
    System.out.print(minHeap.poll() + " ");  // 2 3
}

PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a,b) -> b - a);
maxHeap.add(3);
maxHeap.add(1);
maxHeap.add(2);
System.out.println(maxHeap.poll()); // 3

while (!maxHeap.isEmpty()) {
    System.out.print(maxHeap.poll() + " ");  // 2 1
}

class Task {
    int deadline, duration;
    Task(int d, int t) { deadline = d; duration = t; }
}
PriorityQueue<Task> pq = new PriorityQueue<>((a,b) -> a.deadline - b.deadline);
```

---

### ✅ TrieNode and Trie

```java
class TrieNode {
    TrieNode[] children = new TrieNode[26];
    boolean isEnd;
}

class Trie {
    TrieNode root = new TrieNode();

    void insert(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (node.children[i] == null)
                node.children[i] = new TrieNode();

            node = node.children[i];
        }
        node.isEnd = true;
    }

    boolean search(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (node.children[i] == null)
                return false;

            node = node.children[i];
        }
        return node.isEnd;
    }

    void dfs(TrieNode node, String path) {
        if (node.isEnd)
            System.out.println(path);

        for (int i = 0; i < 26; i++) {
            if (node.children[i] != null) {
                dfs(node.children[i], path + (char)('a' + i));
            }
        }
    }
}

// Usage
Trie trie = new Trie();
trie.insert("cat");
trie.insert("car");
trie.insert("dog");
trie.dfs(trie.root, ""); // car, cat, dog
```

---

### ✅ TreeNode and Tree Traversal

```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}

// Create tree:
TreeNode root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
root.left.left = new TreeNode(4);
root.left.right = new TreeNode(5);

DFS (Pre-order):

void dfs(TreeNode root) {
    if (root == null) return;
    System.out.print(root.val + " ");
    dfs(root.left);
    dfs(root.right);
}

dfs(root); // 1 2 4 5 3

BFS (Level-order):

Queue<TreeNode> q = new LinkedList<>();
q.offer(root);

while (!q.isEmpty()) {
    TreeNode node = q.poll();
    System.out.print(node.val + " ");
    if (node.left != null) q.offer(node.left);
    if (node.right != null) q.offer(node.right);
}
// 1 2 3 4 5
```

---

### ✅ Graph using Adjacency List and BFS/DFS

```java
class GraphNode {
    int val;
    List<GraphNode> neighbors;
    GraphNode(int val) {
        this.val = val;
        neighbors = new ArrayList<>();
    }
}

// Create graph
GraphNode node0 = new GraphNode(0);
GraphNode node1 = new GraphNode(1);
GraphNode node2 = new GraphNode(2);
node0.neighbors.add(node1);
node0.neighbors.add(node2);
node1.neighbors.add(node2);

DFS:

Set<GraphNode> visited = new HashSet<>();
void dfs(GraphNode node) {
    if (node == null || visited.contains(node)) return;
    visited.add(node);
    System.out.print(node.val + " ");
    for (GraphNode nei : node.neighbors) {
        dfs(nei);
    }
}

dfs(node0); // 0 1 2

BFS:

Queue<GraphNode> q = new LinkedList<>();
Set<GraphNode> visitedBFS = new HashSet<>();
q.offer(node0);
visitedBFS.add(node0);

while (!q.isEmpty()) {
    GraphNode curr = q.poll();
    System.out.print(curr.val + " ");
    for (GraphNode nei : curr.neighbors) {
        if (!visitedBFS.contains(nei)) {
            visitedBFS.add(nei);
            q.offer(nei);
        }
    }
}
// 0 1 2
```

---

### ✅ Graph using Adjacency Matrix (DFS/BFS)

```java
void dfsMatrix(int[][] graph, int node, boolean[] visited) {
    if (visited[node]) return;
    visited[node] = true;
    System.out.print(node + " ");
    for (int i = 0; i < graph.length; i++) {
        if (graph[node][i] == 1 && !visited[i]) {
            dfsMatrix(graph, i, visited);
        }
    }
}

void bfsMatrix(int[][] graph, int start) {
    boolean[] visited = new boolean[graph.length];
    Queue<Integer> queue = new LinkedList<>();
    queue.offer(start);
    visited[start] = true;

    while (!queue.isEmpty()) {
        int node = queue.poll();
        System.out.print(node + " ");
        for (int i = 0; i < graph.length; i++) {
            if (graph[node][i] == 1 && !visited[i]) {
                queue.offer(i);
                visited[i] = true;
            }
        }
    }
}

// Usage:
int[][] graph = {
    {0, 1, 1, 0},
    {1, 0, 1, 1},
    {1, 1, 0, 0},
    {0, 1, 0, 0}
};
boolean[] visited = new boolean[4];
dfsMatrix(graph, 0, visited);  // 0 1 2 3
bfsMatrix(graph, 0);           // 0 1 2 3
```
