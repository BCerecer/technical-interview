# ULTIMATE CHEATSHEET

## TECHNIQUES/ALGORITHMS
### Backtrack


### Binary Search
- Use Case:
	- Find elemnt in sorted array
- Code Example:

		int l = 0, r = arr.length - 1; 
        while (l <= r) { 
            int m = l + (r - l) / 2; 
            if (arr[m] == x) 
                return m; 
            if (arr[m] < x) 
                l = m + 1; 
            else
                r = m - 1; 
		}

- Time Complexity:
	- O(logn)


### Bit Manipulation
- Use Case:
	- multiplications/divitions involving multiples of 2
- Code Example:
		
		method( int num, int i )

		//Get Bit = returns true if bit@i = 1; else false
		return ( (num & (1 << i) ) != 0 );

		//Set Bit = sets bit@i = 1; returns new number
		return num | (1 << i);

		//Clear Bit = set bit@i = 0; returns new number
		return (num & (( ~(1 << i)) ));

- Notes:
	- ^ = XOR = eXclusive OR = only 1 when different bits
	- ~ = NOT = negation = opposite of current bits
	- signed integer = when integer right digit = 
	- 2's Comp = For positive numbers, left bit=0; other bits same
				 For negative numbers, left bit=1; write absolute value in bits; NOT bits; add 1 bit;
	- >> 1 = Shift all bits 1 space to right = / 2
	- >> 2 = Shift all bits 2 space to right = / 4
	- << 3 = Shift all bits 3 space to right = * 8



### Dynamic Programing
- Use Case:
	 - When pattern involves result of previous result
	 - Overlapping subproblems
- Notes
	 - Design for simple scenario, once it works test on complex


### Greedy Algorithms
- Definition: Algorithms that make optimal choice per iteration to achieve optimal solution
- Use Case:
	- Optimal local solution


### Recursion


### Two Pointers (sliding window)
- Use Case:
	- substring/subarray
	- sliding window
- Code Example:

		int i = 0, j = 0;
		while(scenario)			//j<ra.length
		{
			i++, j++;
		}

- Check:
	- Empty sequence
	- Sequence with 1 or 2 elements
	- Sequence with repeated elements
- Notes:
	- When using two pointers always use while NOT for loops!
	- The way you implement the while loop and its conditions will vary depending on problem

		
## DATA STRUCTURES
### Graphs
- Code Example:
		
		//Graph represented by adjacency list
		class Graph{
			public Node[] nodes;
		}

		class Node{
			public String name;
			public Node[] children;
		}
 - Notes: 
	 - Directed graphs explicitly tells the direction of which nodes are connected
	 - Undirected graphs have two way connection as long as nodes have one path
	 - Adjacency list is the most common/efficient way to represent a graph. Alternative: Adjacency Matrices

#### •Breadth First Search
- Use Case:
	 - Find shortest path between two nodes
- Code Example:

		public static <T> Optional<Node<T>> search(T value, Node<T> start) {
		    Queue<Node<T>> queue = new ArrayDeque<>();
		    queue.add(start);
		 
		    Node<T> currentNode;
		 
		    while (!queue.isEmpty()) {
			    currentNode = queue.remove();
			    LOGGER.info("Visited node with value: {}", currentNode.getValue());
			 
			    if (currentNode.getValue().equals(value)) {
			        return Optional.of(currentNode);
			    } else {
			        alreadyVisited.add(currentNode);
			        queue.addAll(currentNode.getNeighbors());
			        queue.removeAll(alreadyVisited);
			    }
			}
		 
		    return Optional.empty();
		}
		
- Time Complexity:
	- O(|V| + |E|)
- Notes:
	 - 

#### •Depth First Search
- Use Case:
	 - Preferred to visit every node in the graph (Simpler)
