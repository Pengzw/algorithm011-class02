### 题解思路
```
根据一棵树的中序遍历与后序遍历构造二叉树。

注意:
你可以假设树中没有重复的元素。

例如，给出

中序遍历 inorder = [9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7
```
### 代码
```php
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     public $val = null;
 *     public $left = null;
 *     public $right = null;
 *     function __construct($value) { $this->val = $value; }
 * }
 */
class Solution {

    /**
     * @param Integer[] $inorder
     * @param Integer[] $postorder
     * @return TreeNode
     */
    /**
     * @param Integer[] $inorder
     * @param Integer[] $postorder
     * @return TreeNode
     */
    function buildTree($inorder, $postorder) {
        $this->inorder = $inorder;
        $this->postorder = $postorder;
        $this->inmap = array_flip($inorder);
        $this->postindex = count($postorder)-1;
        return $this->helper(0,count($inorder)-1);
    }
    
    private $inmap; //反转中序数组中所有键以及它们关联的值
    private $postindex; // 后序参数索引
    private $inorder;
    private $postorder;
    
    function helper($instart,$inend){
        if($instart > $inend) return null;
        $nodeval = $this->postorder[$this->postindex];
        $inindex = $this->inmap[$nodeval];
        $node = new TreeNode($nodeval);
        $this->postindex--;
        $node->right = $this->helper($inindex+1,$inend);
        $node->left = $this->helper($instart,$inindex-1);
        return $node;
    }
}
```
