题解思路
```
给定一个非空的整数数组，返回其中出现频率前 k 高的元素。

输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```
### 代码
```
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $k
     * @return Integer[]
     */
    function topKFrequent($nums, $k) {
        $count  = array_count_values($nums);
        $pq     = new SplPriorityQueue();
        foreach ($count as $value => $counts) {
            $pq->insert($value, $counts);// php 大顶堆
        }

        $ans = [];
        for ($i = 0; $i < $k; ++$i) {
            $ans[] = $pq->extract();
        }

        return $ans;
    }
}
```
