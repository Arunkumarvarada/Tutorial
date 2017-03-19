## 题目分析：
给你word1、word2两个字符串，问最少需要几步才能把word1变成word2，下面每种操作都是一步：
a)添加一个字符；
b)添加一个字符；
c)把一个字符用另一个字符代替。

### 解题思路：
动态规划。用dp[i][j]表示把word1的前i个字符变成word2的前j个字符所需的步数，word1的前i个字符变成word2的前j个字符可以由三种方法得到：（1）word1先删去最后一个字符，然后把word1的前i-1个字符变成word2的前j个字符；（2）word1的前i个字符先变成word2的前j-1个字符；然后word2最后添上一个字符；（3）word1的前i-1个字符先变成word2的前j-1个字符；然后word1的最后一个字符和word2的最后一个字符匹配上。因此有状态转移方程：当word1[i-1]==word2[j-1]时dp[i][j]=dp[i-1][j-1]，否则dp[i][j]=min(dp[i-1][j]+1,dp[i][j-1]+1,dp[i-1][j-1]+1)。另外边界需要初始化：dp[0][0]=0，dp[i][0]=i对于i从1到len1，dp[0][i]=i对于i从1到len2,。最终答案为dp[len1][len2]，算法复杂度为O(len1\*len2)。

#### 算法正确性：
算法的关键点在于是否可以用动态规划的思想把问题拆分成一个个子问题。可以这么考虑：当你能确定用了若干步把word1的前i个字母变成word2的前j个字母后，接下来就可以处理相邻的状态。对于删除字母，可以把word1的第i+1个字母先删掉，然后再执行那若干步，这样可以得到把word1的前i+1个字母变成word2的前j个字母的步数；对于添加字母，可以先执行那若干步，再加上word2的第j+1个字母，这样可以得到把word1的前i个字母变成word2的前j+1个字母的步数；对于代替字母，可以先执行那若干步，再把word1的第i+1个字母和word2的第j+1个字母匹配上，这样可以得到把word1的前i+1个字母变成word2的前j+1个字母的步数。因此上述算法是正确的。

下面举一个简单例子走一遍算法帮助理解：word1=”ad”，word2=”abc”。</br>
初始化：dp[0][0]=0，dp[1][0]=1，dp[2][0]=2，dp[0][1]=1，dp[0][2]=2，dp[0][3]=3；</br>
i=1，j=1，word1[0]==word2[0]，dp[1][1]=min(dp[0][1]+1,dp[1][0]+1,dp[0][0])=0；</br>
i=1，j=2，word1[0]!=word2[1]，dp[1][2]=min(dp[0][2]+1,dp[1][1]+1,dp[0][1]+1)=2；</br>
i=1，j=3，word1[0]!=word2[2]，dp[1][3]=min(dp[0][3]+1,dp[1][2]+1,dp[0][2]+1)=3；</br>
i=2，j=1，word1[1]!=word2[0]，dp[2][1]=min(dp[1][1]+1,dp[2][0]+1,dp[1][0]+1)=1；</br>
i=2，j=2，word1[1]!=word2[1]，dp[2][2]=min(dp[1][2]+1,dp[2][1]+1,dp[1][1]+1)=1；</br>
i=2，j=3，word1[1]!=word2[2]，dp[2][3]=min(dp[1][3]+1,dp[2][2]+1,dp[1][2]+1)=2；</br>
最终结果为dp[2][3]=3。