---
layout: post
title: 使用servlet结合jsp开发购物车功能
categories: Excel
description: 使用servlet结合jsp开发购物车功能
keywords: servlet, jsp, java
---

[toc]
#购物车

>在开发购物车之前，首先要把几个关键类之间的关系理清楚

## 1 : 类图    
首先各个类的意义：
1. Product 产品
2. User 用户
3. Order 订单
4. OrderItem 订单项
![error](leanote://file/getImage?fileId=58d48eca0b47e54e4b000014)

订单项

:    一条记录就是一个订单项，对应一种商品，以及购买数量。

## 2 : 类关系图    
1. 产品和订单项的关系是 一对多
一种产品，对应多条订单项。 
一条订单项，对应一种产品
2. 订单项和订单的关系 多对一
一个订单里有多条订单项
一个订单项，只会出现在一个订单里
3. 订单和用户的关系： 多对一
一个订单，只能属于一个用户
一个用户，可以下多个订单
![](leanote://file/getImage?fileId=58d48eda0b47e54e4b000015)