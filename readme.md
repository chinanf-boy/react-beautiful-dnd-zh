# react-beautiful-dnd [![explain]][source] [![translate-svg]][translate-list]

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list

「 `React.js` 漂亮,可移植性 列表拖拽库 」{翻译}

---

## 更新 ✅

<!-- doc-templite START generated -->
<!-- time = '2018 10.31' -->
<!-- repo = 'atlassian/react-beautiful-dnd' -->
<!-- commit = '5fc46a8296e8a91ab7e417d0a948c2f69cfafd43' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018 10.31 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/atlassian/react-beautiful-dnd.svg
[commit]: https://github.com/atlassian/react-beautiful-dnd/tree/5fc46a8296e8a91ab7e417d0a948c2f69cfafd43

<!-- doc-templite END generated -->

- [x] readme
- [x] docs/**
  - [x] [拖拽`<svg>`](docs/guides/dragging-svgs.zh.md)
  - [x] [屏幕阅读器指南](docs/guides/screen-reader.zh.md)
  - [x] [运用`innerRef`](docs/guides/using-inner-ref.zh.md)
  - [x] [我们如何使用DOM事件](docs/guides/how-we-use-dom-events.zh.md)
  - [x] [钩子-`Hook`s](docs/guides/hooks.zh.md)
  - [x] [表格](docs/patterns/tables.zh.md)
  - [x] [使用 portal](docs/patterns/using-a-portal.zh.md)
  - [x] [多拖动模式](docs/patterns/multi-drag.zh.md)

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

更新了版本，但有点走神，多多见谅，大力Issue与PR，致歉

## 生活

[If help, **buy** me coffee —— 营养跟不上了，给我来瓶营养快线吧! 💰](https://github.com/chinanf-boy/live-need-money)

---


![react beautiful dnd](https://raw.githubusercontent.com/alexreardon/files/master/resources/react-beautiful-dnd-logo.png)

# react-beautiful-dnd

 [`React.js`](https://facebook.github.io/react/) 美丽,无障碍的列表拖放库

[![CircleCI branch](https://img.shields.io/circleci/project/github/atlassian/react-beautiful-dnd/master.svg)](https://circleci.com/gh/atlassian/react-beautiful-dnd/tree/master)
[![npm](https://img.shields.io/npm/v/react-beautiful-dnd.svg)](https://www.npmjs.com/package/react-beautiful-dnd) [![dependencies](https://david-dm.org/atlassian/react-beautiful-dnd.svg)](https://david-dm.org/atlassian/react-beautiful-dnd) [![Greenkeeper badge](https://badges.greenkeeper.io/atlassian/react-beautiful-dnd.svg)](https://greenkeeper.io/) [![SemVer](https://img.shields.io/badge/SemVer-2.0.0-brightgreen.svg)](http://semver.org/spec/v2.0.0.html)

![quote application example](https://raw.githubusercontent.com/alexreardon/files/master/resources/website-board.gif?raw=true)


<details>

<summary> <strong> ❤️ react-beautiful-dnd 文档目录 ❤️</strong> </summary>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [例子🎉](#%E4%BE%8B%E5%AD%90)
  - [在桌面上查看](#%E5%9C%A8%E6%A1%8C%E9%9D%A2%E4%B8%8A%E6%9F%A5%E7%9C%8B)
  - [在手机或平板电脑上查看](#%E5%9C%A8%E6%89%8B%E6%9C%BA%E6%88%96%E5%B9%B3%E6%9D%BF%E7%94%B5%E8%84%91%E4%B8%8A%E6%9F%A5%E7%9C%8B)
- [基本使用示例](#%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8%E7%A4%BA%E4%BE%8B)
- [核心特点](#%E6%A0%B8%E5%BF%83%E7%89%B9%E7%82%B9)
- [来来来,入门 🤩](#%E6%9D%A5%E6%9D%A5%E6%9D%A5%E5%85%A5%E9%97%A8-)
- [Read this in other languages](#read-this-in-other-languages)
- [目前支持的功能集](#%E7%9B%AE%E5%89%8D%E6%94%AF%E6%8C%81%E7%9A%84%E5%8A%9F%E8%83%BD%E9%9B%86)
  - [更多即将推出](#%E6%9B%B4%E5%A4%9A%E5%8D%B3%E5%B0%86%E6%8E%A8%E5%87%BA)
- [升级](#%E5%8D%87%E7%BA%A7)
- [并不适合所有人](#%E5%B9%B6%E4%B8%8D%E9%80%82%E5%90%88%E6%89%80%E6%9C%89%E4%BA%BA)
- [驾驶理念: 物理性](#%E9%A9%BE%E9%A9%B6%E7%90%86%E5%BF%B5-%E7%89%A9%E7%90%86%E6%80%A7)
  - [应用1: 没有即时移动](#%E5%BA%94%E7%94%A81-%E6%B2%A1%E6%9C%89%E5%8D%B3%E6%97%B6%E7%A7%BB%E5%8A%A8)
  - [应用2: 知道何时移动](#%E5%BA%94%E7%94%A82-%E7%9F%A5%E9%81%93%E4%BD%95%E6%97%B6%E7%A7%BB%E5%8A%A8)
  - [应用3: 没有阴影](#%E5%BA%94%E7%94%A83-%E6%B2%A1%E6%9C%89%E9%98%B4%E5%BD%B1)
  - [应用4: 最大化交互性](#%E5%BA%94%E7%94%A84-%E6%9C%80%E5%A4%A7%E5%8C%96%E4%BA%A4%E4%BA%92%E6%80%A7)
  - [应用5: 无拖动轴锁定](#%E5%BA%94%E7%94%A85-%E6%97%A0%E6%8B%96%E5%8A%A8%E8%BD%B4%E9%94%81%E5%AE%9A)
  - [应用6: 自然交叉表移动](#%E5%BA%94%E7%94%A86-%E8%87%AA%E7%84%B6%E4%BA%A4%E5%8F%89%E8%A1%A8%E7%A7%BB%E5%8A%A8)
- [精心设计的动画](#%E7%B2%BE%E5%BF%83%E8%AE%BE%E8%AE%A1%E7%9A%84%E5%8A%A8%E7%94%BB)
  - [删除](#%E5%88%A0%E9%99%A4)
  - [走出困境](#%E8%B5%B0%E5%87%BA%E5%9B%B0%E5%A2%83)
- [关心交互细节](#%E5%85%B3%E5%BF%83%E4%BA%A4%E4%BA%92%E7%BB%86%E8%8A%82)
  - [焦点管理](#%E7%84%A6%E7%82%B9%E7%AE%A1%E7%90%86)
  - [自动滚动](#%E8%87%AA%E5%8A%A8%E6%BB%9A%E5%8A%A8)
    - [对于鼠标和触摸输入 🐭📱](#%E5%AF%B9%E4%BA%8E%E9%BC%A0%E6%A0%87%E5%92%8C%E8%A7%A6%E6%91%B8%E8%BE%93%E5%85%A5-)
      - [鼠标滚轮和触控板](#%E9%BC%A0%E6%A0%87%E6%BB%9A%E8%BD%AE%E5%92%8C%E8%A7%A6%E6%8E%A7%E6%9D%BF)
      - [关于大`Draggable`的笔记](#%E5%85%B3%E4%BA%8E%E5%A4%A7draggable%E7%9A%84%E7%AC%94%E8%AE%B0)
      - [iOS自动滚动摇晃 📱🤕](#ios%E8%87%AA%E5%8A%A8%E6%BB%9A%E5%8A%A8%E6%91%87%E6%99%83-)
    - [用于键盘拖动 🎹](#%E7%94%A8%E4%BA%8E%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8-)
  - [无障碍](#%E6%97%A0%E9%9A%9C%E7%A2%8D)
    - [示例屏幕阅读器行为](#%E7%A4%BA%E4%BE%8B%E5%B1%8F%E5%B9%95%E9%98%85%E8%AF%BB%E5%99%A8%E8%A1%8C%E4%B8%BA)
- [鼠标拖动](#%E9%BC%A0%E6%A0%87%E6%8B%96%E5%8A%A8)
  - [马虎点击并点击预防🐱🎁](#%E9%A9%AC%E8%99%8E%E7%82%B9%E5%87%BB%E5%B9%B6%E7%82%B9%E5%87%BB%E9%A2%84%E9%98%B2)
  - [键盘快捷键: 鼠标拖动](#%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E9%94%AE-%E9%BC%A0%E6%A0%87%E6%8B%96%E5%8A%A8)
- [键盘拖动](#%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8)
  - [键盘快捷键: 键盘拖动](#%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E9%94%AE-%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8)
    - [在一个垂直列表中](#%E5%9C%A8%E4%B8%80%E4%B8%AA%E5%9E%82%E7%9B%B4%E5%88%97%E8%A1%A8%E4%B8%AD)
    - [在一个水平列表中](#%E5%9C%A8%E4%B8%80%E4%B8%AA%E6%B0%B4%E5%B9%B3%E5%88%97%E8%A1%A8%E4%B8%AD)
- [触摸拖动](#%E8%A7%A6%E6%91%B8%E6%8B%96%E5%8A%A8)
  - [理解意图: 点击,强按,滚动并拖动](#%E7%90%86%E8%A7%A3%E6%84%8F%E5%9B%BE-%E7%82%B9%E5%87%BB%E5%BC%BA%E6%8C%89%E6%BB%9A%E5%8A%A8%E5%B9%B6%E6%8B%96%E5%8A%A8)
  - [开始拖动: 长按](#%E5%BC%80%E5%A7%8B%E6%8B%96%E5%8A%A8-%E9%95%BF%E6%8C%89)
  - [点按支持](#%E7%82%B9%E6%8C%89%E6%94%AF%E6%8C%81)
  - [原生滚动支持](#%E5%8E%9F%E7%94%9F%E6%BB%9A%E5%8A%A8%E6%94%AF%E6%8C%81)
  - [大力按压支持](#%E5%A4%A7%E5%8A%9B%E6%8C%89%E5%8E%8B%E6%94%AF%E6%8C%81)
  - [振动](#%E6%8C%AF%E5%8A%A8)
- [多拖](#%E5%A4%9A%E6%8B%96)
- [预设样式](#%E9%A2%84%E8%AE%BE%E6%A0%B7%E5%BC%8F)
  - [在每个阶段](#%E5%9C%A8%E6%AF%8F%E4%B8%AA%E9%98%B6%E6%AE%B5)
    - [总是: 拖动控制](#%E6%80%BB%E6%98%AF-%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6)
    - [总是: 可以放下](#%E6%80%BB%E6%98%AF-%E5%8F%AF%E4%BB%A5%E6%94%BE%E4%B8%8B)
  - [阶段: 停在元素](#%E9%98%B6%E6%AE%B5-%E5%81%9C%E5%9C%A8%E5%85%83%E7%B4%A0)
    - [(阶段: 停在元素) : 拖动控制](#%E9%98%B6%E6%AE%B5-%E5%81%9C%E5%9C%A8%E5%85%83%E7%B4%A0--%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6)
  - [阶段: 拖动](#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8)
    - [(阶段: 拖动) : 拖动控制元素](#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6%E5%85%83%E7%B4%A0)
    - [(阶段: 拖动) : 可拖动的元素](#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--%E5%8F%AF%E6%8B%96%E5%8A%A8%E7%9A%84%E5%85%83%E7%B4%A0)
    - [(阶段: 拖动) : body元素](#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--body%E5%85%83%E7%B4%A0)
  - [阶段: 放下](#%E9%98%B6%E6%AE%B5-%E6%94%BE%E4%B8%8B)
    - [(阶段: 放下) : 拖动控制元素](#%E9%98%B6%E6%AE%B5-%E6%94%BE%E4%B8%8B--%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6%E5%85%83%E7%B4%A0)
    - [(阶段: 放下) : 可拖动](#%E9%98%B6%E6%AE%B5-%E6%94%BE%E4%B8%8B--%E5%8F%AF%E6%8B%96%E5%8A%A8)
  - [阶段: 用户取消](#%E9%98%B6%E6%AE%B5-%E7%94%A8%E6%88%B7%E5%8F%96%E6%B6%88)
  - [预设样式是供应商的前缀](#%E9%A2%84%E8%AE%BE%E6%A0%B7%E5%BC%8F%E6%98%AF%E4%BE%9B%E5%BA%94%E5%95%86%E7%9A%84%E5%89%8D%E7%BC%80)
- [安装](#%E5%AE%89%E8%A3%85)
  - [包管理器](#%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8)
  - [分发包](#%E5%88%86%E5%8F%91%E5%8C%85)
- [`ClojureScript`](#clojurescript)
- [API](#api)
- [`DragDropContext`](#dragdropcontext)
  - [Props](#props)
  - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
  - [钩子们{Hook}](#%E9%92%A9%E5%AD%90%E4%BB%AChook)
- [`Droppable`](#droppable)
  - [可拖 Props](#%E5%8F%AF%E6%8B%96-props)
  - [子函数](#%E5%AD%90%E5%87%BD%E6%95%B0)
    - [1.提供:  (DroppableProvided) \*\*:](#1%E6%8F%90%E4%BE%9B--droppableprovided-%5C%5C)
    - [2.快照:  (DroppableStateSnapshot)](#2%E5%BF%AB%E7%85%A7--droppablestatesnapshot)
  - [有条件地放下](#%E6%9C%89%E6%9D%A1%E4%BB%B6%E5%9C%B0%E6%94%BE%E4%B8%8B)
  - [滚动容器](#%E6%BB%9A%E5%8A%A8%E5%AE%B9%E5%99%A8)
  - [空`Droppable`](#%E7%A9%BAdroppable)
  - [推荐 Droppable 性能优化](#%E6%8E%A8%E8%8D%90-droppable-%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96)
- [`Draggable`](#draggable)
  - [可拖动 Props](#%E5%8F%AF%E6%8B%96%E5%8A%A8-props)
  - [子函数 (渲染 Props )](#%E5%AD%90%E5%87%BD%E6%95%B0-%E6%B8%B2%E6%9F%93-props-)
    - [1.提供:  (DraggableProvided)](#1%E6%8F%90%E4%BE%9B--draggableprovided)
      - [`innerRef`: 例子](#innerref-%E4%BE%8B%E5%AD%90)
      - [`draggableProps` 类型信息](#draggableprops-%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
      - [`draggableProps` 例子](#draggableprops-%E4%BE%8B%E5%AD%90)
      - [定位所有权](#%E5%AE%9A%E4%BD%8D%E6%89%80%E6%9C%89%E6%9D%83)
      - [警告: `position: fixed`](#%E8%AD%A6%E5%91%8A-position-fixed)
      - [在列表之间移动时保持焦点](#%E5%9C%A8%E5%88%97%E8%A1%A8%E4%B9%8B%E9%97%B4%E7%A7%BB%E5%8A%A8%E6%97%B6%E4%BF%9D%E6%8C%81%E7%84%A6%E7%82%B9)
      - [扩展`DraggableProps.style`](#%E6%89%A9%E5%B1%95draggablepropsstyle)
      - [避免 margin 折叠 多个`Draggable`](#%E9%81%BF%E5%85%8D-margin-%E6%8A%98%E5%8F%A0-%E5%A4%9A%E4%B8%AAdraggable)
      - [`Draggable`们应该是可见的兄弟姐妹](#draggable%E4%BB%AC%E5%BA%94%E8%AF%A5%E6%98%AF%E5%8F%AF%E8%A7%81%E7%9A%84%E5%85%84%E5%BC%9F%E5%A7%90%E5%A6%B9)
      - [`dragHandleProps`类型信息](#draghandleprops%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
      - [`dragHandleProps`例子: 标准](#draghandleprops%E4%BE%8B%E5%AD%90-%E6%A0%87%E5%87%86)
      - [`dragHandleProps`例子: 自定义拖动控制](#draghandleprops%E4%BE%8B%E5%AD%90-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6)
      - [`dragHandleProps`猴子补丁](#draghandleprops%E7%8C%B4%E5%AD%90%E8%A1%A5%E4%B8%81)
    - [2.快照:  (DraggableStateSnapshot)](#2%E5%BF%AB%E7%85%A7--draggablestatesnapshot)
  - [`Draggable`占位符](#draggable%E5%8D%A0%E4%BD%8D%E7%AC%A6)
  - [添加一个`onClick`控制到一个`Draggable`或者一个*拖动控制*](#%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AAonclick%E6%8E%A7%E5%88%B6%E5%88%B0%E4%B8%80%E4%B8%AAdraggable%E6%88%96%E8%80%85%E4%B8%80%E4%B8%AA%E6%8B%96%E5%8A%A8%E6%8E%A7%E5%88%B6)
  - [交互式的子元素`Draggable`](#%E4%BA%A4%E4%BA%92%E5%BC%8F%E7%9A%84%E5%AD%90%E5%85%83%E7%B4%A0draggable)
- [`resetServerContext`](#resetservercontext)
- [Flow 使用](#flow-%E4%BD%BF%E7%94%A8)
  - [公共 Flow 类型](#%E5%85%AC%E5%85%B1-flow-%E7%B1%BB%E5%9E%8B)
  - [使用 Flow 类型](#%E4%BD%BF%E7%94%A8-flow-%E7%B1%BB%E5%9E%8B)
- [Typescript](#typescript)
  - [用 flow 类型示例应用程序](#%E7%94%A8-flow-%E7%B1%BB%E5%9E%8B%E7%A4%BA%E4%BE%8B%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F)
- [社区作品](#%E7%A4%BE%E5%8C%BA%E4%BD%9C%E5%93%81)
- [其他](#%E5%85%B6%E4%BB%96)
- [工程健康](#%E5%B7%A5%E7%A8%8B%E5%81%A5%E5%BA%B7)
  - [类型化](#%E7%B1%BB%E5%9E%8B%E5%8C%96)
  - [经测试](#%E7%BB%8F%E6%B5%8B%E8%AF%95)
  - [性能](#%E6%80%A7%E8%83%BD)
- [大小](#%E5%A4%A7%E5%B0%8F)
- [支持的浏览器](#%E6%94%AF%E6%8C%81%E7%9A%84%E6%B5%8F%E8%A7%88%E5%99%A8)
- [作者](#%E4%BD%9C%E8%80%85)
- [维护者](#%E7%BB%B4%E6%8A%A4%E8%80%85)
- [合作者](#%E5%90%88%E4%BD%9C%E8%80%85)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</details>


## 例子🎉

看看它对你自己有多美丽!

### 在桌面上查看

[所有的例子!](https://react-beautiful-dnd.netlify.com)

### 在手机或平板电脑上查看

-   [简单的列表](https://react-beautiful-dnd.netlify.com/iframe.html)
-   [排板](https://react-beautiful-dnd.netlify.com/iframe.html?selectedKind=board&selectedStory=simple)- 最好在风景中观看

> 目前,我们为触摸设备提供不同的[故事书{storybook}](https://github.com/storybooks/storybook)链接,但没有很好的移动菜单体验[更多信息](https://github.com/storybooks/storybook/issues/124)

## 基本使用示例

我们已经创建了一些基本的例子`codesandbox`为你直接玩: 

-   [简单的垂直列表](https://codesandbox.io/s/k260nyxq9v)
-   [简单的水平列表](https://codesandbox.io/s/mmrp44okvj)
-   [两个列表之间的简单 DnD「drag and drop」](https://codesandbox.io/s/l7ro2231o7)

> 即将推出: 获取入门指南!

## 核心特点

-   美丽,自然的物品移动
-   简洁且功能强大的api快速开始
-   与标准浏览器交互非常好
-   Unopinionated 「没有固执己见」样式
-   没有创建额外的包装DOM节点 -  flexbox 和 焦点{focus} 管理友好!
-   无障碍

## 来来来,入门 🤩

我们 漂亮地创建了课程 [a free course on `egghead.io`](https://egghead.io/courses/beautiful-and-accessible-drag-and-drop-with-react-beautiful-dnd) 去帮助人们 尽可能快地入门 `react-beautiful-dnd` 

![Course logo](https://user-images.githubusercontent.com/2182637/43372837-8c72d3f8-93e8-11e8-9d92-a82adde7718f.png)

## Read this in other languages

- [![kr](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/South-Korea.png) **한글/Korean**](https://github.com/LeeHyungGeun/react-beautiful-dnd-kr)

- [![china](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/China.png) **中文/Chinese**](https://github.com/chinanf-boy/react-beautiful-dnd-zh)


## 目前支持的功能集

-   垂直列表 ↕
-   水平列表 ↔
-   列表之间的移动 (▤ ↔ ▤) 
-   鼠标 🐭,键盘 🎹 和触摸 👉📱 (手机,平板电脑等) 支持
-   自动滚动 - 在拖动过程中根据需要自动滚动容器和窗口 (即使是使用键盘🔥) 
-   [多拖动支持](/docs/patterns/multi-drag.zh.md)
-   令人难以置信的屏幕阅读器支持 - 我们为开箱即用的英文屏幕阅读器提供了惊人的体验. 我们还为需要它的人提供完整的定制控制和国际化支持
-   [拖动](https://github.com/atlassian/react-beautiful-dnd#props-1)和[放下](https://github.com/atlassian/react-beautiful-dnd#conditionally-dropping)条件
-   在一个页面上有多个独立的列表
-   灵活的项目大小 - 可拖动的项目可以有不同的高度 (垂直列表) 或宽度 (水平列表) 
-   兼容 semantic 表格 重新排序 -[表格模式](/docs/patterns/tables.zh.md)
-   兼容[`React.Portal`](https://reactjs.org/docs/portals.html)-[ Portal 模式「portal pattern」](/docs/patterns/using-a-portal.zh.md)
-   自定义拖动控制 - 您可以通过拖动整个项目的一部分
-   一个`Droppable`列表可以是滚动容器 (没有可滚动的父项) 或者是滚动容器的子项 (也没有可滚动的父项) 
-   独立的嵌套列表 - 列表可以是另一个列表的子项,但不能将项目从父列表拖到子列表中
-   服务器端渲染兼容
-   默认与[嵌套的交互式元素](https://github.com/atlassian/react-beautiful-dnd#interactive-child-elements-within-a-draggable)兼容

### 更多即将推出

您可以查看即将登陆的所有功能[在我们的问题页面上](https://github.com/atlassian/react-beautiful-dnd/issues). 

## 升级

我们在发行说明中创建了升级说明,以帮助您升级到最新版本!

- [从 `7.x` 到 `8.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v8.0.0)
- [从 `6.x` 到 `7.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v7.0.0)
- [从 `5.x` 到 `6.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v6.0.0)
- [从 `4.x` 到 `5.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v5.0.0)
- [从 `3.x` 到 `4.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v4.0.0)


## 并不适合所有人

有很多库允许React中的拖放交互. 其中最值得注意的是惊人的[`react-dnd`](https://github.com/react-dnd/react-dnd). 它提供了一套非常出色的拖放函数,这些函数在特定情况下非常适用[疯狂地不一致](https://www.quirksmode.org/blog/archives/2009/09/the_html5_drag.html)的html5拖放功能. `react-beautiful-dnd` **是为垂直和水平列表专门构建的更高级别的抽象**. 在该功能的子集内`react-beautiful-dnd`提供强大,自然和美丽的拖放体验. 但是,它没有提供 react-dnd 提供的广泛功能. 所以这个库可能不适合你,这取决于你的用例是什么. 

## 驾驶理念: 物理性

核心设计理念`react-beautiful-dnd`是物理性的: 我们希望用户感觉他们正在移动物体

### 应用1: 没有即时移动

这是一个相当标准的拖放模式,用于响应用户拖动而消失并重新出现的东西. 对于更自然的拖动,我们为物品的移动设置动画,因为它们需要在拖动时`偏移`以更清晰地显示拖动效果. 我们还制作了一件物品的下落动画,以便将其移动到新的位置. 在任何时候,无论它是否在拖动, 物品都不会随时随地移动. 

### 应用2: 知道何时移动

常见用法: 拖放交互基于用户开始拖动的位置. 

在`react-beautiful-dnd`拖动物品的影响是基于其重心 - 无论用户从哪里抓取物品. 拖动项目的影响遵循 类似的规则 ⚖️. 以下是一些遵循的规则,即使对于灵活高度的物品也可以实现自然的拖拽体验: 

-   当拖动物品的中心位置越过列表的边界之一时, 列表是*拖过去*
-   当拖动物品的中心位置越过`休息{没拖着}`物品的边缘时,没拖动物品将移出拖动物品的路线. 换句话说: 一旦物品 (A) 的中心位置越过另一物品 (B) 的边缘,B就会移开. 

### 应用3: 没有阴影

在物品及其目的地四处移动的环境中,阴影很有用. 但是,与`react-beautiful-dnd`根据物品的移动情况, 物品的放置位置应该很明显. 这可能会在未来发生变化 - 这一点上是要看看接下来, 我们在没有任何这些可供选择的情况下能够获得多少. 

### 应用4: 最大化交互性

`react-beautiful-dnd`真的很难避免尽可能多的非互动性阶段. 用户应该觉得他们在控制界面,而不是等待动画完成,然后才能继续与界面交互. 然而,为了让每个人的生活更加健康,在 正确性和权力 之间需要做出平衡. 以下是有些事情不具有互动性的唯一情况: 

1.  从用户取消拖动到拖放动画完成时. 取消时有很多事情要回到他们应该在的地方. 如果您在不是 真正的家的`位置` 抓取物品,则拖动将不正确. 
2.  真正拖动物品后就开始动画了. 为了简单起见,情况就是这样 - 在实际动画的期间上很难再抓东西. 它可以被编码 - 但它似乎是一个边缘案例,会增加很多复杂性. 

请记住,这些不活动时间可能并不总是存在. 

### 应用5: 无拖动轴锁定

目前,库不支持拖动轴锁定 (又名拖轨) . 这是用户被限制在只沿一个轴拖动的地方. 目前的想法是,这打破了我们正在寻找的物理隐喻,并向用户发送一条消息,即他们正在与一个软件进行交互,而不是移动物理对象. 可以确保用户只能通过使用 Props 放入单个列表中`type`和`isDropDisabled`. 您也可以对列表进行一些视觉处理到`onDragStart`函数,这是唯一的用户显示他们互动的地方. 

### 应用6: 自然交叉表移动

比起使用基于索引的方法在列表之间移动键盘,`react-beautiful-dnd`更倾向于执行交叉表移动 **惯性,重力和碰撞**. 您可以通过阅读博客了解更多关于这是如何工作的["列表之间的自然键盘移动"](https://medium.com/@alexandereardon/friction-gravity-and-collisions-3adac3a94e19). 

![例子🌰](https://raw.githubusercontent.com/alexreardon/files/master/resources/collision.gif?raw=true)

## 精心设计的动画

随着事情的发展,用户会很容易被动画分散注意力或阻碍他们前进. 我们调整了各种动画,以确保指导,表演和互动性之间的平衡. 

### 删除

当你拖放一个拖动项目时,它的运动是基于物理的 (谢谢[`react-motion`](https://github.com/chenglou/react-motion)) . 这导致放下感觉更加重和物理. 

### 走出困境

移出拖动项目的项目是通过 CSS过渡 而非物理过程来实现的. 这是通过允许 GPU处理运动来最大化性能. CSS动画曲线的设计是为了避免沟通. 

它是如何组成的: 

1.  一个模拟自然反应时间的热身期
2.  一个小阶段,可以快速移除
3.  长尾巴,以便人们可以阅读 动画后半部分正在动画时 的任何文字

![animation curve](https://raw.githubusercontent.com/alexreardon/files/master/resources/dnd-ease-in-out-small.png?raw=true)

> 动画曲线在移动时使用

## 关心交互细节

### 焦点管理

`react-beautiful-dnd`不会创建任何包装元素. 这意味着它不会影响文档的常用选项卡流程. 例如,如果你正在包装一个*目标*标签,则用户将直接 tab 到目标点,而不是一个围绕该*目标*的元素. 无论你包装什么元素都会得到一个`tab-index`以确保用户通过 tab 拖动. 

### 自动滚动

当用户拖动一个`Draggable{可拖动物品}`靠近*容器*边缘时, 我们会自动滚动容器,以便为其腾出`Draggable`空间. 

> 一个*容器*称为一个`Droppable`,是因为可滚动的或有一个滚动父辈 - 或`window`. 

| 鼠标和触摸                                                                                                                     | 键盘                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| ![auto-scroll-mouse](https://user-images.githubusercontent.com/2182637/36520373-c9e2cb7e-17e4-11e8-9e93-4d2389d51fa4.gif) | ![auto-scroll-keyboard](https://user-images.githubusercontent.com/2182637/36520375-cc1aa45c-17e4-11e8-842d-94aed694428a.gif) |

它也适用于多列表所有输入类型的配置

| 鼠标和触摸                                                                                                                           | 键盘                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| ![auto-scroll-board-mouse](https://user-images.githubusercontent.com/2182637/36520670-57752526-17e6-11e8-95b3-b5a3978a5312.gif) | ![auto-scroll-board-keyboard](https://user-images.githubusercontent.com/2182637/36520650-3d3638f8-17e6-11e8-9cba-1fb439070285.gif) |

#### 对于鼠标和触摸输入 🐭📱

当一个`Draggable`中心在距离容器边缘很小的距离内,我们开始自动滚动. 随着用户靠近容器的边缘,我们增加了自动滚动的速度. 这种加速度使用缓动功能来指数地增加我们移向边缘越近的加速度. 我们从容器的真实边缘到达最大加速度,使得用户不需要非常精确以获得最大的滚动速度. 该逻辑适用于可滚动的任何边缘. 

自动滚动所需的距离分别基于容器的垂直和水平滚动的高度或宽度的百分比. 通过使用百分比而不是原始像素值,无论容器的大小和形状如何,我们都可以获得丰富的体验. 

##### 鼠标滚轮和触控板

除了自动滚动,我们还允许用户滚动窗口或一个`Droppable`手动使用他们的*鼠标滚轮*要么*触控板*👌

##### 关于大`Draggable`的笔记

如果`Draggable`比您要滚动的轴上的容器大 - 我们将不允许在该轴上滚动. 例如,如果你有一个`Draggable`这比窗口的高度更长,我们不会自动垂直滚动. 不过,我们仍然会允许水平滚动. 

##### iOS自动滚动摇晃 📱🤕

当在iOS浏览器 (webkit) 上自动滚动时`Draggable`明显地震动. 这是由于一个[与webkit的错误](https://bugs.webkit.org/show*bug.cgi?id=181954)没有已知的工作. 我们尝试了很长时间来解决这个问题!如果你看到这种改进感兴趣,请与我们联系[webkit问题](https://bugs.webkit.org/show*bug.cgi?id=181954). 

#### 用于键盘拖动 🎹

拖动键盘时,我们也会根据需要正确更新滚动位置. 为了移动一个`Draggable`进入正确的位置,我们可以做一个`Droppable`滚动,`window`滚动和手动移动的组合以确保`Draggable`响应用户移动指令结束在正确的位置. 这是大焦点🔥. 

对于有视觉障碍的用户来说,这是惊人的,因为他们可以在大列表中正确移动项目而无需使用鼠标定位. 

### 无障碍

传统上,拖放交互一直是鼠标或触摸交互. 这个库支持拖放交互 **只使用键盘**. 这使高级用户可以完全从键盘上获得他们的体验. 以及向以前被排除在外的用户开放这些体验. 

我们提供 **对屏幕阅读器的精彩支持**帮助视觉 (或其他) 损伤的用户. 我们随机附带英文短信📦. 但是,欢迎您使用`announce`函数覆盖这些消息, 函数提供给所有的函数`DragDropContext > hook`功能. 

见我们的[屏幕阅读器指南](docs/guides/screen-reader.zh.md)为指导制作有用的屏幕阅读器信息. 

#### 示例屏幕阅读器行为

![screen-reader-text](https://user-images.githubusercontent.com/2182637/36571009-d326d82a-1888-11e8-9a1d-e44f8b969c2f.gif)

## 鼠标拖动

### 马虎点击并点击预防🐱🎁

当用户在元素上按下鼠标时,我们无法确定用户是在点击还是在拖动. 另外,有时当用户点击时,他们可以稍微移动光标 - 一个马虎的点击. 所以我们只有在用户用鼠标向下移动 超过一定距离 时才会开始拖拽 (拖拽阈值)  - 如果他们只是马上点击,它们会比他们更多. 如果没有超过拖拽阈值,则用户交互就像常规点击一样. 如果超过了拖拽阈值,则该交互将被分类为 拖拽 并且不会发生 标准点击行为. 

这允许消费者包装诸如目标的交互元素,并且以自然的方式使其既是标准目标也是可拖动项. 

 (🐱🎁是一个[薛定谔的猫](https://www.youtube.com/watch?v=IOYyCHGWJq4)玩笑) 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.zh.md)

### 键盘快捷键: 鼠标拖动

当一个拖动 **没有发生** `react-beautiful-dnd`不会影响任何标准键盘交互 (它没有绑定的监听器) . 

当一个拖动 **正在发生**与*鼠标*用户可以执行以下键盘快捷键: 

-   **逃逸** <kbd>esc</kbd>- 取消拖动

在鼠标拖动过程中,以下标准键盘事件被阻止,以防止出现不好的体验: 

-   **tab** <kbd>tab ↹</kbd>- 防止绊倒
-   **enter** <kbd>⏎</kbd>- 防止提交

除了这些明确禁止键盘事件外,所有标准键盘事件都应按预期工作. 

## 键盘拖动

`react-beautiful-dnd`仅支持使用键盘进行拖动. 我们审核了我们的键盘快捷键如何与标准浏览器键盘交互进行交互. 当用户没有拖动时,他们可以像平常一样使用键盘. 拖动时,我们覆盖并禁用某些浏览器快捷方式 (如`tab`) 以确保用户的流畅体验. 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.zh.md)

### 键盘快捷键: 键盘拖动

当在使用该标准的页面上没有发生拖动时,用户将能够通过 **tab** <kbd>tab↹</kbd>浏览`Draggable`可放置元素 前进和 (**shift**+**tab**)  (<kbd>shift</kbd>+) <kbd>tab↹</kbd>) 向后移动. 我们通过添加一个`tab-index`到了`Draggable`. 当一个`Draggable`已经触发了 **空格键** <kbd>space</kbd>, 将 **标记**一个`Draggable`. 这将开始拖动. 

一旦开始拖动,可以使用以下键盘快捷键: 

-   **空格键** <kbd>space</kbd>- 放下`Draggable`
-   **逃逸** <kbd>esc</kbd>- 取消拖动

以下命令也可用,但它们依赖于*目前*的`Droppable`的`type`: 

#### 在一个垂直列表中

-   **向上箭头** <kbd>↑</kbd>- 移动一个`Draggable`向上`Droppable`
-   **向下箭头** <kbd>↓</kbd>- 移动一个`Draggable`向下在一个`Droppable`
-   **右箭头** <kbd>→</kbd>- 移动一个`Draggable`到一个`Droppable`到了*对*目前`Droppable` (移至新列表) 
-   **左箭头** <kbd>←</kbd>- 移动一个`Draggable`到一个`Droppable`到了*剩下*目前`Droppable` (移至新列表) 

#### 在一个水平列表中

-   **向上箭头** <kbd>↑</kbd>- 移动一个`Draggable`到一个`Droppable`至*以上*目前`Droppable` (移至新列表) 
-   **向下箭头** <kbd>↓</kbd>- 移动一个`Draggable`到一个`Droppable`至*下面*目前`Droppable` (移至新列表) 
-   **右箭头** <kbd>→</kbd>- 移动一个`Draggable`到了*对*在目前`Droppable`
-   **左箭头** <kbd>←</kbd>- 移动一个`Draggable`到了*剩下*在目前`Droppable`

在拖动过程中,以下标准键盘事件的默认行为被阻止 (通过`event.preventDefault()`) 以避免不好的体验: 

-   **tab** <kbd>tab ↹</kbd>- 防止绊倒
-   **enter** <kbd>⏎</kbd>- 防止提交

## 触摸拖动

`react-beautiful-dnd`支持拖动手机和平板电脑等触摸设备. 

![Mobile landscape](https://github.com/alexreardon/files/blob/master/resources/iphone-landscape.gif?raw=true)

> 录制在iPhone 6s上

### 理解意图: 点击,强按,滚动并拖动

当用户按下他们的手指 (或其他输入) 时`Draggable`我们不确定他们是否有意*点击*,*强按*,*滚动容器*要么*拖动*. **越多越好`react-beautiful-dnd`旨在确保用户默认的交互体验不受影响**. 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.zh.md)

### 开始拖动: 长按

用户可以通过在一个元素上长时间握住手指开始拖动🕑 (长按) 

### 点按支持

如果用户在定时器完成之前提起手指,然后我们将该事件释放给浏览器,以确定是否执行标准的点击/点击操作. 这可以让你有一个`Draggable`这既是可点击的,例如目标点以及可拖动的. 如果该项目被拖动,那么我们会阻止点击操作的发生. 

### 原生滚动支持

如果我们发现一个`touchmove`在长按计时器到期之前,我们取消挂起的拖动并允许用户正常滚动. 这意味着用户需要相当有意和准确地抓住他们. 第一次`touchmove`发生时,我们必须选择是否加入本地滚动. 

-   如果长按定时器**没有**过期: *允许本地滚动并防止拖动*
-   如果长按定时器**具有**过期: *拖动已经开始,我们阻止本地滚动*

### 大力按压支持

> 只有 Safari

如果用户在移动元素之前按下元素 (即使拖动已经开始) ,则拖动被取消并且发生标准的力按压操作. 对于一个目标点,这是一个网站预览. 

### 振动

> 这只是一个想法 - 如果你想要这种行为,你可以添加它. 

如果你喜欢,你也可以触发一个[振动事件](https://developer.mozilla.org/en-US/docs/Web/API/Vibration*API)当用户拿起一个`Draggable`. 这可以提供用户正在做的事情的触觉反馈. 目前仅在 Android版Chrome 中支持. 

```js
class App extends React.Component {
  onDragStart = () => {
    // good times
    if (window.navigator.vibrate) {
      window.navigator.vibrate(100);
    }
  };
  /*...*/
}
```

## 多拖

我们创造了一个[多拖动模式](/docs/patterns/multi-drag.zh.md)你可以建立在顶部`react-beautiful-dnd`为了支持拖动多个`Draggable`项目一次. 

![multi drag demo](https://user-images.githubusercontent.com/2182637/37322724-7843a218-26d3-11e8-9ebb-8d5853387bb3.gif)

## 预设样式

我们应用了许多不可见的样式来促进拖拽体验. 我们使用 style 目标和技术的组合来做到这一点. 库的目标是提供 无选择的造型. 但是,我们确实在`默认情况下应用了一些合理的`cursor`拖动控制样式. 这是为了使 库 尽可能简单地工作而设计的. 如果你想使用你自己的鼠标样式,你是不是欢迎. 您所需要做的就是通过使用规则来覆盖 光标 样式规则[高定义性](https://css-tricks.com/specifics-on-css-specificity/). 

以下是在拖动生命周期中的各个点上应用的样式: 

### 在每个阶段

#### 总是: 拖动控制

样式适用于: **拖动控制元素**使用`data-react-beautiful-dnd-drag-handle`属性. 

长按目标点通常会弹出一个内容菜单,其中包含链接选项,例如"在新标签中打开". 由于长按是用来开始拖动,我们需要退出此行为

```css
-webkit-touch-callout: none;
```

基于 Webkit 的浏览器在目标点处于活动状态时, 为其添加灰色叠加层. 我们删除了这个点按叠加层,因为它会让用户感到困惑. [更多信息](https://css-tricks.com/snippets/css/remove-gray-highlight-when-tapping-links-in-mobile-safari/). 

```css
-webkit-tap-highlight-color: rgba(0,0,0,0);
```

避免情况*拉动以刷新行动*和*延迟目标定焦点*在Android Chrome上

```css
touch-action: manipulation;
```

#### 总是: 可以放下

样式适用于: **droppable元素**使用`data-react-beautiful-dnd-droppable`属性. 

当浏览器功能试图保持滚动位置,当DOM变化超过边缘时,选择退出. 我们已经正确地保持滚动位置. 自动`overflow-anchor`行为导致错误的滚动定位后放下. 

```css
overflow-anchor: none;
```

### 阶段: 停在元素

####  (阶段: 停在元素) : 拖动控制

样式适用于: **拖动控制元素**使用`data-react-beautiful-dnd-drag-handle`属性. 

添加一个光标样式让用户知道这个元素是可拖动的. 欢迎您覆盖此. 

```css
cursor: grab;
```

### 阶段: 拖动

####  (阶段: 拖动) : 拖动控制元素

**使用该样式应用的样式`data-react-beautiful-dnd-drag-handle`属性**

拖动时避免处理的优化`pointer-events`. 还用于允许滚动通过拖动控制带轨迹板或鼠标滚轮. 

```css
pointer-events: none;
```

####  (阶段: 拖动) : 可拖动的元素

**使用该样式应用的样式`data-react-beautiful-dnd-draggable`属性**

这是我们用来控制的`Draggable`这需要摆脱拖拉的方式`Draggable`. 

```css
transition: ${string};
```

**使用内联样式应用的样式**

这由类型描述[`DraggableStyle`](https://github.com/atlassian/react-beautiful-dnd#type-information-1). 

####  (阶段: 拖动) : body元素

我们在拖动时应用光标,以向用户反馈发生拖动的情况. 欢迎您覆盖此. 一个好的方面是做到这一点`onDragStart`事件. 

```css
cursor: grabbing;
```

为防止用户在拖动时选择文本,应用此样式

```css
user-select: none;
```

### 阶段: 放下

####  (阶段: 放下) : 拖动控制元素

**使用该样式应用的样式`data-react-beautiful-dnd-drag-handle`属性**

我们将 抓取光标应用于所有拖动,除拖动控制`Draggable`之外的. 此时用户可以拖动其他`Draggable`如果他们喜欢的话. 

```css
cursor: grab;
```

####  (阶段: 放下) : 可拖动

与拖动阶段相同

### 阶段: 用户取消

> 当用户显式取消拖动时

这与之相同`Phase: dropping`. 但我们不适用`cursor: grab`拖动控制. 在用户启动取消期间,我们不允许拖放其他项目,直到放下动画完成. 

### 预设样式是供应商的前缀

所有应用的样式都是供应商正确的前缀,以符合我们的要求[支持浏览器矩阵](https://confluence.atlassian.com/cloud/supported-browsers-744721663.html). 这是手工完成的,以避免通过包含一个 css-in-js 库来增加 react-beautiful-dnd 的大小

## 安装

### 包管理器

```bash
# yarn
yarn add react-beautiful-dnd

# npm
npm install react-beautiful-dnd --save
```

### 分发包

一个[通用模块 umd 定义](https://github.com/umdjs/umd)捆绑发布于`npm`在下面`/dist`文件夹. 我们发布以下文件: 

-   `dist/react-beautiful-dnd.js`
-   `dist/react-beautiful-dnd.min.js` (缩小束) 

这`react`捆绑列表作为需要提供的外部. 这样做是为了减少捆绑包的大小并防止消费者加载`react`多次. 你可以提供`react`通过你的模块系统 或 简单地通过`window`拥有`react`. 

您可以使用 umd 运行`react-beautiful-dnd`直接在浏览器中. 

```html
<!-- peer dependency -->
<script src="https://unpkg.com/react@16.3.1/umd/react.development.js"></script>
<!-- lib (change x.x.x for the version you would like) -->
<script src="https://unpkg.com/react-beautiful-dnd@x.x.x/dist/react-beautiful-dnd.js"></script>
<!-- needed to mount your react app -->
<script src="https://unpkg.com/react-dom@16.3.1/umd/react-dom.development.js"></script>

<script>
  const React = window.React;
  const ReactDOM = window.ReactDOM;
  const { DragDropContext, Draggable, Droppable } = window.ReactBeautifulDnd;

  class App extends React.Component {
    //...
  }

  // You can use JSX if your environment supports it
  ReactDOM.render(React.createElement(App), document.getElementById('app'));
</script>
```

还有一个[示例codepen](https://codepen.io/alexreardon/project/editor/ZyNMPo)你可以使用这个安装方法来玩. 

## [`ClojureScript`](https://clojurescript.org/)

你可以构建`react-beautiful-dnd`使用内部`ClojureScript`[CLJSJS](https://cljsjs.github.io/)!

## API

好吧,进入有趣的东西 - 那么你如何使用 库 ?

## `DragDropContext`

为了使用拖放,你需要拥有你的部分`React`树,你想能够在包裹在一个`DragDropContext`使用拖放. 建议将您的整个应用程序包装在一个`DragDropContext`. 嵌套`DragDropContext`是的*不*支持的. 你将能够使用 Props 实现你想要的条件拖放`Droppable`和`Draggable`. 你可以想到`DragDropContext`与[react-redux 提供程序组件](https://github.com/reactjs/react-redux/blob/master/docs/api.md#provider-store)有类似的目的

### Props

```js
type Hooks = {|
  // optional
  onDragBeforeStart?: OnDragBeforeStartHook,
  onDragStart?: OnDragStartHook,
  onDragUpdate?: OnDragUpdateHook,
  // required
  onDragEnd: OnDragEndHook,
|};

type OnBeforeDragStartHook = (start: DragStart) => mixed;
type OnDragStartHook = (start: DragStart, provided: HookProvided) => mixed;
type OnDragUpdateHook = (update: DragUpdate, provided: HookProvided) => mixed;
type OnDragEndHook = (result: DropResult, provided: HookProvided) => mixed;

type Props = {|
  ...Hooks,
  children: ?Node,
|};
```

### 基本用法

```js
import { DragDropContext } from 'react-beautiful-dnd';

class App extends React.Component {
  onDragStart = () => {
    /*...*/
  };
  onDragUpdate = () => {
    /*...*/
  }
  onDragEnd = () => {
    // the only one that is required
  };

  render() {
    return (
      <DragDropContext
        onDragStart={this.onDragStart}
        onDragUpdate={this.onDragUpdate}
        onDragEnd={this.onDragEnd}
      >
        <div>Hello world</div>
      </DragDropContext>
    );
  }
}
```

### 钩子们{Hook}

Hooks是顶级应用程序事件,您可以使用它来执行自己的状态更新 以及 制作屏幕阅读器公告. 有关控制屏幕阅读器的更多信息,请参阅我们的[屏幕阅读器指南](docs/guides/screen-reader.zh.md)

[请查看Hooks，指南](docs/guides/hooks.zh.md)，了解更多 ❤️

## `Droppable`

`Droppable`组件可以 **由一个`Draggable`**. 他们也 **包含** `Draggable`们. 一个`Draggable`必须包含在一个`Droppable`. 

```js
import { Droppable } from 'react-beautiful-dnd';

<Droppable droppableId="droppable-1" type="PERSON">
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      style={{ backgroundColor: snapshot.isDraggingOver ? 'blue' : 'grey' }}
      {...provided.droppableProps}
    >
      <h2>I am a droppable!</h2>
      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

### 可拖 Props 

-   `droppableId`:  一个*需要* `DroppableId(string)`唯一标识该应用程序的可投入程序. 请不要更改此 Props  - 特别是在拖动时. 

-   `type`: *可选的* `TypeId(string)`可以用来简单地接受一类`Draggable`. 例如,如果您使用该类型`PERSON`那么它只会允许`Draggable`类型的`PERSON`放下自己. `Draggable`类型的`TASK`将无法被放在`Droppable`与类型`PERSON`上. 如果不提供`type`,它将被设置为`'DEFAULT'`. 目前来说`Draggable`的`type`在`Droppable`之内 **一定是**一样. 如果有一个有效的用例,这个限制在将来可能会放松. 

-   `isDropDisabled`: *可选的*标志来控制当前是否允许丢弃`Droppable`. 你可以用它来实现你自己的条件丢弃逻辑. 它将默认为`false`.

-   `direction`: 物品在这个物品中流动的方向. 选项是`vertical` (默认) 和`horizontal`. 

-   `ignoreContainerClipping`:  当一个`Droppable`在一个可滚动的容器内,它的区域受到限制,所以你只能放在容器的一部分`Droppable`你可以看到. 设置这个 Props 不会出现这种行为,允许你放在任何地方`Droppable`即使它被一个可滚动的父级视觉隐藏. 默认行为适用于大多数情况,所以您不需要使用此 Props ,但如果您的 Props 很长,它可能会很有用`Draggable`s在一个短的滚动容器内. 请记住,如果您有多个,它可能会导致一些意外的行为`Droppable`在同一页面上滚动容器. 

### 子函数

该`React`一个孩子`Droppable`必须是返回a的函数[`ReactElement`](https://tylermcginnis.com/react-elements-vs-react-components/). 

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => ({
    /*...*/
  })}
</Droppable>;
```

该函数提供了两个参数: 

#### 1.提供:  (DroppableProvided) \*\*: 

```js
type DroppableProvided = {|
  innerRef: (?HTMLElement) => void,
  droppableProps: DroppableProps,
  placeholder: ?ReactElement,
|}

type DroppableProps = {|
  // used for shared global styles
  'data-react-beautiful-dnd-droppable': string,
|}
```

-   `provided.innerRef`:为了使 droppable 能够正常工作,你必须 **绑定**到最高可能的DOM节点中`provided.innerRef`. `ReactElement`我们这样做是为了避免需要使用查找您的DOM节点. `ReactDOM`有关使用的更多信息

> 看我们的`innerRef`运用[指南`innerRef`: 这用于在中创建空间](/docs/patterns/using-inner-ref.zh.md)

-   `provided.placeholder`根据需要拖动. `Droppable`当用户拖动不是主列表的列表时,需要此空间. 请确保将 占位符 放在您为其提供 ref 的组件中. 我们需要增加大小本身. `Droppable`: 这是一个 Object,它包含需要应用于 Droppable 元素的属性. 

-   `provided.droppableProps (DroppableProps)`它需要应用于您应用的相同元素. `provided.innerRef`它目前包含一个`data`属性,我们用它来控制一些不可见的CSS. 

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.droppableProps}>
      Good to go

      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

#### 2.快照:  (DroppableStateSnapshot) 



```js
type DroppableStateSnapshot = {|
  // Is the Droppable being dragged over?
  isDraggingOver: boolean,
  // What is the id of the draggable that is dragging over the Droppable?
  draggingOverWith: ?DraggableId,
|};
```

`children`函数还提供有与当前拖动状态有关的少量状态. 这可以选择用于增强组件. 一个常见的用例是正在被拖动的它改变外观. 

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      style={{ backgroundColor: snapshot.isDraggingOver ? 'blue' : 'grey' }}
      {...provided.droppableProps}
    >
      I am a droppable!

      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

### 有条件地放下

-   `Droppable`s 只能通过那些共享相同的`type`的`Droppable`. `Draggable`这是允许有条件丢弃的一种简单方法. 如果你不提供一个`type`给`Droppable`,那么它只会接受默认的类型`Draggable`s. 当没有提供`Draggable`s 和`Droppable`两个人都会有他们的`types`设置`'DEFAULT'`. 目前没有办法设置多个`types`或者一个`type`通配符,将接受`Draggable`s 的多种任何类型. 如果有一个有效的用例,可以添加它. 

-   使用`isDropDisabled`你可以有条件地允许掉落. 这使您可以执行任意复杂的条件转换. 这只会被视为如果`Droppable`的`type`, 匹配`type`当前正在拖动`Draggable`. 

-   您可以禁用放弃`Droppable`总是由总设定`isDropDisabled`到`true`. 你可以这样做来创建一个永远不能被拖放但包含的列表`Draggable`s. 

-   技术上你不需要使用`type`并用你的所有条件放置逻辑来完成`isDropDisabled`函数. 该`type`参数是常见用例的便捷捷径. 

### 滚动容器

该库支持在滚动容器 (具有DOM元素) 中拖动`overflow: auto;`要么`overflow: scroll;`) . 该 **只要**支持的用例有: 

1.  该`Droppable`本身可以是一个滚动容器 **没有可滚动的父母**
2.  该`Droppable`具有 **一个可滚动的父项**

哪里一个*可滚动的父级*指的是一个不是窗口本身的滚动容器. 

### 空`Droppable`

建议你把一个`min-height`给到在垂直`Droppable`或者一个`min-width`给到在水平`Droppable`. 否则当`Droppable`是空的可能没有足够的目标`Draggable`被触摸或鼠标输入*过度*拖动该`Droppable`. 

### 推荐 Droppable 性能优化

当用户拖拉或停止拖动一个`Droppable`时,我们重新渲染`Droppable`与更新`DroppableStateSnapshot > isDraggingOver`值. 这对于设计样式非常有用`Droppable`. 但是,默认情况下,这将导致所有的孩子的渲染`Droppable`- 可能是100个`Draggable`的!这可能导致明显的帧速放下. 为了避免这个问题,我们建议您创建一个子组件`Droppable`组件,责任是避免渲染 children ,如果不是必需的话. 

以下是你如何做到这一点的例子: 

```js
import React, { Component } from 'react';

class Student extends Component<{ student: Person }> {
  render() {
    // Renders out a draggable student
  }
}

class InnerList extends Component<{ students: Person[] }> {
  // do not re-render if the students list has not changed
  shouldComponentUpdate(nextProps: Props) {
    if(this.props.students === nextProps.students) {
      return false;
    }
    return true;
  }
  // You could also not do your own shouldComponentUpdate check and just
  // extend from React.PureComponent

  render() {
    return this.props.students.map((student: Person) => (
      <Student student={student} />
    ))
  }
}

class Students extends Component {
  render() {
    return (
      <Droppable droppableId="list">
        {(provided: DroppableProvided, snapshot: DroppableStateSnapshot) => (
          <div
            ref={provided.innerRef}
            style={{ backgroundColor: provided.isDragging ? 'green' : 'lightblue' }}
            {...provided.droppableProps}
          >
            <InnerList students={this.props.students} />
            {provided.placeholder}
          </div>
        )}
      </Droppable>
    )
  }
}
```

通过使用该方法,您可以将样式更改为一个`Droppable`当它被拖动时,但你避免不必要地重新渲染所有的孩子. 请记住,如果你正在使用`React.PureComponent`你的组件会[对上下文中的变化没有反应](https://github.com/facebook/react/issues/2517). 

不幸的是我们[无法为您应用此优化](https://medium.com/merrickchristensen/function-as-child-components-5f3920a9ace9). 它是使用函数作为子模式的副产品. 

## `Draggable`

`Draggable`组件可以拖动并拖放到其`Droppable`s上. 一个`Draggable`必须始终包含在一个`Droppable`. 它是 **可能**重新排序`Draggable`在其`Droppable`家中或移动到另一个`Droppable`. 它是 **可能**因为一个`Droppable`可以自由地控制它允许投入的内容. 

每个`Draggable`有一个*拖动控制*. 一个*拖动控制*是用户为了拖动而与之交互的元素`Draggable`. 一个*拖动控制*可以是`Draggable`元素本身,还是孩子的`Draggable`. 

```js
import { Draggable } from 'react-beautiful-dnd';

<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      <h4>My draggable</h4>
    </div>
  )}
</Draggable>;
```

> 注意: 当库移动到React 16时,这将被清理一些,因为我们可以将占位符作为兄弟返回到您的子函数,而无需创建包装元素

### 可拖动 Props 

-   `draggableId`:  一个*需要* `DraggableId(string)`唯一标识的`Draggable`为应用程序. 请不要更改此 Props  - 特别是在拖动时. 
-   `index`:  一个*需要* `number`它与`Draggable`的顺序相匹配在`Droppable`里面. 它只是简单的索引`Draggable`在列表中. 该`index`在一个内部需要是唯一的`Droppable`, 但不需要是唯一的`Droppables`. 通常情况下`index`价值将是简单的`index`由`Array.prototype.map`函数提供: 

```js
{
  this.props.items.map((item, index) => (
    <Draggable draggableId={item.id} index={index}>
      {(provided, snapshot) => (
        <div
          ref={provided.innerRef}
          {...provided.draggableProps}
          {...provided.dragHandleProps}
        >
          {item.content}
        </div>
      )}
    </Draggable>
  ));
}
```

-   `isDragDisabled`: *可选的*标志来控制是否`Draggable`被允许拖动. 您可以使用它来实现自己的条件拖动逻辑. 它将默认为`false`. 
-   `disableInteractiveElementBlocking`: *可选的*标志选择不阻止交互式元素的拖动. 有关更多信息,请参阅本节*交互式的子元素`Draggable`*

### 子函数 (渲染 Props ) 

该`React`一个孩子`Draggable`必须是返回一个函数`ReactElement`. 

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
      >
        Drag me!
      </div>
  )}
</Draggable>;
```

该函数提供了两个参数: 

#### 1.提供:  (DraggableProvided) 

```js
type DraggableProvided = {|
  innerRef: (HTMLElement) => void,
  draggableProps: DraggableProps,
  // will be null if the draggable is disabled
  dragHandleProps: ?DragHandleProps,
|}
```

*提供的*对象中的所有内容必须适用于“Draggable”才能正常运行.

-   `provided.innerRef (innerRef: (HTMLElement) => void)`: 为了`Droppable`正确运行, 你必须 **绑定**`innerRef`函数到你认为的`ReactElement`节点. `Draggable`我们这样做是为了避免需要使用查找您的DOM节点. `ReactDOM`有关使用的更多信息

> 看我们的`innerRef`运用[指南`innerRef`例](/docs/patterns/using-inner-ref.zh.md)

##### `innerRef`: 例子

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => <div ref={provided.innerRef}>Drag me!</div>}
</Draggable>;
```

-   `provided.draggableProps (DraggableProps)`这是一个包含的 `data`属性和内联`style`的 Object , 此对象需要应用于您应用的同一节点至`provided.innerRef`. 这将控制可拖动或不可拖动的操作. 欢迎您将自己的样式添加到`DraggableProps.style` - 但请不要移除或替换任何属性.

##### `draggableProps` 类型信息

```js
// Props that can be spread onto the element directly
export type DraggableProps = {|
  // inline style
  style: ?DraggableStyle,
  // used for shared global styles
  'data-react-beautiful-dnd-draggable': string,
|}

type DraggableStyle = DraggingStyle | NotDraggingStyle
type DraggingStyle = {|
  position: 'fixed',
  width: number,
  height: number,
  boxSizing: 'border-box',
  pointerEvents: 'none',
  top: number,
  left: number,
  margin: 0,
  transition: 'none',
  transform: ?string,
  zIndex: ZIndex,
|}
type NotDraggingStyle = {|
  transform: ?string,
  transition: null | 'none',
|}
```

##### `draggableProps` 例子

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.draggableProps}>
      Drag me!
    </div>
  )}
</Draggable>;
```

##### 定位所有权

它是该库的一个合约,它拥有拖动元素的定位逻辑. 

这包括诸如`top`,`right`,`bottom`,`left`和`transform`.  库 可能会改变它是如何定位事物以及它使用的是哪些属性,而不会执行主要的版本冲突. 也建议你不要使用你自己的`transition`属性添加到拖动元素. 

##### 警告: `position: fixed`

`react-beautiful-dnd`使用`position: fixed`定位拖动元素. 这是相当强大的,并允许你有`position: relative | absolute | fixed`父母. 然而,不幸的是`position:fixed`是[受到影响`transform`](http://meyerweb.com/eric/thoughts/2011/09/12/un-fixing-fixed-elements-with-css-transforms/) (如`transform: rotate(10deg);`) . 这意味着如果你有一个`transform: *`在`Draggable`的父母之一时, 那么拖动时定位逻辑将不正确. 瘸!对于大多数消费者来说,这不会是一个问题. 

为了解决这个问题,你可以使用[`React.Portal`](https://reactjs.org/docs/portals.html). 我们不会默认启用此功能,因为它有性能问题. 我们有一个[使用 Portal 指南](/docs/patterns/using-a-portal.zh.md)更详细地解释性能问题以及如何设置自己的问题`React.Portal`如果你想. 

##### 在列表之间移动时保持焦点

当移动一个`Draggable`从一个列表到另一个列表,默认的浏览器行为是为了*拖动控制*元素放松焦点. 这是因为旧元素正在被破坏,并且正在创建一个新元素. 当用键盘拖动时,焦点丢失并不好,因为用户无法继续与元素交互. 为了改善这种用户体验,我们自动给出一个*拖动控制*焦点 当: 

-   它在拖动结束时被卸载
-   它有焦点
-   它在安装时启用
-   在拖动控制安装之前,没有其他元素获得浏览器焦点

##### 扩展`DraggableProps.style`

如果您使用内联样式,欢迎您将其扩展`DraggableProps.style`目的. 也欢迎申请`DraggableProps.style`使用内联样式的对象,并为组件本身使用自己的样式解决方案 - 例如[风格组件](https://github.com/styled-components/styled-components). 

如果您重写内联样式,请务必在进行`provided.draggableProps`或者传播展开后会覆盖你的内联风格. 

```js
<Draggable draggable="draggable-1" index={0}>
  {(provided, snapshot) => {
    // extending the DraggableStyle with our own inline styles
    const style = {
      backgroundColor: snapshot.isDragging ? 'blue' : 'white',
      fontSize: 18,
      ...provided.draggableProps.style,
    };
    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        style={style}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

##### 避免 margin 折叠 多个`Draggable`

[边缘崩溃](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS*Box*Model/Mastering*margin*collapsing)是CSS中非常困难的部分之一. 对于我们的目的,如果你有一个`Draggable`与`margin-bottom: 10px`和下一个`Draggable`有一个`margin-top: 12px`这些折叠将会*坍方*并由此产生的余量将是两者中较大的一个: `12px`. 当我们进行我们的计算时,我们目前没有考虑边缘折叠. 如果你确实想在兄弟姐妹身上留下一个空白,那么把它们都包在一个`div`并将边缘应用于内部`div`, 所以他们不是直系兄弟姐妹. 

##### `Draggable`们应该是可见的兄弟姐妹

这是一个假设`Draggable`s是*可见的兄弟姐妹*彼此之间. 中间还可以有其他元素,但这些元素不应占用额外的空间. 无论如何,你可能不会这样做,但只要说出来就非常清楚. 

```js
// Direct siblings ✅
<Draggable draggableId="draggable-1" index={0}>
  {() => {}}
</Draggable>
<Draggable draggableId="draggable-2" index={1}>
  {() => {}}
</Draggable>

// Not direct siblings, but are visible siblings ✅
<div>
  <Draggable draggableId="draggable-1" index={0}>
    {() => {}}
  </Draggable>
</div>
<div>
  <Draggable draggableId="draggable-2" index={1}>
    {() => {}}
  </Draggable>
</div>

// Spacer elements ❌
<Draggable draggableId="draggable-1" index={0}>
    {() => {}}
</Draggable>
<p>I will break things!</p>
<Draggable draggableId="draggable-2" index={1}>
    {() => {}}
</Draggable>

// Spacing on non sibling wrappers ❌
<div style={{padding: 10}}>
  <Draggable draggableId="draggable-1" index={0}>
    {() => {}}
  </Draggable>
</div>
<div style={{padding: 10}}>
  <Draggable draggableId="draggable-2" index={1}>
    {() => {}}
  </Draggable>
</div>
```

-   `provided.dragHandleProps (?DragHandleProps)`一切`Draggable`有一个*拖动控制*. 这是用来拖动整个的`Draggable`. 通常这将是对`Draggable`,但有时它可能是一个`Draggable`的孩子. `DragHandleProps`需要应用到您想要成为拖动控制的节点. 这是一些 Props 需要应用到 `Draggable`节点. 最简单的方法是将 Props 散布到 可拖动节点上 (`{...provided.dragHandleProps}`) . 但是,你也欢迎[猴子补丁](https://davidwalsh.name/monkey-patching)这些 Props 如果你还需要回应他们. DragHandleProps将会`null`当`isDragDisabled`被设定为`true`. 

##### `dragHandleProps`类型信息

```js
type DragHandleProps = {|
  onFocus: () => void,
  onBlur: () => void,
  onMouseDown: (event: MouseEvent) => void,
  onKeyDown: (event: KeyboardEvent) => void,
  onTouchStart: (event: TouchEvent) => void,
  'data-react-beautiful-dnd-drag-handle': string,
  'aria-roledescription': string,
  tabIndex: number,
  draggable: boolean,
  onDragStart: (event: DragEvent) => void,
|}
```

##### `dragHandleProps`例子: 标准

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      Drag me!
    </div>
  )}
</Draggable>;
```

##### `dragHandleProps`例子: 自定义拖动控制

通过它的一部分控制整个可拖动

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.draggableProps}>
      <h2>Hello there</h2>
      <div {...provided.dragHandleProps}>Drag handle</div>
    </div>
  )}
</Draggable>;
```

##### `dragHandleProps`猴子补丁

你可以重写一些`dragHandleProps`, 如果你需要的话,你可以使用自己的行为. 

```js
const myOnMouseDown = event => console.log('mouse down on', event.target);

<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => {
    const onMouseDown = (() => {
      // dragHandleProps might be null
      if (!provided.dragHandleProps) {
        return onMouseDown;
      }

      // creating a new onMouseDown function that calls myOnMouseDown as well as the drag handle one.
      return (event) => {
        provided.dragHandleProps.onMouseDown(event);
        myOnMouseDown(event);
      };
    })();

    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
        onMouseDown={onMouseDown}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

#### 2.快照:  (DraggableStateSnapshot)

```js
type DraggableStateSnapshot = {|
  // 如果正在拖动Draggable，或者如果它是drop动画，则设置为true
  // 主动拖动和拖放动画都被视为拖动的一部分
  isDragging: boolean,
  // 如果Draggable是放置动画，则设置为true。 不是每次拖放互动
  // 作为放置动画。 当Draggable已经进入最终掉落时的位置时，没有放置动画
  //  使用键盘拖动时通常会出现这种情况
  isDropAnimating: boolean,
  // 拖动 Draggable 在确切覆盖 （如果有的话）着的Droppable id
  draggingOver: ?DroppableId,
|};
```

 该`children`函数还提供有与当前拖动状态有关的少量状态.这可以选择用于增强组件. 一个常见的用例是改变`Draggable`的外观当它被拖拽. 注意: 如果你想改变光标到类似`grab`的东西您需要将样式添加到可拖动.  (看到[扩展`DraggableProps.style`](#extending-draggableprops-style)以上) 

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => {
    const style = {
      backgroundColor: snapshot.isDragging ? 'blue' : 'grey',
      ...provided.draggableProps.style,
    };

    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
        style={style}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

### `Draggable`占位符

当拖动一个`Draggable`我们留下了一个*占位符* `React.Element`保持空间`Droppable`以防止它崩溃. 占位符模仿样式和布局 (包括`width`,`height`,`margin`,`tagName`和`display`) 以确保列表尺寸在拖动时不受影响. 它将被`react-beautiful-dnd`作为直接兄弟插入由`Draggable`子函数返回的`React.Node`。

### 添加一个`onClick`控制到一个`Draggable`或者一个*拖动控制*

欢迎您添加您自己的`onClick`处理程序`Draggable`或者一个*拖动控制* (这可能是相同的元素) . `onClick`如果发生点击,事件处理程序将始终被调用. 如果我们阻止点击,那么我们就是`event.defaultPrevented`财产将被设置为`true`. 我们阻止发生点击事, 当用户拖动项目时 件. 看到[#马虎点击并点击预防🐱🎁](#%E9%A9%AC%E8%99%8E%E7%82%B9%E5%87%BB%E5%B9%B6%E7%82%B9%E5%87%BB%E9%A2%84%E9%98%B2) 了解更多信息. 

### 交互式的子元素`Draggable`

这是你的`Draggable`可能包含交互元素. 默认情况下,我们阻止拖动这些元素. 通过这样做,我们允许这些元素以通常的方式运行. 以下是默认阻止拖动的交互式元素列表: 

-   `input`
-   `button`
-   `textarea`
-   `select`
-   `option`
-   `optgroup`
-   `video`
-   `audio`
-   [`contenteditable`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global*attributes/contenteditable) (任何元素是`contenteditable`或者在一个`contenteditable`容器) 

您可以通过添加选项`disableInteractiveElementBlocking`到`Draggable`来退出此行为. 但是,您是否应该这样做是值得怀疑的,因为它会使交互式元素无法使用. 如果你需要*有条件的*阻止交互式元素拖动,可添加`disableInteractiveElementBlocking`退出默认的阻塞 和 猴子补丁到`dragHandleProps (DragHandleProps)`事件处理程序禁用拖动. 

## `resetServerContext`

该`resetServerContext`函数应该在服务器端呈现 (SSR) 时使用. 它确保 上下文状态 不会在服务器上的多个呈现中持续存在,这会在服务器上呈现多个请求后 导致 客户端/服务器标记 不匹配. 

在调用服务器端渲染方法之前使用它: 

```js
import { resetServerContext } from 'react-beautiful-dnd';
import { renderToString } from 'react-dom/server';

...

resetServerContext();
renderToString(...);
```

## Flow 使用

`react-beautiful-dnd`是使用 类型化 的[`flowtype`](https://flow.org). 这大大提高了代码库内部的一致性. 我们还公开了许多公共类型,如果您愿意,可以输入您的 javascript 类型. 如果你不使用`flowtype`这不会阻止你使用该库. 对于那些想要它的人来说,这只是额外的安全. 

### 公共 Flow 类型

```js
// id's
type Id = string;
type TypeId = Id;
type DroppableId = Id;
type DraggableId = Id;

// hooks
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|}

type DragUpdate = {|
  ...DragStart,
  // may not have any destination (drag to nowhere)
  destination: ?DraggableLocation,
|}

type DropResult = {|
  ...DragUpdate,
  reason: DropReason,
|}

type DropReason = 'DROP' | 'CANCEL'

type DraggableLocation = {|
  droppableId: DroppableId,
  // the position of the droppable within a droppable
  index: number
|};

// Droppable
type DroppableProvided = {|
  innerRef: (?HTMLElement) => void,
  placeholder: ?ReactElement,
|}

type DroppableStateSnapshot = {|
  isDraggingOver: boolean,
  draggingOverWith: ?DraggableId,
|}

// Draggable
type DraggableProvided = {|
  innerRef: (?HTMLElement) => void,
  draggableProps: DraggableProps,
  dragHandleProps: ?DragHandleProps,
|}

type DraggableStateSnapshot = {|
  isDragging: boolean,
  isDropAnimating: boolean,
  draggingOver: ?DroppableId,
|}

export type DraggableProps = {|
  style: ?DraggableStyle,
  'data-react-beautiful-dnd-draggable': string,
|}
type DraggableStyle = DraggingStyle | NotDraggingStyle
type DraggingStyle = {|
  position: 'fixed',
  width: number,
  height: number,
  boxSizing: 'border-box',
  pointerEvents: 'none',
  top: number,
  left: number,
  transition: 'none',
  transform: ?string,
  zIndex: ZIndex,
|}
type NotDraggingStyle = {|
  transition: ?string,
  transition: null | 'none',
|}

type DragHandleProps = {|
  onFocus: () => void,
  onBlur: () => void,
  onMouseDown: (event: MouseEvent) => void,
  onKeyDown: (event: KeyboardEvent) => void,
  onTouchStart: (event: TouchEvent) => void,
  'data-react-beautiful-dnd-drag-handle': string,
  'aria-roledescription': string,
  tabIndex: number,
  draggable: boolean,
  onDragStart: (event: DragEvent) => void,
|}
```

### 使用 Flow 类型

这些类型作为模块的一部分导出,因此使用它们非常简单: 

```js
import type { DroppableProvided } from 'react-beautiful-dnd';
```

##  Typescript

如果你正在使用[Typescript](https://www.typescriptlang.org/)你可以使用社区维护[DefinitelyTyped 类型定义](https://www.npmjs.com/package/@types/react-beautiful-dnd). [安装说明](http://definitelytyped.org/). 

这有些 [typescript 的例子](https://github.com/abeaudoin2013/react-beautiful-dnd-multi-list-typescript-example).


### 用 flow 类型示例应用程序

我们创造了一个[简单示例](https://github.com/alexreardon/react-beautiful-dnd-flow-example)它练习 flow . 这是一个超级简单`React`基于[`react-create-app`](https://github.com/facebookincubator/create-react-app). 你可以用它作为参考,看看如何正确设置. 

## 社区作品

- [kanban-dnd](https://kanban-dnd.glitch.me) \- 一个看云样式的TODO列表，能够创建自定义通道，并在运行中重新排序. 
- Simple Trello - Trello的简单clone版本, 使用 React 生态.
  - [Demo](https://simple-trello.netlify.com/)
  - [Source](https://github.com/ng-hai/simple-trello)

## 其他

- [natural-drag-animation-rbdnd](https://github.com/rokborf/natural-drag-animation-rbdnd) adds natural dragging animation

## 工程健康

### 类型化

这个代码库是用[flowtype](https://flow.org)的类型化促进更大的内部一致性和更有弹性的代码. 

### 经测试

该代码库使用许多不同的测试策略,包括单元,性能和集成测试. 测试系统的各个方面有助于提高其质量和稳定性. 

代码覆盖率[不是代码健康的保证](https://stackoverflow.com/a/90021/1374236),这是一个很好的指标. 此代码库目前位于 ~**90%的覆盖率** . 

### 性能

这个代码库被设计为 **非常高效**- 它是它的DNA的一部分. 它旨在执行尽可能少的更新. 您可以阅读关于完成的性能工作`react-beautiful-dnd`这里: 

-   [反思 拖放](https://medium.com/@alexandereardon/rethinking-drag-and-drop-d9f5770b4e6b)
-   [拖动 React性能 前瞻](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33)

## 大小

已经非常谨慎地保持 库 尽可能轻. 这是目前 ~**38kb(gzip)** 在尺寸方面. 如果您已经在使用某个基础依赖关系,那么净成本可能会更低. 

## 支持的浏览器

该库支持该标准[Atlassian 支持的浏览器](https://confluence.atlassian.com/cloud/supported-browsers-744721663.html)用于桌面: 

| 桌面                                     | 版               |
| -------------------------------------- | --------------- |
| Microsoft Internet Explorer (Windows)  | 版本11   (Need to [polyfill `Array.prototype.find`][iepolyfill])         |
| Microsoft Edge                         | 支持最新的稳定版本       |
| Mozilla Firefox (所有平台)                 | 支持最新的稳定版本       |
| Google Chrome (Windows和Mac)            | 支持最新的稳定版本       |
| Safari (Mac)                           | 支持最新OS版本的最新稳定版本 |

| 移动                    | 版                              |
| --------------------- | ------------------------------ |
| Chrome (Android和iOS)  | 支持最新的稳定版本                      |
| 移动Safari (iOS)        | 支持最新的稳定版本                      |
| Android (Android)     | Android 4.0.3上的默认浏览器 (冰淇淋三明治-Ice Cream Sandwich)  |

[iepolyfill]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find#Polyfill))

## 作者

亚历克斯里尔登 -[@alexandereardon](https://twitter.com/alexandereardon)

## 维护者

杰瑞德克罗 -[@jaredjcrowe](https://twitter.com/jaredjcrowe)

## 合作者

Bogdan Chadkin  -[@IAmTrySound](https://twitter.com/IAmTrySound)  
卢克 Batchelor  -[@alukebatchelor](https://twitter.com/alukebatchelor)  
很多 别的[@Atlassian](https://twitter.com/Atlassian)的!
