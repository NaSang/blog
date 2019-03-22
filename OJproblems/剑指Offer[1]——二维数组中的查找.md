### 问题描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

### 考点
- 数组
- 查找

### 思路
![image](http://github.com/NaSang/blog/OJproblems/images/offer1.png)

如图所示，从左下或者右上角开始搜索，即可以有明确的搜索方向。

### 代码
~~~cpp
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int row = array.size();
        int col = array[0].size();
        int i = row-1, j = 0;
        while(i>=0 && j<col){
            if(target > array[i][j]) j++;
            else if(target <array[i][j]) i--;
            else return true;
        }
        return false;
    }
};
~~~
