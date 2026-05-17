# Google OTP Decoder

本项目是一个纯静态前端工具，用于本地解密 Google Authenticator 导出的 migration 数据，并实时显示 OTP、有效期和可重新导入的二维码。

## 目录

- `index.html`: 主页面
- `assets/vendor/`: 本地静态依赖
- `wrangler.toml`: Cloudflare Workers 静态资源配置
- `src/worker.js`: Workers 入口，直接回源到静态资源

## 部署到 Cloudflare Pages

适用于零构建静态站点。

1. 安装依赖：

```bash
npm install
```

2. 登录 Cloudflare：

```bash
npx wrangler login
```

3. 首次部署到 Pages：

```bash
npx wrangler pages deploy .
```

如果你想指定项目名：

```bash
npx wrangler pages deploy . --project-name google-otp-decoder
```

## 部署到 Cloudflare Workers

当前项目同时提供了 Workers 静态资源配置。

1. 安装依赖：

```bash
npm install
```

2. 登录 Cloudflare：

```bash
npx wrangler login
```

3. 部署：

```bash
npx wrangler deploy
```

## 本地预览

Pages 模式：

```bash
npm run dev:pages
```

Workers 模式：

```bash
npm run dev:worker
```

## 说明

- 页面依赖都已本地化，不访问 CDN。
- `.assetsignore` 已排除 `decodeGoogleOTP/`、`old.html` 等无关内容，避免上传到 Cloudflare 静态资源目录。
