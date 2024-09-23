---
title: "Leetcode Day 43 - Graph Theory Basic "
description: 图论基础， 深度优先搜索， 广度优先搜索
author: yoyo
date: 2024-09-23 10:36:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Graph Theory]
tags: [graph theory]
---

## Graph Theory

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Kama](https://img.shields.io/badge/Kama-gray)                                               | [Kama 98 所有可达路径](#所有可达路径)                                          |✅      |      |



## 所有可达路径

> [Link to the question](https://kamacoder.com/problempage.php?pid=1170)[^sykdlj]
{: .prompt-info }

**题目描述**

> 给定一个有 n 个节点的有向无环图，节点编号从 1 到 n。请编写一个函数，找出并返回所有从节点 1 到节点 n 的路径。每条路径应以节点编号的列表形式表示。

**输入描述**

>第一行包含两个整数 N，M，表示图中拥有 N 个节点，M 条边<br>
>后续 M 行，每行包含两个整数 s 和 t，表示图中的 s 节点与 t 节点中有一条路径

**输出描述**

> 输出所有的可达路径，路径中所有节点之间空格隔开，每条路径独占一行，存在多条路径，路径输出的顺序可任意。如果不存在任何一条路径，则输出 -1。<br>
> 注意输出的序列中，最后一个节点后面没有空格！ 例如正确的答案是 `1 3 5`,而不是 `1 3 5 `， 5后面没有空格！

**输入示例**

```
5 5
1 3
3 5
1 2
2 4
4 5
```

**输出示例**

```
1 3 5
1 2 4 5
```

[image]: sykdlj

**用例解释**
> 有五个节点，其中的从 1 到达 5 的路径有两个，分别是 1 -> 3 -> 5 和 1 -> 2 -> 4 -> 5。<br>
> 因为拥有多条路径，所以输出结果为：<br>
> `1 3 5`<br>
> `1 2 4 5`<br>
> 或<br>
> `1 2 4 5`<br>
> `1 3 5`<br>
> 都算正确。

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/kamacoder/0098.所有可达路径.html)[^Solution].

```python
n, m = map(int, input().split())

grid = [[] for _ in range(n + 1)]

for _ in range(m):
    s, d = map(int, input().split())
    grid[s].append(d)

def search(node, destination, path):
    if node == destination:
        return [path]
    
    paths = []
    for nextNode in grid[node]:
        paths.extend(search(nextNode, destination, path + [nextNode]))
    
    return paths

all_paths = search(1, n, [1])
if all_paths:
    for path in all_paths:
        print(" ".join(map(str, path)))
else:
    print(-1)
```

## Reference

[^sykdlj]:卡码网 KamaCoder-所有可达路径: [https://kamacoder.com/problempage.php?pid=1170](https://kamacoder.com/problempage.php?pid=1170).
[^Solution]:代码随想录-所有可达路径: [https://programmercarl.com/kamacoder/0098.所有可达路径.html](https://programmercarl.com/kamacoder/0098.所有可达路径.html).
