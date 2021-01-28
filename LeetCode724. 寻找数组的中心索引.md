# 题目内容
## 724. 寻找数组的中心索引
[原题链接](https://leetcode-cn.com/problems/find-pivot-index/)  

给定一个整数类型的数组 ```nums```，请编写一个能够返回数组 “中心索引” 的方法。

我们是这样定义数组 中心索引 的：数组中心索引的左侧所有元素相加的和等于右侧所有元素相加的和。

如果数组不存在中心索引，那么我们应该返回 -1。如果数组有多个中心索引，那么我们应该返回最靠近左边的那一个。

 

示例 1：

输入：
nums = [1, 7, 3, 6, 5, 6]
输出：3
解释：
索引 3 (nums[3] = 6) 的左侧数之和 (1 + 7 + 3 = 11)，与右侧数之和 (5 + 6 = 11) 相等。
同时, 3 也是第一个符合要求的中心索引。
示例 2：

输入：
nums = [1, 2, 3]
输出：-1
解释：
数组中不存在满足此条件的中心索引。
 

说明：

nums 的长度范围为 [0, 10000]。
任何一个 nums[i] 将会是一个范围在 [-1000, 1000]的整数。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/find-pivot-index
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

走了点弯路，一开始很自然地当做左右都至少有一个数，结果给两个测试用例教做人  
提交以后运行效率不高，参考评论区，通过少一次循环计算省了很多内存

## AC代码

执行用时：332 ms, 在所有 JavaScript 提交中击败了20.05%的用户
内存消耗：39.9 MB, 在所有 JavaScript 提交中击败了85.01%的用户

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
// 评论区思路@帕吉先生：左求和*2+中心索引值 = 总和
var pivotIndex = function(nums) {
    let left=0
    let sum=0
    const len=nums.length
    for(let s=0;s<len;s++){
        sum+=nums[s]
    }
    for(let i=0;i<len;i++){
        for(let l=0;l<i;l++){
            left+=nums[l]
        }
        if(left*2+nums[i]==sum)
            return i
        left=0
    }
    return -1
};

// 效率低
// 分别左右求和，然后相加
// var pivotIndex = function(nums) {
//     let left=0
//     let right=0
//     const len=nums.length
//     for(let i=0;i<len;i++){
//         for(let l=0;l<=i;l++){
//             left+=nums[l]
//         }
//         for(let r=i;r<len;r++){
//             right+=nums[r]
//         }
//         if(left==right)
//             return i
//         left=right=0
//     }
//     return -1
// };
```