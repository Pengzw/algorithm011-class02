### 解题思路
1. 暴力法

一般是两层循环，虽然可以解题，不过时间复杂度偏高了点O(n^2)
2. hash+for

空间换时间，少了一层for，时间复杂度为O(n)
### 代码

```
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $target
     * @return Integer[]
     */
    function twoSum($nums, $target) {
        $ret = [];
        $arr = [];
        foreach ($nums as $key => $value) {
            $arr[$value] = $key;
        }
        for ($i=0; $i < count($nums); $i++) { 
            $get = $target - $nums[$i];
            if (isset($arr[$get]) && $arr[$get] != $i) {
                $ret = [
                    $arr[$get],$i
                ];
                break;
            }
        }
        return $ret;
    }
}
```
