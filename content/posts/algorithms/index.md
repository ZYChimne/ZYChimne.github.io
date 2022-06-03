---
title: "Algorithms"
description: "Algorithms Must Known"
date: "2022-05-01"
slug: "algorithms"
categories:
  - Algorithms
tags:
  - algorithms
---

## Tree

## String

### Split

C++ string doesn't have built-in split function. To split string into an array of substrings by a character,

```c++
vector<string> split(string str, char c){
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
