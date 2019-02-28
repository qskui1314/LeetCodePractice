# 重复 N 次的元素 n-repeated-element-in-size-2n-array
## 题目
[重复 N 次的元素](https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array/)  
在大小为 2N 的数组 A 中有 N+1 个不同的元素，其中有一个元素重复了 N 次。

返回重复了 N 次的那个元素。

示例 1：

	输入：[1,2,3,3]
	输出：3
示例 2：

	输入：[2,1,2,5,3,2]
	输出：2
示例 3：

	输入：[5,1,5,2,5,3,5,4]
	输出：5
 
提示：

	4 <= A.length <= 10000
	0 <= A[i] < 10000
	A.length 为偶数
## 解题思路
简单的先排序，然后查找重复元素

	class Solution {
	public:
			int repeatedNTimes(vector<int>& A) {
					sort(A.begin(),A.end());
					for(int i=1;i<A.size();i++){
							if(A[i]==A[i-1]){
									return A[i];
							}
					}
					return 0;
			}
	};
