### 解题思路

盛水容器

暴力法&双指针法

> 双指针法：指的是在遍历对象的过程中，不是普通的使用单个指针进行访问，而是使用两个相同方向或者相反方向的指针进行扫描，从而达到相应的目的。
### 代码

```
class Solution {

    /**
     * @param Integer[] $height
     * @return Integer
     */
    function maxArea($height) {
        $max = 0;
        $count = count($height);
        // 暴力法：大数组下超出时间限制，且时间复杂度O(n^2)
        // for($i = 0; $i < $count; $i ++){
        //     for ($j=$i+1; $j < $count; $j++) { 
        //         // 长*宽=面积。。
        //         $area = ($j-$i)*($height[$i] > $height[$j] ? $height[$j] : $height[$i]);
        //         $max = $area > $max ? $area : $max;
        //     }
        // }
        
        // 双指针法：时间复杂O(n)
        $i = 0;         // 左指针
        $j = $count-1;  // 右指针
        while ($i<$j) {
            // 每次循环移动矮柱子
            if ($height[$i] < $height[$j]) {
                $minHei = $height[$i];
                $i++;
            }else{
                $minHei = $height[$j];
                $j--;
            }
            // 因为提前移动，所以+1
            $area = ($j - $i + 1) * $minHei;
            $max = $area > $max ? $area : $max;
        }
        return $max;
    }
}
```