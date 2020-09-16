# 翻转二叉树 Invert Binary Tree
## 题目
[原题链接](https://leetcode-cn.com/problems/invert-binary-tree/)  

翻转一棵二叉树。

示例：

输入：

         4
       /   \
      2     7
     / \   / \
    1   3 6   9
输出：

         4
       /   \
      7     2
     / \   / \
    9   6 3   1
备注:
这个问题是受到 Max Howell 的 原问题 启发的 ：

谷歌：我们90％的工程师使用您编写的软件(Homebrew)，但是您却无法在面试时在白板上写出翻转二叉树这道题，这太糟糕了。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/invert-binary-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
  
## 解题思路  
直接交换所有左右子树
  
    /**
    * Definition for a binary tree node.
    * function TreeNode(val) {
    *     this.val = val;
    *     this.left = this.right = null;
    * }
    */
    /**
    * @param {TreeNode} root
    * @return {TreeNode}
    */
    var invertTree = function(root) {
        if(!root){
            return null;
        }
        let temp=root.right
        root.right=root.left
        root.left=temp

        invertTree(root.left)
        invertTree(root.right)
        return root
    };