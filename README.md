# 京东联盟验证站点（GitHub Pages）

用途：为「钱包增肥」返利小程序的京东联盟「网站媒体」提供域名验证，从而拿到
AppKey / SecretKey / siteID，让 H5 预览能真实转链、查券、查佣金。

## 你的固定地址
- GitHub 用户名：`qianbaozengfei`
- Pages 根域名：`https://qianbaozengfei.github.io`

## 一、在 GitHub 建仓库（只做一次）
1. 登录 https://github.com
2. 右上角 「＋」→ New repository
3. Repository name 必须精确填：**`qianbaozengfei.github.io`**
   （这是用户/组织 Pages，仓库名即根域名，京东验证最省事）
4. 设为 **Public**（私有仓库 Pages 旧版需付费，公开免费）
5. 点 Create repository

## 二、把本目录文件推上去
本目录已含：
- `index.html` —— 占位首页（让站点可访问）
- `jd_verify_placeholder.txt` —— 占位说明，稍后替换

方式 A（让助手帮你推，需 GitHub Personal Access Token）：
  生成 PAT（勾 repo 全部权限）→ 把 token 发我 → 我执行 git 推送。

方式 B（自己推，任选其一）：
  - 网页上传：进仓库 → Add file → 把 `index.html` 和验证文件拖上去 → Commit。
  - 或用 GitHub Desktop / git 命令行推送本目录内容到仓库根。

## 三、开启 GitHub Pages
1. 仓库 → Settings → Pages
2. Source 选 **Deploy from a branch**
3. Branch 选 **main**（或 master），目录 **/ (root)** → Save
4. 等 1~2 分钟，浏览器访问 `https://qianbaozengfei.github.io` 应能看到占位页。

## 四、去京东联盟填写并验证
1. 登录 union.jd.com → 我的推广 → 推广管理 → **网站管理** → 创建网站
2. 网站名称：`钱包增肥省钱助手`
3. 网站域名：`qianbaozengfei.github.io`（不带 https://）
4. 网站简介：`提供商品优惠查询与购物返利积分服务，帮助用户发现高性价比商品、养成省钱习惯。`
5. 提交后，京东会给出验证文件名（形如 `jd_verify_8f3a.txt`）和文件内容
6. **把京东给的验证文件（保持原文件名）放到本目录根下，覆盖 `jd_verify_placeholder.txt` 并重新推送**
7. 京东自动检测到 `https://qianbaozengfei.github.io/jd_verify_8f3a.txt` → 验证通过
8. 在媒体详情「查看」拿到 **AppKey / SecretKey / siteID**
9. 推广位管理 → 新建推广位 → 拿到 **positionId**

## 五、把密钥接进项目
把以下 4 个值发给我（或自己填进 `返利小程序/.env`）：
- JD_APP_KEY
- JD_APP_SECRET
- JD_SITE_ID
- JD_POSITION_ID

填好后重启服务，京东链接转链即走真实接口（返回 source:"jd"）。
