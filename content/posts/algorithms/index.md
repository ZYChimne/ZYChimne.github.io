---
title: "Algorithms"
description: "Algorithms Must Known"
date: "2022-06-10"
slug: "algorithms"
categories:
  - Algorithms
tags:
  - algorithms
---

## Tree

### Binary Tree

```c++
/* *
 * Definition for a binary tree node.
 * From LeetCode.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right)
 *       : val(x), left(left), right(right) {}
 * };
 */
```

#### Delete a Node in Binary Tree

```c++
TreeNode* delete_node(TreeNode* root, int key) {
    if(root==nullptr) return nullptr;
    else if(root->val>key) {
        root->left=delete_node(root->left, key);
    }
    else if(root->val<key) {
        root->right=delete_node(root->right, key);
    }
    else {
        if(root->left==nullptr) return root->right;
        else if(root->right==nullptr) return root->left;
        else {
            TreeNode* new_root=root->right;
            while(new_root->left!=nullptr) new_root=new_root->left;
            new_root->right=delete_node(root->right, new_root->val);
            new_root->left=root->left;
            return new_root;
        }
    }
    return root;
}
```

### Segment Tree

[My Calendar III](https://leetcode.cn/problems/my-calendar-iii/) (Also Differentiation & Prefix Sum)  
[Segment Tree OI-WIKI](https://oi-wiki.org/ds/seg/)  
Segment Tree is efficient to tell how many times a point has appeared in a segment.

### Trie (Prefix Tree)

[Implement Trie](https://leetcode.cn/problems/implement-trie-prefix-tree/description/)

## String

### Split

C++ string doesn't have built-in split function. To split string into an array of substrings by a character,

```c++
vector<string> split(string str, char c) {
    stringstream ss(&str);
    vector<string>res;
    string temp;
    while(getline(ss, temp, c)){
        res.emplace_back(temp);
    }
    return res;
}
```

### KMP

Heuristic string matching algorithm time complexity is O(m*n). KMP (Knuth Morris Pratt) Pattern Searching algorithm uses the previous matching result to optimize the searching process.
```c++
vector<int>longest_prefix_array;
void compute_longest_prefix_array(const string& pattern) {
    longest_prefix_array.resize(pattern.size(), -1);
    for(int i=1; i<pattern.size(); i++) {
        int j=longest_prefix_array[i-1];
        while(j!=-1&&pattern[j+1]!=pattern[i]) {
            j=longest_prefix_array[j];
        }
        if(pattern[j+1]==pattern[i]) {
            longest_prefix_array[i]=j+1;
        }
    }
}

bool kmp_search(const string& str, const string& pattern) {
    compute_longest_prefix_array(pattern);
    for(int i=1, j=-1; i<str.size()-1; i++) {
        while(j!=-1&&pattern[j+1]!=str[i]) {
            j=longest_prefix_array[j];
        }
        if(pattern[j+1]==str[i]) {
            j++;
            if(j==str.size()-1) return true;
        }
    }
    return false; // mismatch
}
``` 

## Sort

### Insertion Sort

Insertion sort outperforms other sorting algorithms in small sizes and is stable.

```c++
void insertion_sort(vector<int>& arr) {
    for(int i=1; i<arr.size(); i++) {
        int temp=arr[i], j=i;
        // Move greater elements to positions of greater indexes
        while(arr[j]>temp) {
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1]=temp;
    }
}
```

### Quick Sort

Quick Sort is preferred over Merge Sort for arrays.
```c++
vector<int>arr;
/* This function takes last element as pivot, places
the pivot element at its correct position in sorted
array, and places all smaller (smaller than pivot)
to left of pivot and all greater elements to right
of pivot */
int partition(int low, int high) {
    int pivot=arr[high]; // pivot
    // Index of smaller element 
    // and indicates the right position of pivot found so far
    int i=(low-1); 
    for (int j=low; j<=high-1; j++) {
        // If current element is smaller than the pivot
        if (arr[j]<pivot) {
            i++; // increment index of smaller element
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}
/* The main function that implements QuickSort
arr[] --> Array to be sorted,
low --> Starting index,
high --> Ending index */
void quickSort(int low, int high) {
    if (low < high) {
        /* pi is partitioning index, arr[p] is now
        at right place */
        int pi = partition(low, high);
        // Separately sort elements before
        // partition and after partition
        quickSort(low, pi - 1);
        quickSort(pi + 1, high);
    }
}
```

### Merge Sort

Merge Sort is preferred over Quick Sort for linked lists. [Merge Sort](https://www.geeksforgeeks.org/merge-sort/)

### Hybrid Sort

Hybrid sort uses different sorting algorithms in different scenarios, and thus maintaining high performance across the cases.
For example, [pattern defeating sort](https://github.com/orlp/pdqsort) use insertion sort when the partition of target is slower than a preset threshold (24). For larger target size, it applies quicksort. Once it learns the partition of target is bad in its definition, it uses a fallback strategy (heap sort).
Other hybrid sorts include introsort, timsort, etc.

## Heap

## Stack

## Random 

### Mersenne Twister (MT19937)

The Mersenne Twister is a general-purpose pseudorandom number generator (PRNG). Its name derives from the fact that its period length is chosen to be a Mersenne Prime. [Read More on Wikipedia](https://en.wikipedia.org/wiki/Mersenne_Twister). MT19937 stands for mersenne twister with a long period of 219937 – 1 which means mt19937 produces a sequence of 32-bit integers that only repeats itself after 2^19937 – 1 number have been generated.

```c++
#include <ctime> 
#include <iostream>
#include <random>
using namespace std;
int main() {
  // Using the constructor to
  // initialize with a seed value
  mt19937 mt(time(nullptr));
  // Operator() is used to 
  // generate random numbers
  cout << mt();
  return 0;
}
```

## Search

### Binary Search

```c++
// assume target in candidates
vector<int>candidates;
// return index of target in candidates
int binary_search(int target) {
    int low=0, high=candidates.size();
    while(low<high) {
        int mid=(high-low)/2+low;
        if(candidates[mid]==target) {
            return mid;
        } else if(candidates[mid]>target) {
            high=mid;
        } else {
            low=mid+1;
        }
    }
    return low;
}
```

## Union Find

### With Path Compression

```c++
class UnionFind {
public:
    UnionFind(int n) {
        for(int i=0; i<n; i++) {
            parent.push_back(i);
            rank.push_back(0);
        }
    }
    int find(int x) {
        if(parent[x]!=x) {
            parent[x]=find(parent[x]);
        }
        return parent[x];
    }
    void unite(int x, int y) {
        x=find(x);
        y=find(y);
        if(x==y) return;
        if(rank[x]<rank[y]) {
            parent[x]=y;
        } else {
            parent[y]=x;
            if(rank[x]==rank[y]) rank[x]++;
        }
    }
    bool same(int x, int y) {
        return find(x)==find(y);
    }  
private:
    vector<int>parent;
    vector<int>rank;
};
```