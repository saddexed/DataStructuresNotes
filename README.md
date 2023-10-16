# Data Structures and Algorithms Notes
Unsorted. Clean up presentation later.

## Arrays
### Print function to display array elements
```cpp
void print(int arr[], int arrSize) {
    cout << "[";
    for (int i=0; i < arrSize; i++) {
        cout << arr[i];
        if (i != arrSize-1) {
            cout << ",";
        }
    }
    cout << "]" << endl;
}
```
### main.cpp
```cpp
#include <iostream>     // Standard I/O Library - cin, cout etc
#include <algorithm>    // Some predifined functions like swap(x, y)
#include <string>       // String data support - str x
#include <vectors>      // To use vectors - vector<int> x
using namespace std;    // duh, no one wants to use std:: for everything smh

int arr[] = {1,2,3,4,5,6,7,8,9,0};  
int arrSize = *(&arr + 1) - arr;    // Array Size (10); alt to [size_of(arr)/size_of(arr[0])] 
```
### Transversing Array
```cpp
for (int i=0; i < arrSize; i++) (cout << arr[i] << " ");
cout << endl;
```
## Insertion Operations
### Insertion at the beginning
```cpp
void insertionAtStart(int arr[], int arrSize, int insValue) { 
    for (int i = arrSize; i>0; i--) (arr[i]=arr[i-1]);
        // arr[9] = arr[8] ... arr[1] = arr[0]
    arr[0] = insValue;
    arrSize++;
}
print(arr, arrSize);
```

### Insertion at the end

```cpp
void insertionAtEnd(int arr[], int arrSize, int insValue) {
    arr[arrSize] = insValue;
    arrSize++;
}
print(arr, arrSize);
```

### Insertion at specified position

```cpp
void insertionAtPosition(int arr[], int arrSize, int insValue = 10, int insPos = 6) {
    for (int i = arrSize; i>insPos; i--) (arr[i]=arr[i-1]);
    arr[insPos] = insValue; // arr[6] = 10
    arrSize++;
}   
print(arr, arrSize); // [1,2,3,4,5,6,10,7,8,9,0]
```
### Swap (any) elements
```cpp
#include <algorithm>
swap(arr[i], arr[j]) 
```
or
```cpp
int temp = arr[i];
arr[i] = arr[j];
arr[j] = temp;
```


### Sorting Arrays
This is bubble sort
```cpp
for (int i = 0; i < arrSize; i++) {
        for (int j = 0; j < arrSize; j++) {
            if (arr[i] < arr [j]) {
                swap(arr[i], arr[j]);
            }
        }
    }
```

### Merging Arrays
```cpp
//array size [get_size(a1)/get_size(a1[0])] = 5
//Using defined array for now
int a1[5] = {1,3,5,7,9};
int a2[5] = {2,4,6,8,10};
int a3[10];

// Elements of a1 to a3
for(int i = 0; i<5; i++) { 
    a3[i] = a1[i]; // {1,3,5,7,9}
} // {1,3,5,7,9}

// Elements of a2 to a3
for(int i = 0; i<5; i++) {
    a3[i+5] = a2[i]; // {1,3,5,7,9,2,4,6,8,10}
  //a3[i+a2.size()]
} // {1,3,5,7,9,2,4,6,8,10}
```
### Linear Search
```cpp
int search = 12;
int nf = 1; //Flag to check if found
for (int i = 0; i < arrSize; i++) { // Search interation
    if (arr[i] == search) {
        cout << "Found " << search << " at arr[" << i << "]" <<endl;
        nf = 0; break;  
    }
}
if (nf != 0) (cout << "Element Not Found."); //If element not found
}
```

### Binary Search
Fuck Binary Search

## Sorting Algorithms 

### Bubble Sort 
```If arrSize is not used then I'm using defined size
```
```cpp
for (int i = 0; i < 10; i++) {
    for (int j = 0; j < 10; j++) {        
        if (a3[j] > a3[j+1]) { // > if ascending; < if decending
            swap(a3[j], a3[j+1]);
        }
    }
} // {1,2,3,4,5,6,7,8,9,10}
```
Requires 2 loops so Time Complexity = O(n\*n) = O($n^2$) \
Used if: \
• Complexity does not matter \
• Short and simple code is preferred \

### Insertion Sort

<img src="https://cdn.discordapp.com/attachments/1036803415155679252/1160988051594543184/image.png" alt="Insertion Sort" style="width: auto; height: 300px;">

```cpp
void insertionSort(int arr[], int arrSize) {
for (int i = 1; i < n; i++) {
    int key = arr[i];
    int j = i - 1;
    // Move elements of arr[0..i-1] that are greater than key
    // to one position ahead of their current position
    while (j >= 0 && arr[j] > key) {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
    }
}
```
Time Complexity Θ($N^2$) \
The insertion sort is used when: \
• Array has small number of elements \
• Few elements left to be sorted 

