# ULTIMATE CHEATSHEET FOR CODING INTERVIEW
***
## TECHNIQUES/ALGORITHMS
### Backtrack
- Definition:
	- Use recursion in order to explore all the possibilities until you get the best result for the problem
- Use Case:
	- Permutation/Combinations/Subsets to find all solutions possible being able to have different starts 
	- When need to explore different possibilities. Choose, Check, Undo
- Technique:
	- On recursive: 
		- At top, have an exit, found solution (we found a way to solved it)
		- Marked element as visited
		- Do recursiveness 
		- Since we returned, we didn't find solution; remove previously visited element mark
- Code Example:

		private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, int remain, int start){
		    if(remain < 0) return;										//check
		    else if(remain == 0) list.add(new ArrayList<>(tempList));	//check
		    else{ 
		        for(int i = start; i < nums.length; i++){				//choose
		            tempList.add(nums[i]);
		            backtrack(list, tempList, nums, remain - nums[i], i); // not i + 1 because we can reuse same elements
		            tempList.remove(tempList.size() - 1);				//undo
		        }
		    }
		}

- Notes: 
	- Sort array for permutations/combinations/subsets before sending it to helper method
***
### Binary Search
- Use Case:
	- Find element in sorted array
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

***
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
	- & = AND = when both are 1, result is 1
	- | =  OR = if 1 of them is 1, result is 1
	- ^ = XOR = eXclusive OR = only 1 when different bits
	- ~ = NOT = negation = opposite of current bits
	- signed integer = when left bit indicates that number is negative if it has 1, or positive if 0
	- 2's Comp = For positive numbers, left bit=0; other bits same
				 For negative numbers, left bit=1; write absolute value in bits; NOT bits; add 1 bit; `~n+1`
	- >> 1 = Shift all bits 1 space to right = / 2
	- >> 2 = Shift all bits 2 space to right = / 4
	- << 3 = Shift all bits 3 space to right = * 8
	- >>> unsigned shift
	- >> 	signed shift

***
### Dynamic Programing
- Definition:
	 - Tabulation: Bottom Up
	 - Memoization: Top Down
	 	- Combinations: +=
	 	- Min/Max: =
- Use Case:
	 - Optimization, MINIMIZE/MAXIMIZE 		- Math.min/max
	 - Distinct ways						- += dp[i-1] + 1 
	 - Merging intervals
	 - DP on String
	 - Decision Making
	 - When pattern involves result of previous result
	 - Problem can be divided into subproblems
- Code:

		//Tabulation:
		int fib(int n) { 
		    int f[] = new int[n+1]; 
		    f[0] = 0; 
		    f[1] = 1; 
		    for (int i = 2; i <= n; i++) {
				f[i] = f[i-1] + f[i-2]; 
			}
		    return f[n]; 
		}

		//Memoization:
		public static long fibArray[]=new long[26];
		public static long fibonacci(long n) {
			long fibValue=0;
			if(n==0 ) {
				return 0;
			} else if (n==1) {
				return 1;
			} else if (fibArray[(int)n]!=0){
				return fibArray[(int)n];
			} else {
				fibValue=fibonacci(n-1)+fibonacci(n-2);
				fibArray[(int) n]=fibValue;
				return fibValue;
			}
		}

- Memoization:
	- Technique: 
		- Have a way to store results (i.e. array/matrix)
		- On recursive:
			- At top, have a check if we already saw it, return it
			- Do recursiveness
			- At bottom, return result for the current that we're checking
	- Example: 
		https://leetcode.com/problems/longest-increasing-path-in-a-matrix/

	    public int longestIncreasingPath(int[][] matrix) {
	        if (matrix.length == 0) return 0;
	        m = matrix.length; n = matrix[0].length;
	        int[][] cache = new int[m][n];
	        int ans = 0;
	        for (int i = 0; i < m; ++i)
	            for (int j = 0; j < n; ++j)
	                ans = Math.max(ans, dfs(matrix, i, j, cache));
	        return ans;
	    }

	    private int dfs(int[][] matrix, int i, int j, int[][] cache) {
	        if (cache[i][j] != 0) return cache[i][j];
	        for (int[] d : dirs) {
	            int x = i + d[0], y = j + d[1];
	            if (0 <= x && x < m && 0 <= y && y < n && matrix[x][y] > matrix[i][j])
	                cache[i][j] = Math.max(cache[i][j], dfs(matrix, x, y, cache));
	        }
	        return ++cache[i][j];
	    }

