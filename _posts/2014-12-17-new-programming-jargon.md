---
layout: post
title: "新编程术语"
date: 2014-12-17 19:30:00
category: essay
excerpt: <p>介绍一篇文章，New Programming Jargon。文章讲述了一些非常有趣的新编程术语。推荐阅读原文，不过，如果你英文太烂或因为太懒，那以下是我为你挑选并翻译的内容。</p>
---

介绍一篇文章，New Programming Jargon。文章讲述了一些非常有趣的新编程术语。推荐阅读原文，不过，如果你英文太烂或因为太懒，那以下是我为你挑选并翻译的内容。

原文链接： [http://blog.codinghorror.com/new-programming-jargon/#rd](http://blog.codinghorror.com/new-programming-jargon/#rd)

## 尤达句式

尤达句式 (Yoda Conditions) 是指在作条件判断时，常量在前，变量在后的写法。

```cpp
if (5 == count)
```

此名称来自《星球大战》中的角色尤达，据说他说话时不遵循正常语法。

## 鸭子

鸭子 (A Duck) 是指这样一种功能，它被添加进产品中，就是用来让产品经理将其干掉，以保护产品的其他部分不被修改。

此典故据说来自 Interplay 公司（就是作《辐射》的那家）。众所周知，产品经理们都有个毛病，就是你做完任何事情后，他们总是喜欢再改那么一下，仿佛不这么做，便不足以证明他们存在的价值。Interplay 公司的一名设计师也深知这一点，他在做完一段动画之后，感到非常满意，于是，他又为动画里的皇后添加了一只宠物鸭子。

最后，他把这段动画提交给了产品经理。产品经理完整地看了一遍，然后回头对设计师说：

> 非常好！不过，把那只鸭子去掉吧。

## 海森堡 bug

海森堡 bug (Heisenbug)，一种遵循「海森堡 (Heisenberg) 测不准原理」的程序 bug。当你试图测量这个 bug 时，将不可避免地扰动它的状态，使结果产生不确定性。

\\[
\Delta{x} \Delta{p} \ge \frac \hbar 2
\\]

## 生气的女友 bug

生气的女友 bug (Mad Girlfriend Bug) 出现时，你会发现明明结果不对，程序却始终告诉你没有错误。

## 恐惧驱动开发

恐惧驱动开发 (Fear-Driven Development)，类似测试驱动开发 (Test-Driven Development)，功能驱动开发 (Feature-Driven Development)。当领导不断给你施加压力时，你将会倾向于采用这种「最高效」的开发模式。

## 忍者注释

又叫「隐形注释」，「机密注释」，或者「没有注释」。
