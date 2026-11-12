# JLL OKX EMA 自动交易系统部署指南

这是一个基于 GitHub Pages 发布的静态说明页，介绍 JLL OKX EMA 策略机器人的环境准备、配置、试运行与风险检查流程。

- 在线页面：<https://ftwbitcoin911.github.io/jll-okx-ema-bot/>
- 页面源文件：[`index.html`](./index.html)

## 项目结构

```text
.
├── index.html
├── README.md
└── .github/
    └── workflows/
        └── pages.yml
```

## 本地预览

需要安装 Python 3。在仓库根目录运行：

```bash
python3 -m http.server 8000
```

浏览器打开 <http://localhost:8000/> 即可预览。按 `Ctrl+C` 停止本地服务器。

## 发布到 GitHub Pages

仓库使用 GitHub Actions 发布根目录中的静态文件。首次配置时：

1. 打开仓库 **Settings → Pages**。
2. 在 **Build and deployment** 的 **Source** 中选择 **GitHub Actions**。
3. 将 `index.html` 和 `.github/workflows/pages.yml` 推送到 `main` 分支，或在 **Actions** 中手动运行 Pages 工作流。
4. 在 Actions 页面确认部署工作流成功。首次发布可能需要几分钟。
5. 访问 <https://ftwbitcoin911.github.io/jll-okx-ema-bot/>。若页面未更新，稍后刷新或清除浏览器缓存。

之后每次更新 `main` 分支都会触发自动部署。也可以在 **Actions** 页面使用 `workflow_dispatch` 手动触发。

## 安全与风险提示

- 本项目页面是部署说明，不是交易建议，也不保证策略收益或运行正确性。
- 自动交易可能造成全部或部分资金损失；先进行代码审查和模拟环境测试，不要仅凭页面说明直接启用实盘。
- 不要把 OKX API 密钥、Secret、Passphrase、Telegram Bot Token 或其他凭据提交到 GitHub。使用最小必要权限，禁止提现权限，并配置 IP 白名单。
- 对任何实盘交易，都应先独立核实交易所当前 API 参数、合约规则、账户模式、仓位与风控设置，并保留可验证的人工停机手段。
- 页面中的示例参数和操作提示可能过时。部署前请根据机器人实际代码与交易所官方文档复核；不要在未确认程序行为时用真实仓位做“自动平仓”测试。

## 维护

修改 `index.html` 后提交到 `main`，等待 Pages workflow 完成。若部署失败，请查看仓库 **Actions** 中对应运行的日志；若尚未启用 Pages，请按上面的首次配置步骤设置。