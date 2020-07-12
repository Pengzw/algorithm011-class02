### 解题思路

```
此处撰写解题思路给定一个 没有重复 数字的序列，返回其所有可能的全排列。

示例:

输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```


### 代码

```php
class Solution {

    /**
     * @param Integer[] $nums
     * @return Integer[][]
     */
    function permute($nums) {
        $ret = [];
        $this->process($nums, 0, count($nums), $ret);
        var_export($ret);
        return $ret;
    }
    function process($arr, $p, $q, &$ret){
        if ($q == $p) {
            $ret[] = $arr;
            return ;
        }
        for ($i=$p; $i < $q; $i++) { 
            $this->swap($arr, $p, $i);// 交换
            $this->process($arr, $p+1, $q, $ret);// 下一个节点继续交换
        }
    }
    /**
    * 两个key交换
    */
    function swap(&$arr, $p, $q){
        if ($q == $p) return ;
        $temp = $arr[$p];
        $arr[$p] = $arr[$q];
        $arr[$q] = $temp;
    }
}
```