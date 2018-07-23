---
title: css选择器
date: 2018-07-19 12:00:00
tags: css
---


这篇文章来介绍一下 css 中的选择器


## id选择器:

### id选择器在css中有着比较高的优先级 代表唯一元素 在html中: id="box"

```css
#box {
  // somethings
}
```

## 类选择器:
### 类选择器 可以有很多个 优先级低于 id选择器 在html中:  class="item" 

```css
.item {
  // somethings
}

```

## 元素选择器:
### 元素选择器(标签选择器) 是html/xml中的标签 优先级低于类选择器 

```css
div {}
span {}
article {}
```

## 属性选择器
### 属性选择器为 为拥有指定属性的html标签来添加样式

```css
[title] {}
[placeholder] {}
[href] {}
[src] {}
```

## 通配符选择器
### 通配符选择器 为 * 为所有的html标签添加样式

```css
* { margin: 0; padding: 0; }
```

## 伪类选择器
### 伪类选择器是css2.0规范中的 用 : 一个冒号隔开
```css
button:active {} /* 激活元素 */
button:hover {} /* 鼠标移入 */
button:visited {} /* 已访问链接的样式 */
button:focus {} /* 获取焦点 */
button:link {} /* 未访问链接的样式 */
```

## 伪元素选择器
### 这货是css3.0规范 和 伪类选择不同 `::`用双引号隔开
```css
button::last-child {}
button::first {}
button::nth-child(even) {}

```

## 相邻兄弟选择器
### 相邻兄弟选择器  适用于其他选择器 一个元素跟在另一个元素的后面

```html
<h1>title</h1>
<div>test</div>
<div>test2</div>
<ul>
  <li class="item">item1-1</li>
</ul>
<ul>
  <li class="item">item2-1</li>
  <li class="item">item2-2</li>
  <li class="item">item2-3</li>
</ul>
```

```css
h1 + div {
  color: red; /* div test 的颜色会变为红色 */
}
.item + .item {
  font-weight: bold; /* ul下的li除了第一个其他的字体都会加粗 找不到相邻的元素就不会生效 */
}
```

## 后代选择器
### 格式为 `selector1 ~ selector2` 元素必须要有相同的父元素，但是selector2不必紧紧跟再selector1的后面

## 子元素选择器
### 格式为: `selector1 > selector2`
```css
div > p {
  color: red;
}
```

## 选择器分组
### 格式为: `selector1 + , selector2 `
```css
#box,.item,p {} /* 用来同时给一组选择器设置样式 */
```

通常我们去设置css的时候 可能会用选择器来覆盖其他选择器的样式，选择器有一个权重的概念，我简单的做了一个区分

| selector | example | weight |
| :-: | :-: | :-: |
| 通配符选择器 | * | 1
| 属性选择器 | [title] | 10
| 标签选择器 | div | 100 | 
| 类选择器 | .item | 1000 |
| id选择器 | #box | 10000 |
| 伪类选择器 | div:hover | 冒号前的选择器的和 + 10 |
| 伪元素选择器 | div::nth-child(even) | 冒号前的选择器的和 + 10 |
| 相邻兄弟选择器 | div + div | 选择器权重的和 |
| 后代选择器 | div ~ p | 选择器权重的和 |

>> 注意！这里不包括css3中的查询和动画的规则