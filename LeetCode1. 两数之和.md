# 两数之和 two-sum
## 题目
[原题链接](https://leetcode-cn.com/problems/two-sum/submissions/)  
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:

    给定 nums = [2, 7, 11, 15], target = 9

    因为 nums[0] + nums[1] = 2 + 7 = 9
    所以返回 [0, 1]
## 解题思路
这是一个非常有特色的题目，因为在以前从来都没有见过返回一个提示是一个数组的形式，也就是因为这个，所以在这一题上研究了很久……  
一开始对vector的返回形式不了解，所以尝试  

	class Solution {
	public:
			vector<int> twoSum(vector<int>& nums, int target) {
					for(int i=0;i<nums.size();i++)
							for(int j=i+1;j<nums.size();j++)
									if((nums[i]+nums[j])==target)
											return nums;
			}
	};
这样直接在编译的时候就出错，没看懂提示，主要也是不懂怎么处理这种返回值，然后默默打开搜索引擎  
在查资料的时候发现要做成vector（或者哈希表）之类比较高级的东西来返回，然而我并不会……就找到了之前的错误的原因  
后来根据其他人都解法，新建一个vector，然后用push_back()方法来赋值，最后返回就行，但是这样不管是时间还是空间的复杂度都太大，只击败了不到1%的用户……  
emmm先学习，以后再来优化算法吧  

	class Solution {
	public:
		vector<int> twoSum(vector<int>& nums, int target) {
			vector<int> twoSum;
			for(int i=0;i<nums.size();i++)
				for(int j=i+1;j<nums.size();j++)
					if((nums[i]+nums[j])==target){
						twoSum.push_back(i);
						twoSum.push_back(j);
					}
			return twoSum;
		}
	};
