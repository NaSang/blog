## 剑指Offer[7]——斐波那契数列
### 问题描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。

n<=39
### 考点
- 递归和循环（？）

### 思路
针对f(i)，有用的信息只有f(i-1)和f(i-2)，迭代更新`x`和`y`两个变量即可。

### 代码
~~~cpp
class Solution {
 public:
  int Fibonacci(int n) {
    int x = 0, y = 1;
    while (n--) {
      y = x + y;
      x = y - x;
    }
    return x;
  }
};
~~~
