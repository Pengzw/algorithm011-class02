N叉树的前序遍历

### 代码
```php

/**
 * Definition for a Node.
 * class Node {
 *     public $val = null;
 *     public $children = null;
 *     function __construct($val = 0) {
 *         $this->val = $val;
 *         $this->children = array();
 *     }
 * }
 */

class Solution {
    /**
     * @param Node $root
     * @return integer[]
     */
    function preorder($root) {
        $res = [];
        $this->helper($root, $res);
        return $res;
    }

    function helper($root, &$res){
        if (!$root) return ;
        // 前序遍历的值先入列
        $res[] = $root->val;
        // 这里没有left right，只有children arr
        foreach($root->children as $children){
            $this->helper($children, $res);
        }
    }
}
```
