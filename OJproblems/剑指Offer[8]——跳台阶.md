## 剑指Offer[8]——跳台阶
### 问题描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

### 考点
- 循环和递归

### 思路
反过来思考，如果最后一步跳1级台阶，则只需考虑 n-1 级台阶有多少种跳法；如果最后一步跳2级台阶，则只需考虑 n-2 级台阶有多少种跳法。
二者相加即为所求。

### 代码
- 递归，时间开销特别大
~~~cpp
class Solution {
 public:
  int jumpFloor(int number) {
    if (number == 1 || number == 0) return 1;
    return jumpFloor(number - 1) + jumpFloor(number - 2);
  }
};
~~~

- 斐波那契数列，方法同上题。
~~~cpp
class Solution {
public:
    int jumpFloor(int number) {
        int x = 1, y = 2;
        while(--number){
            y = x + y;
            x = y - x;
        }
        return x;
    }
};
~~~
