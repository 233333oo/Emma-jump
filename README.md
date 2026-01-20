# Emma Jump

一个基于 Vue 3 的 2D 跳跃游戏，控制角色不断向上跳跃，收集道具，挑战更高分数。

## 游戏玩法

- 使用 **←/→ 方向键** 或 **A/D 键** 控制角色左右移动
- 角色会自动跳跃，踩到平台后会再次弹起
- 不断向上跳跃，获得更高分数
- 小心不要掉落到屏幕下方！

## 道具系统

游戏中会出现三种随机道具：

- 🚀 **火箭**：快速向上飞行 2 秒
- 🛡️ **保护帽**：抵挡一次掉落
- ⭐ **分数加成**：额外获得 500 分

## 技术栈

- **Vue 3** - 渐进式 JavaScript 框架
- **Vite** - 快速的前端构建工具
- **Composition API** - Vue 3 组合式 API

## 快速开始

### 前置要求

- 安装 [Node.js](https://nodejs.org/)
- 安装 [npm](https://www.npmjs.com/)

### 安装与运行步骤

#### 1. 安装依赖
在release中获取项目文件夹。
在项目根目录下打开终端/命令行，运行：

```bash
npm install
```

这将安装项目所需的所有依赖包（Vue 3、Vite 等）。

#### 2. 启动开发服务器

安装完成后，运行：

```bash
npm run dev
```

终端会显示本地服务器地址，例如：

```
  VITE v5.0.0  ready in 234 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
```

#### 3. 打开游戏

在浏览器中访问显示的地址即可开始游戏！

#### 4. 开始游戏

- 点击屏幕上的「开始游戏」按钮
- 使用键盘方向键或 A/D 键控制角色移动

## 项目结构

```
emma-jump/
├── public/          # 静态资源
├── src/
│   ├── components/  # 游戏组件
│   │   ├── GameCanvas.vue    # 游戏画布
│   │   ├── Player.vue        # 玩家角色
│   │   ├── Platform.vue      # 平台
│   │   ├── Item.vue          # 道具
│   │   ├── ScoreBoard.vue    # 分数板
│   │   ├── StartScreen.vue   # 开始界面
│   │   └── GameOver.vue      # 游戏结束界面
│   ├── composables/
│   │   └── useGameLogic.js   # 游戏逻辑
│   ├── App.vue      # 主应用组件
│   └── main.js      # 入口文件
├── index.html
├── package.json
└── vite.config.js
```

## 游戏特性

- 🎮 流畅的物理引擎和跳跃手感
- 🎨 随机生成的彩色平台
- 🔄 无限游戏模式，挑战最高分
- 💫 多种道具增加游戏趣味性
- 📱 响应式设计
