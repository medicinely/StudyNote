---
title: 机器学习笔记
date: 2020-09-25 10:14:38
tags:



---

# 剑指offer数据结构题目笔记

## 5-用两个栈实现队列

``` python
# -*- coding:utf-8 -*-
class Solution:
    def __init__(self):
        self.acceptStack = [] #创建空接受栈
        self.outputStack = [] #创建空输出栈
    def push(self, node): #输入
        self.acceptStack.append(node) #将元素存入接受栈
        # write code here
    def pop(self): #弹出
        if self.outputStack == []: #如果输出栈是空
            while self.acceptStack: #只要接收栈不是空
                self.outputStack.append(self.acceptStack.pop())#就一直弹出接受栈的内容到输出栈
        
        if self.outputStack !=[]:  #如果输出栈不空
            return self.outputStack.pop() #则返回输出栈弹出的结果
        else: #如果输出栈空
            return None #不返回
        # return xx
```

## 6-旋转数组的最小数字

```python
# 二分查找法
def bSearch(array, target):

    left = 0 # 左指针
    right = len(array) - 1 # 右指针
    while left <= right:
        # 101 = 5 => 10 =2
        # 1100 = 12 => 110 = 6
        mid = (left + right) // 2 # 向取整数（弱智方法）
        #mid = (left + right) >> 1 # 移位（除2取整数）
        if array[mid] == target:
            return mid
        elif array[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return None

if __name__ == '__main__':
    ret = bSearch([1 ,2 ,3 ,4 ,5 ,6 ,7 ,8 ,9 ,10], 1)
    print(ret)

```

