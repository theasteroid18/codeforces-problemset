# A. [Suborrays](https://codeforces.com/problemset/problem/1391/A)

## 问题描述

要求构造长度n的1到n的全排列p，满足：p的所有连续子串的或>=连续子串的长度。



## 问题思路

乍一看没有思路，尝试在长度上找突破口。



先从简单的1和n开始：

子串长度为1很简单，因为最小值都>=1，所以没有提供有价值的信息。

子串长度为n，如果以n作为基础，开始往上面与1 2 3 ... n-1。因为是或操作，所以结果不会比原来的小，因此1-n的或必然大于等于n。



研究长度n的时候，注意到：或操作相当于加法。因此我们应该让：

每个长度为1的子数组中，存在x >= 1.

每个长度为2的子数组中，存在x >= 2.

每个长度为3的子数组中，存在x >= 3.

...

每个长度为n的子数组中，存在x >= n.



考虑一个从1到n的升序全排列：

它以1开头，j作为结尾（j >= 1)，显然它有n种可能，并且每种都是符合要求的。

它以2开头，j作为结尾呢(j >= 2)？显然也全是满足的。因为构成同等长度的子数组的最大值会比前一个的（以1开头的）要大，既然以1

开头的能够满足要求，所以以2开头的也是满足的。



这个结论可以很快推广到n上面。

总之：输出1到n即可。



## 实现代码

```c++
#include<iostream>

int t, n;
int main() {
	std::cin >> t;
	while(t--) {
		std::cin >> n;
		for(int i = 1; i <= n; i++) {
			std::cout << i << " ";
		}
		std::cout << "\n";
	}
	return 0;
}
```



## 要点

把题目的要求转换为：长度i的子数组必须存在x，x >= i。