# 514 解題思路

[題目 514](514-zh.md)

要找出最長連續數列長度

先設定最長連續數列長度為 longestAccum = 0

利用 HashSet 先把所有數值先存入

接著把 HashSet 內部所有元素

找出不具有該元素值 - 1的元素(也就是最小值元素)

然後紀錄目前找到的值為 currentNum ， 目前累計長度為 currentAccum = 1

然後檢查 HashSet 中有沒有 currentNum + 1 ，如果有則把 currentNum 與 currentAccum 都各加 1

如果 HashSet 沒有 currentNum + 1 ， 則將 longestAccum 設定為 longestAccum 與 currentAccum 的最大值

當走訪完所有 HashSet 中元素

longestAccum 則為最長連續長度

## 解法

[yuanyu90221's golang 解法](https://github.com/yuanyu90221/DailyCodingProblem514Go)
[yuanyu90221's kotlin 解法](https://github.com/yuanyu90221/DailyCodingProblem514)