- Notes
	 - Design for simple scenario, once it works test on complex
	 - Dynamic programming is used to solve problems that can be solved using recursion. The trick is that it leverages call stacks by using memory(array)
	 - Tabulation is more optimal, however, harder to come up with
	 - Memoization is recursive


### Greedy Algorithms
- Definition: Algorithms that make optimal choice per iteration to achieve optimal solution
- Use Case:
	- Optimal local solution

### Recursion
- Use Case:
	- Permutations/Combinations to find solutions starting always from the same beginnning 
***
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
***
***
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
***
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
		.isEmpty()				//returns true if empty
		.keySet()				//returns set of key, you can do for each in this set
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
***
### LinkedHashMap
- Use Case:
	- HashMap with order of keys by insertion position (default) (last inserted, last key in keySet())
- Code Example:

		LinkedHashMap<Integer, String> map = new LinkedHashMap<>();	
- Use Case:
	- HashMap with order of keys by access order  (last accessed [get or put], last key in keySet())
- Code Example:

		LinkedHashMap<Integer, String> map = new LinkedHashMap<>(16, .75f, true);
											//int initialCapacity, float loadFactor, boolean accessOrder			
***
### TreeMap
- Use Case:
	- HashMap with order of keys by lexicographic/numerical smallest by default
- Code Example:

		TreeMap<Integer, String> map = new TreeMap<>();
***
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
***
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

		PriorityQueue<Integer> maxHeap = new PriorityQueue(Collections.reverseOrder());
		.add(i);				//adds i
		.size();				//returns size of heap
		.remove();				//removes root, returns element
		.peek();				//returns root element
		.contains();			//returns true if element exists

	- Custom Order:

		PriorityQueue<Temp> pq = new PriorityQueue<>(new Comparator<Temp>() {
        	public int compare(Temp t1, Temp t2) {
                return t2.temperature - t1.temperature;
            }
        });
        


- Time Complexity:
	- Time:				O(n)			//to build
	- Access Max / Min: O(1)
	- Insert: 			O(log(n))
	- Remove Max / Min: O(log(n))
	- Memory:			O(n)			//elements inserted
- Notes
	- Element you want to return needs to be at root
***
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
***
### Queue
- Code Examples:

		Queue<Integer> q = new LinkedList<>();
		q.add(e);			//Inserts element and returns true iff it was successfull
		q.peek();			//Returns head of queue but doesn't remove head of queue. Returns null, if queue empty
		q.poll();			//Returns head of queue and removes head of queue. Returns null, if queue empty
		q.size();			//Returns size

