## 题目分析：
有若干项目，每个项目有一个完成所获得的收益和启动的资产要求，初始时有资产W，求完成不超过k个项目的情况下的最终资产的最大值。

### 解题思路：
先将项目按启动资产要求从小到大排序，然后用优先队列求解，每次求解把启动资产要求不超过当前资产的项目放入优先队列中，然后若队列空则直接结束求解，否则取出一个收益最大的项目，更新答案，当取了k个项目的时候，上述求解过程结束。

下面举一个简单例子走一遍算法帮助理解：k=2，W=0，收益为[1,2,3]，资产要求为[0,1,1]。</br>
对项目进行排序，排序结果为[{1,0},{2,1},{3,1}]（数组元素表示为{收益，资产要求}）；</br>
当前已有资产设为0；</br>
第一次求解：</br>
项目{1,0}资产要求为0，不大于当前已有资产0，放入优先队列；</br>
项目{2,1}资产要求为1，大于当前已有资产0，不放入优先队列；</br>
从游戏队列中取出收益最大的项目{1,0}，更新当前收益为1；</br>
第二次求解：</br>
项目{2,1}资产要求为1，不大于当前已有资产1，放入优先队列；</br>
项目{3,1}资产要求为1，不大于当前已有资产1，放入优先队列；</br>
此时所有项目都已放入优先队列；</br>
从游戏队列中取出收益最大的项目{3,1}，更新当前收益为4；</br>
最终答案为4。