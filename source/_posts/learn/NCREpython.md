---
title: 在学习、在更新…………
date: 2023-09-13 12:01:58
tags:
- 学校
- python
- 学习
---
**人的差别在于业余时间，而一个人的命运决定在晚上8点到10点之间。**

**因为一开始大家都在同一高度，做的工作一样，拿的薪水一样，大部分人下班后想休息，然后一直刷视频、打游戏，这样得到了即时满足，很爽，但你最终就什么都没有得到。**

**但是如果你能每天把握住这两个小时好好学习，能够习惯延迟满足，每天进步1%，那么一年后你将比现在的自己优秀3倍。**

![](https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885_1280.jpg)

<!-- more -->

1、input()函数返回值是字符串(str)类型，当用户输入的是数字的时候，需要用eval()或者float()或者int()转化成数值类型才能参加运算。

2、pow()函数是指数运算函数，例如pow(2,3)就是2的3次方。

3、format输出格式符号：

```python
a = "{}说他完成了，{}不相信它。".format('小明','老师')
# 结果：小明说他完成了，老师不相信它。
b = "{1:-^15.1s}说他完成了，{0}不相信它。".format('小明','老师')
# 结果：-------老-------说他完成了，小明不相信它。
c = "{1:-^15.1f}说他完成了，{0}不相信它。".format('小明',9527)
# 结果：----9527.0-----说他完成了，小明不相信它。

{ <参数序号> : < 填充字符  对齐方式   宽度  .  精度  类别 > }
```

![](https://pic2.zhimg.com/v2-579ed657a7e62beea77e5b16abf3c971_r.jpg)

4、内置库函数sorted()对于一个序列类型数据进行排序将排序后的结果返回出来 。

```python
sorted(ss.reverse = True) # 逆序输出ss序列。
```

5、\0表示一个空格，占1个长度。

6、all(x)组合类型变量X中所有元素都为真时返回True,否则返回False。若x为空，返回True。（一假则假）

7、any(x)组合类型变量X中任一元素为真时返回True，否则返回False。若x为空，返回False。（一真为真）

8、在python中，非零为真（True）

9、isinstance(obiect,classinfo)是如果object与classinfo类型相同返回True。

10、字符串的大小比较：0<9<A<Z<a<z  。列表大小比较：从左往右依次比较

11、**random库：**（脚注4，来自知乎）

```python
# 梅森循环算法
random.seed(10)
print(random.random())  # 初始化随机种子 ，相同种子会产生相同的随机数，如果不设置随机种子，以系统当前时间为默认值
print(random.random())
for i in range(10):
    print(random.randint(1, 10), end=' ')    # 产生[a, b]之间的随机整数（其中a和b都可以取到，左闭右闭区间）
print('\n')
print([random.randrange(10) for i in range(10)])    # 产生[0, a)之间的随机整数，（不包含a，左闭右开区间）
print([random.randrange(0, 10, 2) for i in range(10)])  # randrange(a, b, step)--产生[a, b)之间以setp为步长的随机整数
print([random.random() for i in range(10)])     # 产生[0.0, 1.0)之间的随机浮点数
print([random.uniform(2.1, 3.5) for i in range(10)])    # 产生[a, b]之间的随机浮点数
print(random.choice(['win', 'lose', 'draw']))   # 从目标序列类型中随机返回一个元素
print(random.choice("python"))
print(random.choices(['win', 'lose', 'draw'], k=5))     # choices(seq,weights=None, k)对序列类型进行k次重复采样，可设置权重，权重小的说明被取到的概率更小
print(random.choices(['win', 'lose', 'draw'], [4, 4, 2], k=10))   # 这里的[4,4,2]就是每个元素分别对应的权重
number = ['one', 'two', 'three', 'four']
random.shuffle(number)            # 将序列类型中元素随机排列，返回打乱后的序列
print(number)
print(random.sample([10, 20, 30, 40, 50], k=3))     # sample(pop, k)从pop类型中随机选取k个元素，以列表类型返回，如果k大于所有元素的个数，则报错
```

12、d.item() 返回d字典的所有键值对

13、









#### 相关链接：



[^1]: [下班后的时间，决定了你的人生高度！ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/42776218)
[^2]: [format()方法的基本使用 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/60357679)
[^3]: [Python format 格式化函数 | 菜鸟教程 (runoob.com)](https://www.runoob.com/python/att-string-format.html)

[^4]: [[python--random库（纯干货教程） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/571870972)](https://blog.csdn.net/zhongguoren666/article/details/6682749)

