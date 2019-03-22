## 剑指Offer[3]——从尾到头打印链表
### 问题描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。
### 考点
- 栈
- 队列

### 思路
入队：将元素进栈A

出队：判断栈B是否为空，如果为空，则将栈A中所有元素pop，并push进栈B，栈B出栈；
**如果不为空，栈B直接出栈。**

### 代码
~~~cpp
class Solution {
 public:
  void push(int node) { 
    stack1.push(node); 
  }

  int pop() {
    if (stack2.empty()) {
      while (!stack1.empty()) {
        stack2.push(stack1.top());
        stack1.pop();
      }
    }
    int value = stack2.top();
    stack2.pop();
    return value;
  }

 private:
  stack<int> stack1;
  stack<int> stack2;
};
~~~
