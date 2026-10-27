# 我的博客

一个纯静态个人博客，托管于 Cloudflare Pages，源码管理在 GitHub。

## 目录结构

```
my-blog/
├── index.html              # 首页（文章列表）
├── about.html              # 关于页
├── posts/                  # 文章目录
│   ├── hello-world.html
│   └── cloudflare-pages-guide.html
├── css/style.css           # 全站样式（含深色模式）
└── js/main.js              # 主题切换脚本
```

## 如何发布新文章

1. 复制 `posts/` 下任意一篇现有文章作为模板，改标题和正文
2. 在 `index.html` 的 `.post-list` 里加一张文章卡片
3. 提交并推送：

```bash
git add .
git commit -m "post: 新文章标题"
git push
```

Cloudflare Pages 会自动重新部署，约 1 分钟内生效。

## 部署步骤（一次性）

### 1. 推送到 GitHub

在 GitHub 上新建一个空仓库（如 `my-blog`），然后：

```bash
git init
git add .
git commit -m "init: 个人博客"
git remote add origin https://github.com/你的用户名/my-blog.git
git branch -M main
git push -u origin main
```

### 2. 连接 Cloudflare Pages

1. 登录 https://dash.cloudflare.com
2. 左侧 **Workers & Pages** → **Create** → **Pages** 标签 → **Connect to Git**
3. 授权 GitHub，选择 `my-blog` 仓库
4. 构建配置（纯静态站）：
   - Framework preset: **None**
   - Build command: 留空
   - Build output directory: **/**
5. 点击 **Save and Deploy**

完成后获得 `xxx.pages.dev` 免费域名。绑定自定义域名：项目 **Custom domains** 里添加即可。
