### 解题思路
写一个程序，输出从 1 到 n 数字的字符串表示。

1. 如果 n 是3的倍数，输出“Fizz”；

2. 如果 n 是5的倍数，输出“Buzz”；

3. 如果 n 同时是3和5的倍数，输出 “FizzBuzz”。

### 代码
```
class Solution {

    /**
     * @param Integer $n
     * @return String[]
     */
    function fizzBuzz($n) {
        $ret = [];
        for ($i=1; $i <= $n; $i++) { 
            $s = '';
            if ($i%3 == 0) {
                $s .= "Fizz";
            }
            if ($i%5 == 0) {
                $s .= "Buzz";
            }
            $ret[] = $s ? $s : "{$i}";
        }
        return $ret;
    }
}
```
