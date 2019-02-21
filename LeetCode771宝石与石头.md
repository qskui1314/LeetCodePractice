# 宝石与石头 Jewels and Stones  
## 题目  
<a href="https://leetcode-cn.com/problems/jewels-and-stones/">原题链接</a>  
给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

示例 1:

输入: J = "aA", S = "aAAbbbb"
输出: 3
示例 2:

输入: J = "z", S = "ZZ"
输出: 0
注意:

S 和 J 最多含有50个字母。
 J 中的字符不重复。
 
 ## 解题思路
因为LeetCode直接给定的数据是两个字符串的形式，所有可以直接操作字符串。题目确定字符串J中不会有重复的，所需要的结果是字符串S中所有和J中相同更多字符的数量，所以直接用双层for来一一类比即可。最终把重复的次数返回。
第一次尝试我用了常用的简单语法，在for循环内的参数用了.length()计算数组长度，所有执行时间比较长，时间用了20ms

    class Solution {
    public:
        int numJewelsInStones(string J, string S) {
        int sum=0;
        for(int m=0;m<J.length();m++)
            for(int n=0;n<S.length();n++)
                if(J[m]==S[n])
                    sum++;
        return sum;
        }
    };

第二次先把两个数组的长度放到了常量里，这样不需要一直重复的调用length函数，执行时间缩短到了12ms，相当于节约了40%的时间（本身需求的体量比较小）

    class Solution {  
    public:  
        int numJewelsInStones(string J, string S) {  
        int sum=0;  
        int jl=J.length();  
        int sl=S.length();  
        for(int m=0;m<jl;m++)  
            for(int n=0;n<sl;n++)  
                if(J[m]==S[n])  
                    sum++;  
        return sum;  
        }  
    };
