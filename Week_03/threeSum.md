### 题解思路

```
给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。

给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]

```

### 代码
```
class Solution {

    /**
     * @param Integer[] $nums
     * @return Integer[][]
     */
    function threeSum($nums) {
        // 结果数组
        $res = [];

        // 数组为空或长度小于 3，返回空数组
        if (!$nums || ($len = count($nums)) < 3) {
            return $res;
        }

        // 对数组进行排序
        sort($nums);

        // 遍历数组
        foreach ($nums as $k => $v) {
            // 定义左右指针
            $l = $k + 1;
            $r = $len - 1;

            // 数组是经过排序的，当前值大于 0，
            // 说明后面相加后肯定是大于 0 的
            if ($v > 0) {
                break;
            }

            // 如果当前值和前一个值相同，
            // 则跳过当前循环，防止重复
            if ($k > 0 && $v === $nums[$k - 1]) {
                continue;
            }

            while ($l < $r) {
                $sum = $v + $nums[$l] + $nums[$r];

                // 对求和结果进行判断
                if ($sum === 0) {
                    // 和为 0，给结果数组添加元素
                    array_push($res, [$v, $nums[$l], $nums[$r]]);

                    // 去重操作
                    while ($l < $r && $nums[$l] === $nums[++$l]);
                    while ($l < $r && $nums[$r] === $nums[--$r]);
                } elseif ($sum < 0) {
                    // 和小于 0，左指针 + 1
                    $l++;
                } else {
                    // 和大于 0，右指针 - 1
                    $r--;
                }
            }
        }
        
        return $res;
    }
}
```
