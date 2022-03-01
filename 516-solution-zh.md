# 516 解題思路

[題目516](516-zh.md)

已知每個 sevenish 數字都是 7 的次方數或是 7 的平方數之和。

所以每個 sevenish 數字化作以 7 為基數的字串都會符合 
1[0,1]*$

而從例子中可以發現

1 -> 0b1 -> 1(以7為基數) -> 1 (7 的 0 次方)

2 -> 0b10 -> 10(以7為基數) -> 7 (7 的 1 次方)

3 -> 0b11 -> 11(以7為基數) -> 8 = 7 + 1 (7 的 1 次方 + 7 的 0 次方)

4 -> 0b100 -> 100(以7為基數) -> 49 = (7 的 2 次方)

n -> n 的 2 進位表示式 -> (n 的 2 進位表示式) 把基數改為 7 轉回 10 進位數值。

## 解法

[yuanyu90221's golang 解法](https://github.com/yuanyu90221/DailyCodingProblem516Go)
[yuanyu90221's kotlin 解法](https://github.com/yuanyu90221/DailyCodingProblem516)