---
title: CaseFile
categories: Information Gathering
tags: [information gathering,casefile,recon,kali linux,reporting]
date: 2020-10-12 22:14:00
---
CaseFile 包描述
-------------

CaseFile 是 Maltego 的弟弟。它本质上与 Maltego 是一样的图形应用程序，但不具备运行转换的能力。CaseFile 让你能够快速添加、链接和分析数据。该应用程序针对的是 "离线 "分析师这一独特的市场，这些人的主要信息来源不是从开源情报方面获得的，也不是可以通过程序查询的。我们把这些人看作是在 "实地 "工作的调查员和分析师，他们从团队中的其他人那里获取情报，并建立起他们调查的信息地图。

CaseFile也可以简单地作为一个免费的图形查看器，用于查看Maltego中构建的图形。

工具来源： http://paterva.com/web6/products/casefile.php

[CaseFile主页][1] | [Kali CaseFile Repo仓库][2]

 - 作者：Paterva
 - 证书：Commercial

## CaseFile 是做什么的？

CaseFile 的诞生是由于许多 Maltego 用户使用该工具来使用他们从调查中获得的离线数据建立图形。这些用户并没有使用 Maltego 中的转换功能，只是需要 Maltego 图形功能的灵活性和性能。

- CaseFile是一个可视化智能应用程序，可用于确定数百种不同类型信息之间的关系和现实世界的联系。

- CaseFile可用于绘制信息片段之间的关系--即使它们相隔多个等级，也能看到隐藏的联系。
- CaseFile 捆绑了许多不同类型的实体，这些实体在调查中常用，允许你快速有效地行动。CaseFile 还能够添加自定义实体类型，允许你将产品扩展到你自己的数据集。

CaseFile 工具包中包含的工具
---------------------

### CaseFile——离线情报工具

CaseFile为你提供了快速添加、链接和分析数据的能力，它具有与Maltego相同的图形灵活性和性能，而无需使用变换。

CaseFile用法示例
-----------------

```shell
[/vc_column_text][/vc_column][/vc_row][vc_row][vc_column][vc_column_text]
root@kali:~# casefile
```
![casefile.png][3]


[1]: http://paterva.com/
[2]: https://gitlab.com/kalilinux/packages/casefile
[3]: http://tools.kali.org/wp-content/uploads/2014/02/casefile.png
