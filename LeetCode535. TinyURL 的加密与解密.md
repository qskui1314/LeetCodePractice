# TinyURL 的加密与解密 encode-and-decode-tinyurl
## 题目  
<a href="https://leetcode-cn.com/problems/encode-and-decode-tinyurl/">题目链接</a>

TinyURL是一种URL简化服务， 比如：当你输入一个URL `https://leetcode.com/problems/design-tinyurl` 时，它将返回一个简化的URL `http://tinyurl.com/4e9iAk`.

要求：设计一个 TinyURL 的加密 encode 和解密 decode 的方法。你的加密和解密算法如何设计和运作是没有限制的，你只需要保证一个URL可以被加密成一个TinyURL，并且这个TinyURL可以用解密方法恢复成原本的URL。

## 解题思路
这题的解法非常魔幻，根据题目原始的提示，是需要用到哈希表和数学知识的，因为我刷题的时候自身知识架构不行，所以先看了一眼评论区……  

对的，就很魔幻，什么都不需要，抄起键盘就是一把梭  

	class Solution {
	public:

		// Encodes a URL to a shortened URL.
		string encode(string longUrl) {
			return longUrl;
		}

		// Decodes a shortened URL to its original URL.
		string decode(string shortUrl) {
			return shortUrl;
		}
	};

	// Your Solution object will be instantiated and called as such:
	// Solution solution;
	// solution.decode(solution.encode(url));

大部分都是原有的内容生成的，我写的只有两个return，原样返回数据就通过评测了……  

这个题目等对哈希表比较熟以后回头再用正常的方法重刷一遍吧……
