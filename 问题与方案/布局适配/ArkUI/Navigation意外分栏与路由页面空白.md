---
title: "ArkUI Navigation 宽屏主页变窄、右栏空白与跳转白屏"
summary: "区分 Navigation 隐式 Auto 分栏、NavDestination 构造错误、嵌套分区和真实路由异常；按原单栏或已确认双栏语义修复，不因设备范围擅自增加分栏。"
createdAt: "2026-11-24T00:00:00Z"
updatedAt: "2026-11-24T00:00:00Z"
---

# ArkUI Navigation 宽屏主页变窄、右栏空白与跳转白屏

## Overview 总体概述

平板主页被压进左侧窄栏、右侧空白，可能不是页面宽度太小，而是 Navigation 自动进入分栏。跳转后白屏则还可能是目标页没有正确构造 NavDestination。先确认当前导航模式及页面归属，再决定修尺寸、路由还是分栏内容。

## 问题现象与适用条件

- 手机正常，宽屏主页突然变窄，右边没有内容。
- 已推入路由，但目标页面不出现，只剩导航栏。
- 已确认列表—详情双栏，右侧首次进入为空。
- Tabs、SideBarContainer 或自定义分区嵌入后，内容又被分割一次。

适用于 Navigation/NavPathStack/NavDestination 页面。Router 页面、系统平行视界和自定义 Row 双栏应先分清，不能用同一修改替代所有问题。

## 原因与判断依据

| 分支 | 核对内容 |
|---|---|
| 意外 Auto | 没写 `.mode()` 不代表 Stack；默认 Auto 会按 Navigation 自身可用宽度适配。阈值及行为需按目标版本确认，不能硬套某机型宽度 |
| 双栏无内容 | navBar 中有主页，而内容区没有有效目标页；查看真实路由栈、选中项和默认详情 |
| 目标页构造错误 | 页面映射名与 push 名是否一致，构建结果是否包含正确的 NavDestination，参数是否足够创建页面 |
| 嵌套分区错误 | 外层 Navigation 把整套 Tabs 或 SideBar 当成 navBar，又在外部产生一层空详情区 |
| 非布局异常 | 页面构建抛错、资源未加载或参数非法，也会白屏；应核对日志和构建入口，不能只改宽度 |

## 解决方案

### 1. 原本不需要分栏：显式保持 Stack

```ts
Navigation(this.paths) {
  this.homeContent()
}
.mode(NavigationMode.Stack)
.navDestination(this.destinationMap)
.width('100%')
.height('100%')
```

片段沿用已有路由栈和构建函数。不因 task 设备范围包含平板或折叠屏，就把 Stack 改为 Auto/Split。增加信息量可以通过列表增列或模块挪移完成，导航语义不必改变。

### 2. 已确认双栏：填好两栏，保留业务状态

检查 navBar 放主列表，目标 NavDestination 放详情。首次进入双栏时，按已确认设计选择默认项或有说明的空状态；只有确实需要默认详情且路由尚未存在时才推入，避免回调每次都重复入栈。

宽变窄时保留当前选择、路由和返回关系，不能直接清空 pathStack 来“恢复单栏”。需要自定义栏宽时同时检查内容最小宽度与窗口高度，不让左栏挤掉详情可用区。

### 3. 修目标页与分区归属

navDestination 构建器可直接返回 NavDestination，也可调用内部以 NavDestination 构造的组件；不要在两层同时重复包裹。目标页最小结构例如：

```ts
NavDestination() {
  Column() {
    this.detailContent()
  }.width('100%').height('100%')
}
```

若一级 Tabs 已负责全页分区，而外层 Navigation 的 Auto 又产生不需要的第二套分区，可保持外层 Stack，或按已确认路由架构把 Navigation 放入对应业务内容区。不是所有嵌套都必须机械调换，关键是每层导航与内容区职责清楚。

## 相关方案

若确认当前采用系统 EasyGo，且问题出在配置生效、页面配对或栏内尺寸，再读《ArkUI 平行视界不生效、页面配对错误与跨栏截断》；不把普通 Navigation 的 Auto 问题直接按平行视界修改。

## 修复后检查

从首页直接进入、深链进入、详情返回及折展切换检查；记录当前模式、栈顶和两栏实际宽度。单栏不留空详情，双栏不重复推页，窄屏返回不丢选中项、输入和滚动位置。
