Visualizations: [Data Structure Visualization (usfca.edu)](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html) [Visualising data structures and algorithms through animation - VisuAlgo](https://visualgo.net/en) 

---

# Intro

## How computers work

General purpose computers consist of 2 main components:
- **Hardware components**: physical electronics that include CPU, GPU, RAM, etc.. 
- **Software components**: instructions to these electronics which conveyed in a user friendly way by means of programing languages

---

With the evolution of electronic circuits it became easier to make a general purpose device that can change it's functionality without having to change the hardware. but surely at the cost of less optimizations to each functionality.

So it's very important to learn how to make good use of the instructions provided by the hardware.

---

## Why learn
### Problem Solving

- **Critical Thinking**: Enhances logical reasoning and breaking down complex problems.
- **Adaptability**: Prepares you for varied challenges.
- **Foundation**: Essential for advanced computer science topics.
---

### Data Structures

- **Efficient Data Management**: Organize and manage data effectively.
- **Performance Optimization**: Optimize for specific operations (e.g., search, insert).
- **Trade-offs**: Choose the best structure for a problem.
---

### Algorithms

- **Systematic Methods**: Provide structured problem-solving techniques.
- **Efficiency**: Write efficient and scalable code.
- **Innovation**: Explore new problem-solving approaches.
---

### Practical Application

- **Real-world Problems**: Solve practical issues like network routing and data encryption.
- **Software Development**: Write clean, efficient, and maintainable code.
- **Coding Interviews**: Essential for technical job interviews.

---

## What makes a good software

**Software Engineering** is a disciplined approach to the design, production, and maintenance of computer programs that are developed on time and within cost estimates, and utilizing tools that help to manage the size and complexity of the resulting software products.

---

**Goals**: 
- Works (that is, accomplishes its intended function)
- Can be read and understood
- Can be modified if necessary without excruciating effort 
- Is completed on time and within its budget.

---

# Complexity analysis

### Comparison of Algorithms:
- **Correctness**: judged by how close you are to the answer or how many you got right
- **Runtime**: judged by how long your code takes to run
- **Memory**: judged by how much space your code needs

---

### Analysis of Algorithms
- **Worst Case Analysis (*Usually done*)**: by calculating the upper bound(worst) of usages. annotated by `Big O` notations 
- **Average Case Analysis (*Sometimes done*)**: by calculating the average of usages. annotated by `Big Theta (Θ)` notations
- **Best Case Analysis (*Never done*)**: by calculating the lower bounds(best) of usages. annotated by `Big Omega (Ω)` notations 

---

### Estimating the Analysis
A simple way to get `Big O` notation of an expression is to drop low order terms and ignore
leading constants (**Why?**). For example, consider the following expression.
- 3$n^3$ + 6$n^2$ + 6000 = O($n^3$)

---
### Analysis comparison
The common levels in order from best to worst:
- **0($1$)**: constant
- **O($log_2(n)$)**: logarithmic 
- **O($n$)**: linear
- **O($n^2$)**: quadratic
- **O($n^3$)**: cubic
- **O($2^n$)**: exponential
- **O($n!$)**: factorial
---

![](_attachments/Data%20Structures%20and%20Algorithms/dbb9814939a46dcf84a784160e25924a.png)

![](_attachments/Data%20Structures%20and%20Algorithms/66caa5cd1cd9dd7ea5c0e35960eb7c80.png)

---

# Algorithms

## Divide and conquer

- **Idea**: used to solve problems by dividing the main problem into subproblems, solving them individually and then merging them to find solution to the original problem
- **Usual Complexity**:
	- **Time**: O($log_2(n)$)
	- **Space**: O($n$)

---

## Search Algorithms

Used to find one or more elements from a dataset. 

We can achieve this using a linear search `O(n)` but with some extra information about the dataset we can further optimize the process

---

Examples:
- **Linear Search (Sequential Search)**: Works on random data, **O($n$)**
- **Binary Search**: Works on sorted data, **O($log_2(n)$)**
- **Exponential Search**: Works on sorted data, **O($log_2(n)$)**
- **Ternary Search**: Works on sorted data, **O($log_3(n)$)**
- **Interpolation Search**: Works on sorted data, good on uniform data but otherwise **O($n$)**

---
### Linear search (Sequential Search)
- **Idea**: iterate through the data one by one until you reach goal or dataset end
- **Complexity**:
	- **Time**: O($n$)
	- **Space**: O($1$)

```C++
// sponge
int search(int arr[], int N, int x) {
    for (int i = 0; i < N; i++)
        if (arr[i] == x)
            return i;
    return -1;
}
```

---
### Binary search
- **Assumption**: dataset is sorted
- **Idea**: apply divide and conquer technique by dividing dataset into 2 segments, then checking the middle element to determine which segment to keep and which to discard, then repeat until you reach goal or dataset end 
- **Complexity**:
	- **Time**: O($log_2(n)$)
	- **Space**: O($1$)

---

![](_attachments/Data%20Structures%20and%20Algorithms/43d67e25f0e3b9af2ad059ce6c99def0.gif)

---

**Iterative**:
```c++
int binarySearch(int arr[], int low, int high, int x) {
    while (low <= high) {
        int mid = low + (high - low) / 2;

        // Check if x is present at mid
        if (arr[mid] == x)
            return mid;

        // If x is smaller, ignore right half
        if (arr[mid] > x)
            high = mid - 1;

        // If x is greater, ignore left half
        else
            low = mid + 1;
    }

    // If we reach here, then element was not present
    return -1;
}
```

---

**Recursive**:
```c++
int binarySearch(int arr[], int low, int high, int x) {
    if (high < low) return -1; 
	int mid = low + (high - low) / 2;

	// Check if x is present at mid
	if (arr[mid] == x)
		return mid;

	// If x is smaller, ignore right half
	if (arr[mid] > x)
		return binarySearch(arr, low, mid - 1, x);

	// If x is greater, ignore left half
	return binarySearch(arr, mid + 1, high, x);
    
}
```

---
### Labs

- [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/)
- [441. Arranging Coins](https://leetcode.com/problems/arranging-coins/)
- Implement Sequential Search & Binary Search on array of integers & strings (4 total)
- Implement Sequential Search on array of Employees (search by code and search by name)
- **Bonus**: Implement Sequential search or Binary Search on array of Complex


---

## Sort Algorithms
Used to organize a dataset in a certain order. 

There are many Algorithms to achieve this but with varying complexities like:
- **Selection Sort**: O($n^2$)
- **Bubble Sort**: O($n^2$)
- **Merge Sort**: O($nlog_2(n)$)
- **Insertion Sort**: O($n^2$)
- **Heap Sort**: O($nlog_2(n)$)
- **Quick Sort**: Θ($nlog_2(n)$), O($n^2$)

---
#### Selection sort

- **Idea**: repeatedly select the smallest (or largest) element from the unsorted portion of the list and move it to the end of the sorted portion of the list
- **Complexity**:
	- **Time**: O($n^2$)
	- **Space**: O($1$)
---

![](_attachments/Data%20Structures%20and%20Algorithms/f2fa63db66e38f76792a0f208b9549d3.png)

---

```c++
void selectionSort(int arr[], int n) {
    int i, j, min_idx;

    // One by one move boundary of
    // unsorted subarray
    for (i = 0; i < n - 1; i++) {
        // Find the minimum element in
        // unsorted array
        min_idx = i;
        for (j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_idx])
                min_idx = j;
        }

        // Swap the found minimum element
        // with the first element
        if (min_idx != i)
            swap(arr[min_idx], arr[i]);
    }
}
```

---

#### Bubble sort

- **Idea**: repeatedly swap the adjacent elements if they are in the wrong order.
- **Complexity**:
	- **Time**: O($n^2$)
	- **Space**: O($1$)

---


![](_attachments/Data%20Structures%20and%20Algorithms/a9754da580463b9d0beca32cb1fd9b75.webp)

---

```c++
void bubbleSort(int arr[], int n) {
    int i, j;
    bool swapped;
    for (i = 0; i < n - 1; i++) {
        swapped = false;
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }

        // If no two elements were swapped
        // by inner loop, then break
        if (swapped == false)
            break;
    }
}
```

---

#### Merge sort

- **Idea**: apply divide and conquer technique by repeatedly dividing the input array into smaller subarrays (halves) and sorting those subarrays then merging them back together to obtain the sorted array
- **Complexity**:
	- **Time**: O($nlog_2(n)$)
	- **Space**: O($n$)

---

![](_attachments/Data%20Structures%20and%20Algorithms/6b89d866159edaf274f73b86e22f6555.png)

---


```c++
// Merge two subarrays L and M into arr
void merge(int arr[], int p, int q, int r) {
  // Create L ← A[p..q] and M ← A[q+1..r]
  int n1 = q - p + 1;
  int n2 = r - q;

  int L[n1], M[n2];

  for (int i = 0; i < n1; i++)
    L[i] = arr[p + i];
  for (int j = 0; j < n2; j++)
    M[j] = arr[q + 1 + j];

  // Maintain current index of sub-arrays and main array
  int i, j, k;
  i = 0;
  j = 0;
  k = p;

  // Until we reach either end of either L or M, pick larger among
  // elements L and M and place them in the correct position at A[p..r]
  while (i < n1 && j < n2) {
    if (L[i] <= M[j]) {
      arr[k] = L[i];
      i++;
    } else {
      arr[k] = M[j];
      j++;
    }
    k++;
  }

  // When we run out of elements in either L or M,
  // pick up the remaining elements and put in A[p..r]
  while (i < n1) {
    arr[k] = L[i];
    i++;
    k++;
  }

  while (j < n2) {
    arr[k] = M[j];
    j++;
    k++;
  }
}

// Divide the array into two subarrays, sort them and merge them
void mergeSort(int arr[], int l, int r) {
  if (l < r) {
    // m is the point where the array is divided into two subarrays
    int m = l + (r - l) / 2;

    mergeSort(arr, l, m);
    mergeSort(arr, m + 1, r);

    // Merge the sorted subarrays
    merge(arr, l, m, r);
  }
}
```

---

#### Complexity Comparison summary

| **Sorting Algorithm** | **Time Complexity Worst** | **Time Complexity Average** | **Time Complexity Best** | **Space Complexity** | **Stability** |
| --------------------- | ------------------------- | --------------------------- | ------------------------ | -------------------- | ------------- |
| **Bubble Sort**       | O(n^2)                    | O(n^2)                      | O(n)                     | O(1)                 | Stable        |
| **Selection Sort**    | O(n^2)                    | O(n^2)                      | O(n^2)                   | O(1)                 | Not Stable    |
| **Insertion Sort**    | O(n^2)                    | O(n^2)                      | O(n)                     | O(1)                 | Stable        |
| **Merge Sort**        | O(n log n)                | O(n log n)                  | O(n log n)               | O(n)                 | Stable        |
| **Quick Sort**        | O(n^2)                    | O(n log n)                  | O(n log n)               | O(log n)             | Not Stable    |
| **Heap Sort**         | O(n log n)                | O(n log n)                  | O(n log n)               | O(1)                 | Not Stable    |
| **Counting Sort**     | O(n+k)                    | O(n+k)                      | O(n+k)                   | O(k)                 | Stable        |
| **Radix Sort**        | O(nk)                     | O(nk)                       | O(nk)                    | O(n+k)               | Stable        |
- **n** is the number of elements in the input array.
- **k** is the range of the input (for Counting Sort and Radix Sort).
- **Stability**: A stable sorting algorithm maintains the relative order of records with equal keys.


---
#### Labs

- [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) 
- [912. Sort an Array](https://leetcode.com/problems/sort-an-array/)
- [1637. Widest Vertical Area Between Two Points Containing No Points](https://leetcode.com/problems/widest-vertical-area-between-two-points-containing-no-points/) 
- Implement Selection sort & Bubble sort & Merge sort on array of integers (3 total)
- **Bonus**: Implement any sorting on array of Complex

---

## Two pointers

- **Idea**: works by defining 2 iterators to loop through the data structure, allowing to look at 2 places at the same time
- **Usual Complexity**:
	- **Time**: O($n$)
	- **Space**: O($1$)


---

### Labs

- [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
- [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)
- [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)


---

## Sliding window 

- **Idea**: works by defining 2 iterators to loop through the data structure. allowing to look at the range in between, usual the 2nd iterator adds elements to the range while the 1st removes them
- **Usual Complexity**:
	- **Time**: O($n$)
	- **Space**: O($1$)


---

### Labs

- [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
- [1456. Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)
- [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [1208. Get Equal Substrings Within Budget](https://leetcode.com/problems/get-equal-substrings-within-budget/)

---



##  Prefix sum 

- **Idea**: cache all previous sums to be able to calculate sum of ranges in O(1)
- **Usual Complexity**:
	- **Time**: O($n$) for build, O(1) for use
	- **Space**: O($n$)

---

### Labs

- [1732. Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/)
- [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)


---

## Frequency array/map

- **Idea**: count the frequency of elements either by using array index or map
- **Usual Complexity**:
	- **Time**: O($n$)
	- **Space**: O($k$)

---

### Labs

- [771. Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/)
- [1160. Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)

---

## Graph 

### Breadth First Search(BFS)


```c++
void bfs(TreeNode* root) {
	queue<TreeNode*> q;
	q.push(root);

	while (!q.empty()) {
		int c = size(q);

		while (c--) {
			auto cur = q.front();
			q.pop();
			
			if (cur->left)
				q.push(cur->left);
			if (cur->right)
				q.push(cur->right);
				
			cout << cur->val << endl;
		}
	}
}
```



---

#### Labs

- [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
- [1379. Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)
- [513. Find Bottom Left Tree Value](https://leetcode.com/problems/find-bottom-left-tree-value/)

---

### Depth First Search(DFS)

**Iterative**:
```c++
void dfs(TreeNode* root) {
	stack<TreeNode*> q;
	q.push(root);

	while (!q.empty()) {
		auto cur = q.top();
		q.pop();

		if (cur->left)
			q.push(cur->left);
		if (cur->right)
			q.push(cur->right);

		cout << cur->val << endl;
	}
}
```


**Recursive**:
```c++
void dfs(TreeNode* node) {
	if(!node) return;

	cout << node->val << endl;

	dfs(node->right), dfs(node->left);
}
```



---

#### Labs

- [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
- [1379. Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)
- [513. Find Bottom Left Tree Value](https://leetcode.com/problems/find-bottom-left-tree-value/)



---

### Labs

- [958. Check Completeness of a Binary Tree](https://leetcode.com/problems/check-completeness-of-a-binary-tree/) 

---

### Backtracking




---

## Dynamic Programing




---

## Monotonic Stack




---

# Data structures
is a systematic way of organizing data for efficient usage.

**Main operations**:
- Random access
- Search
- Insert
- Delete

Each data structure has varying efficiencies with each operation and it's all about trade-offs so we must carefully select the best candidate for our use case  

---

## Array
- **Concept**: a contiguous block of memory is reserved to store blocks of data 
- **Runtime Complexity**
	- **Random access**: O(n)
	- **Search**: O(n), (worst case, if target is at the end)
	- **Insert**: O(n), (worst case, if inserting at the beginning or middle, shifting elements is required)
	- **Delete**: O(n), (worst case, if deleting from the beginning or middle, shifting elements is required)

---

### Labs

- [58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/)
- [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

---

## LinkedList / Doubly LinkedList
- **Concept**: blocks of data are chained together to form a list
- **Runtime Complexity**
	- **Random Access**: O(n) (sequential access required)
	- **Search**: O(n)
	- **Insert**: O(1) (if inserting at the head or given a reference to a node)
	- **Delete**: O(1) (if given a reference to the node to be deleted)

```c++
// Node class
class Node {
public:
    int data;
    Node* prev;
    Node* next;
    Node(int data) : data(data), prev(nullptr), next(nullptr) {}
};

// DoublyLinkedList class
class DoublyLinkedList {
private:
    Node* head;
    Node* tail;

public:
    DoublyLinkedList() : head(nullptr), tail(nullptr) {}

    // Function to get the length of the list
    int getLength() const {
        int length = 0;
        Node* current = head;
        while (current != nullptr) {
            ++length;
            current = current->next;
        }
        return length;
    }

    // Function to insert at the front
    void insertFront(int data) {
        Node* newNode = new Node(data);
        if (head == nullptr) {
            head = tail = newNode;
        } else {
            newNode->next = head;
            head->prev = newNode;
            head = newNode;
        }
    }

    // Function to insert at the back
    void insertBack(int data) {
        Node* newNode = new Node(data);
        if (tail == nullptr) {
            head = tail = newNode;
        } else {
            newNode->prev = tail;
            tail->next = newNode;
            tail = newNode;
        }
    }

    // Function to insert at a specific position
    void insertAtPosition(int data, int position) {
        if (position <= 0) {
            insertFront(data);
            return;
        }
        int length = getLength();
        if (position >= length) {
            insertBack(data);
            return;
        }
        Node* newNode = new Node(data);
        Node* current = head;
        for (int i = 0; i < position - 1; ++i) {
            current = current->next;
        }
        newNode->next = current->next;
        newNode->prev = current;
        if (current->next != nullptr) {
            current->next->prev = newNode;
        }
        current->next = newNode;
    }

    // Function to delete a node with a specific value
    void deleteNode(int data) {
        Node* current = head;
        while (current != nullptr && current->data != data) {
            current = current->next;
        }
        if (current == nullptr) {
            std::cout << "Node with value " << data << " not found." << std::endl;
            return;
        }
        if (current->prev != nullptr) {
            current->prev->next = current->next;
        } else {
            head = current->next;
        }
        if (current->next != nullptr) {
            current->next->prev = current->prev;
        } else {
            tail = current->prev;
        }
        delete current;
    }

    // Function to print the list from front to back
    void printForward() const {
        Node* current = head;
        while (current != nullptr) {
            std::cout << current->data << " ";
            current = current->next;
        }
        std::cout << std::endl;
    }

    // Function to print the list from back to front
    void printBackward() const {
        Node* current = tail;
        while (current != nullptr) {
            std::cout << current->data << " ";
            current = current->prev;
        }
        std::cout << std::endl;
    }

    // Destructor to free memory
    ~DoublyLinkedList() {
        Node* current = head;
        while (current != nullptr) {
            Node* next = current->next;
            delete current;
            current = next;
        }
    }
};


```

---

### Labs

- [1290. Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/) 
- [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) 
- [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) 
- implement LinkedList on array of integers

---

## Queue
- **Concept**: you draw the first block of data you insert, first in first out (FIFO)
- **Runtime Complexity**
	- **Random Access**: O(n) (if implemented with a linked list, needs traversal)
	- **Enqueue**: O(1)
	- **Dequeue**: O(1)

```c++
// Define the default capacity of a queue
const int MAX_SIZE = 5; // Maximum size of the stack
 
// A class to store a queue
class Queue {
    int *arr;       // array to store queue elements
    int capacity;   // maximum capacity of the queue
    int front;      // front points to the front element in the queue (if any)
    int rear;       // rear points to the last element in the queue
    int count;      // current size of the queue
 
public:
    Queue(int size = MAX_SIZE);     // constructor
    ~Queue();                   // destructor
 
    int dequeue();
    void enqueue(int x);
    int peek();
    int size();
    bool isEmpty();
    bool isFull();
};
 
// Constructor to initialize a queue
Queue::Queue(int size) {
    arr = new int[size];
    capacity = size;
    front = 0;
    rear = -1;
    count = 0;
}
 
// Destructor to free memory allocated to the queue
Queue::~Queue() {
    delete[] arr;
}

 
// Utility function to return the size of the queue
int Queue::size() {
    return count;
}
 
// Utility function to check if the queue is empty or not
bool Queue::isEmpty() {
    return (size() == 0);
}
 
// Utility function to check if the queue is full or not
bool Queue::isFull() {
    return (size() == capacity);
}
 
// Utility function to dequeue the front element
int Queue::dequeue() {
    // check for queue underflow
    if (isEmpty())
    {
        cout << "Underflow\nProgram Terminated\n";
        exit(EXIT_FAILURE);
    }
 
    int x = arr[front];
    cout << "Removing " << x << endl;
 
    front = (front + 1) % capacity;
    count--;
 
    return x;
}
 
// Utility function to add an item to the queue
void Queue::enqueue(int item) {
    // check for queue overflow
    if (isFull())
    {
        cout << "Overflow\nProgram Terminated\n";
        exit(EXIT_FAILURE);
    }
 
    cout << "Inserting " << item << endl;
 
    rear = (rear + 1) % capacity;
    arr[rear] = item;
    count++;
}
 
// Utility function to return the front element of the queue
int Queue::peek() {
    if (isEmpty())
    {
        cout << "Underflow\nProgram Terminated\n";
        exit(EXIT_FAILURE);
    }
    return arr[front];
}


```

---

### Labs

- [2073. Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/)
- [933. Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)
- [225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)
- implement Queue using Array & LinkedList on integers
---

## Stack
- **Concept**: you draw the last block of data you insert, last in first out (LIFO)
- **Runtime Complexity**
	- **Random Access**: O(n) (if implemented with a linked list, needs traversal)
	- **Push**: O(1)
	- **Pop**: O(1)

```c++
const int MAX_SIZE = 5; // Maximum size of the stack

class Stack {
private:
    int arr[MAX_SIZE];
    int top;

public:
    Stack() { top = -1;} // Initialize top to -1 to indicate an empty stack

    bool isEmpty() { return (top == -1);}

    bool isFull() { return (top == MAX_SIZE - 1);}

    void push(int element) {
        if (!isFull()) {
            top++;
            arr[top] = element;
            std::cout << "Pushed element: " << element << " onto the stack.\n";
        } else {
            std::cout << "Stack is full. Cannot push element " << element << ".\n";
        }
    }

    void pop() {
        if (!isEmpty()) {
            int poppedElement = arr[top];
            top--;
            std::cout << "Popped element: " << poppedElement << " from the stack.\n";
        } else {
            std::cout << "Stack is empty. Cannot pop from an empty stack.\n";
        }
    }

    int topElement() {
        if (!isEmpty()) {
            return arr[top];
        } else {
            std::cout << "Stack is empty.\n";
            return -1; // In this example, we consider -1 as an invalid value.
        }
    }
};
```

---

### Labs

- [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
- [1021. Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)
- [1614. Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)
- implement Stack using Array & LinkedList on integers

---

## Graph
- **Concept**: blocks of data are called node and the relationships between them are represented by edge connecting 2 nodes
- **Runtime Complexity**
	- **Random Access**: O(n)
	- **Search**: O(n)
	- **Insert**: O(n)
	- **Delete**: O(n)
---
- **Terminology**:
	- **Node**: basic building block of Graph
	- **Edge**: the linking between 2 nodes
	- **Path**: the sequence of nodes along the edges of a Graph
	- **Root**: a topmost node in a Graph from which edges originate
	- **Leaf**: a node that has no children
	- **Parent**: a predecessor of a node
	- **Child**: a successor of a node
	- **Sibling**: shares the same parent
	- **Grandparent**: parent of parent
	- **Grandchild**: child of child
	- **Ancestor**: parents of parents or parents of parents of parents and so on
	- **Descendant**: children of children or children of children of children and so on
	- **Degree**: number of edges connected to the node
	- **InDegree**: number of edges coming into the node
	- **OutDegree**: number of edges leaving the node
	- **Isolated node**: a Node with a Degree of 0

---

![](_attachments/Data%20Structures%20and%20Algorithms/fb0e91522134df0b1922eead2a3d5b93.jpg)

![](_attachments/Data%20Structures%20and%20Algorithms/2b735256e7c174b7cb11c885a6bfa6a8.png)


---

### Tree
- **Concept**: is a Directed Acyclic Graph with each node having only 1 parent 
- **Runtime Complexity**
	- **Random Access**: O(n)
	- **Search**: O(n)
	- **Insert**: O(n)
	- **Delete**: O(n)
- **Terminology**:
	- **Root**: the topmost node in a Tree
	- **Height**: number of edges on the longest path from the root to a leaf
	- **Level/Depth**: its distance from the root

---

![](_attachments/Data%20Structures%20and%20Algorithms/cacff075bcfec21ba6ee4f12a5b49ae5.png)

![](_attachments/Data%20Structures%20and%20Algorithms/10c82b9db4695709d9e3589e67c3d59e.jpg)

---

#### Binary Search Tree
- **Concept**: a binary tree where every node in the left subtree is less than the parent, and every node in the right subtree is of a value greater than the parent
- **Runtime Complexity**
	- **Random Access**: O(log n) average, O(n) worst case (unbalanced tree)
	- **Search**: O(log n) average, O(n) worst case (unbalanced tree)
	- **Insert**: O(log n) average, O(n) worst case (unbalanced tree)
	- **Delete**: O(log n) average, O(n) worst case (unbalanced tree)

![](_attachments/Data%20Structures%20and%20Algorithms/6d191b299a4c3ccd2d348892be716e90.webp)

---

#### Labs

- [700. Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)
- [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)
- [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

---

## Set
- **Concept**: stores unique blocks of data
- **Type**: 
	- **HashSet**: unsorted set (fastest)
	- **TreeSet**: sorted set

---

### HashSet
- **Concept**: A Set built using a hash table to store and retrieve data by hash
- **Runtime Complexity**
	- **Random Access**: Not supported. HashSet does not maintain any order of elements, and it does not provide a method to access elements by index.
	- **Search**: O(1) average, O(n) worst-case due to hash collisions.
	- **Insert**: O(1) average, O(n) worst-case due to hash collisions.
	- **Delete**: O(1) average, O(n) worst-case due to hash collisions.

![](_attachments/Data%20Structures%20and%20Algorithms/41cfc85cf9a9b821adc4ce3760d44308.png)

---

### TreeSet
- **Concept**: a Set where data is sorted (built based on a Red-Black tree)
- **Runtime Complexity**
	- **Random Access**: Not supported. TreeSet does not maintain an index-based structure.
	- **Search**: O(log n)
	- **Insert**: O(log n)
	- **Delete**: O(log n)

![](_attachments/Data%20Structures%20and%20Algorithms/5225994840c4f3e662f6d0948fa0c9ff.png)

---

### Labs

- [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
- [771. Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/)
- [575. Distribute Candies](https://leetcode.com/problems/distribute-candies/)

---

## Map
- **Concept**: stores data in pairs of key & value, with key being unique and the value representing a block of data
- **Type**: 
	- **HashMap**: unsorted map (fastest)
	- **TreeMap**: sorted map


---

### HashMap
- **Concept**: a Map built using a hash table to store and retrieve keys by hash
- **Runtime Complexity**
	- **Random Access**: O(1) average, O(n) worst case (if many collisions)
	- **Search**: O(1) average, O(n) worst case (if many collisions)
	- **Insert**: O(1) average, O(n) worst case (if resizing is required)
	- **Delete**: O(1) average, O(n) worst case (if many collisions)

![](_attachments/Data%20Structures%20and%20Algorithms/6443e1946c0a4353da5a66dded7cc229.png)


---

### TreeMap
- **Concept**: a Map where keys are sorted (built based on a Red-Black tree)
- **Runtime Complexity**
	- **Random Access**: Not supported. TreeMap does not maintain an index-based structure.
	- **Search**: O(log n)
	- **Insert**: O(log n)
	- **Delete**: O(log n)


---

### Labs

- [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)
- [1512. Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)
- [884. Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/)
- [535. Encode and Decode TinyURL](https://leetcode.com/problems/encode-and-decode-tinyurl/)
- [811. Subdomain Visit Count](https://leetcode.com/problems/subdomain-visit-count/)

---

## Heap / Priority Queue
- **Concept**: a Balanced binary tree where for every node the values of its children is less than or equal to its own value
- **Runtime Complexity**
	- **Random Access (find min/max)**: O(1)
	- **Search**: O(n)
	- **Insert**: O(log n)
	- **Delete**: O(log n) (removing the root and reheapifying)

![](_attachments/Data%20Structures%20and%20Algorithms/f29e112da8df05d64d930d3d8e8c75d3.png)

---

### Labs

- [2558. Take Gifts From the Richest Pile](https://leetcode.com/problems/take-gifts-from-the-richest-pile/)
- [1046. Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)
- [2974. Minimum Number Game](https://leetcode.com/problems/minimum-number-game/)

---

## Prefix Tree (Trie)
- **Concept**: a Tree for storing and retrieving strings efficiently by connecting letters in chains
- **Runtime Complexity**
	- **Random Access**: Not applicable. Tries are not designed for direct index-based access to elements.
	- **Search**: O(m), where m is the length of the string being searched.
	- **Insert**: O(m), where m is the length of the string being inserted.
	- **Delete**: O(m), where m is the length of the string being deleted.

![](_attachments/Data%20Structures%20and%20Algorithms/e1ab4c3f00f9f3c28fd101051e9b1865.png)

---

### Labs

- [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
- [1268. Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/)
- [3042. Count Prefix and Suffix Pairs I](https://leetcode.com/problems/count-prefix-and-suffix-pairs-i/)

---

## Complexity Comparison summary

| Data Structure | Random Access | Search    | Insert    | Delete    |
| -------------- | ------------- | --------- | --------- | --------- |
| Array          | O(1)          | O(n)      | O(n)      | O(n)      |
| Linked List    | O(n)          | O(n)      | O(1)      | O(1)      |
| Queue          | O(n)          | O(n)      | O(1)      | O(1)      |
| Stack          | O(n)          | O(n)      | O(1)      | O(1)      |
| BST            | O(log n)*     | O(log n)* | O(log n)* | O(log n)* |
| HashSet        | Not supported | O(1)**    | O(1)**    | O(1)**    |
| TreeSet        | Not supported | O(log n)  | O(log n)  | O(log n)  |
| HashMap        | O(1)**        | O(1)**    | O(1)**    | O(1)**    |
| TreeMap        | Not supported | O(log n)  | O(log n)  | O(log n)  |
| Heap           | O(1)          | O(n)      | O(log n)  | O(log n)  |
- `*` BST complexities are average cases; worst-case scenarios (unbalanced) are O(n)
- `**` HashSet and HashMap complexities are average cases; worst-case scenarios with many collisions are O(n)
