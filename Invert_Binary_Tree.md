翻转一棵二叉树。

示例：

输入：

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
输出：

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

```
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
    if (root === null) return root
    if (root.left !== null || root.right !== null) {
        let tempNode = root.right
        root.right = root.left
        root.left = tempNode
        invertTree(root.left)
        invertTree(root.right)
    }
    return root
};

```
