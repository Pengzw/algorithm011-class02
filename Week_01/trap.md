### 解题思路
双指针对比左右两边高度，低的移动，如果遇到更低的则可以蓄水；
记录左右最高柱子，右边移动指针事计算右边最高柱子与当前柱子差，
反之，左边移动指针事计算左边最高柱子与当前柱子差.

### 代码

```
class Solution {

    /**
     * @param Integer[] $height
     * @return Integer
     */
    function trap($height) {
        $left       = 0;
        $right      = count($height)-1;
        $leftMax    = $height[0];
        $rightMax   = $height[$right];
        $rain       = 0;
        while ($left < $right) {
            if ($height[$left] < $height[$right]) {
                $left ++;
                if ($height[$left] < $leftMax) {
                    $rain += $leftMax - $height[$left];
                }else{
                    $leftMax = $height[$left];
                }
            }else{
                $right --;
                if ($height[$right] < $rightMax) {
                    $rain += $rightMax - $height[$right];
                }else{
                    $rightMax = $height[$right];
                }
            }
        }
        return $rain;
    }
}
```
