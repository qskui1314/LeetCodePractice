# 在排序数组中查找元素的第一个和最后一个位置
## 题目
[原题链接](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)  

34. 在排序数组中查找元素的第一个和最后一个位置
给定一个按照升序排列的整数数组 ```nums```，和一个目标值 ```target```。找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值 ```target```，返回 ```[-1, -1]```。

进阶：

* 你可以设计并实现时间复杂度为 ```O(log n)``` 的算法解决此问题吗？
 

示例 1：

    输入：nums = [5,7,7,8,8,10], target = 8
    输出：[3,4]
示例 2：

    输入：nums = [5,7,7,8,8,10], target = 6
    输出：[-1,-1]
示例 3：

    输入：nums = [], target = 0
    输出：[-1,-1]
 

提示：

* ```0 <= nums.length <= 105```
* ```-109 <= nums[i] <= 109```
* ```nums``` 是一个非递减数组
* ```-109 <= target <= 109```

## 解题思路

<details>
  <summary>走了几步弯路，一开始没考虑到不存在的情况，```WA```了一次，点击展开错误代码</summary>

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    let start=0
    let end=0
    let res=[]
    for(let i=0;i<nums.length;i++){
        if(nums[i]==target){
            start=i
            // console.log(nums[i])
            break
        }
    }
    for(let i=nums.length-1;i>start;i--){
        if(nums[i]==target){
            end=i
            break
        }
    }
    res.push(start)
    res.push(end)
    return res
};
```
</details>

<details>
  <summary>然后被只有一个```nums```只有一个数字的```WA```了一次，点击展开错误代码</summary>
  
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    let start=0
    let end=0
    let res=[]
    for(let i=0;i<nums.length;i++){
        if(nums[i]==target){
            start=i
            // console.log(nums[i])
            break
        }
    }
    for(let i=nums.length-1;i>start;i--){
        if(nums[i]==target){
            end=i
            break
        }
    }
    if(start==0&&end==0){
        start=end=-1
    }
    res.push(start)
    res.push(end)
    return res
};
```
</details>

都考虑进去以后AC了：
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    let start=-1
    let end=-1
    let res=[]
    for(let i=0;i<nums.length;i++){
        if(nums[i]==target){
            start=i
            // console.log(nums[i])
            break
        }
    }
    for(let i=nums.length-1;i>=start;i--){
        if(nums[i]==target){
            end=i
            break
        }
    }
    res.push(start)
    res.push(end)
    return res
};
```

但是……  

    执行用时：104 ms, 在所有 JavaScript 提交中击败了9.02%的用户
    内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了34.00%的用户

这就肯定是算法优化不够了，时间复杂度为``` O(log n) ```的算法才是题目中提到的最优解，题解里说的都是二分查找，需要再学习

## AC代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    let start=-1
    let end=-1
    let res=[]
    for(let i=0;i<nums.length;i++){
        if(nums[i]==target){
            start=i
            // console.log(nums[i])
            break
        }
    }
    for(let i=nums.length-1;i>=start;i--){
        if(nums[i]==target){
            end=i
            break
        }
    }
    res.push(start)
    res.push(end)
    return res
};
```