- Code Example:
		
		//Recursive version
		public void dfs(int start) {
		    boolean[] isVisited = new boolean[adjVertices.size()];
		    dfsRecursive(start, isVisited);
		}
		 
		private void dfsRecursive(int current, boolean[] isVisited) {
		    isVisited[current] = true;
		    visit(current);
		    for (int dest : adjVertices.get(current)) {
		        if (!isVisited[dest])
		            dfsRecursive(dest, isVisited);
		    }
		}

		//Iterative version
		public void dfsWithoutRecursion(int start) {
		    Stack<Integer> stack = new Stack<Integer>();
		    boolean[] isVisited = new boolean[adjVertices.size()];
		    stack.push(start);
		    while (!stack.isEmpty()) {
		        int current = stack.pop();
		        isVisited[current] = true;
		        visit(current);
		        for (int dest : adjVertices.get(current)) {
		            if (!isVisited[dest])
		                stack.push(dest);
		        }
		    }
		}

- Time Complexity:
	 - 
- Notes:
	 - 


### HashMap
- Use Case:
	- Count frequency of an element
	- Leverage finding in unsorted arrays
- Code Example:

		Map<Integer, Integer> hashmap = new HashMap();
		.clear()				//removes all mappings in map
		.containsKey(k)			//returns true if key exists
		.containsValue(v)		//returns true if value exists 
		.get(k)					//returns value of specified key, else null
		.getOrDefault(k, v)		//if value is assigned, returns value; //else, returns v	
		.isEmpty()				//return true if empty
		.put(k, v)				//inserts key and value
		.putIfAbsent(k, v)		//if key doesn't exist, inserts key and value //else nothing
		.remove(k)				//removes the value mapped to k, returns value
		.size()					//returns int size of hashmap
		.values()				//iterate by doing for(int val:map.values())

- Time Complexity:
	- Time		O(1)			//to look for values
	- Memory	O(n)			//elements inserted
- Notes
	- key = ra[index]; value = index
	- Most cases, check containsKey and then put

### HashSet
- Use Case:
	- Have unique
- Code Example:

		Set<Integer> hashset = new HashSet();
		.add(e)					//inserts element into hashset
		.clear()				//removes all elements of hashset
		.contains(o)			//returns true if element is in hashset
		.isEmpty()				//returns true if empty
		.remove(o)				//removes value from hashset, returns true if element was in set 
		.size()					//returns intsize of hashset



### Heaps
- Use Case:
	- Find the x largest(minHeap)/smallest(maxHeap) element
- Types:
	- Min Heap = each node its smaller or equal to its children (root is smallest element in heap)
	- Max Heap = each node its greater or equal to its children (root is greatest element in heap)
- Code Example:
	- Min Heap:

		PriorityQueue<Integer> minHeap = new PriorityQueue();

	- Max Heap:

		PriorityQueue<Integer> minHeap = new PriorityQueue(Collections.reverseOrder());
		.add(i);				//adds i
		.size();				//returns size of heap
		.remove();				//removes root, returns element
		.peek();				//returns root element

- Time Complexity:
	- Time:				O(n)			//to build
	- Access Max / Min: O(1)
	- Insert: 			O(log(n))
	- Remove Max / Min: O(log(n))
	- Memory:			O(n)			//elements inserted
- Notes
	- Element you want to return needs to be at root


### LinkedList
- Code Example:
		
		//reverse singly linkedlist
		ListNode prev = null;
		ListNode curr = head;
		while (curr != null) {
	        ListNode nextTemp = curr.next;
	        curr.next = prev;
	        prev = curr;
	        curr = nextTemp;
		}
		return prev;

- Time Complexity:
	- Iterate: O(n)
	- Recursive: O(n)
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)
- Memory Complexity:
	- Iterate: O(1)
	- Recursive: O(n)
- Notes:
	- Remember to use 3 pointers and move iteratively!
	- IMPORTANT: You can have a linkedlist with different pointers and return a different part depending on which pointer you return


