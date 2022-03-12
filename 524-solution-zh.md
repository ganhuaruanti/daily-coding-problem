# 524 解題思路

[題目524](524-zh.md)

要找出最大子陣列的之和

已知子陣列需要符合一個條件

每個值需要是連續的

假設陣列 A ， 存在一個  n > 1 使得 A 的前 n 的和 < An ，

可以透過以下關係去理解則要形成最大和就會直接從第 n 個開始算，因為必須要連續

所以計算方式如下

初始化最大值 S = 0 ， 當下累計連續何 Accum = 0

遍歷每個元素 A[i]， 每次計算 Accum += A[i]， i 為該元素位址

比較 Accum 跟 A[i] 大小，如果 A[i] > Accum 則設定 Accum = A[i]

比較 S 跟 Accum 大小，如果 Accum > S 則設定  S = Accum

## 解法

[yuanyu90221's golang 解法](https://github.com/yuanyu90221/DailyCodingProblem524Go)

[yuanyu90221's kotlin 解法](https://github.com/yuanyu90221/DailyCodingProblem524Kotlin)