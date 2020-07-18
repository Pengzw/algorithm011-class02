### 解题思路

```
此处撰写解题思路您需要在二叉树的每一行中找到最大的值。

示例：

输入: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

输出: [1, 3, 9]

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
     * @param TreeNode $root
     * @return Integer[]
     */
    function largestValues($root) {
        //层序遍历
        $res = [];
        $this->helper($root,0,$res);
        return $res;
    }
    function helper($root, $level, &$res){
        if ($root === null) return ;

        if ($level >= count($res)) {
            $res[$level] = $root->val;
        } else if ($root->val > $res[$level]) {
             $res[$level] = $root->val;
        }

        $this->helper($root->left, $level+1, $res);
        $this->helper($root->right, $level+1, $res);
    }
}
```