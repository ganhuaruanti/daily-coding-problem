# 513 解題思路

[題目 513](513-zh.md)

要找出特定值 K 和的子陣列

需要符合兩個條件

1 所有元素都是鄰近的

2 和為特定值

因此可以, 從當下位址的值往連續加到某一個值接近直到和的等於 K 或是走到陣列尾部

如果加到某一個位址的值剛好是該陣列的值

則回傳該子陣列

如果加到陣列尾部都不等於 K 則繼續從下一個位址加

## 解法

[yuanyu's golang solution](https://github.com/yuanyu90221/DailyCodingProblem513Go)

[yuanyu's kotlin solution](https://github.com/yuanyu90221/DailyCodingProblem513)