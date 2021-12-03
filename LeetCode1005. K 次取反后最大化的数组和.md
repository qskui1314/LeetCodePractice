<!--
 * @Author: qskui1314
 * @Date: 2021-12-03 11:37:23
 * @LastEditTime: 2021-12-03 11:54:32
 * @LastEditors: qskui1314
 * @FilePath: \LeetCodePractice\LeetCode1005. K 次取反后最大化的数组和.md
-->
# 题目内容
## 1005. K 次取反后最大化的数组和
[原题链接](https://leetcode-cn.com/problems/maximize-sum-of-array-after-k-negations/)  

1005. K 次取反后最大化的数组和
给你一个整数数组 `nums` 和一个整数 `k` ，按以下方法修改该数组：

+ 选择某个下标 `i` 并将 `nums[i]` 替换为 `-nums[i]` 。

重复这个过程恰好 `k` 次。可以多次选择同一个下标 `i` 。

以这种方式修改数组后，返回数组 <b>可能的最大和</b> 。

 

示例 1：

    输入：nums = [4,2,3], k = 1
    输出：5
    解释：选择下标 1 ，nums 变为 [4,-2,3] 。
示例 2：

    输入：nums = [3,-1,0,2], k = 3
    输出：6
    解释：选择下标 (1, 2, 2) ，nums 变为 [3,1,0,2] 。
示例 3：

    输入：nums = [2,-3,-1,5,-4], k = 2
    输出：13
    解释：选择下标 (1, 4) ，nums 变为 [2,3,-1,5,4] 。
 

提示：

+ `1 <= nums.length <= 104`
+ `-100 <= nums[i] <= 100`
+ `1 <= k <= 104`

## 解题思路


## AC代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var largestSumAfterKNegations = function(nums, k) {

    // 先从小到大排序
    nums.sort(function(a, b){return a - b})
    
    for(let i=0;i<k;i++){
        // 如果最小值是负数，则将其取反，并重新排序
        nums[0]*=-1
        nums.sort(function(a, b){return a - b})
    }

    // 求和
    let res=0
    nums.forEach(e=>{
        res+=e
    })

    return res
};
```