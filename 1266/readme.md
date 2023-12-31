# B. [Dice Tower](https://codeforces.com/problemset/problem/1266/B)

## 问题描述

给定整数x，判断能否用数个堆叠在一起的骰子，满足：

1. 骰子塔上面可见的数的和等于x



## 问题思路

如果只有1个骰子，它的和是从1加到6=21，可以有选择地把底面隐藏，也就是：

只有1个骰子，能取到的值有：15、16、17、18、19、20。



如果只有2个骰子，上面那一个需要去除底面，所以取值和上面一样，需要重新探讨的是会被去掉对边两面的放在下面的骰子。



骰子的对边的和有：

1 6=7

2 5=7

3 4=7

发现其和都是7，所以加上一个放在底部的骰子，其增加的值是固定的：21-7=14。



因此，对于x，我们可以把它对14取余再加上14。此时x的取值范围在 [14, 27]。



如果x是在[15, 20]，那么就是可以构造出来的，输出YES

否则，无法构造，输出NO



总结：

令x = (x % 14) + 14

如果 15 <= x <= 20，输出YES

否则，输出ＮＯ



## 实现代码

```c++
#include<iostream>

int t;

int main() {
	std::cin >> t;
	while(t--) {
		long long x, y;
		std::cin >> x;
		y = (x % 14) + 14;
		if(15 <= x && 15 <= y && y <= 20) std::cout << "YES\n";
		else std::cout << "NO\n";
	}
	return 0;
} 
```



## 要点

找规律，发现n个筛子的和在：x + (n-1) * 14（15  <= x <= 20）