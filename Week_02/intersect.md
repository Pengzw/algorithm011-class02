### 解题思路
两个数组的交集 II用哈希解法

### 代码

```
class Solution {

    /**
     * @param Integer[] $nums1
     * @param Integer[] $nums2
     * @return Integer[]
     */
    function intersect($nums1, $nums2) {
        $ret = [];
        foreach ($nums1 as $value) {
            $ret[$value] ++;
        }
        $arr = [];
        foreach ($nums2 as $value) {
            if (isset($ret[$value]) && $ret[$value] > 0) {
                $arr[] = $value;
                $ret[$value]--;
            }
        }
        return $arr;
    }
}
```
