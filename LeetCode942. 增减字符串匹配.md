# 增减字符串匹配 di-string-match
## 题目
[原题链接](https://leetcode-cn.com/problems/di-string-match/)  
给定只含 `"I"`（增大）或 `"D"`（减小）的字符串 `S` ，令 `N = S.length`。

返回 `[0, 1, ..., N]` 的任意排列 `A` 使得对于所有 `i = 0, ..., N-1`，都有：

如果 `S[i] == "I"`，那么 `A[i] < A[i+1]`
如果 `S[i] == "D"`，那么 `A[i] > A[i+1]`
 
示例 1：

	输出："IDID"
	输出：[0,4,1,3,2]
示例 2：

	输出："III"
	输出：[0,1,2,3]
示例 3：

	输出："DDI"
	输出：[3,2,0,1]
 
提示：

	1 <= S.length <= 1000
	S 只包含字符 "I" 或 "D"。
## 解题思路
1. 在例子中可以看出返回序列中的最大值N是输入字符串长度+1，输出是0-N
2. 每次的I或者D都是只和前一位相关的
3. 如果第一个是I，则输出的第一个是0，否则第一位就是N
4. 模板样例给的是动态数组vector，所以返回值也要是vector
5. 从给第二位开始，如果是I的话，就从大到小插入数组，反之就是从小到大，所以考虑双指针，考虑到指针耗时间比较多，所以采用两个标志数字记录的形式
第一次尝试：测试样例IDID通过，但是不能通过III的测试例子

		class Solution {
		public:
				vector<int> diStringMatch(string S) {
						vector<int> v;
						int flag1=0;
						int flag2=S.length();
						if(S[0]=='I'){
								v.push_back(0);
								flag1++;
						}
						else{
								v.push_back(S.length()+1);
								flag2--;
						}
						for(char& item : S){
								if(item=='I'){
										v.push_back(flag2);
										flag2--;
								}
								else{
										v.push_back(flag1);
										flag1++;
								}
						}
						return v;
				}
		};
倒推发现我只有检查增减错杂的情况，对于连续加/减的情况没做处理，所以出现这种错误
返回查看代码，加上和评论区对（chao）比（xi）发现问题可能出在我对第一个单独处理了
把对一个的单独处理部分删掉，然后改了一下向数组里插入的逻辑，就通过了

		class Solution {
		public:
				vector<int> diStringMatch(string S) {
						vector<int> v;
						int flag1=0,flag2=S.length();
						for(char& item : S){
								if(item=='I'){
										v.push_back(flag1);
										flag1++;
								}
								else{
										v.push_back(flag2);
										flag2--;
								}
						}
						v.push_back(flag1);
						return v;
				}
		};
