# HUAWEI Mate 60 系列：屏幕、形态与设备能力

更新日期：2026-11-04。各表中的“全部型号”仅指本档案列出的型号。

## 1. 型号与适用范围

| 项目 | 内容 |
| --- | --- |
| 设备类型 | `phone`（知识库分类） |
| 适用范围 | 运行 HarmonyOS 5 及以上原生鸿蒙的下列型号；旧系统设备需先完成升级。官网所列系统不代表用户当前安装的版本。 |

| 型号 | 检索名称 |
| --- | --- |
| HUAWEI Mate 60 | Mate 60、Mate60 |
| HUAWEI Mate 60 Pro | Mate 60 Pro、Mate60Pro |
| HUAWEI Mate 60 Pro+ | Mate 60 Pro+、Mate60Pro+ |
| HUAWEI Mate 60 RS 非凡大师 | Mate 60 RS 非凡大师、Mate60RS非凡大师 |

| 适用型号 | 官网系统或升级说明 |
| --- | --- |
| 全部型号 | 支持升级至原生鸿蒙，具体版本见官方支持名单 |

## 2. 屏幕与使用形态

宽高按“宽 × 高”记录。px 为硬件分辨率，vp 为设计参考值，不是应用当前窗口的实测尺寸；各型号、年份和屏幕的参数分别对应，不相互补齐。

| 型号 | 使用形态 | 参考方向 | 屏幕尺寸 | 分辨率 px | 参考尺寸 vp | 横向断点 | 纵向断点 | 数据说明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| HUAWEI Mate 60 | 屏幕 | 竖向 portrait | 未收录 | 1216 × 2688 | 374 × 826 | sm | lg | 官方设计参考 |
| HUAWEI Mate 60 Pro | 屏幕 | 竖向 portrait | 未收录 | 1260 × 2720 | 388 × 836 | sm | lg | 官方设计参考 |
| HUAWEI Mate 60 Pro+ | 屏幕 | 竖向 portrait | 未收录 | 未收录 | 按实际窗口读取 | 按窗口读取 | 按窗口读取 | 未收录机型专用尺寸 |
| HUAWEI Mate 60 RS 非凡大师 | 屏幕 | 竖向 portrait | 未收录 | 未收录 | 按实际窗口读取 | 按窗口读取 | 按窗口读取 | 未收录机型专用尺寸 |

### 通用预览参考

HUAWEI Mate 60 Pro+、HUAWEI Mate 60 RS 非凡大师：缺少机型专用 vp 参考值时，可采用通用手机竖屏基线 **374 × 827 vp**，横向／纵向参考断点为 **sm / lg**。它不是这些型号的固定窗口尺寸，实际适配读取当前窗口。

## 3. 窗口与交互能力

| 适用型号 | 能力 | 支持情况 | 说明 |
| --- | --- | --- | --- |
| 全部型号 | 全屏、分屏、悬浮窗 | 支持 | 应用需满足相应窗口模式的配置要求 |
| 全部型号 | 自由多窗 | 官方指南未列为支持类型 | 不将平板的自由多窗能力直接用于本机型 |

## 4. 相机信息

| 适用型号 | 位置 | 配置 |
| --- | --- | --- |
| 全部型号 | 镜头配置 | 未收录精确机型参数，不使用同系列其他型号替代 |

镜头配置不等于应用可打开或同时打开的相机集合。可用相机、输出规格、旋转和镜像参数以运行时查询为准，不依赖固定 cameraId 或数组顺序。

## 5. 使用注意

- 先确认具体型号、年份和版本，再读取对应参数；未收录的项目不使用同系列其他型号替代。
- 屏幕英寸和 px 不直接换算为 vp；旋转、分屏、多窗或显示缩放后，重新读取窗口或容器尺寸。
- 设备类型和断点不直接决定导航位置、列表列数或分栏，按页面内容和已确认方案选择布局。

公共规则：[设备分类与形态](../../公共规则/设备分类与形态.md)、[尺寸单位与断点](../../公共规则/尺寸单位与断点.md)。

## 6. 官方资料

| 适用型号 | 资料 |
| --- | --- |
| 全部型号 | [HarmonyOS 官方支持名单](https://consumer.huawei.com/cn/support/harmonyos/models-6/) |
| HUAWEI Mate 60、HUAWEI Mate 60 Pro | [布局基础—设备屏幕尺寸](https://developer.huawei.com/consumer/cn/doc/design-guides/design-layout-basics-0000001795579413) |
| 全部型号 | [窗口模式](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-device-window-mode) |
| HUAWEI Mate 60 Pro+、HUAWEI Mate 60 RS 非凡大师 | [响应式布局—尺寸与断点参考](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-device-responsive-layout) |
