# 有序数组的平方 squares-of-a-sorted-array
## 题目
<a href="https://leetcode-cn.com/problems/squares-of-a-sorted-array/">题目链接</a>  
给定一个按非递减顺序排序的整数数组 A，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。

示例 1：

    输入：[-4,-1,0,3,10]
    输出：[0,1,9,16,100]
示例 2：

	输入：[-7,-3,2,3,11]
	输出：[4,9,9,49,121]
提示：

	1.1 <= A.length <= 10000
	2.-10000 <= A[i] <= 10000
	3.A 已按非递减顺序排序。

## 解题思路
首先这是一个简单题，所以不需要考虑太多。  

需要的结果是数组A中每个数字的平方，然后对他们进行排序。又因为有负数，负数的平方会变成正数，所以提示中的第三条就可以直接跳过。  

根据题目给定的代码模板，本题中的数据以**vector**的方式给出，所以用访问vector的方法使用数据。  

因为只需要将数字变为原来的平方，所以直接对原数组进行操作就可以，然后使用C++的STL模板中的sort进行排序，最后返回排序后的A。

	class Solution {
	public:
		vector<int> sortedSquares(vector<int>& A) {
			for(int i=0;i<A.size();i++){
				A[i]*=A[i];
			}
			sort(A.begin(),A.end());
			return A;
		}
	};
