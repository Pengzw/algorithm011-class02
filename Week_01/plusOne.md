### 解题思路
从末尾向前进位，如果首位也需要进位则插入1

### 代码

```
class Solution {

    function plusOne($digits) {
        return $this->up($digits, count($digits)-1);
    }
    public function up(&$digits, $p){
        $digits[$p] ++;
        if($digits[$p] > 9) {
            $digits[$p] = 0;
            if($p > 0) {
                $digits = $this->up($digits, --$p);
            } else {
                array_unshift($digits, 1);
            }
        }
        return $digits;
    }
}
```
