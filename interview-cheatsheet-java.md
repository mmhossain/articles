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
boolean isJavaFun = true;  // true or false
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

// Logical operators example
if (a > 0 && b > 0) {
    System.out.println("Both positive");
} else if (a > 0 || b > 0) {
    System.out.println("At least one is positive");
} else if (!(a > 0)) {
    System.out.println("a is not positive");
}
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
```
Iteration:
```java
for (int i = 0; i < nums.length; i++) { System.out.print(nums[i] + " "); }
for (int num : nums) { System.out.print(num + " "); }
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
System.out.println(list.get(0));        // 20
System.out.println(list.contains(20)); // true
System.out.println(list.size());       // 1
```
Iteration:
```java
for (int val : list) {
    System.out.print(val + " ");
}
```

---

### ✅ Stack
```java
Stack<Integer> stack = new Stack<>();
stack.push(10);                    // [10]
stack.push(20);                    // [10, 20]
System.out.println(stack.peek()); // 20
System.out.println(stack.pop());  // 20 => [10]
System.out.println(stack.isEmpty()); // false

for (int val : stack) {
    System.out.print(val + " ");
}
```

---

### ✅ Queue / ArrayDeque
```java
Queue<String> q = new ArrayDeque<>();
q.offer("A");             // [A]
q.offer("B");             // [A, B]
System.out.println(q.peek()); // A
System.out.println(q.poll()); // A => [B]
System.out.println(q.isEmpty()); // false

for (String s : q) {
    System.out.print(s + " ");
}
```

---

### ✅ Set / HashSet
```java
Set<String> set = new HashSet<>();
set.add("apple");               // [apple]
set.add("banana");              // [apple, banana]
System.out.println(set.contains("apple")); // true
set.remove("banana");           // [apple]
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
```
Custom:
```java
TreeSet<Integer> desc = new TreeSet<>((a,b)->b-a);
desc.add(5); desc.add(10); desc.add(1);
System.out.println(desc); // [10, 5, 1]
```

---

### ✅ Map / HashMap
```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);              // {a=1}
map.put("b", 2);              // {a=1, b=2}
System.out.println(map.get("a"));          // 1
System.out.println(map.containsKey("b")); // true
map.remove("b");              // {a=1}
System.out.println(map.size());           // 1

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

for (int val : minHeap) {
    System.out.print(val + " ");
}

PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a,b)->b-a);
maxHeap.add(3);
maxHeap.add(1);
maxHeap.add(2);
System.out.println(maxHeap.poll()); // 3
```

Custom object:
```java
class Task {
    int deadline, duration;
    Task(int d, int t) { deadline = d; duration = t; }
}
PriorityQueue<Task> pq = new PriorityQueue<>((a,b)->a.deadline - b.deadline);
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
            if (node.children[i] == null) node.children[i] = new TrieNode();
            node = node.children[i];
        }
        node.isEnd = true;
    }

    boolean search(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (node.children[i] == null) return false;
            node = node.children[i];
        }
        return node.isEnd;
    }

    void dfs(TrieNode node, String path) {
        if (node.isEnd) System.out.println(path);
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
trie.dfs(trie.root, ""); // Outputs: car, cat, dog
```

---
