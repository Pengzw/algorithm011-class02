### 解题思路
第一次：1

第二次：2

第三次：3

第四次：5

典型的斐波拉数列：fbnq(n-1)+fbnq(n-2)

### 代码
```
class Solution {

    /**
     * @param Integer $n
     * @return Integer
     */
    function climbStairs($n) {
        if ($n <= 2) return $n;
        // // 斐波拉类型
        $f1 = 1;
        $f2 = 2;
        for($i = 2; $i < $n; $i++){
            $f3 = $f1 + $f2;
            $f1 = $f2;
            $f2 = $f3;
        }
        return $f3;
        
        // $f = [1,2];
        // for($i = 2; $i < $n; $i++){
        //     // 缓存上次计算
        //     $f[$i] = $f[$i-1] + $f[$i-2];
        // }
        // return $f[$n-1];
    }
}

```
