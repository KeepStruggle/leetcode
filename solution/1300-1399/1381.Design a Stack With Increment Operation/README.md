# [1381. 设计一个支持增量操作的栈](https://leetcode.cn/problems/design-a-stack-with-increment-operation)

[English Version](/solution/1300-1399/1381.Design%20a%20Stack%20With%20Increment%20Operation/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>请你设计一个支持下述操作的栈。</p>

<p>实现自定义栈类 <code>CustomStack</code> ：</p>

<ul>
	<li><code>CustomStack(int maxSize)</code>：用 <code>maxSize</code> 初始化对象，<code>maxSize</code> 是栈中最多能容纳的元素数量，栈在增长到 <code>maxSize</code> 之后则不支持 <code>push</code> 操作。</li>
	<li><code>void push(int x)</code>：如果栈还未增长到 <code>maxSize</code> ，就将 <code>x</code> 添加到栈顶。</li>
	<li><code>int pop()</code>：弹出栈顶元素，并返回栈顶的值，或栈为空时返回 <strong>-1</strong> 。</li>
	<li><code>void inc(int k, int val)</code>：栈底的 <code>k</code> 个元素的值都增加 <code>val</code> 。如果栈中元素总数小于 <code>k</code> ，则栈中的所有元素都增加 <code>val</code> 。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>
[&quot;CustomStack&quot;,&quot;push&quot;,&quot;push&quot;,&quot;pop&quot;,&quot;push&quot;,&quot;push&quot;,&quot;push&quot;,&quot;increment&quot;,&quot;increment&quot;,&quot;pop&quot;,&quot;pop&quot;,&quot;pop&quot;,&quot;pop&quot;]
[[3],[1],[2],[],[2],[3],[4],[5,100],[2,100],[],[],[],[]]
<strong>输出：</strong>
[null,null,null,2,null,null,null,null,null,103,202,201,-1]
<strong>解释：</strong>
CustomStack customStack = new CustomStack(3); // 栈是空的 []
customStack.push(1);                          // 栈变为 [1]
customStack.push(2);                          // 栈变为 [1, 2]
customStack.pop();                            // 返回 2 --&gt; 返回栈顶值 2，栈变为 [1]
customStack.push(2);                          // 栈变为 [1, 2]
customStack.push(3);                          // 栈变为 [1, 2, 3]
customStack.push(4);                          // 栈仍然是 [1, 2, 3]，不能添加其他元素使栈大小变为 4
customStack.increment(5, 100);                // 栈变为 [101, 102, 103]
customStack.increment(2, 100);                // 栈变为 [201, 202, 103]
customStack.pop();                            // 返回 103 --&gt; 返回栈顶值 103，栈变为 [201, 202]
customStack.pop();                            // 返回 202 --&gt; 返回栈顶值 202，栈变为 [201]
customStack.pop();                            // 返回 201 --&gt; 返回栈顶值 201，栈变为 []
customStack.pop();                            // 返回 -1 --&gt; 栈为空，返回 -1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= maxSize &lt;= 1000</code></li>
	<li><code>1 &lt;= x &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= 1000</code></li>
	<li><code>0 &lt;= val &lt;= 100</code></li>
	<li>每种方法 <code>increment</code>，<code>push</code> 以及 <code>pop</code> 分别最多调用 <code>1000</code> 次</li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class CustomStack:

    def __init__(self, maxSize: int):
        self.s = [0] * maxSize
        self.tail = 0

    def push(self, x: int) -> None:
        if self.tail < len(self.s):
            self.s[self.tail] = x
            self.tail += 1

    def pop(self) -> int:
        if self.tail == 0:
            return -1
        self.tail -= 1
        return self.s[self.tail]

    def increment(self, k: int, val: int) -> None:
        for i in range(min(k, self.tail)):
            self.s[i] += val


# Your CustomStack object will be instantiated and called as such:
# obj = CustomStack(maxSize)
# obj.push(x)
# param_2 = obj.pop()
# obj.increment(k,val)
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class CustomStack {
    private int[] s;
    private int tail;

    public CustomStack(int maxSize) {
        s = new int[maxSize];
    }

    public void push(int x) {
        if (tail < s.length) {
            s[tail++] = x;
        }
    }

    public int pop() {
        return tail == 0 ? -1 : s[--tail];
    }

    public void increment(int k, int val) {
        for (int i = 0; i < Math.min(k, tail); ++i) {
            s[i] += val;
        }
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */
```

### **TypeScript**

```ts
class CustomStack {
    maxSize: number;
    size: number;
    stack: Array<number>;
    constructor(maxSize: number) {
        this.maxSize = maxSize;
        this.size = 0;
        this.stack = [];
    }

    push(x: number): void {
        if (this.size >= this.maxSize) return;
        this.size++;
        this.stack.unshift(x);
    }

    pop(): number {
        if (!this.size) return -1;
        this.size--;
        return this.stack.shift();
    }

    increment(k: number, val: number): void {
        let tmp: Array<number> = [];
        for (let i = Math.max(this.size - k, 0); i < this.size; i++) {
            this.stack[i] = this.stack[i] + val;
        }
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * var obj = new CustomStack(maxSize)
 * obj.push(x)
 * var param_2 = obj.pop()
 * obj.increment(k,val)
 */
```

### **...**

```

```

<!-- tabs:end -->
