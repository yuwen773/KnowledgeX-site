# KnowledgeX 介绍页

KnowledgeX 的公开介绍页，托管在 <https://yuwen773.github.io/KnowledgeX-site/>。

这是一份**无构建步骤**的静态页面：一个 HTML、一个 CSS、一个字体目录和若干真实截图。
仓库用 GitHub Pages 直接发布 `main` 分支的根目录。

## 内容边界

- 页面里出现的每一张界面截图都来自真实运行记录，存放在 `assets/`，
  没有用 div 拼出来的假截图。
- 截图只包含模型输出与本机管理界面，不含密钥、会话标识或真实题目。
- 未验证的部分在页面最后一节明确列出，不因为其他验收通过而被算作通过。

## 目录

```
index.html          页面结构
styles.css          样式与主题变量
assets/             真实截图与品牌标记
assets/fonts/       自托管的子集化字体
LICENSE             GNU AGPL-3.0
```

## 字体

字体全部自托管，并按页面实际用到的字符做了子集化：

| 文件 | 来源 | 用途 |
| --- | --- | --- |
| `outfit.woff2` | Outfit | 拉丁字母与数字 |
| `noto-sc-regular.woff2` | Noto Sans SC | 中文正文 |
| `noto-sc-bold.woff2` | Noto Sans SC | 中文标题 |
| `noto-sc-black.woff2` | Noto Sans SC | 中文主标题 |
| `jetbrains-mono.woff2` | JetBrains Mono | 代码与标签 |

子集化使用 `fonttools` 的 `pyftsubset`。改动页面文案后如果出现缺字，
按新的字符集重新生成子集即可。

## 主题

深色与浅色两套主题由 `:root` 与 `:root[data-theme="light"]` 下的同一组变量控制。
页面在首次绘制前用内联脚本读取 `localStorage` 里的 `kx-theme` 并设置
`data-theme`，避免刷新时闪烁。两套主题的正文都通过 WCAG AA 对比度检查。

## 本地预览

不需要依赖，直接用浏览器打开 `index.html` 即可。仓库主项目
(https://github.com/yuwen773/KnowledgeX) 里的 `scripts/site-audit.mjs`
可以对这份页面做视觉审计，需要 Chrome 和 `playwright-core`。