### Selection Sort

<img src="https://media.discordapp.net/attachments/1036803415155679252/1160995785362636800/image.png" alt="Selection Sort" style="width: auto; height: 300px;">


```cpp
void selectionSort(int arr[], int arrSize) {
    for (int i=0; i<arrSize; i++) {             
        int low = i;                          // Presume element at arr[i] is lowest and note index
        for (int j = i+1; j<arrSize; j++) {   // Loop through all other than first element
            if (arr[j] < arr[low]) (low = j); // If any other element is smaller, change smallest index
        }
        swap(arr[i], arr[pos]);               // Swap elements
    }
}
```

Again, two loops so Time Complexity is O($n^2$) \
Used when: \
• Writes on device has to be reduced \
• a small list is to be sorted \
• cost of swapping does not matter \
• checking of all the elements is compulsory


# LinkedList   

## 
```cpp
struct Node {
    int data;   // Value
    Node* next; // Next Memory Address
};
```

## 
```cpp
class LinkedList {
    private:
        Node* head;                     // Element start address; Head is not part of node
    public:
        LinkedList() {                  // Init; Runs by default
            head = nullptr;             // Points to very first node of list; Makes empty list
        }
        // Methods here
}
```
## Public Methods in Linked List

### Insertion At Start/Beginning of Linked List
```cpp
void insertAtStart(int value) { // AtBeginning; [X<--- ... 2 1 0]
    Node* makeNode = new Node;  // new allocates memory and returns it's address for Node
    makeNode->data = value;     // Set node data
    if (head == nullptr) {
        head = makeNode;
    } else {
        makeNode->next = head;      // Node is now first element, points to next node
        head = makeNode;            // Make head it point to new start
    }
}
```
Node0 = null; head = null &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \\\\ Empty List \
Node0 = (0, 0x0); head = Node0 &nbsp; \\\\ List with one Node {Node0}         \
Node1 = (1, 0x1); head = Node1 &nbsp; \\\\ List with two nodes {Node1, Node0} \
So the list becomes {Node10, Node9, Node8, ... , Node1, Node0}

### Insertion At End of Linked List
```cpp
void insertAtEnd(int value) {       // AtEnd; [0 1 2 ... --->X]
    Node* makeNode = new Node;
    makeNode->data = value;
    makeNode->next = nullptr;       // Last element, so points to null
    if (head == nullptr) {
        head = makeNode;
    } else {
        Node* index = head;         // make temp var as to tranverse
        while (index->next != nullptr) {
            index = index->next;    // iterate to last element
        }
        index->next = makeNode;     // update last element to point to new node
    }
};
```

### Insertion At Specified Position of Linked List
```cpp
void insertAt(int value, int position) {
    Node* makeNode = new Node;
    makeNode->data = value;
    Node* current = head;
    for (int i = 0; i < position-1; i++) { // i=1 as head is already position 0
        current = current->next;
        if (current == nullptr) {
            cout << "Pointer Out of Range";
            break;
        }
    }
    makeNode->next = current->next; 
    current->next = makeNode;       
};
```

### Node Deletion
```cpp
void deleteValue(int value) {
    Node* index = head;
    if (index->data == value) {         // If head is node to delete
        head = index->next;             // Make head second element
        delete index;                   // Delete first element
    )
    while (index->next->data != value) (index = index->next);
    if (index->next->next == nullptr) { // If node is last element
        delete index->next;             // Delete last element
        index->next = nullptr;          // Make last element point to null
    } else {                                
        index->next = index->next->next; // Make it point one element over    
    //current0.next1 = next1.next2       // Deleting node is pain :painpeko:
    }
```

### Display List
```cpp
void display() {
    Node* index = head;             // Reference node
    cout << "[";
    while (index != nullptr) {
        cout << index->data << " ";
        index = index->next;        // Move to next node
    }
    cout << "\b]" << endl; // \b backspace
};
```

### Main Function
```cpp
int main() {
    LinkedList LinkTest; // Create structure LinkedList called Link Test
    LinkTest.insertAtStart(0);  // [0]
    LinkTest.insertAtStart(1);  // [1 0]
    LinkTest.insertAtStart(2);  // [2 1 0]
    LinkTest.insertAtStart(3);  // [3 2 1 0]
    LinkTest.insertAtStart(4);  // [4 3 2 1 0]
    LinkTest.insertAtStart(5);  // [5 4 3 2 1 0]
    LinkTest.insertAtStart(6);  // [6 5 4 3 2 1 0]
    LinkTest.insertAtEnd(9);    // [6 5 4 3 2 1 0 9]
    LinkTest.deleteNode(3);     // [6 5 4 2 1 0 9]
    LinkTest.insertAt(7, 2);    // [6 5 7 4 2 1 0 9]
    LinkTest.display();
}
```

