# A. [Mocha and Math](https://codeforces.com/problemset/problem/1559/A)

## 问题描述

给长度n的整数数组a，可以执行操作：选择l，r然后把a中[l,r]的每个元素与a中[l, r]翻转得到的元素按照位置一一做与操作。



现在想让数组a的最大值最小，求这个最大值。

## 问题思路

题目的数据范围里，数组a最小的元素是0，而0与任何数都是0.而操作可以让所有数都与0，因此如果有0，那么输出0.



贪心地想，如果存在被执行的l，r序列能够使得a的最大值最小，因为&操作是封闭的，所以顺序并没有要求。

先尝试把相邻的2个元素与操作。很快就会发现每次与都会导致相邻两个元素相等。从前往后走，会得到一个固定值。



而这个值就是最小值。因为其中每一位的1，每个a都包含，自然无法再小了。



综上：循环a，每个元素做&操作。

## 实现代码

```c++
#include<iostream>

int n, t;
int main () {
	std::cin >> t;
	while(t--) {
		int x;
		std::cin >> n >> x;
		for(int i = 1; i < n; i++) {
			int y;
			std::cin >> y;
			
			x &= y;
		}
		
		std::cout << x << "\n";
	}
	return 0;
} 
```



## 要点

发现先相邻2个元素与操作对最小值没有影响。发现循环执行相邻2个元素的与操作得到的结果就是最小值。