# Dust

个人 Hugo 博客，使用 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) 构建并通过 GitHub Actions 发布到 GitHub Pages。

- 站点：https://heguangv.github.io/myblog/
- 默认语言：简体中文
- Hugo：Extended 0.165.0
- 主题：Stack v4.0.3（Git 子模块）

## 本地开发

首次克隆时初始化主题子模块：

```bash
git clone --recurse-submodules git@github.com:heguangV/myblog.git
cd myblog
```

启动本地预览：

```bash
hugo server --buildDrafts
```

创建文章：

```bash
hugo new content post/article-name.md
```

构建检查：

```bash
hugo --minify --gc --cleanDestinationDir --noBuildLock
```

`public/`、`resources/_gen/` 和构建锁文件均为生成内容，不应提交到源码分支。

## 目录结构

```text
assets/             图片、图标等由 Hugo 处理的资源
config/_default/    站点、菜单、语言和渲染配置
content/            页面与文章 Markdown 源文件
layouts/            针对 Stack 主题的局部覆盖
static/             原样复制到站点的静态文件
themes/             Git 子模块形式的主题
```

## 部署

推送到 `main` 后，`.github/workflows/deploy.yml` 会执行以下操作：

1. 拉取源码和主题子模块。
2. 使用 Hugo Extended 0.165.0 构建。
3. 将生成结果发布到 `gh-pages` 分支。

也可以在 GitHub Actions 页面手动触发部署。

## 维护约定

- 不要把 SSH 私钥、访问令牌或其他凭据放入仓库。
- 主题升级后先在本地构建并检查页面，再提交子模块指针。
- 评论功能默认关闭；配置有效的评论服务和隐私说明后再启用。
- 内容改动和基础设施维护尽量使用不同提交，便于回滚。