### Queue
- Code Examples:

		Queue<Integer> q = new LinkedList<>();
		q.add(e);			//Inserts element and returns true iff it was successfull
		q.peek();			//Returns, but doesn't remove head of queue. Returns null, if queue empty
		q.poll();			//Returns, and removes head of queue. Returns null, if queue empty

- Time Complexity:
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)


### Stack
- Use Case
	- brackets
- Code Example:

		Stack<Integer> s = new Stack<Integer>();
		s.empty();			//Returns true if stack empty
		s.peek();			//Returns object at top of stack without removing it
		s.pop();			//Returns object at top of stack and removes it
		s.push();			//Pushes item to top of stack and returns it
		s.search();			//Returns position in stack from bottom to top. Returns -1 if not found

- Time Complexity
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)


### Trees
#### •Breadth First Search
- Code Example:
		
		//Iterative version
        Queue<Node> queue = new LinkedList<Node>(); 
        queue.add(root); 
        while (!queue.isEmpty())  
        { 
            Node current = queue.remove(); 
            //do
            if (current.left != null)
                queue.add(current.left); 
            if (current.right != null) 
                queue.add(current.right); 
        }

- Time Complexity:
	 - Traversal: O(n)
- Notes:
	 - Similar to queue

#### •Depth First Search
- Use Case:
	 - Preorder: Create copy of tree
	 - Postorder: Delete tree
- Code Example:
		
		//Recursive version
		void dfs(Node n){
			if(n == null)
				return;
			//do preorder: left node first
			dfs(n.left);
			//do inorder: root node first
			dfs(n.left);
			//do postorder: right node first
		}

		//Iterative versions
		public void traversePreOrderWithoutRecursion() {
		    Stack<Node> stack = new Stack<Node>();
		    Node current = root;
		    stack.push(root);
		    while(!stack.isEmpty()) {
		        current = stack.pop();
		        visit(current.value);
		         
		        if(current.right != null) {
		            stack.push(current.right);
		        }    
		        if(current.left != null) {
		            stack.push(current.left);
		        }
		    }        
		}

		public void traverseInOrderWithoutRecursion() {
		    Stack<Node> stack = new Stack<Node>();
		    Node current = root;
		    stack.push(root);
		    while(! stack.isEmpty()) {
		        while(current.left != null) {
		            current = current.left;                
		            stack.push(current);                
		        }
		        current = stack.pop();
		        visit(current.value);
		        if(current.right != null) {
		            current = current.right;                
		            stack.push(current);
		        }
		    }
		}

		public void traversePostOrderWithoutRecursion() {
		    Stack<Node> stack = new Stack<Node>();
		    Node prev = root;
		    Node current = root;
		    stack.push(root);
		 
		    while (!stack.isEmpty()) {
		        current = stack.peek();
		        boolean hasChild = (current.left != null || current.right != null);
		        boolean isPrevLastChild = (prev == current.right || (prev == current.left && current.right == null));
		 
		        if (!hasChild || isPrevLastChild) {
		            current = stack.pop();
		            visit(current.value);
		            prev = current;
		        } else {
		            if (current.right != null) {
		                stack.push(current.right);
		            }
		            if (current.left != null) {
		                stack.push(current.left);
		            }
		        }
		    }   
		}

 - Time Complexity:
	 - Traversal: O(n)
 - Notes: 
	 - Similar to stack
	 - Preorder: (Root, Left, Right) 
	 - Inorder: (Left, Root, Right)
	 - Postorder: (Left, Right, Root)
	 - Trees are connected graph without cycles

### Tries
- Use Case:
	 - Word/prefix lookups
	 - Longest Common Prefix
