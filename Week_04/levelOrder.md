### 解题思路
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

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
     * @param TreeNode $root
     * @return Integer[][]
     */
    function levelOrder($root) {
        //层序遍历
        $res = [];
        $this->helper($root,0,$res);
        return $res;
    }

    function helper($root, $level, &$res) {
        if ($root === null) return ;
        if ($level == count($res)) {
            $res[$level] = []; 
        }
        array_push($res[$level], $root->val);
        $this->helper($root->left, $level+1, $res);
        $this->helper($root->right, $level+1, $res);
    }
}
```