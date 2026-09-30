# Cloudflare 导航页

一个单文件 Cloudflare Worker 个人导航页，基于 [Card-Tab](https://github.com/hmhm2022/Card-Tab) 二次开发。把全部前端 + 后端打进一个 `worker.js`，部署即用。

在线演示：https://card-tab.3838669.workers.dev

## 功能

- **单文件部署**：一个 `worker.js` 搞定，无需构建
- **链接管理**：密码登录后可增删改分类、卡片、私密链接，数据存 Cloudflare KV（自动备份）
- **深色 / 浅色主题**：默认深色，一键切换
- **每日壁纸**：Wallhaven 真实壁纸 API，每小时自动换一张（暗黑太空风），右下角按钮可手动切换
- **天气小组件**：和风天气代理，支持城市搜索切换
- **多搜索引擎**：百度 / 必应 / 谷歌 / DuckDuckGo，下拉切换
- **书签搜索**：一键搜索自己收藏的链接
- **移动端优化**：两列卡片、分类横滑、触控目标放大、iOS 兼容
- **分类收起**：收起状态本地持久化

## 部署

1. Cloudflare Dashboard → Workers & Pages → 创建 Worker，把 `worker.js` 内容粘贴进去
2. 创建 KV 命名空间，绑定变量名 `CARD_ORDER`
3. 添加环境变量（Variables）：
   - `ADMIN_PASSWORD`：管理密码（必填）
   - `WEATHER_API_HOST`：和风天气 API 域名，如 `api.qweather.com`
   - `WEATHER_API_KEY`：和风天气 Key（不填则天气功能不可用）
4. 保存并部署，绑定自定义域名即可

> 免费计划下个人使用量极小，一般不会产生费用，以 Cloudflare 实际账单为准。

## 本地开发

直接改 `worker.js` 里的 HTML/CSS/JS 即可。注意内联 `<script>` 在模板字符串里，`node --check worker.js` 只能检查外层，改完建议实际部署验证。

## License

MIT
