---
title: "Bit Manipulation"
description: "Bit Manipulation Tricks"
date: "2022-05-28"
slug: "bit-manipulation"
categories:
    - Algorithms
tags:
    - algorithms
---

Bit Manipulation is elegant, as it operates on bits and has unparalleled efficiency. It is also confusing and difficult to understand, because its algorithms are not intuitive. Here is my collection of bit manipulation tricks.

## Simple Bit Manipulation Tricks

* Set Union: A | B
* Set Intersection: A & B
* Set Subtraction: A & ~B
* Set Negation of All Bits: ^A or ~A
* Set Bit of A: A |= (1 << bit)
* Clear Bit: A & ~(1 << bit)
* Test Bit: (A & (1 << bit)) != 0
* Toggle Bit: (A ^ (1 << bit))
* Extract Last Bit: A & ~A or A & (A-1) or A ^ (A & (A-1))
* Remove Last Bit: A & (A-1)
* Get All 1 Bits: ~0
* Isolate Rightmost Bit: A & (-A)
* Propagate Rightmost Bit: (A | (A-1))
* Isolate Rightmost 0: ~A & (A+1)
* Turn on Rightmost 0 Bit: (A | (A+1))
* Contrast Number: ~A + 1 or (A ^ -1) + 1
* Modulo 2^A against B: A & (B - 1);
* Absolute Value: (A ^ (A >> 31)) - (A >> 31)
* Get Max Value: B & ((A-B) >> 31) | A & (~(A-B) >> 31)
* Get Min Value: A & ((A-B) >> 31) | B & (~(A-B) >> 31)

## Count the Number of Ones

```C++
int count_one(int n) {
    while(n) {
        n = n&(n-1);
        count++;
    }
    return count;
}
```

## Is Power of 2

```C++
int is_power_of_two(int n) {
    return !(n&(n-1));
}
```

## Is Power of 4

```C++
int mask = 0x55555555 // check the 1-bit location;
bool is_power_of_four(int n) {
    return !(n&(n-1)) && (n&mask);
}
```

## Sum of 2 Integers

```C++
int sum(int a, int b) {
    // be careful about the terminating condition
    return b==0? a:sum(a^b, (a&b)<<1); 
}
```
```C++
int sum(int a, int b) {
    while(b!=0){
        unsigned int c=(unsigned int)(a&b)<<1;
        a=a^b;
        b=c;
    }
    return a;
}
```
## Missing Number

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array. 
```C++
int missing_number(vector<int>& nums) {
    int ret = 0;
    for(int i = 0; i < nums.size(); ++i) {
        ret ^= i;
        ret ^= nums[i];
    }
    return ret^=nums.size();
}
```

## The Most Significant Bit

Find the largest power of 2 (most significant bit in binary form), which is less than or equal to the given number N.
```C++
long most_significant_bit(long n) {
    //changing all right side bits to 1.
    n = n | (n>>1);
    n = n | (n>>2);
    n = n | (n>>4);
    n = n | (n>>8);
    n = n | (n>>16);
    return (n+1)>>1;
}
```

## Reverse Bits

```C++
uint32_t reverse_bits(uint32_t n) {
    unsigned int mask = 1<<31, res = 0;
    for(int i = 0; i < 32; ++i) {
        if(n & 1) res |= mask;
        mask >>= 1;
        n >>= 1;
    }
    return res;
}
```
```C++
uint32_t reverse_bits(uint32_t n) {
    uint32_t mask = 1, ret = 0;
    for(int i = 0; i < 32; ++i){
        ret <<= 1;
        if(mask & n) ret |= 1;
        mask <<= 1;
    }
    return ret;
}
```
```C++
uint32_t reverse_bits(uint32_t n) {
    n = (n >> 16) | (n << 16);
    n = ((n & 0xff00ff00) >> 8) | ((n & 0x00ff00ff) << 8);
    n = ((n & 0xf0f0f0f0) >> 4) | ((n & 0x0f0f0f0f) << 4);
    n = ((n & 0xcccccccc) >> 2) | ((n & 0x33333333) << 2);
    n = ((n & 0xaaaaaaaa) >> 1) | ((n & 0x55555555) << 1);
    return n;
}
```
```C++
const uint32_t M1 = 0x55555555; // 01010101010101010101010101010101
const uint32_t M2 = 0x33333333; // 00110011001100110011001100110011
const uint32_t M4 = 0x0f0f0f0f; // 00001111000011110000111100001111
const uint32_t M8 = 0x00ff00ff; // 00000000111111110000000011111111
uint32_t reverse_bits(uint32_t n) {
    n = n >> 1 & M1 | (n & M1) << 1;
    n = n >> 2 & M2 | (n & M2) << 2;
    n = n >> 4 & M4 | (n & M4) << 4;
    n = n >> 8 & M8 | (n & M8) << 8;
    return n >> 16 | n << 16;
}
```

