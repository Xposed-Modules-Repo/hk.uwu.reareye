# REAREye

适用于小米 17 Pro / 17 Pro Max 的背屏增强模块。

REAREye 基于 LSPosed / Xposed，为系统框架、背屏中心和主题管理提供更细粒度的可配置能力，用来补足原厂背屏在应用放行、音乐歌词、壁纸轮播、组件模板、视频壁纸限制等方面的不足。

[![GitHub release](https://img.shields.io/github/v/release/killerprojecte/REAREye?display_name=tag)](https://github.com/killerprojecte/REAREye/releases)
[![GitHub license](https://img.shields.io/github/license/killerprojecte/REAREye)](https://github.com/killerprojecte/REAREye/blob/main/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/killerprojecte/REAREye)](https://github.com/killerprojecte/REAREye/issues)
[![Android](https://img.shields.io/badge/Android-16%2B-3DDC84?logo=android&logoColor=white)](https://developer.android.com/)

## 功能概览

- 放行指定应用在背屏启动，并支持活动白名单控制
- 自定义音乐控件白名单，兼容更多媒体类应用
- 增强歌词显示，支持原文、翻译、罗马音与不同歌词提供器
- 管理背屏组件模板、常驻卡片与组件额外显示选项
- 管理背屏壁纸、定时轮播、拖拽排序与轮播间隔
- 解除主题管理中的多项限制，包括视频壁纸时长、帧率和模板数量限制
- 移除国行 GMS 功能限制
- 提供切换主屏 / 背屏的快捷设置 Tile

## 主要功能

### 模块设置

- 主题模式切换
  - 支持 Miuix / Monet 两套风格
  - 支持跟随系统、浅色、深色模式
- 隐藏桌面入口
  - 可选隐藏 REAREye 的 Launcher 图标
- 更多调试输出
  - 便于排查模块行为与兼容性问题

### 系统框架增强

- 背屏应用活动白名单
  - 自定义哪些应用允许在背屏中打开
  - 可单独维护允许的应用列表
- 允许所有 Activity 在背屏打开
  - 适合自行测试未适配应用
- 后台白名单
  - 让指定应用在背屏使用时更不容易被系统杀掉
- 锁定应用进程
  - 将指定应用以更强的保活方式维持在后台
- 阻止锁屏后背屏返回桌面
  - 保持背屏当前状态，减少锁屏后的自动跳回
- 禁用背屏保护
  - 主屏进入全屏模式时，不再自动锁定背屏

### 背屏中心增强

#### 背屏个性化管理

- 组件模板管理器
  - 管理 Widget 到模板文件的映射关系
  - 支持导入模板文件并立即更新运行时映射
- 卡片管理器
  - 管理常驻卡片的标题、目标包名、组件名称、优先级与启用状态
- 组件额外设置管理器
  - 手动添加需要额外显示选项的组件
  - 当前支持为指定组件关闭通知时间显示
- 壁纸管理器
  - 查看当前系统可用背屏壁纸
  - 设定当前壁纸
  - 将壁纸加入轮播列表
  - 拖拽调整轮播顺序
  - 按毫秒配置每张壁纸的切换间隔
  - 开启或关闭背屏壁纸轮播

#### 音乐控件增强

- 音乐控件白名单
  - 自定义哪些应用的音乐控件允许显示在背屏中
  - 对使用标准媒体控件的应用更友好
- 强制刷新音乐控件状态
  - 解决部分应用在切歌或状态变化后背屏控件更新不及时的问题

#### 歌词增强

- 歌词显示模式
  - 支持原文、翻译、罗马音
- 歌词提供器切换
  - 支持 `Lyricon`
  - 支持 `SuperLyric`
- 逐行歌词显示模式
  - 可选择显示原文或翻译

#### 视频与媒体行为

- 强制视频壁纸循环播放
- 视频壁纸音量调节
  - 支持从 0% 到 100% 细粒度调节播放音量

### 主题管理增强

- 解除视频壁纸限制
  - 移除视频时长限制
  - 移除默认帧率限制，尽量按素材原始帧率加载
- 解除背屏模板数量上限
  - 不再受原厂默认模板数量限制
- 解除视频壁纸静音限制
  - 允许添加带音频的视频壁纸

### 杂项功能

- 移除国行 GMS 服务限制
  - 用于解除部分国行系统对 Google 服务功能的限制
  - 例如时间线、位置记录等功能的可用性问题

### 额外功能

- 快捷设置 Tile
  - 切换当前应用到背屏
  - 将先前移至背屏的应用切回主屏
- 首页状态与快捷操作
  - 查看模块工作状态、版本信息、更新状态
  - 提供针对背屏中心 / 主题管理等目标应用的快捷操作入口

## 模块作用域

默认作用域包含以下目标进程：

- `android`
- `com.xiaomi.subscreencenter`
- `com.android.thememanager`
- `com.android.systemui`

## 前置要求

- Android 8.1 及以上
- LSPosed / Xposed 兼容环境
- Xposed API 93 及以上
- 适用于带背屏的目标机型，当前仓库主要面向小米 17 Pro / 17 Pro Max
- 部分功能或快捷操作需要 Root 权限

## 安装方式

1. 从 [Releases](https://github.com/killerprojecte/REAREye/releases) 下载最新 APK 并安装。
2. 在 LSPosed 或兼容框架中启用 `REAREye`。
3. 确认模块作用域包含：`android`、`com.xiaomi.subscreencenter`、`com.android.thememanager`、`com.android.systemui`。
4. 重启设备，或至少重启相关目标应用后再进入模块配置。
5. 打开模块应用，根据自己的需求启用对应功能。

## 使用说明

- 背屏白名单、音乐控件白名单、组件模板、卡片与壁纸轮播等配置修改后，建议重启 `com.xiaomi.subscreencenter`。
- 系统框架类修改通常需要重启系统后才能稳定生效。
- 主题管理相关修改建议在变更后重启 `com.android.thememanager`，必要时重启系统。
- 部分快捷操作或系统级能力依赖 Root 权限，请确保 Root 管理器已正确授权。
- 本模块不内置背屏应用启动器；如果你需要直接在背屏拉起某些应用，可以配合 ADB 或其他启动方式使用。
- 解锁模板数量上限后，极端大数量模板场景仍建议自行测试稳定性。

## 适用场景

- 想让更多应用在背屏上正常启动或驻留
- 想在背屏使用更多第三方音乐 App 的媒体控件
- 想更自由地控制歌词来源和显示内容
- 想自己维护背屏组件模板和常驻卡片
- 想给背屏壁纸做定时轮播和排序管理
- 想解除原厂主题管理器对视频壁纸和模板数量的限制
- 想在不刷额外 Magisk 模块的情况下处理国行 GMS 限制

## 获取帮助

- 提交问题反馈: [Issues](https://github.com/killerprojecte/REAREye/issues)
- 查看版本发布: [Releases](https://github.com/killerprojecte/REAREye/releases)
- 项目仓库地址: [killerprojecte/REAREye](https://github.com/killerprojecte/REAREye)

## 免责声明

- 本模块会修改系统与目标应用行为，请自行评估风险。
- 不同系统版本、不同固件版本、不同 Root / Xposed 环境之间可能存在兼容性差异。
- 使用本模块造成的功能异常、数据问题或设备风险，请自行承担。

## License

See [LICENSE](./LICENSE).
