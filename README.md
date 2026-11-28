# 逐字 VOICE V2（开发构建版）

## 当前包含
- 深蓝黑 / 米白 / 琥珀金的移动端 App 风格界面
- 多项目本地历史：新建、打开、搜索、复制、重命名、删除
- 文稿自动断句、添加、编辑、删除、上下调整
- 逐句录音、重录、试听、上一句 / 下一句
- IndexedDB 本地自动保存
- 单句 MP3、全部句子 ZIP（每句 MP3）、合并完整 MP3
- 项目备份与恢复（包含实际录音 Blob）
- PWA manifest / service worker 基础离线壳
- Capacitor Android 配置

## 本地运行
需要 Node.js 18 或更高版本。

```bash
npm install
npm run dev
```

## 构建网页
```bash
npm run build
npm run preview
```

## Android 工程生成
需要安装 Android Studio、Android SDK 和 JDK 17。

```bash
npm install
npx cap add android
npm run android:sync
npm run android:open
```

然后在 Android Studio 中构建 APK。正式发布前需要配置应用签名、检查麦克风权限和文件保存行为。

## 重要说明
1. MP3 编码由 `lamejs` 在本地完成，ZIP 使用 `jszip`。两者通过 npm 安装并由 Vite 打包；不是把 WAV/WebM 改名成 MP3。
2. 浏览器录音源格式由设备支持情况决定；导出时统一解码并转换为 MP3。
3. IndexedDB 数据只保存在当前应用/浏览器数据空间。卸载应用或清理数据可能造成丢失，请定期导出完整项目备份。
4. 这是 V2 开发构建版，仍需在真实 Android 设备上测试录音、MP3 解码、文件下载/保存、后台切换和长音频内存占用。
5. 旧版项目不自动迁移。你已确认旧项目有独立备份；如需恢复，可先从旧版导出 JSON。当前恢复入口支持 V2 项目格式，旧版 JSON 结构不同，需单独转换。
6. 字体使用系统字体为主；样式表中的 Google Fonts 仅为可选字体增强，不影响核心功能。若要求完全离线，可移除 @import。


## GitHub Pages 快速预览
将这些文件提交到仓库 `main` 分支后，GitHub Actions 会构建并部署 `dist`。仓库 Settings → Pages → Build and deployment 选择 **GitHub Actions**。部署完成后，打开仓库的 Pages 地址即可预览。若已有旧版 Pages 工作流，请先确认新旧工作流不会同时发布同一个站点。
