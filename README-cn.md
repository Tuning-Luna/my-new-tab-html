> [🇬🇧 English](README.md)

# MyNewTab — Chrome 新标签页扩展

一款极简美观的 Chrome 新标签页，太空主题的 3D 交互式着陆页。

基于 **Vue 3** + **TypeScript** + **SCSS** 构建，使用 **Vite 7** 驱动。

## 特性

- **太空主题背景** — 地球照片搭配动态星云与星空粒子
- **3D Google 标志** — 跟随鼠标移动的视差倾斜交互，自带悬浮动画与悬停霓虹发光效果
- **头像光环动画** — 脉冲青色波纹扩散效果
- **打字机动画** — 循环输出 "Always Learning, Always building."，带打字/停顿节奏
- 点击 Google 标志跳转到 Google 搜索

## 作为扩展使用

1. 构建项目：
   ```bash
   npm run build
   ```
2. 将 `manifest.json` 复制到 `dist/`：
   ```bash
   Copy-Item manifest.json dist/
   ```
3. 打开 Chrome → `chrome://extensions` → 开启开发者模式 → **加载已解压的扩展程序** → 选择 `dist/` 目录

## 开发

```bash
# 安装依赖
npm i

# 启动开发服务器（自动打开浏览器）
npm run dev

# 类型检查
npm run type-check

# 代码检查并修复
npm run lint

# 生产构建（类型检查 + vite 构建）
npm run build
```

## 技术栈

| 工具 | 用途 |
|---|---|
| Vue 3 `<script setup>` | 组件框架 |
| TypeScript | 类型安全 |
| SCSS | 作用域样式 |
| Vite 7 | 构建工具，`base: './'` 适配扩展 |
| vue-tsc | 类型检查 |
| ESLint 9 扁平配置 | 代码规范 |
| Chrome Extension MV3 | `chrome_url_overrides: { newtab }` |

## 项目结构

```
src/
├── main.ts              # 入口文件
├── App.vue              # 根组件 — 太空背景、星云、星空
├── reset.css            # 全局样式重置
├── components/
│   ├── Logo3D.vue       # 3D Google 标志 + 头像光环
│   └── TypeWriter.vue   # 打字机动画
└── assets/
    ├── earch.jpg        # 地球背景图
    ├── google_logo.svg  # Google 标志
    └── Tuning.png       # 头像图片
```

## 资源替换

地球背景、Google 标志和头像均可通过替换 `src/assets/` 中对应文件进行自定义。