## Circular Linked List
Just make the the last node next pointer point to head    \
lastNode->next = head

## Doubly Linked Lists
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

struct Node {
    Node* prev; // Prev Memory Address
    int data;   // Value
    Node* next; // Next Memory Address
};

class LinkedList {
    private:
        Node* head;                     // Element start address; Head is not part of node
        Node* tail;
    public:
        LinkedList() {                  // Init; Runs by default
            head = nullptr;             // Points to very first node of list; Makes empty list
            tail = nullptr;
        }

        void insertAtEnd(int value) {       // AtEnd; [0 1 2 ... --->]
            Node* makeNode = new Node;
            makeNode->data = value;
            makeNode->next = nullptr;
            if (tail == nullptr) {
                tail = head = makeNode;
                makeNode->prev = nullptr;
            } else {
                makeNode->prev = tail;
                tail->next = makeNode;
                tail = makeNode;
            }
        }

        void insertAtStart(int value) {
            Node* makeNode = new Node;
            makeNode->data = value;
            makeNode->prev = nullptr;
            if (head == nullptr) {
                head = tail = makeNode;
                makeNode->next = nullptr;
            } else {
                makeNode->next = head;
                head->prev = makeNode;
                head = makeNode;
            }
        };

        void insertAt(int value, int position) {
            Node* makeNode = new Node;  // Assume [0 1 2 3 4 5 6] is the node values
            makeNode->data = value;     // Data value
            Node* index = head;         // Temp Node to transverse
            for (int i = 0; i < position-1; i++) {  
                index = index->next;
            }//[0 1 2 3 4 5 6]
             //       ^ Index here rn
            makeNode->next = index->next;   // newNode.next = 4
            makeNode->prev = index;         // newNode.prev = 3
            index->next->prev = makeNode;   // 4.prev = newNode
            index->next = makeNode;         // 3.next = newNode; always do this last
        };

        void deleteValue(int value) {
            Node* index = head;
            if (index==head) {
                head = index->next;
                index->next->prev = nullptr;
                delete index;
            }
            while (index!=nullptr) {
                if (index->data == value) {
                    if (index==tail) {
                        tail-> index->prev;
                        index->prev->next = nullptr;
                        delete index;
                    } else {
                        index->prev->next = index->next;
                        index->next->prev = index->prev;
                        delete index;
                        break;
                    }
                }
                index = index->next;
        };

        void display() {
            Node* index = head;
            cout << "[";
            while (index != nullptr) {
                cout << index->data << " ";
                index = index->next;
            }
            cout << "\b]" << endl; // \b backspace
        };
};

int main() {
    LinkedList LinkTest; // Create structure LinkedList called Link Test
    LinkTest.insertAtEnd(2);    // [2]
    LinkTest.insertAtEnd(3);    // [2 3]
    LinkTest.insertAtEnd(4);    // [2 3 4]
    LinkTest.insertAtStart(0);  // [0 2 3 4]
    LinkTest.insertAtStart(1);  // [1 0 2 3 4]
    LinkTest.insertAtEnd(5);    // [1 0 2 3 4 5]
    LinkTest.insertAtEnd(6);    // [1 0 2 3 4 5 6]
    LinkTest.deleteValue(3);    // [1 0 2 4 5 6]
    LinkTest.insertAt(111, 4);  // [1 0 2 4 111 5 6]
    LinkTest.display();         // [1 0 2 4 111 5 6]
}

```






## Vectors

```cpp
vector<int> vec = {1,3,5,7,9,11}; // init
```

### Size of Vector

```cpp
cout << vec.size() << endl; // 6
```

### Append to end

```cpp
vec.push_back(13); // {1,3,5,7,9,11,13}
```

### Delete from End

```cpp
vec.pop_back(); // {1,3,5,7,9,11}
```

### Insert at pos

```cpp    
pos = 3;
//insert(vec.begin() + position, value)
vec.insert(vec.begin() + pos, 123); // {1,3,5,123,7,9,11}
vec.insert(vec.begin() + 0, 101);   // {101,1,3,5,123,7,9,11}
```
### Delete at pos

```cpp
vec.erase(4); // {101,1,3,5,7,9,11}
vec.erase(0); // {1,3,5,7,9,11}
```


## Unrelated shortcut things
### Single line for/if/while(when applicable) loop
Works only on single statement loops. The {} container is not needed
```cpp
int main() {
    for (int i = 0; i<10; i++) (cout << "Loop No. " << i << endl);
//  for/if (       condition       ) (        statement       );
}
```
