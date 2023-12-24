# A. [Kids Seating](https://codeforces.com/problemset/problem/1443/A)

## 问题描述

从1到4*n，找出n个数，满足：

1. 任意两两不互质。
2. 任意两两不被整除。

## 问题思路

两两不互质？

假设选出来的n个数有超过1个质数，那么必然存在两两互质的，舍去。

如果有且仅有一个质数，那么它必然与非1的数互质，但如果加上1，第二个条件就不满足。



故n个数必然都不是质数。



任意两两不互质，代表**所有元素都有一个大于1的公因子。**



可以让这个因子是2，于是有4 6 8 ... 2n+2 这n个数。但是注意到8被4整除，所以有部分数需要舍去。



这里简单起见，这里不妨倒着选择：4n 4n-2 4n-4 ... 2n+2，这n个数。

首先它们都被2整除，满足任意两两不互质。

其次，2n+2 乘 2 比 最大值4n要大，代表数组所有元素都不被2n+2整除。同理数组所有元素都不被2n+4整除 .... 这样一直做下去，可以证明，数组任意两两不被整除。



## 实现代码

```c++
#include<iostream>

int t, n;
int main() {
	std::cin >> t;
	while(t--) {
		std::cin >> n;
		for(int i = 4 * n; i >= 2 * n + 2; i -= 2) {
			std::cout << i << " ";
		}
		std::cout << "\n";
	}
	return 0;
}
```



## 要点

倒着找公因数2