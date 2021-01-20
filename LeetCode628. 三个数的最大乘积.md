# 题目内容
## 三个数的最大乘积
[原题链接](此处放https://leetcode-cn.com/problems/maximum-product-of-three-numbers/网页链接)  

给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。

示例 1:

    输入: [1,2,3]
    输出: 6
示例 2:

    输入: [1,2,3,4]
    输出: 24
注意:

· 给定的整型数组长度范围是[3,104]，数组中所有的元素范围是[-1000, 1000]。
· 输入的数组中任意三个数的乘积不会超出32位有符号整数的范围。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximum-product-of-three-numbers
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## AC代码

执行用时：160 ms, 在所有 JavaScript 提交中击败了21.27%的用户 内存消耗：41.8 MB, 在所有 JavaScript 提交中击败了72.71%的用户

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumProduct = function(nums) {
    let ffz = 0
    let res = 0
    // 降序排序
    const numarray=nums.sort(
        function(a,b){
			return b - a;
		}
    )
    // 排序后前三位的乘积，和第一位以及最后两位的乘积，取较大的那个
    return numarray[0]*numarray[numarray.length-1]*numarray[numarray.length-2]>numarray[0]*numarray[1]*numarray[2]?numarray[0]*numarray[numarray.length-1]*numarray[numarray.length-2]:numarray[0]*numarray[1]*numarray[2]
};
```