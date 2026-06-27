# GIS Aide — 让 ArcGIS Pro 拥有浏览器的力量

[![Version](https://img.shields.io/badge/version-2.8.0-blue)](releases/current)
[![ArcGIS Pro](https://img.shields.io/badge/ArcGIS%20Pro-3.6+-orange)](https://www.esri.com/en-us/arcgis/products/arcgis-pro)
[![.NET](https://img.shields.io/badge/.NET-8.0-purple)](https://dotnet.microsoft.com/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

> 以前每次处理数据或出图，总要同时打开浏览器、ArcGIS Pro、AI 对话窗口……在十几个界面之间来回跳转。这个插件把所有东西装进了同一个窗口。

**GIS Aide** 是一个 ArcGIS Pro Add-in（3.6+），把 WebView2 浏览器、AI 助手、地址定位、自定义工具和插件开发工作台整合在同一个功能区里，彻底结束"界面跳转马拉松"。

---

## 🚀 快速下载

| 通道 | 地址 |
|------|------|
| **微信公众号** | 前往“[生活地理通](https://mp.weixin.qq.com/s/LMvORo1VQg8OcThtXCoeSw)”，向后台发消息"**软件**"，进入"软件开发系列 > ArcGIS Pro内嵌浏览器"文件夹，可下载到插件及其源码源代码 |

> 安装方式：下载 `.esriAddInX` 后双击，跟随安装向导完成即可。安装后**重启 ArcGIS Pro**，在功能区即可看到"GIS Aide"选项卡。

---

## 🎯 它解决了什么问题？

| 痛点 | 以前 | 有了 GIS Aide |
|------|------|---------------|
| 下载数据 | 浏览器下载 → 切换回 Pro → 找文件夹 → 拖入 | 插件内浏览器直接下载 → 解压 → 拖入 |
| 查资料/问 AI | 切到浏览器 → 提问 → 复制结果 → 切回 Pro | GeoAI 助手嵌入在侧边栏，直接对话 |
| 执行代码 | 复制到 Notebook / Python 窗口 → 粘贴 → 运行 | AI 生成代码，**一键执行** |
| 国内地址搜索 | Pro 自带定位器常搜不到 | 高德/百度地理编码，结果缩放到地图 |
| 测投影 / 找方法 | 翻文档、试参数、反复报错 | 在浏览器里直接搜教程，边看边做 |
| 常用入口 | 每次手动输入网址 | 书签一键直达，功能区 Gallery 快速切换 |
| 管理 API Key | 记在文本里，到处粘贴 | 加密管理器统一存储，一键切换默认 |

---

## 🧩 核心功能

### 🌐 内嵌浏览器
- WebView2 多标签页浏览器，停靠在 ArcGIS Pro 右侧
- 支持网页**下载**（解压后直接拖入地图）
- **书签管理** — 收藏常用数据/教程网站，功能区 Gallery 快速切换
- 滑动条支持，超大页面无压力

### 🤖 GeoAI 助手
- 接入任意 OpenAI 兼容接口（讯飞星辰、DeepSeek、通义千问等免费 / 低价 API 均可）
- **Agent 模式**：26 个 GIS 工具，AI 可直接操作图层、执行地理处理、查询空间数据
- 三种交互模式：对话复制 / Notebook 插入 / 工具执行
- Markdown 渲染、框选复制、流式输出、对话历史持久化
- 支持 Temperature / MaxTokens / AppId 等参数调节

### 📍 地址定位
- 高德地图 / 百度地图地理编码
- 候选列表检索 + 勾选导出
- 一键缩放到选中地点
- 导出 CSV / Shapefile 点图层（WGS84）

### 🔧 自定义功能区工具
- 一键保存 Python 脚本、GP 工具、网页地址为功能区按钮
- 支持 `.atbx` / `.tbx` / `.pyt` 工具箱发现
- GP 工具"预设参数 + 打开原生面板"模式

### 🛠️ 插件开发工作台
- **学习路线**：8 步入门 ArcGIS Pro Add-in 开发
- **组件模板**：Module / Button / DockPane / Gallery 代码模板
- **DAML 助手**：交互式生成功能区片段
- **SDK 文档**：精选主题，支持离线阅读
- **构建发布**：编译打包安装清单

### 🔑 API 密钥管理器（v2.8.0）
- 独立窗口，类型树 + DataGrid，表格化管理 LLM / 高德 / 百度 / ArcGIS / 自定义密钥
- 完整 CRUD + 测试连接
- DPAPI 加密存储，默认遮蔽显示，5 秒明文查看
- 一键"设为默认"即时切换
- 批量导入/导出 JSON，支持右键批量删除、批量导出

---

## 🔨 自行编译

```powershell
# 清理（百度同步盘会锁 obj/ 临时文件）
rm -r -Force src/ArcGisProEmbeddedBrowser/obj

# 验证编译
dotnet build ArcGisProEmbeddedBrowser.sln -c Release /p:SkipArcGISAddInTargets=true

# 打包 .esriAddInX
.\tools\package-release.ps1 -Version 2.8.0
```

### 个性化二次开发

本项目从零开始就是靠 AI Agent 开发出来的。你也可以在现有代码基础上，用 AI（Codex / Cursor / WorkBuddy 等）继续扩展功能，无需读懂全部代码：

1. 将源码下载到本地
2. 用 AI IDE 打开项目目录
3. 告诉 AI "接管此项目，先阅读 PROJECT_MEMORY.md"
4. 清晰描述需求，AI 即可接手开发

> 经验分享：① 先问 AI"能做吗"再动手；② 如果担心 AI 盲猜，在指令末尾加一句"还有什么需要说明清楚的信息请及时问我，不要擅作主张"；③ 提供成熟的开源参考案例减少漏洞；④ 引导 AI 维护项目记忆文档，确保后续开发无缝衔接。

---

## 🧪 AI 配置

配置保存在 `%APPDATA%\LiToolbox\ArcGisProEmbeddedBrowser\browser-settings.json`，API Key 使用 Windows DPAPI 加密。

推荐免费 / 低门槛 API 接入方案：
- **讯飞星辰 MaaS**：注册后在模型集市选模型，获取 OpenAI 接口地址和 Key
- **DeepSeek**：注册获赠额度
- **通义千问**：阿里云百炼平台

---

## 📋 版本历史摘要

| 版本 | 日期 | 亮点 |
|------|------|------|
| v2.8.0 | 2026-06-15 | API 密钥管理器、DAML 助手、Agent 稳定版 |
| v2.7.x | 2026-06 | 插件开发工作台、地址定位候选检索、AI 对话持久化 |
| v2.6.x | 2026-06 | 自定义工具系统、Agent 模式、地址定位、Markdown 渲染 |

完整更新日志见 [docs/RELEASE_NOTES.md](docs/RELEASE_NOTES.md)。

---

## 📄 许可证

MIT License

---

**GIS Aide** — 把你在 ArcGIS Pro 里需要的一切，装进一个窗口。
