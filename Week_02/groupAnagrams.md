### 示例

```
输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

```

### 代码

```
class Solution {

    /**
     * @param String[] $strs
     * @return String[][]
     */
    function groupAnagrams($strs) {
        $map = [];
        foreach ($strs as $str) {
            $arr = str_split($str);
            sort($arr);
            $tmp_str = implode("", $arr);
            $map[$tmp_str][] = $str;
        }
        return array_values($map);
    }
}
```
