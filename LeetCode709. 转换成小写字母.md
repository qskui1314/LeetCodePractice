# 转换成小写字母 to-lower-case
## 题目
<a href="https://leetcode-cn.com/problems/to-lower-case/">题目链接</a>  
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。

示例 1：

    输入: "Hello"
    输出: "hello"
示例 2：

    输入: "here"
    输出: "here"
示例 3：

    输入: "LOVELY"
    输出: "lovely"

## 解题思路
因为我用的是C++，在C++中大写字母转换成小写字母是有专门的一个函数的，所以直接调用函数返回即可。  

一开始我的思路是直接把字符串当做一个字符数组处理，直接在字符数组内对每个字符进行处理。  

	class Solution {
	public:
		string toLowerCase(string str) {
			for(int i=0;i<str.length();i++)
				str[i]=tolower(str[i]);
			return str;
		}
	};
这次提交结果是8ms，4.4MB，从LeetCode提示的数据来看，这个算法距离最优解的差距很大。  

然后尝试着将直接对整个字符串进行操作：  

	class Solution {
	public:
		string toLowerCase(string str) {
			transform(str.begin(), str.end(), str.begin(), ::tolower);
			return str;
		}
	};
结果消耗的资源数量一模一样，此处涉及STL模板的具体原理，暂且按下不表（其实是我对内部原理不了解）。

想到js也有个专门用来转换大小写的函数，所以试了一下：

	/**
	 * @param {string} str
	 * @return {string}
	 */
	var toLowerCase = function(str) {
		return str.toLowerCase()
	};
这次占用资源直接涨到了96ms，14.5MB……js占资源大户果然名不虚传：）
