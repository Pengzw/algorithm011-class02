### 解题思路
SplStack是php的标准库，但是一般我们都用array实现，秉着学习的态度，也接触了SplStack，并尝试解题

### 代码

```
class MinStack {
    
    private $stack;
    private $minStack;
    /**
     * initialize your data structure here.
     */
    function __construct() {
        $this->stack    = new SplStack();
        $this->minStack = new SplStack();
    }
  
    /**
     * @param Integer $x
     * @return NULL
     */
    function push($x) {
        $this->stack->push($x);

        if ($this->minStack->count()) {
            $x = min($this->minStack->top(), $x);
        }
        $this->minStack->push($x);
    }
  
    /**
     * @return NULL
     */
    function pop() {
        if($this->stack->isEmpty()) return null;
        $this->stack->pop();
        
        if($this->minStack->count()) $this->minStack->pop();
    }
  
    /**
     * @return Integer
     */
    function top() {
        return $this->stack->top();
    }
  
    /**
     * @return Integer
     */
    function getMin() {
        if($this->minStack->isEmpty())return null;
        return $this->minStack->top();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * $obj = MinStack();
 * $obj->push($x);
 * $obj->pop();
 * $ret_3 = $obj->top();
 * $ret_4 = $obj->getMin();
 */
```
