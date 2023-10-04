# Arrays

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
for (int i=0; i < arrSize; i++) {
    cout << arr[i] << " ";
}
cout << endl;
```
## Insertion Operations
### Insertion at the beginning
```cpp
int ins = 10;
for(int i = arrSize; i>0; i--) {
    arr[i]=arr[i-1]; 
    // arr[9] = arr[8]; arr[1] = arr[0]
}
arr[0] = ins;
arrSize++;
print(arr, arrSize);
```
### Insertion at the end
```cpp
int ins = 10;
arr[arrSize] = ins;
arrSize++;
print(arr, arrSize);
```
### Insertion at specified position
```cpp
int ins = 10; int pos = 6;
for(int i = arrSize; i>pos; i--) {
    arr[i]=arr[i-1];
}
arr[pos] = ins;
arrSize++;
print(arr, arrSize);
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

//Sort in decending order
for (int i = 0; i < 10; i++) {
    for (int j = 0; j < 10; j++) {        
        if (a3[i] < a3[j]) {
            swap(a3[i], a3[j]);
        }
    }
} // {1,2,3,4,5,6,7,8,9,10}
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
