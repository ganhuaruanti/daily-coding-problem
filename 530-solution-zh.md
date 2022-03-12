# 530 解題思路

[題目530](530-zh.md)

所謂兩個字串的修改距離就是看兩個字串有有多少字元不同。

首先算出兩個字串長度。

然後以較短長度的字串去遍歷找出每個對應位置字元與較長字串的字元不同的個數 n

最後把 n + 兩個字串的長度差就是所謂兩個字串的修改距離。

## 解法

[yuanyu90221's golang 解法](https://github.com/yuanyu90221/DailyCodingProblem530Go)

[yuanyu90221's kotlin 解法](https://github.com/yuanyu90221/DailyCodingProblem530Kotlin)