- Time Complexity:
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)
***
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
***
### Trees
Depth of Tree is about logn
#### •Breadth First Search (Level Order Traversal)
- Code Example:
		
		//Iterative version
        Queue<Node> queue = new LinkedList<Node>(); 
        queue.add(root); 
        while (!queue.isEmpty())  
        { 
            Node current = queue.poll(); 
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
***
#### •Depth First Search
- Use Case:
	 - Preorder: Create copy of tree
	 - Postorder: Delete tree
- Code Example:
		
		//Recursive version
		void dfs(Node n){
			if(n == null)
				return;
			//do preorder: Root, Left, Right
			dfs(n.left);
			//do inorder: Left, Root, Right
			dfs(n.right);
			//do postorder: Left, Right, Root
		}

		//Iterative versions
		public void traversePreOrderWithoutRecursion() {
		    Stack<Node> stack = new Stack<Node>();
		    stack.push(root);
		    while(!stack.isEmpty()) {
		        Node current = stack.pop();
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
		    Stack<TreeNode> s = new Stack();
	        TreeNode current = root;
	        while(current != null || !s.isEmpty()){
	            while(current != null){
	                s.push(current);
	                current = current.left;
	            }
	            current = s.pop();
	            answer.add(current.val);
	            current = current.right()
	        }
		}

		public void traversePostOrderWithoutRecursion() {
		    Stack<TreeNode> s = new Stack<TreeNode>();
		    Stack<TreeNode> out = new Stack<TreeNode>();
		    s.push(root);
		    while (!s.isEmpty()) {
		        TreeNode current = s.pop();
		        out.push(current);
		        if (current.left != null) {
		            s.push(cur.left);
		        }
		        if (current.right != null) {
		            s.push(cur.right);
		        }
		    }

		    while (!out.isEmpty()) {
		        visit(current.value);
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

#### •Morris Traversal
- Code Example:
	
		//Morris inorder
		//Main idea is to create a link between the rightest after left node to current node
		//If, rightest right child == null, then we need to create a link to parent
		//Else, we found that rightest node == current, we already visited and need to cut link
		public void inorder(Node root) {
	        Node current = root;
	        while(current != null) {
	            //left is null then print the node and go to right
	            if (current.left == null) {
	                System.out.print(current.data + " ");
	                current = current.right;
	            }
	            else {
	                //find the predecessor.
	                Node predecessor = current.left;
	                //To find predecessor keep going right till right node is not null or right node is not current.
	                while(predecessor.right != current && predecessor.right != null){
	                    predecessor = predecessor.right;
	                }
	                //if right node is null then go left after establishing link from predecessor to current.
	                if(predecessor.right == null){
	                    predecessor.right = current;
	                    current = current.left;
	                }else{ //left is already visit. Go rigth after visiting current.
	                    predecessor.right = null;
	                    System.out.print(current.data + " ");
	                    current = current.right;
	                }
	            }
	        }
	    }
 - Time Complexity:
	 - Time: O(n)
	 - Space: O(1)
***
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
	 - Search/Insert/Delete: O(mn)	//m = length of longest word, n = number of words
	 - Prefix Lookup: O(a)			//a = length of word
	 - Worst Case Runtime: O(mn)	//m = length of longest word, n = number of words
- Space Complexity:
	 - O(mn)						//when there are n words each with length m
	 - O(k^l)						//on a dense trie, complexisty becomes k = (26 letter alphabet) ^ l = avg length of word
- Notes: 
	 - Root node is empty
	 - Add [* nodes (null nodes)/or set a value]  at end of each word
	 - Each node has 26 children (even if they're not used)
	 - Size of trie is directly correlated to alphabet used
	 - Null nodes take up space (a lot!). 26 children nodes per node
***
***
## TOOLS
### Arrays
- `Arrays.fill(ra, value)									//fills every element of ra with given value`
- `Arrays.sort(array)										//Time O(nlogn)`
- `Arrays.sort(intervals, (a, b) -> a.start - b.start)		//Custom object Intervals[], .start returns value, lambda`
- `Arrays.sort(ra, (a,b) -> (Integer.compare(a, b)))		//Orders depending of comparison`
- `Arrays.binarySearch(ra, tar)								//Returns index of location of target. If not found, returns -(insertionpoint)-1`
- `Arrays.binarySearch(ra, start, end, tar)					//Same as above; start and end are indexes of ra to where do search`
- `Arrays.asList(array)										//Converts array to list`
- Notes
	 - Array can be null or empty
***
### ArrayList
- `List<Type> str = new ArrayList<Type>()				//Dynamic array`
- `					  .add(o)								//Adds element`
- `					  .add(int i, o)						//Adds element at index i`
- `					  .clear()								//Removes all elements from list`
- `					  .contains(o) 							//Returns true if element in list`
- `					  .get(int i)							//Returns element at index i`
- `					  .indexOf(o)							//Returns index i of first occurence of element`
- `					  .isEmpty()							//Returns true if list has no elements`
- `					  .lastIndexOf(o)						//Returns index i of last occurence of element`
- `					  .remove(o)							//Removes first occurrence of element and returns boolean or removes element at index o`
- `					  .set(int i, o)						//Replaces element at i with new element`
- `					  .size()								//Returns number of elements in list`
- `					  .toArray()							//Returns array of elements in proper order`
`List<int[]> result = new ArrayList<>();   
result.toArray(new int[result.size()][]);`
***
### Character
- `Character.isDigit(char)								//returns true if it is`
- `Character.isLetter(char)								//returns true if it is`
***
### double
- Double.compare(double1, double2). You pass two doubles and returns 0 if they equal, -1 if the first is smaller, or 1 if the first is greater.
- `if (Double.compare(double1, double2) == 0)			//equals`
- `if (Double.compare(d1, d2) < 0)						//d1<d2`
- `if (Double.compare(d1, d2) > 0)						//d1>d2`
***
### int
- NOO! 	`int a; 		if(a == null)`
- YES! 	`int a[]; 	if(a == null)`
- `a = s.charAt(0) != '0' ? 1 : 0;						//conditional question mark number assign`
- `Integer.parseInt(num)								//converts string of numbers to int (only for numbers)`
- `Integer.toBinaryString(num)							//converts integer (number) to string in binary`
- `Integer.valueOf(str);								//converts numbers in string to Integer(also returns ascii for string)`
- `Integer.valueOf(int);								//converts primitive to Integers`
- `int i = IntegerObjectName.intValue();				//converts Integer object to int primitive`
- `Integer.MAX_VALUE = 2^31-1`
- `Integer.MIN_VALUE = -2^31`
- `num.toString()										//returns String representation of Integer`
***
### List
- `Queue<String> test = new LinkedList<String>();`
- `List<String> test2 = new LinkedList<String>();`
- `raString[i] = raList.get(i);							//to copy raList to array`

- In this example, there are 2 LinkedList objects implementing different interfaces. Therefore, each object will have different methods depending on the interface they're implementing
- List is a reference type so when you pass myPassedList as an argument to doSomething you are modifying the original list //NOT 100% sure
***
### Lambda
- Lambdas are function that don't belong to a class and can be pass to methods as if it was an object
- `doubleValue = (int a) -> a*2;						//since it's a one line return can be ommitted`
- `doubleValue = (int a) ->  {
		return a*2;										//same as the inline lambda above
	};`
***
### Math
- `Math.abs(x);`
- `Math.max(x, y);`
- `Math.min(x, y);`
***
### String
- `str = str.replaceAll("substring", "replacement");	//replaces substring for replacement`
- `str1.compareTo(str2);								//returns 0 if they match, -number if str1 smaller`
- `str.indexOf('str');									//returns index of string(or char) in string`
- `s.indexOf('/', 2);									//same as above and starting at the specified index`
- `str.contains('x');									//returns boolean depending if string has character inside`
- `str.isEmpty();										//`
- `str.length();										//returns lenght of string`
- `str.substring(6);									//returns substring after index (including)`
- `str.substring(0, 6);									//returns substring in between those indices (excluding last index)`
- `str.startsWith('str')								//returns boolean of string(or char)`
- `str.split(" ")										//splits string to array elements depending on delimiter`
- `str.toCharArray()									//converts string to char array`
- `str.toUpperCase()									//converts string to uppercase`
- `str.toLowerCase()									//converts string to lowercase`
- `str.trim()											//returns str without beginning and end whitespaces`
- `String.valueOf(int)										//returns string representation of int`
- Notes
	 - Strings can be null or empty
	 - str.substing takes O(n)
***
### StringBuilder
- `StringBuilder str = new StringBuilder(i);			//initialize StringBuilder with i space; can create without i`
- `str.append(c);										//can append char, string, int representation, etc`
- `str.capacity();										//return current capacity`
- `str.charAt(i);										//return char value at index i`
- `str.delete(int l, int r);							//removes substring from index l to index r`
- `str.insert(int i, str);								//insert str/char at i`
- `str.length();										//returns length`
- `str.replace(int l, int r, String strng);				//replaces characters from index l to index r with strng`
- `str.reverse();										//string gets replaced with reverse`
- `String[] raStr = str.split(" ");						//splits String by space and put it in ra"`
- `str.setCharAt(int i, char c);						//set character c at index i`
- `str.setLength(str.length()-1)						//removes everything after provided length`
- `str.substring(int l, int r);							//return substring from index l to index r`
- `str.toString();										//return string representation of str`
***
***
## EXTRAS
### Sorting 
	private class IntervalComparator implements Comparator<Interval> {
        @Override
        public int compare(Interval a, Interval b) {
            return a.start < b.start ? -1 : a.start == b.start ? 0 : 1;
        }
    }

    public List<Interval> merge(List<Interval> intervals) {
        Collections.sort(intervals, new IntervalComparator());
    }

    Same as
    Collections.sort(intervals, (a,b) -> a.start - b.start)
***
### LinkedList
#### Doubly LinkedList
	Have a hashmap and doubly linkedlist
***
### Graph Algorithms:
#### Topological Sort - Find cycle in directed graph
	Steps:
	1) Have a map<Integer, List<Integer>> that has the adjacency list
		a. Integer = node.val; List<Integer> = values that node points to
	2) Have an indegree array to every node on graph
		a. For every node pointing to current node indegree of current node, indegree++
	3) Add to Queue<Integer> all nodes with indegree = 0
	4) While q is not empty
		a. Decrement all the in degrees of nodes that the current node points to on map list
		b. If a indegree = 0, add it to the queue

#### DFS - Find cycle in undirected graph
	Steps:
	1) Have a map<Integer, List<Integer>> that has the adjacency list  / or List<List<Integer>>
		a. Integer = node.val; List<Integer> = values that node points to
	2) Initialized an empty visited hashSet
		a. Add edges to hashSet as you visit them with DFS
	3) DFS will have as parameters adjList, curr vertex, visited hashSet, parent vertex
	   Example of code:
		boolean hasCycle(List<List<Integer>> adjList, int u, boolean[] visited, int parent) {
	        if (visited[u]) {
	            return true;
	        }
	        visited[u] = true;
	        for(int v : adjList.get(u)){
	        	//point we are going to visit is not where we are coming from
	        	//&& 
	            if(v != parent && hasCycle(adjList, v, visited, u)){
	                return true;
	            }
	        }
	        return false;
	    }
	4) If hasCycle(adList, 0, visited, -1) returns true, there is a cycle in graph
