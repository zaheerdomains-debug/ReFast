# ReFast

<div align="center">
  <h3>A Windows quick launcher based on Tauri 2</h3>
  <p>Similar to utools, it allows you to quickly launch applications, search for files, and manage notes.</p>
  <p>
    <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License"></a>
    <a href="https://github.com/zaheerdomains-debug/ReFast/releases"><img src="https://img.shields.io/github/v/release/Xieweikang123/ReFast" alt="Release"></a>
    <a href="https://github.com/zaheerdomains-debug/ReFast"><img src="https://img.shields.io/github/stars/Xieweikang123/ReFast?style=social" alt="Stars"></a>
  </p>
</div>

## 📑 Table of Contents

- Download
- User Documentation
- Technology Stack
- Project Structure
- Development
- Features
- Contact the author - Join the product discussion group
- Functional status
- Contribute
- License
- Update History
- Related Links

## Download

Download the latest version of the installation package from the [Releases](https://github.com/zaheerdomains-debug/ReFast/releases)

## User Documentation

[📚 Documentation (Wiki)](https://github.com/zaheerdomains-debug/ReFast/wiki)


## Technology Stack

- **Framework**: Tauri 2.x (cross-platform support, but the current project is primarily optimized for Windows)
- **Frontend**: React + TypeScript + Tailwind CSS
- **Backend**: Rust
- **Platform**: Windows 10/11

> **Note**: Due to limited development resources, the project currently focuses primarily on Windows. Although the Tauri framework itself supports macOS and Linux, some features of this project, such as Everything search and Windows system folder search, are Windows-specific. Cross-platform implementations from the community are welcome!

## Project Structure

```
re-fast/
├── src/                    # Frontend code
│   ├── api/               # Tauri API wrappers
│   ├── components/        # React components
│   ├── types/             # TypeScript type definitions
│   ├── App.tsx            # Main application component
│   └── main.tsx           # Entry point
├── src-tauri/             # Tauri backend code
│   ├── src/
│   │   ├── commands.rs    # Tauri command definitions
│   │   ├── launcher.rs    # Launcher core functionality
│   │   ├── hotkey.rs      # Global hotkeys
│   │   ├── everything_search.rs  # Everything search integration
│   │   ├── app_search.rs  # Application search
│   │   ├── memos.rs       # Memo functionality
│   │   ├── error.rs       # Error handling
│   │   └── main.rs        # Application entry point
│   └── Cargo.toml         # Rust dependency configuration
└── package.json           # Frontend dependency configuration
```

## Development

### Prerequisites

- Node.js (v18+)
- Rust (latest stable version)
- Windows 10/11 Development Environment

### Install dependencies

```bash
npm install
```

### Development Model

```bash
npm run dev:tauri
```

### Build

```bash
npm run build:tauri
```

[docs/RELEASE.md](docs/RELEASE.md) for the GitHub Releases.

## Features

### Core Functions
- 🚀 **Quick Launcher** - Quickly accessed via global keyboard shortcuts, supports searching for applications, files, and notes.
- 🔍 **Smart Search** - Integrates with Everything search, supporting app search, file history search, and system folder search. Intelligent sorting ensures frequently used results are displayed first; clicks are disabled until search results stabilize, and phased progress indicators are displayed.
- 📝 **Memo Center** - Quickly record and retrieve memos
- 🔧 **Plug -in System** - Supports custom plug-in extension functionality
- ⌨️ **Global Shortcut Keys** - Customize Shortcut Key Configuration
- 🎨 **Modern UI** - Elegant interface based on React + Tailwind CSS
- ⚡ **Excellent performance** - Based on Rust + Tauri 2, with extremely low resource consumption
- 👆 **Smart Close** - The search box automatically closes when you click on another window, providing a smooth user experience.

#### Search result interaction

When entering keywords to search, the launcher waits until results from multiple sources have stabilized before allowing clicking or pressing Enter to launch an item. This prevents accidental activation while the result list is still changing:

- **Debouncing wait**：The search is not initiated until the input stops (approximately 320ms for short words, even faster for long words).
- **Parallel search**：Simultaneously search applications, file history, system folders, Everything, etc.
- **Stability determination**：After the merge sort is complete, Everything returns, and batch rendering is finished, wait an additional 350ms quiet period.
- **Interaction restrictions**：The search in progress list is semi-transparent and not clickable; launching the search by pressing Enter is also disabled.

During the search process, the top of the results area will display "**Results Updating**" and a detailed label indicating the current stage, for example:

| Label | Meaning |
|------|------|
| `Waiting for stable input` | Image stabilization in progress, search not yet started. |
| `App and file history` | In local applications and file history search |
| `Everything 23/1200 items` | Everything Search Progress |
| `Match "keywords"` | The merge result is not yet aligned with the current input. |
| `Sort` | Merging and sorting results from multiple paths |
| `The list currently displays 150 items.` | A large number of results are being loaded in batches. |
| `Nearly to be completed` | After each stage, we enter the final silent waiting phase. |

If there are no results, the same status details will also be displayed in the centered loading area.

### Built-in tools
- 📄 **JSON Formatter** - Format, compress, and validate JSON data
- 📌 **Calculation Scratch Paper** - Multi-line Recording: Write multi-line equations like you're writing drafts, supporting precise calculations.
- 🌐 **Translation Tool** - Supports Baidu Translate and Sogou Translate, automatically reads clipboard content and translates, supports mutual translation between multiple languages.
- 📦 **File Toolbox** - Batch file find and replace tool, supports regular expressions, file extension filtering, automatic backup and other functions.
- 🎬 **Action Recording and Playback** - Record keyboard and mouse operations, support playback at different speeds, suitable for automating repetitive tasks.
- 🔧 **Plugin Management Interface** - View and manage all available plugins
- ⚙️ **Settings Center** - App Configuration and Personalization Settings

## Contact the author

<div align="center">

**🎉 Welcome to join the ReFast product discussion group!**

Scan the QR code below to add the author on WeChat, and let's exchange user experiences, provide feedback, and offer suggestions!！


![作者微信二维码](https://github.com/user-attachments/assets/3071dd2f-1425-489e-b351-98c3bb34689e)

**We look forward to having you join us!** 🚀

</div>

## Functional status

### Completed
- ✅ Quick Launcher Core Functions
- ✅ App search and launch
- ✅ Everything Search Integration
- ✅ File History
- ✅ Memo feature
- ✅ Global keyboard shortcuts supported
- ✅ Plugin System Framework
- ✅ JSON formatter
- ✅ Calculation sheet plugin (supports precise calculations, uses mathjs)
- ✅ Translation tool (supports Baidu Translate and Sogou Translate, automatically reads clipboard)
- ✅ File Toolbox (Batch find and replace, supports regular expressions and backup)
- ✅ Action recording and playback function
- ✅ Modern UI
- ✅ Automatically close the search box when it loses focus.
- ✅ Click only after the search results have stabilized; the search process will display phased progress indicators.

### In the plan
- ⏳ More built-in plugins
- ⏳ Theme Customization
- ⏳ Search history optimization
- ⏳ More file types supported

## contribute

We welcome you to submit Issue and Pull Requests!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Update History

### 近期更新

*2026 年 7 月 9 日*

- **搜索交互优化**：结果列表在搜索未稳定前禁止点击和 Enter 启动，避免结果跳动时误触；稳定后恢复正常交互。
- **搜索进度提示**：结果区显示「结果更新中」及分阶段标签（等待输入稳定、应用与文件历史、Everything 进度、整理排序、列表加载、即将完成等）。
- **`.lnk` 快捷方式**：悬停显示解析后的真实目标路径（与 `.exe` 一致的原生 tooltip）；右键「打开所在文件夹」会定位到目标文件所在目录，而不是 `Recent` 里的 `.lnk` 文件。

### v1.0.68

*2026 年 1 月 7 日*

- **搜索列表更聪明**：结果里若出现你**最近打开过**的应用或文件，会**自动选中**最近用过的那一项，少按几次方向键。
- **选中更清晰**：当前高亮项的对比略加强，一眼能看出选的是哪一条。
- **启动方式更顺手（Windows）**：批处理、程序、快捷方式的打开方式调整，工作目录和环境变量行为更接近从资源管理器或开始菜单打开。
- **常用系统入口**：在启动器里能搜到环境变量、设备管理器、服务、网络连接等系统项（支持中文、拼音、英文名等）。
- 新增 **Markdown 查看**相关能力。
- 修复搜索框在 **JSON 内容过长**时可能报错的问题。


### v1.0.56
- 🎨 **动画效果优化**
  - 优化 fadeInUp 动画，调整时长为 0.35s，使用 cubic-bezier 缓动函数，提升视觉流畅度
- ⚡ **性能优化**
  - 重构 LauncherWindow 输入处理逻辑，简化状态更新流程
  - 使用 useMemo 对输入框样式进行记忆化，减少不必要的重渲染
- 🖼️ **图标功能增强**
  - 新增可执行文件（.exe 和 .lnk）图标提取和缓存功能
  - 优化搜索结果中的图标显示体验
- 🔧 **代码优化**
  - 优化 app_search.rs，减少约 120 行代码，提升代码质量

### v1.0.34
- 🔧 **插件快捷键优化**
  - 修复插件快捷键重复触发问题，确保按快捷键时只打开一个插件窗口
  - 优化插件执行锁机制，支持不同插件之间的快速切换
  - 修复插件窗口置前问题，按快捷键时窗口会自动置前并获取焦点
  - 改进窗口显示逻辑，新创建的窗口和已存在的窗口都会正确置前

### v1.0.33
- 📁 **文件历史功能增强**
  - 新增文件历史搜索功能，支持按文件名/路径搜索
  - 新增日期范围过滤，支持快速选择时间段（如 5-10 天）
  - 优化使用次数统计和调试日志
  - 使用 `requestIdleCallback` 优化大数据量排序，避免阻塞 UI
  - 添加 15 秒超时保护机制
- 🎨 **图标提取功能**
  - 支持 Native API 和 PowerShell 两种图标提取方式
  - 新增图标验证与统计功能
  - 统一图标提取失败标记，避免重复尝试
  - 支持批量提取应用图标
- ⚡ **LauncherWindow 优化**
  - 重构 `handleLaunch` 函数，优化文件历史更新逻辑
  - 统一提前处理 URL（http/https），避免走文件启动流程
  - 改进路径规范化匹配算法，提高匹配准确性
  - 优化最近使用时间处理，支持秒级和毫秒级时间戳
- 🔍 **应用去重逻辑增强**
  - 统一处理路径大小写和路径分隔符
  - 优化去重优先级（.exe > .lnk > UWP）
  - 改进历史文件与 Everything 搜索结果的去重逻辑
- 🎯 **UI 组件改进**
  - 新增 `FileHistoryPanel` 独立文件历史管理面板
  - 新增 `AppIndexList` 应用索引列表管理组件
  - 新增 `ConfirmDialog` 确认对话框组件
  - 优化按钮样式和布局，改善可访问性

### v1.0.26
- 🔄 **Version Management and Automatic Updates**
  - A new version management script system has been added, supporting version number synchronization and test version settings.
A new automatic update check feature has been added, supporting automatic checks every 24 hours (this can be turned off in settings).
After startup, a 5-second delay is set to check for updates to avoid impacting startup speed.
The "About" page supports manually checking for updates.
- ⚡ **Performance Optimization**
  - The application uses a version number caching mechanism to avoid duplicate retrieval and improve event reporting performance.
LauncherWindow is optimized using useCallback to reduce unnecessary re-rendering.
Implement silent preloading of the application list to improve startup speed.
Optimize application search execution process and database access
Enhance Everything search caching mechanism
- 🔍 **Enhanced search function**
  - Add detailed debug logs (performance logs, search process logs).
Optimize application search and sorting logic, and improve the handling and display of total results.
Enhanced application and file history search functionality
Enhance the search functionality of Everything and system folders.
- 🧹 **Code refactoring and cleanup**
  - Remove SystemFolderItem related references and functions
Remove all agent logging code, but retain necessary debug logs (controlled via configuration).
- 🔧 **Feature improvements**
  - The `reveal_in_folder` command has been refactored, and the file path handling logic has been improved.
Supports special handling of files in the recycle bin.
Optimize the opening logic of Windows Explorer
Refactor the hotkey update handling logic and enhance logging when a search fails.

### v1.0.21
- 🔍 **Major upgrade to the Everything search function**
  - Implement a search session management and pagination system that supports efficient loading of large result sets (500 results per page).
  - A new search cancellation feature has been added, which can interrupt long-running search tasks.
  - Optimize session parameter management to avoid duplicate session creation and improve search performance.
  - Implementing a batch result processing mechanism significantly improves response speed in scenarios with large amounts of data.
  - Add batch event listeners to display search loading progress in real time.
  - Optimizes memory usage, supporting caching up to 8 pages of data (LRU strategy).
- 🎨 **Custom Filter System**
  - Supports custom file type filters and uses SQLite persistent storage.
  - Supports automatic syntax detection for Everything, recognizing advanced search syntax.
  - Added folder name matching preference settings
  - Supports configuration of the maximum number of results (default 5000, maximum 2 million).
  - Optimized sorting options, supporting sorting by size, type, and name.
- 🚀 **Launcher window optimization**
  - Added a rocket launch animation effect to enhance visual feedback.
  - Refactor the search cancellation logic to improve response speed and stability.
  - Added window hiding capability configuration and optimized window management.
- 🔧 **User experience improvements**
  - Add a scroll-to-top feature for quick access to the results list.
  - Optimize error handling and message prompts.
  - Remove redundant search effects and simplify the search process.
  - Refactor the plugin filtering logic and optimize the plugin center interaction.

### v1.0.19
- 🌐 New translation tool: Supports Baidu Translate and Sogou Translate, automatically reads clipboard content and translates.
- 🔄 The translation tool supports translation between multiple languages ​​(Chinese, English, Japanese, Korean, French, German, and 14 other languages).
- 📦 New File Toolbox: Batch File Find and Replace Tool
- 🔍 The File Toolbox supports advanced options such as regular expression matching, file extension filtering, and case sensitivity.
- 💾 The File Toolbox supports automatic backup, automatically backing up folders before replacement to ensure data security.
- 📝 The File Toolbox supports replacing content in filenames.

### v1.0.18
- 🎯 Optimized the plugin system to improve plugin loading and execution performance.
- 🔧 Improved settings interface and optimized user experience

### v1.0.17
- 📊 Added a "Statistics" page: View the total number of users and plugin usage rankings. Activity trends and feature popularity will be added later.
- 🔄 Plugin Usage Statistics: Automatically records the number of times a plugin is launched and its most recent usage time when the plugin is executed, and supports local leaderboard display.
- 📈 Event Tracking: Critical operations such as application startup and application launcher opening the application will report events (configurable event server supported).
- 💾 Added database backup: One-click backup of current data for easy migration or rollback.

### v1.0.16
- 👆 Added the feature to automatically close the search box when it loses focus; the search box will automatically close when you click on another window.
- 🎯 Optimized user experience, making the search box behavior more consistent with common interaction patterns of launcher applications.

### v1.0.15
- 📌 Added a calculation paper plugin, supporting multi-line formula recording and precise calculations.
- 🎨 The calculation paper features a light yellow theme reminiscent of scratch paper.
- 🔢 Use the mathjs library to handle floating-point precision issues and avoid calculation errors.
- 📋 Supports copying single rows of results and copying all results.
- ⌨️ Supports keyboard shortcuts: Enter to add a new line, Backspace to delete a line, and ↑/↓ for navigation.
- 🔍 Optimized search result ranking algorithm; historical file results take precedence over Everything results.
- 📊 Bonus points for historical file results (base score 300 points + 30% weighting for filename matching)
- 📈 Historical files that have been used more often will appear higher in the sorting (maximum score of 200 points for usage frequency).
- ⚡ When the rating difference is within 200 points, historical files take precedence over Everything results.

### v1.0.14
- 🔍 Optimized app search ranking algorithm, apps are displayed first.
- 🎯 Supports Pinyin search; when Pinyin matches, the app is displayed first (e.g., when searching for "weixin", the WeChat app appears first).
- ⚡ Short queries (2-4 characters) that are exact matches are given higher weight.
- 📱 Application type results receive extra points, ensuring frequently used applications are displayed first.

### v1.0.13
- 🔧 Optimized shortcut recording function, supporting repeated modifier key detection (such as Ctrl+Ctrl).
- 🐛 Fixed the issue of duplicate event handling during shortcut recording.
- ⚡ Improved the response speed and stability of shortcut recording

### v1.0.0+
- ✅ Quick Launcher Core Functions
- ✅ App search and launch
- ✅ Everything Search Integration
- ✅ File History
- ✅ Memo feature
- ✅ Global keyboard shortcuts supported
- ✅ Plugin System Framework
- ✅ JSON formatter
- ✅ Modern UI

## 相关链接

- [GitHub 仓库](https://github.com/zaheerdomains-debug/ReFast)
- [问题反馈](https://github.com/zaheerdomains-debug/ReFast/issues)
- [Tauri 官网](https://tauri.app/)








