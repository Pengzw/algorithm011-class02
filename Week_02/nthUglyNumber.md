### 题解思路
```
我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

 

示例:

输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。

```
### 代码
```
class Solution {

    /**
     * @param Integer $n
     * @return Integer
     */
    function nthUglyNumber($n) {
         // 三指针 dp
        $p2 = $p3 = $p5 = 0;
        $dp = array_fill(0, $n, null);
        $dp[0] = 1;
        for ($i = 1; $i < $n; ++$i) {
            $dp[$i] = min($dp[$p2] * 2, $dp[$p3] * 3, $dp[$p5] * 5);
            
            if ($dp[$i] == $dp[$p2] * 2) $p2++;
            if ($dp[$i] == $dp[$p3] * 3) $p3++;
            if ($dp[$i] == $dp[$p5] * 5) $p5++;
        }
        return $dp[$n - 1];
    }
}
```
