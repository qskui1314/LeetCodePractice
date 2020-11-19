# 题目内容
## 题目
[原题链接](https://leetcode-cn.com/problems/move-zeroes/)  

283. 移动零
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

    输入: [0,1,0,3,12]
    输出: [1,3,12,0,0]

说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。  

通过次数250,440提交次数396,711

## 解题思路

这题思路应该是相当清晰容易的，把非0的数字按顺序移动到数组前面来，然后再后面补齐0就好了  
说明里提了一句必须在原数组上操作，一开始没看到，各种逻辑思路找了半天才发现，有点尴尬

## AC代码

``` JavaScript
 /* @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    const len=nums.length//长度
    let res=new Array()
    //下一个非0的位置
    var count=0
    //如果不是0，则按顺序插入到新数组中
    for(let i=0;i<len;i++){
        if(nums[i]!=0){
            nums[count]=nums[i]
            count++
        }
    }
    //最后补齐0
    for(let j=count;j<len;j++){
        nums[j]=0
    }
};
```