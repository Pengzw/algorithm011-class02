### 题解思路
==单词规律==

给定一种规律 pattern 和一个字符串 str ，判断 str 是否遵循相同的规律。

这里的 遵循 指完全匹配，例如， pattern 里的每个字母和字符串 str 中的每个非空单词之间存在着双向连接的对应规律。

示例1:

输入: pattern = "abba", str = "dog cat cat dog"
输出: true
示例 2:

输入:pattern = "abba", str = "dog cat cat fish"
输出: false
示例 3:

输入: pattern = "aaaa", str = "dog cat cat dog"
输出: false
示例 4:

输入: pattern = "abba", str = "dog dog dog dog"
输出: false
说明:
你可以假设 pattern 只包含小写字母， str 包含了由单个空格分隔的小写字母。    

### 代码
```
class Solution {

    /**
     * @param String $pattern
     * @param String $str
     * @return Boolean
     */
    function wordPattern($pattern, $str) {
        $arr 	= explode(" ", $str);
        if (strlen($pattern) != count($arr)) 
            return false;

        $map 	= [];
        for ($i=0; $i < strlen($pattern); $i++) { 
            if (!isset($map[$pattern[$i]])) {
                if (in_array($arr[$i], $map)) {
                    return false;// 值存在，但不是$pattern[$i]
                }
                $map[$pattern[$i]] = $arr[$i];
            }else if($map[$pattern[$i]] != $arr[$i]){
                return false;
            }
        }
        return true;
    }
}
```
