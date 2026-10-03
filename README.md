# Haphyxlos.github.io

个人学术主页,基于开源模板 [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io)(MIT License)搭建,Jekyll 静态站点,由 GitHub Pages 从 `main` 分支自动构建发布,线上地址:https://haphyxlos.github.io/

## 日常怎么改

改任何文件并 push 到 `main` 后,等 1–2 分钟 Pages 自动重新构建即可生效。

| 想改什么 | 改哪里 |
|---|---|
| 姓名 / 头像 / 简介 / 侧边栏社交链接 | `_config.yml` 的 `author:` 一节;头像图片在 `images/` |
| 首页全部正文(News / Publications / Honors / Educations / Talks / Internships) | `_pages/about.md`,文件里有 `TODO` 注释标明要替换的占位内容 |
| 导航栏条目 | `_data/navigation.yml`(锚点必须与 `_pages/about.md` 的标题一致) |
| 站点标题 / 描述 | `_config.yml` 的 `title` / `description` |
| 论文卡片配图 | 放进 `images/`,在 `about.md` 的 paper-box 里引用 |

## 发论文时的常用写法

在 `_pages/about.md` 的 Publications 栏目下,两种条目格式任选:

卡片式(带配图,配图先放进 `images/`):

```html
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">VENUE YEAR</div><img src='images/你的配图.png' alt="sym" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[论文标题](论文链接)

**你的名字**, 合作者 A, 合作者 B

- 一句话介绍这篇论文。
</div>
</div>
```

列表式(一行一条):

```markdown
- [论文标题](论文链接), 合作者, **会议年份**
```

## 以后想启用 Google Scholar 引用数自动更新(可选)

1. 在 Google Scholar 个人页 URL 里找到自己的 ID(`citations?user=XXXX` 中的 `XXXX`);
2. 从[上游模板仓库](https://github.com/RayeRen/acad-homepage.github.io/blob/main/.github/workflows/google_scholar_crawler.yaml)把 workflow 文件复制回 `.github/workflows/`;
3. 在本仓库 Settings → Secrets and variables → Actions 添加 `GOOGLE_SCHOLAR_ID` secret;
4. Actions 会生成 `google-scholar-stats` 分支,然后在 `_config.yml` 填上 `author.googlescholar`,在 `about.md` 里按模板语法加引用数标签。
(`google_scholar_crawler/` 目录已保留,爬虫脚本不用另外找。)

## 其他说明

- 旧的 Hexo 站点内容备份在 `hexo-backup` 分支,不需要可随时删除。
- 本地预览需要 Ruby:先 `bundle install`(仓库 Gemfile 用的是官方 `github-pages` gem),再 `bundle exec jekyll serve` 访问 http://127.0.0.1:4000。不装 Ruby 也完全可以,推上去直接看线上效果。
- 模板版权:AcadHomepage,MIT License(见 `LICENSE`)。
