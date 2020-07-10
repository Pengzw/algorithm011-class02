
```
给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。

示例:

输入: 3
输出:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]

```
### 代码
```php
function generateMatrix($n) {
    $ans = array_fill(0,$n,array_fill(0,$n,0));
    $up = 0;
    $down = $n-1;
    $left = 0;
    $right = $n-1;
    $num = 1;
    while(true){
        // 从左到右
        for($i=$left;$i<=$right;$i++) $ans[$up][$i] = $num++;
        if(++$up>$down) break;
        // 从上到下
        for($i=$up;$i<=$down;$i++) $ans[$i][$right] = $num++;
        if(--$right<$left) break;
        // 从右到左
        for($i=$right;$i>=$left;$i--) $ans[$down][$i] = $num++;
        if(--$down<$up) break;
        // 从下到上
        for($i=$down;$i>=$up;$i--) $ans[$i][$left] = $num++;
        if(++$left>$right) break;
    }
    return $ans;
}
```
