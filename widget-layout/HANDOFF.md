# 小组件布局编辑器 — 交接说明

## 文件
- src/main.ts：TypeScript 源码
- index.html：页面骨架与样式（开发用，引用 dist/main.js）
- tsconfig.json：编译配置
- dist/main.js：编译产物
- widget-layout.html：单文件版本（已内联 JS，双击即可使用）

## 构建
    tsc -p tsconfig.json
    # 然后把 dist/main.js 内联回 index.html，或直接使用 widget-layout.html

## 当前状态
- 机型预设：iPhone 18 Pro（402×874，默认）、16 Pro、16 Pro Max、15 Pro、15 Pro Max
- 小/中/大组件尺寸为估计值，需对照实机确认（18 Pro 的尺寸沿用 16 Pro）
- 导出为 @3x 裁剪 PNG，布局保存在 localStorage

## 已确认的偏移问题（截图 2c2af0e6）— 已在代码中修正（CROP_FIX_X/Y，预览与导出共用）
- 小组件外的壁纸与预览完全对齐（归一化相关 0.994，偏移 0）
- 小组件内的壁纸相对实际位置偏移约 (+2.0, −25.8) pt
- 玻璃框实际位置约 (23.3, 91.7) pt，尺寸约 350×164.5 pt
- 原裁剪原点约 (25.3, 65.9) pt
- 修正方法（已应用）：壁纸裁剪原点加上 (−2.0, +25.8) pt，见 src/main.ts 的 CROP_FIX_X / CROP_FIX_Y

## 未完成
- Vercel CLI 与 MCP 设置未完成（当前环境断网，需在本机执行）
