### 解题思路

```
此处撰写解题思路输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 

```

### 代码

```php
class Solution {

    /**
     * @param Integer[] $numbers
     * @param Integer $target
     * @return Integer[]
     */
    function twoSum($numbers, $target) {
        $l = 0;
        $r = count($numbers)-1;

        if($r > 0) while ($l < $r) {
            $sum = $numbers[$l] + $numbers[$r];
            if ($sum == $target) {
                return [$l+1, $r+1];
            }else if($sum > $target){
                $r--;// 超出右减
            }else{
                $l++;// 小于左加
            }
        }
        return ;
    }
}
```