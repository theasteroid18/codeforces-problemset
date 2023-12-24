# A. [String Generation](https://codeforces.com/problemset/problem/1461/A)

## 问题描述

要求构造一个长度n的字符串，满足：

1. 仅有a、b、c构成。
2. 任意是回文串的子串的长度都不大于k。（k>=1）



## 问题思路

乍一看题目无解，但是找到突破口就很简单。

考虑什么是回文串呢？从索引i开始，左右两边的值相等，长度对应+2。



所以，我们只需要想办法构造一个对应**任意i，左右两边的值都不相等**的字符串即可。所有是回文的子串的长度只能是1<=k，自然满足题目要求。



考虑：n=3的情况，有： abc

考虑：n=4的情况，有：abca

考虑：n=5的情况，有：abcab

考虑：n=6的情况，有：abcabc

...

得出结论：只需要不停地输出 a、b、c即可。



可以对长度分类：

1. 除3余0，长度为3x的只需要输出x个abc即可。
2. 除3余1，长度为3x+1的只需要输出x个abc和a即可。
3. 除3余2，长度为3x+2的只需要输出x个abc和ab即可。



三种的正确性都可以分别由数学归纳法证明。

## 实现代码

```c++
#include<iostream>

int t, n, k;
int main() {
	std::cin >> t;
	while(t--) {
		std::cin >> n >> k;
		for(int i = 0; i < n; i++) {
			char ch = 'a' + i % 3;
			std::cout << ch;
		}
		std::cout << "\n";
	}
	return 0;
}
```





## 要点

想到如何让回文串最小：长度1，左右相邻的值不相等。