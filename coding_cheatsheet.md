# ULTIMATE CHEATSHEET

## TECHNIQUES/ALGORITHMS

### Backtrack
### Binary Search
- Use Case:
	- Sorted Array
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

### Breadth First Search 
#### •Graph
- Time Complexity:
	- O(|V| + |E|)
	
#### •Tree
- Code Example:

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

- Complexity:
	 - O(n)
- Notes:
	 - Similar to queue

### Dynamic Programing
- Use Case:
	 - Optimization
	 - When pattern involves result of previous result
- Notes
	 - Design for simple scenario, once it works test on complex

### Depth First Search Tree
 - Code Example:

		void dfs(Node n){
			if(n == null)
				return;
			//do preorder: left node first
			dfs(n.left);
			//do inorder: root node first
			dfs(n.left);
			//do postorder: right node first
		}

 - Time Complexity:
		O(n)
 - Notes: 
	 - Similar to stack

### Greedy Algorithms

### Recursion

### Tries

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
### Hash Map
- Use Case:
	- Count frequency of an element
- Code Example:

		Map<Integer, Integer> hash = new HashMap();
		.put(k, v)				//inserts key and value
		.putIfAbsent(k, v)		//if key doesn't exist, inserts key and value //else nothing
		.get(k)					//returns value of specified key
		.getOrDefault(k, v)		//if value is assigned, returns value; //else, returns v
		.size()					//returns size of hashmap
		.remove(k)				//removes the value mapped to k, returns value
		.values()				//iterate by doing for(int val:map.values())

- Time Complexity:
	- Time	O(1)			//to look for values
	- Memory	O(n)			//elements inserted
- Notes
	- key = ra[index]; value = index

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
	- Time 	O(n)			//to build
	- Access Max / Min: O(1)
	- Insert: O(log(n))
	- Remove Max / Min: O(log(n))
	- Memory	O(n)			//elements inserted
- Notes
	- Element you want to return needs to be at root

### LindkedList
- Code Example:
	- Iterate single linkelist:

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

### Queue
- Time Complexity:
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)

### Stack
- Use Case
	- brackets
- Time Complexity
	- Access: O(n)
	- Search: O(n)
	- Insert: O(1)
	- Remove: O(1)

### Trees

## TOOLS
### Arrays
- `Arrays.sort(array)										//Time O(nlogn)`
- `Arrays.sort(intervals, (a, b) -> a.start - b.start)		//Custom object Intervals[], .start returns value, lambda`

### int
- NOO! 	`int a; 		if(a == null)`
- YES! 	`int a[]; 	if(a == null)`
- `a = s.charAt(0) != '0' ? 1 : 0;						//conditional question mark number assign`
- `Integer.valueOf(str);								//converts numbers in string to int(only works for string of numbers)`

### Math
- `Math.abs(x);`
- `Math.max(x, y);`
- `Math.min(x, y);`

### String
- `str = str.replaceAll("substring", "replacement");	//replaces substring for replacement`
- `str.indexOf('x');									//returns index of char in string`
- `str.contains('x');									//returns boolean depending if string has character inside`
- `str.length();										//returns lenght of string`
- `str.substring(6);									//returns substring after index (including)`
- `str.substring(0, 6);								//returns substring in between those indices (excluding last index)`


## EXTRAS
### Sorting Algorithms

### Graph Algorithsm:
- #### Topological Sort
- #### Dijkstra's Algorithm
- #### Bellman-Ford Algorithm
- #### Floyd-Warshall Algorithm
- #### Prim's Algorithm
- #### Kruskal's Algorithm

