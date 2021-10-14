# 题目内容
## 题目
[852. 山脉数组的峰顶索引](https://leetcode-cn.com/problems/peak-index-in-a-mountain-array/)  
[剑指 Offer II 069. 山峰数组的顶部](https://leetcode-cn.com/problems/B1IidL/)  

这道题比较特殊，一模一样的题目，存在两个合集里

符合下列属性的数组 `arr` 称为 山脉数组 ：
+ arr.length >= 3
+ 存在 `i`（`0 < i < arr.length - 1`）使得：
  + `arr[0] < arr[1] < ... arr[i-1] < arr[i]`
  + `arr[i] > arr[i+1] > ... > arr[arr.length - 1]`
给你由整数组成的山脉数组 `arr` ，返回任何满足 `arr[0] < arr[1] < ... arr[i - 1] < arr[i] > arr[i + 1] > ... > arr[arr.length - 1]` 的下标 ``i` 。

 

示例 1：

    输入：arr = [0,1,0]
    输出：1
示例 2：

    输入：arr = [0,2,1,0]
    输出：1
示例 3：

    输入：arr = [0,10,5,2]
    输出：1
示例 4：

    输入：arr = [3,4,5,1]
    输出：2
示例 5：

    输入：arr = [24,69,100,99,79,78,67,36,26,19]
    输出：2
 

提示：

+ `3 <= arr.length <= 104`
+ `0 <= arr[i] <= 106`
+ 题目数据保证 `arr` 是一个山脉数组
 

进阶：很容易想到时间复杂度 `O(n)` 的解决方案，你可以设计一个 `O(log(n))` 的解决方案吗？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/peak-index-in-a-mountain-array
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

这题格外的简单（没追求最优解的情况下）

直接找出第一个会比后面数字大的值的索引，然后返回就可以了

## AC代码

```js
/**
 * @param {number[]} arr
 * @return {number}
 */
var peakIndexInMountainArray = function(arr) {
    for(let i=0;i<arr.length-1;i++){
        if(arr[i]>arr[i+1])
            return i;
    }
};
```