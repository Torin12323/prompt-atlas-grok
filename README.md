# Prompt Atlas · 综合提示词库（独立新版本）

这是单独推送的新版本，**没有修改、没有覆盖**原仓库 [Torin12323/prompt-atlas](https://github.com/Torin12323/prompt-atlas)。

- 原仓库线上站仍是：[Prompt Atlas](https://prompt-atlas.ewellyost.chatgpt.site)
- 这一版希望使用的地址：[prompt-atlas.grok.me](https://prompt-atlas.grok.me)
- `*.grok.me` 子域名是 Grok 第一次发布时由平台分配的。把代码推到 GitHub **不会**把已发布的 `prompt-orbit.grok.me` 改成 `prompt-atlas.grok.me`，也 **不会**自动开通这个新地址。
- 目前 `prompt-atlas.grok.me` 还没有对应应用。要拿到它，需要在一个**还没发布过**的新项目里，于首次发布前把域名栏改成 `prompt-atlas`，再发布。不要把本仓库接到原来的 ChatGPT Sites 项目上，以免影响原站。

---

## 当前功能

- 446 条公共提示词，搜索、筛选、收藏和复制
- 446 张独立提示词封面与 52 张不同的首屏旋转插图，来自 Pinterest 公开页面，按内容搭配\n- 图片已本地优化；详情页可查看 Pinterest 来源，完整来源记录在 `public/data/image-sources.json`
- 中英文切换、亮色和深色模式；所有主题的预览文字和封面标签统一增强对比度
- Baleday 品牌字体（用户提供），其余文字和控件采用苹果系统风格
- 首屏旋转动效，支持暂停与减少动态效果偏好
- 使用 ChatGPT 账号登录、注册入口
- 登录后添加个人提示词；服务端按账号隔离数据

## 构建

```sh
npm ci
npm run build
```

构建结果为 `dist/server/index.js`，包含静态资源和 Worker 服务端代码。

## 托管依赖

当前版本部署在 OpenAI Sites，数据库通过 Cloudflare D1 的 `DB` 绑定访问。
数据库结构与已有迁移保存在 `db/`、`drizzle/`。
登录和退出路径由 Sites 平台处理，用户身份由平台转发的可信请求头提供。
迁移到其他平台时，需要替换登录入口及身份验证实现，不能信任公网请求自行提供的身份头。
`PROMPT_ATLAS_OWNER_EMAIL` 由平台作为服务端环境变量配置，用于原有个人记录的兼容读取，不包含在仓库中。

将代码推送到 GitHub 不会自动完成国内托管部署或更改当前网站地址。

## 版本来源

同步自当前已发布 Sites 源码提交：`c70e39cc42c522df9ab37d8bd4be4a6ea5414ba8`
