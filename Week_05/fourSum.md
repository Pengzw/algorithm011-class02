### 解题思路
4数之和

### 代码

```php
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $target
     * @return Integer[][]
     */
    function fourSum($nums, $target) {
        sort($nums);
        $len = count($nums);
        $res = [];
        for($i = 0; $i < $len - 3; $i ++){
            if ($i > 0 && $nums[$i] == $nums[$i-1]) continue;// 去重
            for($j = $i+1; $j < $len -2; $j ++){
                if ($j > $i + 1 && $nums[$j] == $nums[$j-1]) continue;// 去重
                $l = $j+1;
                $r = $len -1;
                while($l < $r){
                    $sum = $nums[$i] + $nums[$j] + $nums[$l] + $nums[$r];
                    if ($sum == $target){
                        $res[] = [$nums[$i], $nums[$j], $nums[$l], $nums[$r]];
                        while($l < $r && $nums[$l] === $nums[$l+1]){
                            $l ++;
                        }
                        while($l < $r && $nums[$r] === $nums[$r-1]){
                            $r --;
                        }
                        $l ++;
                        $r --;
                    }else if($sum > $target){
                        $r --;
                    }else {
                        $l ++;
                    }
                }
            }
        }
        return $res;
    }
}
```