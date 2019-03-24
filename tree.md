## 目录
[0104. 二叉树的最大深度](#0104)    
[0226. 翻转二叉树](#0226)  
[0617. 合并二叉树](#0617)    

## 0104. 二叉树的最大深度 (Easy) <a name="0104"></a>
#### 题目描述
给定一个二叉树，找出其最大深度。  
二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。  
**说明**: 叶子节点是指没有子节点的节点。  
#### 示例 1
```html
给定二叉树 [3,9,20,null,null,15,7]，
    3
   / \
  9  20
    /  \
   15   7
return its depth = 3.
```
#### 代码
``` python3
def maxDepth(self, root: TreeNode) -> int:
        if root is None:
            return 0
        else:
            return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```
LeetCode: https://leetcode.com/problems/maximum-depth-of-binary-tree/

## 0226. 翻转二叉树 (Easy) <a name="0226"></a>
#### 题目描述
翻转一棵二叉树。  
#### 示例 1
```html
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
```
#### 代码
``` python3
def invertTree(self, root: TreeNode) -> TreeNode:
        if root is not None:
            temp = root.right
            root.right = root.left
            root.left = temp
            root.left = self.invertTree(root.left)
            root.right = self.invertTree(root.right)
        return root
```
LeetCode: https://leetcode.com/problems/invert-binary-tree/

## 0617. 合并二叉树 (Easy) <a name="0617"></a>
#### 题目描述
给定两个二叉树，想象当你将它们中的一个覆盖到另一个上时，两个二叉树的一些节点便会重叠。   
你需要将他们合并为一个新的二叉树。合并的规则是如果两个节点重叠，那么将他们的值相加作为节点合并后的新值，否则不为**NULL**的节点将直接作为新二叉树的节点。  
#### 示例 1
```html
Input:
       Tree 1                     Tree 2
          1                         2
         / \                       / \
        3   2                     1   3
       /                           \   \
      5                             4   7

Output:
         3
        / \
       4   5
      / \   \
     5   4   7
```
**注意**: 合并必须从两个树的根节点开始。
#### 代码
``` python3
def mergeTrees(self, t1: TreeNode, t2: TreeNode) -> TreeNode:
        if t1 is None and t2 is None:
            return None
        elif t2 is None:
            return t1
        elif t1 is None:
            return t2
        else:
            t = TreeNode(t1.val + t2.val)
            t.left = self.mergeTrees(t1.left, t2.left)
            t.right = self.mergeTrees(t1.right, t2.right)
            return t
}
```
LeetCode: https://leetcode.com/problems/merge-two-binary-trees/