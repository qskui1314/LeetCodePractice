# 按递增顺序显示卡牌 reveal-cards-in-increasing-order
## 题目
[原题链接](https://leetcode-cn.com/problems/reveal-cards-in-increasing-order/)  
牌组中的每张卡牌都对应有一个唯一的整数。你可以按你想要的顺序对这套卡片进行排序。

最初，这些卡牌在牌组里是正面朝下的（即，未显示状态）。

现在，重复执行以下步骤，直到显示所有卡牌为止：

从牌组顶部抽一张牌，显示它，然后将其从牌组中移出。
如果牌组中仍有牌，则将下一张处于牌组顶部的牌放在牌组的底部。
如果仍有未显示的牌，那么返回步骤 1。否则，停止行动。
返回能以递增顺序显示卡牌的牌组顺序。

答案中的第一张牌被认为处于牌堆顶部。

示例：

	输入：[17,13,11,2,3,5,7]
	输出：[2,13,3,11,5,17,7]
	解释：
	我们得到的牌组顺序为 [17,13,11,2,3,5,7]（这个顺序不重要），然后将其重新排序。
	重新排序后，牌组以 [2,13,3,11,5,17,7] 开始，其中 2 位于牌组的顶部。
	我们显示 2，然后将 13 移到底部。牌组现在是 [3,11,5,17,7,13]。
	我们显示 3，并将 11 移到底部。牌组现在是 [5,17,7,13,11]。
	我们显示 5，然后将 17 移到底部。牌组现在是 [7,13,11,17]。
	我们显示 7，并将 13 移到底部。牌组现在是 [11,17,13]。
	我们显示 11，然后将 17 移到底部。牌组现在是 [13,17]。
	我们展示 13，然后将 17 移到底部。牌组现在是 [17]。
	我们显示 17。
	由于所有卡片都是按递增顺序排列显示的，所以答案是正确的。
 
提示：

	1 <= A.length <= 1000
	1 <= A[i] <= 10^6
	对于所有的 i != j，A[i] != A[j]
## 解题思路
先放结果

	var deckRevealedIncreasing = function(deck) {
		deck.sort((a,b) => {
			return b-a; 
		});
		var temp=new Array()
		var result=new Array()
		for (var i=deck.length;i>1;i--){
			result.unshift(deck.shift())
			result.unshift(result.pop())
		}
		result.unshift(deck.pop())
		return result;
	};
一开始是先排序然后再放到一个地方里，前一下后一下，全都放进去以后再输出  
然而C++里这个东西我并不会，所以考虑使用JavaScript  
一开始的思路是先把数据排序，然后颠倒一下，这样就可以从末位开始提取数据  
每提取一个，就放到输出结果中，然后点到一下输出结果的顺序，做到模拟示例过程的效果  
首先尝试使用数组函数shift提取并push到结果中  

	var deckRevealedIncreasing = function(deck) {
		deck.sort()
		deck.reverse()
		var result=new Array()
		while(deck){
			var temp=deck.shift()
			result.push(temp)
			deck.reverse()
		}
		return result;
	};
但是直接编译错误，接着尝试for循环，将数组中的一位一位拿来放到结果中

	var deckRevealedIncreasing = function(deck) {
		deck.sort()
		deck.reverse()
		var result=new Array()
		for (var i=0;i<deck.length;i++){
			result.push(deck)
			result.reverse()
		}
		return result;
	};
这样就可以完成输出，但是输出的结果和预期不一致，所以考虑是规律没找对的原因  
回头重新观察规律，发现是每次更改都是先把最后一个数字挪到第一位，然后再在最前面加上下一个要加进去的数字  
一直在尝试更改排序算法，但是数字部分一直不对，查了资料才知道js的sort算法排序是会默认先用一次.tostring()再排序的，所以要处理一下sort才能用

	var deckRevealedIncreasing = function(deck) {
		deck.sort((a,b) => {
			return b-a; 
		});
		var temp=new Array()
		var result=new Array()
		for (var i=deck.length;i>1;i--){
			result.unshift(deck.shift())
			result.unshift(result.pop())
		}
		result.unshift(deck.pop())
		return result;
	};