***
### Union Find

Union find is about grouping elements that meet certain criteria, and as group keep growing, they start to join each other. Union uses find to get the root of the group, which will be join.

#### Earliest moment when everyone become friends

- Union find example:
https://leetcode.com/problems/the-earliest-moment-when-everyone-become-friends/

		class Solution {
				public int earliestAcq(int[][] logs, int N) {

						Arrays.sort(logs, (a, b) -> a[0] - b[0]);

						Unionfind uf = new Unionfind(N);
						for(int[] log : logs) {
								// Do union & find and see if the group size is 1 then return the timestamp
								uf.union(log[1], log[2]);
								// When union find count == 1, there is only one group, aka everyone is acquintances
								if(uf.count == 1) {
										return log[0];
								}
						}
						return -1;
				}

				public class Unionfind {
						int[] root;
						int count;

						public Unionfind(int count) {
								this.root = new int[count];
								this.count = count;
								// Initialize root/parent to be the index/element
								for(int i=0; i<count; i++) {
										this.root[i] = i;
								}
						}

						public void union(int i, int j) {
							// Find root/parent of each group
								int x = find(root, i);
								int y = find(root, j);

								// Union into one group and decrement count as there is one less group/element
								if(x != y) {
										root[x] = y;
										count--;
								}
						}

						public int find(int[] root, int i) {
							// If this the root/parent, return it
								if(root[i] == i) {
										return i;
								}
								// Else, go into the parent of current element recursively
								return find(root, root[i]);
						}
				}
		}
