## 剑指Offer[6]——旋转数组的最小数字
### 问题描述
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。 输入一个非减排序的数组的一个旋转，输出旋转数组的最小元素。 

例如数组`{3,4,5,1,2}`为`{1,2,3,4,5}`的一个旋转，该数组的最小值为1。

NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。
### 考点
- 查找
- 排序
### 思路
`旋转数组`的特点是，可以分为左右两部分非递减序列。

如，`{3,4,5,1,2}`可分为①`{3,4,5}`和②`{1,2}`。

可以采用二分查找，根据array[mid]和array[high]的大小关系，可以判断出mid所指向的数字是属于①还是属于②。

我们需要返回的，就是序列②中的第一个数字。

特殊情况，如`{1,1,1,0,1,1}`，无法判断mid指向的数字属于哪个part，所以只能逐步缩小范围。

### 代码
~~~cpp
class Solution {
 public:
  int minNumberInRotateArray(vector<int> rotateArray) {
    if (rotateArray.size() == 0) return 0;
    int low = 0, high = rotateArray.size() - 1;
    while (low < high) {
      int mid = low + (high - low) / 2;
      if (rotateArray[mid] > rotateArray[high]) { /* mid 指向part① */
        low = mid + 1;  /* important！！*/
      } else if (rotateArray[mid] < rotateArray[high]) { /* mid 指向part② */
        high = mid;
      } else {  /* 无法确定 */
        high = high - 1;
      }
    }
    return rotateArray[low]; /* return rotateArray[high] 同样正确 */
  }
};
~~~
