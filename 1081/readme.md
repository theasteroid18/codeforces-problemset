# A. [Definite Game](https://codeforces.com/problemset/problem/1081/A)

## 问题描述

给定整数n，可以执行下面操作任意次：

1. 选择一个正整数a（n%a!=0），然后把n 减去a



现在求n可能的最小值



## 问题思路

如果n等于1，显然不能再找到一个小于1的正整数。因此1就是n的最小值。



现在想办法：如何让n等于1？

我们都知道，一个数x与x-1一定互质，因此n一定与n-1互质。

所以可以快速地：n-(n-1)=1



但是**问题要求的并不是互质，而是不被整除**。当n等于2时，此时n-1=1，显然任何一个数都与1互质，任何一个数都被1整除。所以需要特判n=2时，此时无法选择n-1，因此输出2。



总结：

n=2？是，输出2。否则输出1



## 实现代码

```c++
#include<iostream>

int x;
int main(){
	std::cin >> x;
	if(x == 2) std::cout << "2\n";
	else std::cout << "1\n";
	return 0;
} 
```



## 要点

n与n-1一定互质