***
### Matrix

#### Maximum sum rectangle T: O(col*col*row) S: O(row)

	Steps:
	1) Create new matrix with same lengths and initialize everything to 0
	   Also have variable left, right, maxSumRect, currSumRect, and coordinates of maxSumRect
	2) Traverse original matrix from left to right columns
	3) Keep sum of elements by row on new matrix
	4) For each column, apply Kadane's algorithm and get the maximum sum of each column.
		If we find a number greater than maxSumRect, 
			We update it

    public Result maxSum(int input[][]){
        int rows = input.length;
        int cols = input[0].length;
        int temp[] = new int[rows];
        Result result = new Result();
        for(int left = 0; left < cols ; left++){
            for(int i=0; i < rows; i++){
                temp[i] = 0;
            }
            for(int right = left; right < cols; right++){
                for(int i=0; i < rows; i++){
                    temp[i] += input[i][right];
                }
                KadaneResult kadaneResult = kadane(temp);
                if(kadaneResult.maxSum > result.maxSum){
                    result.maxSum = kadaneResult.maxSum;
                    result.leftBound = left;
                    result.rightBound = right;
                    result.upBound = kadaneResult.start;
                    result.lowBound = kadaneResult.end;
                }
            }
        }
        return result;
    }
    class KadaneResult{
        int maxSum;
        int start;
        int end;
        public KadaneResult(int maxSum, int start, int end) {
            this.maxSum = maxSum;
            this.start = start;
            this.end = end;
        }
    }
