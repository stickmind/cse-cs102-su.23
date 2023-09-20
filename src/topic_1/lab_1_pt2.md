# 圆整

打开 `round.c` 文件，查看函数 `is_power_of_2` 和 `round_up` 的代码。

- `is_power_of_2` 利用了 2 的幂的位模式的独特属性。还记得该属性是什么吗？该值与其前一个值（`num - 1`）之间的关系（就两个值共有的位而言）是什么？代码如何利用这两个属性来确定给定值是否为 2 的幂？
- `round_up` 返回第一个参数圆整后的值，圆整算法是向上舍入到第二个参数最近的倍数。首先考虑一般情况，当倍数不是 2 的幂时，如何使用算术运算向上舍入到下一个倍数？现在考虑倍数为 2 的幂的特殊情况，如何利用位运算取代低效的乘法/除法？

  函数 `round_up` 的计算过程类似于 Excel 中的 `CEILING` 函数，参考：[Round a number up to nearest multiple - exceljet.net](https://exceljet.net/formulas/round-a-number-up-to-nearest-multiple#:~:text=To%20round%20a%20number%20up%20to%20the%20nearest,formula%20in%20cell%20D6%20is%3A%20%3D%20CEILING%20%28B6%2CC6%29)。

这些函数表明，数字的表示只是一种位模式，了解不同表示形式的优势，可以更方便地选择算术运算或位运算，以提高计算效率。
