# 204. 计数质数
## 题目
[原题链接](https://leetcode-cn.com/problems/count-primes/)  

统计所有小于非负整数 n 的质数的数量。

 

示例 1：

    输入：n = 10
    输出：4
    解释：小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。

示例 2：

    输入：n = 0
    输出：0

示例 3：

    输入：n = 1
    输出：0
 

提示：

    0 <= n <= 5 * 106

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/count-primes
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

一开始思路就很单纯：判断是不是质数，是的话结果集+1，不是的话请下一位数字，结果又是喜闻乐见的```	超出时间限制```，这是这次的代码：  
超时这次的输入用例是```499979```

```JS
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
    let res=0
    for(let i=0;i<n;i++){
        res+=IsZS(i)
    }
    return  res
};

function IsZS(n){
    if(n==0||n==1){
        return 0
    }
    if(n==2){
        return 1
    }
    let count=0
    for(let i=2;i<(n-1)/2;i++){
        if(Math.round(n%i)==0)
        count++
    }
    if(count>0){
        return 0
    }
    else{
        // console.log(n)
        return 1
    }
}
```

我又试着精简了一下这次提交的代码，结果同样是```超出时间限制```，考虑重新调整一下算法：

```Js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
    let res=0
    for(let i=0;i<n;i++){
        res+=IsZS(i)
    }
    return  res
};

function IsZS(n){
    if(n==0||n==1){
        return 0
    }
    if(n==2){
        return 1
    }
    for(let i=2;i<(n+1)/2;i++){
        if(Math.round(n%i)==0)
        return 0
    }
    return 1
}
```

    看到一条直击我灵魂的评论———
    wang-154
    wang
    10 分钟前
    看到简单题，我啪的一下就点进来了，很快啊！！！ 一提交，超时了 (oﾟvﾟ)ノ

从解析推答案，判断是否质数的部分精简以后，时间省下非常多

从判断质数的方法，可以得出中间少了很多类似于重复的数，选择性地去挑选判断

## AC代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
    let res=0
    for(let i=0;i<n;i++){
        res+=IsZS(i)
    }
    return  res
};

function IsZS(n){
    if(n==0||n==1){
        return 0
    }
    if(n==2){
        return 1
    }
    for(let i=2;i * i <= n;i++){
        if(Math.round(n%i)==0)
        return 0
    }
    return 1
}
```