***
### Integer Array

#### Kadanes Algorithm - Largest sum contiguous subarray O(n)

	public int maxSubArraySum(int a[], int size) { 
	    int maxSoFar = a[0]; 
	    int currMax = a[0]; 
	  
	    for (int i = 1; i < size; i++) { 
	        currMax = Math.max(a[i], currMax+a[i]); 
	        maxSoFar = Math.max(maxSoFar, currMax); 
	    } 
	    return maxSoFar; 
    } 

#### Largest increasing subsequence O(nlogn)

	public int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        int len = 0;
        for (int num : nums) {
            int i = Arrays.binarySearch(dp, 0, len, num);
            if (i < 0) {
                i = -(i + 1);
            }
            dp[i] = num;
            if (i == len) {
                len++;
            }
        }
        return len;
    }

#### Split array in k parts involving continuous sum of elements
	Steps:
	1) Create ints having largest number and sum of all elemnents
	2) Do a binary search between the largest number and sum; because the minimum sum is largest number and maximum sum is sum
	3) Check if the mid is valid, we can decrement the mid, else increment mid
	   Check that mid is valid by summing elements in array continuously until they are greater,
	   then increment the count and if the count is greater than k, return false
	   		which would mean that we need to decrement mid
	   else increment mid
	4) Return the left element of the binary search

	Time:  O(n∗log(sumofarray))
	Space: O(n)
    public int splitArray(int[] nums, int m) {
        int max = 0; int sum = 0;
        for (int num : nums) {
            max = Math.max(num, max);
            sum += num;
        }
        if (m == 1) return (int)sum;
        //binary search
        int l = max, r = sum;
        while (l <= r) {
            int mid = (l + (r - l))/ 2;
            if (valid(mid, nums, m)) {
                r = mid - 1;
            } else {
                l = mid + 1;
            }
        }
        return (int)l;
    }
    public boolean valid(long target, int[] nums, int m) {
        int count = 1;
        long total = 0;
        for(int num : nums) {
            total += num;
            if (total > target) {
                total = num;
                count++;
                if (count > m) {
                    return false;
                }
            }
        }
        return true;
    }

#### Largest rectangle in histogram	T:O(n) S:O(n)
	Steps:
	1) If current value is equal or bigger than top of stack,
			Add to index to stack
	   Else,
	   		Keep removing from stack until a number is equal or smaller than current bar
	2) Calculate area every time we pop from stack
			if (stack empty)
				area = input[top] * i
			else
				area = input[top] * (i - stack top - 1)

	Key: 
	Stack pushes indexes!
	Push to stack when value is more than or equal to stack peek. Pop and calculate rectangles when you ladder down.

	public int largestRectangleArea(int[] heights) {
      int n = heights.length;
      Stack<Integer> stack = new Stack();
      int maxArea = 0;
      for(int i = 0; i <= n; i++){
        int h = i == n ? 0 : heights[i];
        while(!stack.isEmpty() && h < heights[stack.peek()]){
          int curHeight = heights[stack.pop()];
          int prevIndex = stack.isEmpty() ? -1 : stack.peek();
          int area = curHeight * (i - prevIndex - 1);
          maxArea = Math.max(maxArea, area);
        }
        stack.push(i);
      }
      return maxArea;  
    }

