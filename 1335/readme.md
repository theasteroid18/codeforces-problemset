# B. [Construct the String](https://codeforces.com/problemset/problem/1335/B)

## 问题描述

给定三个整数：n，a，b。要求构造一个仅有小写字母组成的字符串s，s满足：

1. 所有长度为a的子串里面恰好有b个不同的字符



注意：b <= a

## 问题思路

需要对b分类讨论：

b需要我们从字母集合S：'a' ，'b'， 'c' ，...， 'a' + b - 1 中选择一个元素作为s中成员。



假设b=a，那么显然这个s可以是：i循环n次，每个i对b取余，并输出 i+'a'。这种便是一个循环，所有元素都在集合S中，且每个长度a的子串，恰好有b个不同的字符，额外的每个字符只出现一次。

假设b=a-1呢？**依旧选择b=a时的构造得到的s数组，不过此时长度为a的框变成了长度为a+1**。它需要比之前要额外吃掉一个字符，但是因为此时的s中每个元素都在集合S中，所以去重后依旧是b个字符。所以b=a-1时，这种构造得到的s也是满足的。

假设b=a-2呢？相当于a变成了a+2，但无论范围怎样扩大，a > b且s中所有元素都在S，所有长度为a的子串里面都有b个不同的字符。



总结：

i从0开始，循环n次，每个i对b取余，并输出 i+'a'



## 实现代码

```c++
#include<iostream>

int t, n, a, b;
int main() {
	std::cin >> t;
	while(t--) {
		std::cin >> n >> a >> b;
		
		for(int i = 0; i < n; i++) {
			std::cout << (char)(i % b + 'a');
		}
		std::cout << "\n";
	}
	return 0;
} 
```



## 要点

构造b=a时的s，发现s在b<=a的情况下都满足
