### 解题思路
标题为设计循环双端队列，但是描述没有循环的要求。后续再尝试链表

### 代码

```
class MyCircularDeque {
    private $count = 0;
    private $nowCount = 0;
    private $deque = [];
    /**
     * Initialize your data structure here. Set the size of the deque to be k.
     * @param Integer $k
     */
    function __construct($k) {
        $this->count = $k;
    }
  
    /**
     * Adds an item at the front of Deque. Return true if the operation is successful.
     * @param Integer $value
     * @return Boolean
     */
    function insertFront($value) {
        if ($this->isFull()) {
            return false;
        }
        $this->nowCount = array_unshift($this->deque, $value);
        return true;
    }
  
    /**
     * Adds an item at the rear of Deque. Return true if the operation is successful.
     * @param Integer $value
     * @return Boolean
     */
    function insertLast($value) {
        if ($this->isFull()) {
            return false;
        }
        $this->nowCount = array_push($this->deque, $value);
        return true;
    }
  
    /**
     * Deletes an item from the front of Deque. Return true if the operation is successful.
     * @return Boolean
     */
    function deleteFront() {
        if ($this->nowCount <= 0) {
            return false;
        }
        $value = array_shift($this->deque);
        $this->nowCount --;
        return isset($value);
    }
  
    /**
     * Deletes an item from the rear of Deque. Return true if the operation is successful.
     * @return Boolean
     */
    function deleteLast() {
        if ($this->nowCount <= 0) {
            return false;
        }
        $value = array_pop($this->deque);
        $this->nowCount --;
        return isset($value);
    }
  
    /**
     * Get the front item from the deque.
     * @return Integer
     */
    function getFront() {
        return $this->nowCount <= 0 ? -1 : $this->deque[0];
    }
  
    /**
     * Get the last item from the deque.
     * @return Integer
     */
    function getRear() {
        return isset($this->deque[$this->nowCount-1]) ? $this->deque[$this->nowCount-1] : -1;
    }
  
    /**
     * Checks whether the circular deque is empty or not.
     * @return Boolean
     */
    function isEmpty() {
        return (bool)$this->nowCount == 0;
    }
  
    /**
     * Checks whether the circular deque is full or not.
     * @return Boolean
     */
    function isFull() {
        return $this->nowCount >= $this->count;
    }
}

/**
 * Your MyCircularDeque object will be instantiated and called as such:
 * $obj = MyCircularDeque($k);
 * $ret_1 = $obj->insertFront($value);
 * $ret_2 = $obj->insertLast($value);
 * $ret_3 = $obj->deleteFront();
 * $ret_4 = $obj->deleteLast();
 * $ret_5 = $obj->getFront();
 * $ret_6 = $obj->getRear();
 * $ret_7 = $obj->isEmpty();
 * $ret_8 = $obj->isFull();
 */
```
