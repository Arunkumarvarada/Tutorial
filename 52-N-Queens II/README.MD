## 题目分析：
经典的`NPC`问题——N皇后。给出一个数字`N`，要求在`N*N`大小的棋盘之中摆放`N`个皇后，并要求皇后之前彼此不能攻击到。仅需算出合法的棋盘布局数目即可。  
### 解题思路:   
与`#51`类似，但已不需输出每种合法的棋盘布局的具体摆放，仅需计数即可。  
参照`#51`的解法二，使用与主对角线平行的直线的标记、与次对角线平行的直线的标记以及列的标记来判断当前行的棋子能够落在哪一个位置。得到一种合法的摆放情况，将计数值加一即可，整体时间复杂度不变。
