# 题目内容
## 1128. 等价多米诺骨牌对的数量
[原题链接](https://leetcode-cn.com/problems/number-of-equivalent-domino-pairs/)  

给你一个由一些多米诺骨牌组成的列表 ```dominoes```。

如果其中某一张多米诺骨牌可以通过旋转 0 度或 180 度得到另一张多米诺骨牌，我们就认为这两张牌是等价的。

形式上，```dominoes[i] = [a, b]``` 和 ```dominoes[j] = [c, d]``` 等价的前提是 ```a==c``` 且 ```b==d```，或是 ```a==d``` 且 ```b==c```。

在 ```0 <= i < j < dominoes.length``` 的前提下，找出满足 ```dominoes[i]``` 和 ```dominoes[j]``` 等价的骨牌对 ```(i, j)``` 的数量。

 

示例：

    输入：dominoes = [[1,2],[2,1],[3,4],[5,6]]
    输出：1
 

提示：

    1 <= dominoes.length <= 40000
    1 <= dominoes[i][j] <= 9

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/number-of-equivalent-domino-pairs
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

    执行用时：4848 ms, 在所有 JavaScript 提交中击败了12.74%的用户
    内存消耗：41.9 MB, 在所有 JavaScript 提交中击败了93.14%的用户

在暴力的路上越走越远

## AC代码

```js
/**
 * @param {number[][]} dominoes
 * @return {number}
 */
var numEquivDominoPairs = function(dominoes) {
    let res=0
    const len=dominoes.length

    for(let i=0;i<len;i++){
        for(let j=i+1;j<len;j++){
            res+=((dominoes[i][0]==dominoes[j][0]&&dominoes[i][1]==dominoes[j][1])||(dominoes[i][0]==dominoes[j][1]&&dominoes[i][1]==dominoes[j][0]))?1:0
        }
    }

    return res
};
```