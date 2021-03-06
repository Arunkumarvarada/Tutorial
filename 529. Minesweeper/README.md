## 题目分析：
经典扫雷模拟。  
现给出一个二维数组，`M`表示没有被揭开的地雷、`E`表示未被揭开的空方块、`B`表示已经被打开了的空方块且周围没有地雷。如果一个空方块周围有地雷，则显示的是周围地雷的数目。`X`表示被揭开的地雷数目。  
具体规则如下：
+ 若揭开一个埋好的地雷，则游戏结束，将其变为`X`；
+ 若揭开一个周围没有地雷的空方格，则将其变为`B`，并且周围所有的空方格也应都被揭开；
+ 若一个周围有雷的空方格被揭开，则将其变为周围地雷的数值；
+ 当当前的已无方格再被揭开，返回当前矩阵
### 解题思路
一道常规的模拟题，现分情况讨论：
1. 若点击的格子埋雷，则直接将其变为`X`并结束；
2. 若点击的格子为空方格则 找周围八个格子，统计地雷数目，若其周围有雷则将其更改为对应的数字，并结束；否则将周围的格子加入队列进行拓展，重复该步，直到队列为空；(**注意使用bool数组标记，以防重复处理一个空格子**)
