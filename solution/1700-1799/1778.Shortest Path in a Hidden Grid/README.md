# [1778. Shortest Path in a Hidden Grid](https://leetcode.cn/problems/shortest-path-in-a-hidden-grid)

[English Version](/solution/1700-1799/1778.Shortest%20Path%20in%20a%20Hidden%20Grid/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>这是一个<strong>交互式的问题。</strong></p>

<p>一个未知的网格里有一个机器人，你需要让机器人从起点走到终点。这个网格的大小是 <code>m x n</code>，网格中的每个位置只会是可通行和不可通行两种状态。题目<strong>保证</strong>机器人的起点和终点不同，且都是可通行的。</p>

<p>你需要找到起点到终点的最短路径，然而你<strong>不知道</strong>网格的大小、起点和终点。你只能向 <code>GridMaster</code> 对象查询。</p>

<p><code>GridMaster</code>有这些方法：</p>

<ul>
	<li><code>boolean canMove(char direction)</code> 当机器人能向对应方向移动时，返回 <code>true</code>，否则返回 <code>false</code>。</li>
	<li><code>void move(char direction)</code> 把机器人向这个方向移动。如果移动方向上是不可通行的或是网格的边界，则这次移动会被<strong>忽略</strong>，机器人会待在原地。</li>
	<li><code>boolean isTarget()</code> 如果机器人当前位于终点，返回 <code>true</code>，否则返回 <code>false</code>。</li>
</ul>

<p>注意上述方法中的direction应该是 <code>{'U','D','L','R'}</code> 中的一个，分别代表上下左右四个方向。</p>

<p>返回机器人的初始位置到终点的最短距离。如果在起点和终点间没有路径联通，返回 <code>-1</code>。</p>

<p><strong>自定义测试用例</strong></p>

<p>测试用例是一个 <code>m x n</code> 的二维矩阵 <code>grid</code>，其中：</p>

<ul>
	<li><code>grid[i][j] == -1</code> 表明机器人一开始位于位置 <code>(i, j)</code> （即起点）。</li>
	<li><code>grid[i][j] == 0</code> 表明位置 <code>(i, j)</code> 不可通行。</li>
	<li><code>grid[i][j] == 1</code> 表明位置 <code>(i, j)</code> 可以通行.</li>
	<li><code>grid[i][j] == 2</code> 表明位置 <code>(i, j)</code> 是终点.</li>
</ul>

<p><code>grid</code> 里恰有一个<code>-1</code> 和一个 <code>2</code>。记住在你的代码中，你对这些信息将<strong>一无所知</strong>。</p>

<p><strong>示例1：</strong></p>

<pre>
<strong>输入:</strong> grid = [[1,2],[-1,0]]
<strong>输出:</strong> 2
<strong>解释:</strong> 一种可能的交互过程如下：
The robot is initially standing on cell (1, 0), denoted by the -1.
- master.canMove('U') 返回 true.
- master.canMove('D') 返回false.
- master.canMove('L') 返回 false.
- master.canMove('R') 返回 false.
- master.move('U') 把机器人移动到 (0, 0).
- master.isTarget() 返回 false.
- master.canMove('U') 返回 false.
- master.canMove('D') 返回 true.
- master.canMove('L') 返回 false.
- master.canMove('R') 返回 true.
- master.move('R') 把机器人移动到 (0, 1).
- master.isTarget() 返回 true. 
我们现在知道终点是点 (0, 1)，而且最短的路径是2.
</pre>

<p><strong>示例2:</strong></p>

<pre>
<strong>输入:</strong> grid = [[0,0,-1],[1,1,1],[2,0,0]]
<strong>输出:</strong> 4
<strong>解释:</strong> 机器人和终点的最短路径长是4.</pre>

<p><strong>示例3:</strong></p>

<pre>
<strong>输入:</strong> grid = [[-1,0],[0,2]]
<strong>输出:</strong> -1
<strong>解释:</strong> 机器人和终点间没有可通行的路径.</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n, m <= 500</code></li>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>grid[i][j]</code> 只可能是 <code>-1</code>, <code>0</code>, <code>1</code> 或 <code>2</code></li>
	<li><code>grid</code> 中 <strong>有且只有一个</strong> <code>-1</code></li>
	<li><code>grid</code> 中<strong> 有且只有一个</strong> <code>2</code></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python

```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java

```

### **...**

```

```

<!-- tabs:end -->