## Bitwise AND of Numbers Range

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.
```C++
int range_bitwise_and(int m, int n) {
    int a = 0;
    while(m != n) {
        m >>= 1;
        n >>= 1;
        a++;
    }
    return m<<a; 
}
```

## Number of 1 Bits

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).
```C++
int hamming_weight(uint32_t n) {
    int count = 0;
    while(n) {
        n = n&(n-1);
        count++;
    }
    return count;
}
```
```C++
int hamming_weight(uint32_t n) {
    long mask = 1;
    int count = 0;
    for(int i = 0; i < 32; ++i){ // 31 will not do, delicate
        if(mask & n) count++;
        mask <<= 1;
    }
    return count;
}
```
```C++
int hamming_weight(uint32_t z) {
    // each bit in n is a one-bit integer that indicates 
    // how many bits are set in that bit
    z = (z & 0x55555555) + ((z >> 1) & 0x55555555);
    // Now every two bits are a two bit integer that indicate 
    // how many bits were set in those two bits in the original number
    z = (z & 0x33333333) + ((z >> 2) & 0x33333333);
    // Now we're at 4 bits
    z = (z & 0x0f0f0f0f) + ((z >> 4) & 0x0f0f0f0f);
    z = (z & 0x00ff00ff) + ((z >> 8) & 0x00ff00ff);
    z = (z & 0x0000ffff) + ((z >> 16) & 0x0000ffff);
    // 32 bits
    return (int)z;
}
```

## Exchange Two Integers without Additional Parameters

```C++
a = a ^ b;
b = a ^ b;
a = a ^ b;
```

## Find Two Numbers Appearing Twice

```C++
vector<int> single_number(vector<int>& nums) {
    int sum=0;
    for(int& num:nums)sum^=num;
    int type1=sum==INT_MIN?sum:sum&(-sum), sum1=0;
    for(int& num:nums){
        if(num&type1){
            sum1^=num;
        }
    }
    return {sum1, sum^sum1};
}
```

## Binary Number with Alternating Bits

```C++
bool has_alternating_bits(int n) {
    long a = n ^ (n >> 1);
    return (a & (a + 1)) == 0;
}
```

## Number Complement

The complement of an integer is the integer you get when you flip all the 0's to 1's and all the 1's to 0's in its binary representation.
```C++
int find_complement(int num) {
    int highestBit=0;
    for(int i=1;i<31;i++){
        if(num>=(1<<i))highestBit=i;
        else break;
    }
    int mask=highestBit==30?0x7fffffff:((1<<(highestBit+1))-1);
    return num^mask;
}
```

## Counting Bits

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.
```C++
vector<int> count_bits(int n) {
    vector<int>res(n+1);
    for(int i=1;i<=n;i++){
        res[i]=res[i>>1]+(i&1);
    }
    return res;
}
```

## Maximum Product of Word Length

Given a string array words, return the maximum value of length(word[i]) * length(word[j]) where the two words do not share common letters. If no such two words exist, return 0.
```C++
int max_product(vector<string>& words) {
    int size=words.size();
    unordered_map<int, int>m;
    for(const string& word:words){
        int temp=0;
        for(const char& c:word){
            temp|=(1<<(c-'a')); // use bit to save space
        }
        if(!m.count(temp)||word.size()>m[temp]){
            m[temp]=word.size();
        }
    }
    int res=0;
    for(const auto& mask1:m){
        for(const auto& mask2:m){
            if((mask1.first&mask2.first)==0){
                res=max(res, mask1.second*mask2.second);
            }
        }
    }
    return res;
}
```

## References

* [A summary: how to use bit manipulation to solve problems easily and efficiently](https://leetcode.com/problems/sum-of-two-integers/discuss/84278/A-summary%3A-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently)
* [What USEFUL bitwise operator code tricks should a developer know about?](https://stackoverflow.com/questions/1533131/what-useful-bitwise-operator-code-tricks-should-a-developer-know-about)

## Additional Resources
* [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html)