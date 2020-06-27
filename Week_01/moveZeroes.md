### 解题思路
移动零 

数据交替

### 代码


```
class Solution {

    /**
     * @param Integer[] $nums
     * @return NULL
     */
    function moveZeroes(&$num) {
        $j = 0;
        for ($i=0; $i < count($num); $i++) { 
            if ($num[$i] != 0) {
                if ($i != $j) {
                    $num[$j] = $num[$i];
                    $num[$i] = 0;
                }
                $j++;
            }
        }
        return $num;
    }
}
```
