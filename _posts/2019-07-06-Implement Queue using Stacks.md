---
layout: post
title: "Implement Queue using Stacks 用栈实现队列"
subtitle: ""
date: 2019-07-06 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Stack 栈
      

---






#### 用栈实现队列

使用栈实现队列的下列操作：

push(x) -- 将一个元素放入队列的尾部。

pop() -- 从队列首部移除元素。

peek() -- 返回队列首部的元素。

empty() -- 返回队列是否为空。

示例:

MyQueue queue = new MyQueue();

queue.push(1);

queue.push(2);  

queue.peek();  // 返回 1

queue.pop();   // 返回 1

queue.empty(); // 返回 false

说明:

你只能使用标准的栈操作 -- 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。

你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。

假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）。

















##### Solution:

```python
class MyQueue:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.stack1 = []
        self.stack2 = []

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        if self.stack1 == None:
            self.stack1.append(x)
        else:
            while self.stack1:
                self.stack2.append(self.stack1.pop(-1))
            self.stack1.append(x)
            while self.stack2:
                self.stack1.append(self.stack2.pop(-1))
        

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        if self.stack1:
            
            return self.stack1.pop()
        else:
            return None

    def peek(self) -> int:
        """
        Get the front element.
        """
        if self.stack1:
            return self.stack1[-1]
        else:
            return None

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        if len(self.stack1) > 0:
            return False
        else:
            return True


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()               
```
两个栈相当于两个瓶子，1号瓶子为主，2号瓶子为辅。

如果1号瓶子为空，则直接把新的元素倒入1号瓶；

如果1号瓶子不为空，则把1号瓶子元素依次倒入2号瓶，紧接着倒入新的元素，然后再把2号瓶的元素依次倒回来，这就始终保持了最先来的元素在1号瓶的栈顶，最后进来的元素在栈底，从而实现了队列（FIFO）。


![pic](http://ww1.sinaimg.cn/large/006tNc79gy1g4qcolx2m1j30u806sq3v.jpg)


