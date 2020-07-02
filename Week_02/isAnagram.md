
### 解题思路
有效的字母异位词

给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

输入: s = "anagram", t = "nagaram"

输出: true

### 代码

```php
class Solution {

    /**
     * @param String $s
     * @param String $t
     * @return Boolean
     */
    function isAnagram($s, $t) {
        $arr    = [];
        $slen   = strlen($s);
        $tlen   = strlen($t);
        if ($slen != $tlen) return false;
        for ($i=0; $i < $slen; $i++) { 
            $arr[$s[$i]] ++;
        }
        for ($i=0; $i < $tlen; $i++) { 
            if (isset($arr[$t[$i]]) && --$arr[$t[$i]] == 0) {
                unset($arr[$t[$i]]);
            }
        }
        return $arr == [];
    }
}
```
