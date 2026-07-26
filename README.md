# 8-Bit 音乐工房

纯前端的复古游戏机风格音乐制作小工具，只有一个 `index.html` 文件，不需要任何构建工具、依赖或后端。

## 部署到 GitHub + Cloudflare Pages

### 第一步：上传到 GitHub

1. 在 GitHub 上新建一个仓库（Public 或 Private 都可以），例如叫 `chiptune-studio`。
2. 把这个文件夹里的 `index.html`（和这份 `README.md`）上传到仓库根目录：
   - 网页端：打开仓库页面 → `Add file` → `Upload files` → 拖入 `index.html` → `Commit changes`。
   - 或者用命令行：
     ```bash
     git init
     git add index.html README.md
     git commit -m "8-bit 音乐工房"
     git branch -M main
     git remote add origin https://github.com/你的用户名/chiptune-studio.git
     git push -u origin main
     ```

### 第二步：在 Cloudflare Pages 部署

1. 登录 Cloudflare Dashboard → 左侧选择 **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**。
2. 授权并选择刚才的 GitHub 仓库。
3. 构建设置全部留空/默认即可（这是纯静态文件，没有构建步骤）：
   - Framework preset：`None`
   - Build command：留空
   - Build output directory：`/`（仓库根目录，因为 `index.html` 就放在根目录）
4. 点击 **Save and Deploy**，等它跑完，会给一个类似 `https://chiptune-studio-xxx.pages.dev` 的地址，打开即可使用。

之后每次你往 GitHub 仓库 push 新代码，Cloudflare Pages 会自动重新部署，不需要再手动操作。

### 也可以直接用 GitHub Pages（备选，不用 Cloudflare）

仓库 → Settings → Pages → Source 选 `main` 分支 / `root` 目录 → Save，几分钟后会有一个 `https://你的用户名.github.io/chiptune-studio/` 的地址。

## 文件说明

- `index.html`：整个应用（HTML + CSS + JS 全部内联在一个文件里），用 Web Audio API 实时合成声音，没有用到任何外部资源或 CDN，所以部署非常简单，纯静态托管即可。
