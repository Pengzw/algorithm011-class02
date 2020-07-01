### 解题思路
有效的括号

这个题纯算法的话，我用栈的特性作为解法；

也不排序用字符串替换空的模式解这题。

### 代码

```
class Solution {

    /**
     * @param String $s
     * @return Boolean
     */
    function isValid($s) {
        $arr = [
            "{" => "}",
            "[" => "]",
            "(" => ")",
        ];
        $stack = [];// 栈解法

        for ($i = 0, $length = strlen($s); $i < $length; $i++) {
            if (isset($arr[$s[$i]])) {
                $stack[] = $s[$i];
            }else{
                $tmp = array_pop($stack);
                if ($arr[$tmp] !== $s[$i]) {
                    return false;
                }
            }
        }
        return $stack ? false : true;   
    }
}
```
