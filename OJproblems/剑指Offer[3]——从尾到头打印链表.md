## 剑指Offer[3]——从尾到头打印链表
### 问题描述
输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。

### 考点
- 链表

### 思路
善用STL即可通过，如`vector`容器的`insert()`函数。

### 代码
~~~cpp
class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        vector<int> ans;
        ListNode *p = head;
        while(p) {
            ans.insert(ans.begin(),p->val);
            p = p->next;
        }
        return ans;
    }
};
~~~