- Code Example:

		class TrieNode {
		    public char val;
		    public boolean isWord; 
		    public TrieNode[] children = new TrieNode[26];
		    public TrieNode() {}
		    TrieNode(char c){
		        TrieNode node = new TrieNode();
		        node.val = c;
		    }
		}

		public class Trie {
		    private TrieNode root;
		    public Trie() {
		        root = new TrieNode();
		        root.val = ' ';
		    }

		    public void insert(String word) {
		        TrieNode ws = root;
		        for(int i = 0; i < word.length(); i++){
		            char c = word.charAt(i);
		            if(ws.children[c - 'a'] == null){
		                ws.children[c - 'a'] = new TrieNode(c);
		            }
		            ws = ws.children[c - 'a'];
		        }
		        ws.isWord = true;
		    }

		    public boolean search(String word) {
		        TrieNode ws = root; 
		        for(int i = 0; i < word.length(); i++){
		            char c = word.charAt(i);
		            if(ws.children[c - 'a'] == null) return false;
		            ws = ws.children[c - 'a'];
		        }
		        return ws.isWord;
		    }

		    public boolean startsWith(String prefix) {
		        TrieNode ws = root; 
		        for(int i = 0; i < prefix.length(); i++){
		            char c = prefix.charAt(i);
		            if(ws.children[c - 'a'] == null) return false;
		            ws = ws.children[c - 'a'];
		        }
		        return true;
		    }
		}

- Time Complexity:
	 - Search/Insert/Delete: O(an)	//a = length of longest word, n = number of words
	 - Prefix Lookup: O(a)			//a = length of word
	 - Worst Case Runtime: O(mn)	//m = length of longest word, n = number of words
- Notes: 
	 - Root node is empty
	 - Add [* nodes (null nodes)/or set a value]  at end of each word
	 - Each node has 26 children (even if they're not used)
	 - Size of trie is directly correlated to alphabet used
	 - Null nodes take up space (a lot!). 26 children nodes per node

## TOOLS
### Arrays
- `Arrays.sort(array)										//Time O(nlogn)`
- `Arrays.sort(intervals, (a, b) -> a.start - b.start)		//Custom object Intervals[], .start returns value, lambda`
- Notes
	 - Array can be null or empty

### int
- NOO! 	`int a; 		if(a == null)`
- YES! 	`int a[]; 	if(a == null)`
- `a = s.charAt(0) != '0' ? 1 : 0;						//conditional question mark number assign`
- `Integer.valueOf(str);								//converts numbers in string to int(only works for string of numbers)`
- `Integer.MAX_VALUE = 2^31-1`
- `Integer.MIN_VALUE = -2^31`

### Math
- `Math.abs(x);`
- `Math.max(x, y);`
- `Math.min(x, y);`

### String
- `str = str.replaceAll("substring", "replacement");	//replaces substring for replacement`
- `str.indexOf('str');									//returns index of string(or char) in string`
- `str.contains('x');									//returns boolean depending if string has character inside`
- `str.length();										//returns lenght of string`
- `str.substring(6);									//returns substring after index (including)`
- `str.substring(0, 6);									//returns substring in between those indices (excluding last index)`
- `str.startsWtih('str')								//returns boolean of string(or char`
- `str.toCharArray()									`
- Notes
	 - Strings can be null or empty

### StringBuilder
- `StringBuilder str = new StringBuilder(i);			//initialize StringBuilder with i space; can create without i`
- `str.append(c);										//can append char, string, int representation, etc`
- `str.capacity();										//return current capacity`
- `str.charAt(i);										//return char value at index i`
- `str.delete(int l, int r);							//removes substring from index l to index r`
- `str.length();										//returns length`
- `str.replace(int l, int r, String strng);				//replaces characters from index l to index r with strng`
- `str.reverse();										//string gets replaced with reverse`
- `str.setCharAt(int i, char c);						//set character c at index i`
- `str.substring(int l, int r);							//return substring from index l to index r`
- `str.toString();										//return string representation of str`


## EXTRAS
### Sorting Algorithms

### Graph Algorithsm:
- #### Topological Sort
- #### Dijkstra's Algorithm
- #### Bellman-Ford Algorithm
- #### Floyd-Warshall Algorithm
- #### Prim's Algorithm
- #### Kruskal's Algorithm

