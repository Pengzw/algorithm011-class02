### 解题思路
最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。

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
     * @return integer
     */
    function maxDepth($root) {
        if(!$root) return 0;
        $level = 0;
        foreach ($root->children as $children) {
            $temp = $this->maxDepth($children);
            $level = max($temp, $level);
        } 
        return $level+1;
    }
}
```