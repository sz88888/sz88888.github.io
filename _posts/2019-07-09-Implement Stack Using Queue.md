---
layout: post
title: "Implement Stack Using Queues 用队列实现栈"
subtitle: ""
date: 2019-07-09 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Stack 栈
      

---






#### 用队列实现栈

使用队列实现栈的下列操作：

push(x) -- 元素 x 入栈
pop() -- 移除栈顶元素
top() -- 获取栈顶元素
empty() -- 返回栈是否为空
注意:

你只能使用队列的基本操作-- 也就是 push to back, peek/pop from front, size, 和 is empty 这些操作是合法的。
你所使用的语言也许不支持队列。 你可以使用 list 或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。
你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。

















解法1:

设置两个队列，1号队列和2号队列；

当需要压入栈时： 先判断1号队列是否为空。 

若为空，则可以直接将该元素放入队列1，以后要出栈直接从取1号队列头部；

若不为空，则需要将1号队列中的队头元素依次取出放入2号队列队尾 （这样可以保持顺序不变），然后将x元素放入此时已经空了的1号队列，接下来将2号队列的队头元素依次取出加入1号队列的队尾。 需要取出时，依次取出1号队列队头，也就是栈顶。




##### Solution:

```python
class MyStack:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.queue1 = []
        self.queue2 = []

    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """       
        if self.queue1:
            while self.queue1:
                self.queue2.append(self.queue1.pop(0))
            self.queue1.append(x)
            while self.queue2:
                self.queue1.append(self.queue2.pop(0))
        else:
            self.queue1.append(x)
            

    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """
        if self.queue1:
            return self.queue1.pop(0)
        else:
            return None

    def top(self) -> int:
        """
        Get the top element.
        """
        if self.queue1:
            return self.queue1[0]

    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        """
        if self.queue1:
            return False
        else:
            return True


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()                       
```



![pic](http://ww4.sinaimg.cn/large/006tNc79gy1g4tow7wp2rj30sg0hkq4x.jpg)


