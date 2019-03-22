## 剑指offer[2]——替换空格.md
### 问题描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为`We Are Happy`，则经过替换之后的字符串为`We%20Are%20Happy`。

### 考点
- 字符串

### 思路
- 从前往后计算有多少个空格。
- 从后往前遍历字符串，如果遇到字符的不是空格，则将其向后移动`2*count`；（因为`%20`为3个字符，`' '`为1个字符，所以需要挪出2个字符的位置。）
否则，空格计数减1，往后`2*count`插入`%20`。

### 代码
~~~cpp
class Solution {
 public:
  void replaceSpace(char *str, int length) {
    int count = 0;
    for (int i = 0; i < length; i++) {
      if (str[i] == ' ') count++;
    }
    for (int i = length - 1; i >= 0; i--) {
      if (str[i] != ' ') {
        str[i + count * 2] = str[i];
      } else {
        count--;
        str[i + 2 * count] = '%';
        str[i + 2 * count + 1] = '2';
        str[i + 2 * count + 2] = '0';
      }
    }
  }
};
~~~
