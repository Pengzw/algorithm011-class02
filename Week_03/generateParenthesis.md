### 题解思路
```
数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

 

示例：

输入：n = 3
输出：[
   "((()))",
   "(()())",
   "(())()",
   "()(())",
   "()()()"
 ]
```
### 代码
```
class Solution {

    /**
     * @param Integer $n
     * @return String[]
     */
    function generateParenthesis($n) {
        $ret = [];
        $this->generate(0, 0, $n, '', $ret);
        return $ret;
    }

    function generate($left, $right, $n, $s, &$ret){
        if ($left == $n && $right == $n) {
            $ret[] = $s;
            // echo "$s\n";
            return ;
        }
        // echo "{$left} {$right} \n";
        if ($left < $n) {
            $this->generate($left+1, $right, $n, $s."(", $ret);
        }
        if ($left > $right) {// 随着每层lelt的变化导致
            $this->generate($left, $right+1, $n, $s.")", $ret);
        }
    }
}
```
