### 题解思路

```
实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须原地修改，只允许使用额外常数空间。

以下是一些例子，输入位于左侧列，其相应输出位于右侧列。
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

```

### 代码
```php
class Solution {

    /**
     * @param Integer[] $nums
     * @return NULL
     */
    function nextPermutation(&$nums) {
        // -2的好处就是第一个while条件不满足，则当前为最大值，否则还有小数
        $i = count($nums) - 2;
        while($i>=0 && $nums[$i+1]<=$nums[$i]){
            $i--;
        }
        if($i>=0){
            $j = count($nums)-1;
            while($j>=0 && $nums[$j]<=$nums[$i]){
                $j--;
            }
            // 互换
            $this->swap($nums,$i,$j);
        }
        // 当前最大数则翻转
        $this->reverse($nums,$i+1);
        return $nums;
    }

    function reverse(&$nums, $start){
        $i = $start;
        $j = count($nums)-1;
        while($i<$j){
            $this->swap($nums,$i,$j);
            $i++;
            $j--;
        }
    }

    function swap(&$nums, $i, $j){
        $tmp = $nums[$i];
        $nums[$i] = $nums[$j];
        $nums[$j] = $tmp;
    }
}
```
