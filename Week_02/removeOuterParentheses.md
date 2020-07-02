### 题解思路

```
输入："(()())(())"
输出："()()()"
解释：
输入字符串为 "(()())(())"，原语化分解得到 "(()())" + "(())"，
删除每个部分中的最外层括号后得到 "()()" + "()" = "()()()"。


输入："()()"
输出：""
解释：
输入字符串为 "()()"，原语化分解得到 "()" + "()"，
删除每个部分中的最外层括号后得到 "" + "" = ""。
```



### 代码
```
class Solution {

    /**
     * @param String $S
     * @return String
     */
    function removeOuterParentheses($S) {
        $num = 0;
        $s = '';

        for ($i = 0, $length = strlen($S); $i < $length; $i++) {
            if ($S[$i] == '(' && ++$num > 1) {
                $s .= '(';
            }
            if ($S[$i] == ')' && --$num > 0) {
                $s .= ')';
            }
        }

        return $s;
    }
}
```