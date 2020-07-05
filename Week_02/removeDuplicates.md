### 解题思路
给定一个排序数组，你需要在 原地 删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。
### 代码
```
class Solution {

    /**
     * 内置函数
     */
    function removeDuplicates(&$nums) {
        $nums = array_keys(array_flip($nums));
        return count($nums);
    }


    /**
     * @param Integer[] $nums
     * @return Integer
     */
    function removeDuplicates(&$nums) {
        $count = count($nums);
        for ($i=0; $i < $count; $i++) { 
            if (isset($nums[$i+1]) && $nums[$i] == $nums[$i+1]) {
                unset($nums[$i]);
            }
        }
        return count($nums);
    }
}
```
