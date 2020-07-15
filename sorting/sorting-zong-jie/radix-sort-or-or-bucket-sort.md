# radix sort \|\| bucket sort

* radix 是bucket sort的扩展
* stable sort
* 不能sort负数
* 看数据的个位，十位，百位来进行排序。
* 想象一个0-9 的桶。

![](../../.gitbook/assets/image%20%2824%29.png)

排序后arr = \[542, 53, 3, 14, 214, 748\],  根据个位数来进行的排序

![](../../.gitbook/assets/image%20%2823%29.png)

* 排序后arr = \[3，14，214，542，748，53\],  根据十位数来进行的排序

![](../../.gitbook/assets/image%20%2826%29.png)

* 第三轮排序后，arr=\[ 3, 14, 53, 214, 542, 748\]，根据百位来进行的排序。