#### Find median of 2 sorted arrays T:O(log(length of smallest array)) 
	Steps:
	1) Find smallest array (suggestion: make array input 1 always be smallest)
	2) Binary search on smallest array from l=0 to r=length
	...

	index:  0 1  2  3  4  5
	input1: 1 3  8  9  15
	input2: 7 11 18 19 21 25
	combined: 1 3 7 8 9 11 15 18 19 21 25

	Key: 
	Purpose of algorithm is to find a point that divides the 2 arrays in 2 equal partitions (or left greater by 1)
		Checks to validate the point:
			the number on left of point on input1 needs to be smaller or equal to right point on input2
			the number on left of point on input2 needs to be smaller or equal to right point on input1
			that would mean that we found a correct partition that all numbers on left partition are smaller than right partition
			and we can find the median living on these 4 numbers


    public double findMedianSortedArrays(int input1[], int input2[]) {
        //if input1 length is greater than switch them so that input1 is smaller than input2.
        if (input1.length > input2.length) {
            return findMedianSortedArrays(input2, input1);
        }
        int x = input1.length;
        int y = input2.length;

        int low = 0;
        int high = x;
        while (low <= high) {
            int partitionX = (low + high)/2;
            int partitionY = (x + y + 1)/2 - partitionX;

            //if partitionX is 0 it means nothing is there on left side. Use -INF for maxLeftX
            //if partitionX is length of input then there is nothing on right side. Use +INF for minRightX
            int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE : input1[partitionX - 1];
            int minRightX = (partitionX == x) ? Integer.MAX_VALUE : input1[partitionX];

            int maxLeftY = (partitionY == 0) ? Integer.MIN_VALUE : input2[partitionY - 1];
            int minRightY = (partitionY == y) ? Integer.MAX_VALUE : input2[partitionY];

            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                //We have partitioned array at correct place
                // Now get max of left elements and min of right elements to get the median in case of even length combined array size
                // or get max of left for odd length combined array size.
                if ((x + y) % 2 == 0) {
                    return ((double)Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY))/2;
                } else {
                    return (double)Math.max(maxLeftX, maxLeftY);
                }
            } else if (maxLeftX > minRightY) { //we are too far on right side for partitionX. Go on left side.
                high = partitionX - 1;
            } else { //we are too far on left side for partitionX. Go on right side.
                low = partitionX + 1;
            }
        }

        //Only we we can come here is if input arrays were not sorted. Throw in that scenario.
        throw new IllegalArgumentException();
    }
***
### Strings

#### Longest Common Subsequence between two strings T: O(mn)  S: O(min(m, n)) 

	Steps:
	1) Create a matrix of N=text1.length+1 M=text2.length+1 (because first row and first column is always 0)
	2) Loop through matrix skipping first column and row
	3) If the characters text1@i == text2@j, 
			they are the same characters and the matrix[i][j] = matrix[i-1][j-1]+1
	   Else (they don't match),
	   		matrix[i][j] = max of top or left matrix fields
	4) Return the bottom right element of matrix

	Logic: Start by comparing first row character with each of the subsequent strings formed by adding a column each time

    public int longestCommonSubsequence(String text1, String text2) {
        if(text1.length()==0||text2.length()==0) return 0;
        int dp[][] = new int[text1.length()+1][text2.length()+1];
		
        for(int i=1;i<text1.length()+1;i++){
            for(int j=1;j<text2.length()+1;j++){
                if(text1.charAt(i-1)==text2.charAt(j-1)){
				//if match, add lcs +1
                    dp[i][j]=dp[i-1][j-1]+1;
                }else{
				//if no match, skip
                    dp[i][j] = Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[text1.length()][text2.length()];
    }
***
***
## TIPS

### Combination/Permutation
- Usually involves recursion. A problem that can be solved with recursion can be solved iteratively. 

### Matrix Problems
- BFS = Shortest path. Might need to create nodes that have attributes x,y,dist and a matrix of visited. Use queue
- DFS = Find max area, all paths. Use recursion
- DP = If it involves number

### Caution 
- Be careful when sending LinkedList and matrix (int[][]) to methods because they modify the one you sent without return it
- Be careful with LinkedList when use iteratively because they are like pointers




***
### If you have lots of extra time


### KMP Algorithm - Knuth Morris Pratt
- Use Case:
	- Pattern searching in strings
- Steps: 
	1. Preprocess pattern string and create longest prefix that is also suffix (lps) int array that has same size as pattern. This will be used to skip characters while matching. Whole string can't be considered longest prefix/suffix.
	2. Populate lps. First, lps[0] = 0 and have a int length of previous longest prefix/suffix. Then, while loop from int i = 1 to i < lps length. Len will always be smaller than i. If charAt(i) == charAr(len), len++, set lps[i] = len, i++. Else, if, len!=0 back len to the len of previous character len = lps[len-1]. Else (len==0), lps[i]=len(0), i++.
	3. Start the KMPSearch. Have two pointers i and j starting at 0. i will be the index for the txt and j will be for patt. Loop while i < txt.length. If txt.charAt(i)==pat.charAt(j), increment both pointers. If j == M, that means we went though the whole pattern string and we have a match at i-j, also set j = lps[j-1] to skip comparing the patt from beginning(that way we start after prefix). Else if, i<N (to avoid null pointer) && patt.charAt(j) != txt.charAt(i), If j!=0, j=lps[j-1]]. Else, i++.
	4.	
- Code:

	    void KMPSearch(String pat, String txt) 
	    { 
	        int M = pat.length(); 
	        int N = txt.length(); 
	  
	        // create lps[] that will hold the longest 
	        // prefix suffix values for pattern 
	        int lps[] = new int[M]; 
	        int j = 0; // index for pat[] 
	  
	        // Preprocess the pattern (calculate lps[] 
	        // array) 
	        computeLPSArray(pat, M, lps); 
	  
	        int i = 0; // index for txt[] 
	        while (i < N) { 
	            if (pat.charAt(j) == txt.charAt(i)) { 
	                j++; 
	                i++; 
	            } 
	            if (j == M) { 
	                System.out.println("Found pattern " + "at index " + (i - j)); 
	                j = lps[j - 1]; 
	            } 
	  
	            // mismatch after j matches 
	            else if (i < N && pat.charAt(j) != txt.charAt(i)) { 
	                // Do not match lps[0..lps[j-1]] characters, 
	                // they will match anyway 
	                if (j != 0) 
	                    j = lps[j - 1]; 
	                else
	                    i = i + 1; 
	            } 
	        } 
	    } 
	  
	    void computeLPSArray(String pat, int M, int lps[]) 
	    { 
	        // length of the previous longest prefix suffix 
	        int len = 0; 
	        int i = 1; 
	        lps[0] = 0; // lps[0] is always 0 
	  
	        // the loop calculates lps[i] for i = 1 to M-1 
	        while (i < M) { 
	            if (pat.charAt(i) == pat.charAt(len)) { 
	                len++; 
	                lps[i] = len; 
	                i++; 
	            } 
	            else // (pat[i] != pat[len]) 
	            { 
	                // This is tricky. Consider the example. 
	                // AAACAAAA and i = 7. The idea is similar 
	                // to search step. 
	                if (len != 0) { 
	                    len = lps[len - 1]; 
	  
	                    // Also, note that we do not increment 
	                    // i here 
	                } 
	                else // if (len == 0) 
	                { 
	                    lps[i] = len; 
	                    i++; 
	                } 
	            } 
	        } 
	    } 

- Time Complexity:
	- O(n)
- Space Complexity:
	- O(n)

- #### Dijkstra's Algorithm
- #### Bellman-Ford Algorithm
- #### Floyd-Warshall Algorithm
- #### Prim's Algorithm
- #### Kruskal's Algorithm

### Self Balancing BST 
- #### AVL Tree 			//used when we have a lot of search (more balanced, but more rotation when insert/delete)

- #### Red Black Tree 		//used when we have a lot of insertions/deletions

	Rules: 
	1) Every node has a color either red or black.
	2) Root of tree is always black.
	3) There are no two adjacent red nodes (A red node cannot have a red parent or red child).
	4) Every path from a node (including root) to any of its descendant NULL node has the same number of black nodes.
