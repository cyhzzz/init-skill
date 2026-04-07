# Security Rules

路径: `**/*`

## 敏感文件保护

- 禁止读取 `.env`, `.env.*`, `credentials.*`, `secrets.*`
- 禁止写入 `*.pem`, `*.key`, `*.p12`

## 命令限制

- 禁止 `rm -rf /`, `rm -rf ~`, `rm -rf .`
- 禁止 `sudo` 命令
- 禁止 `git push --force`, `git push -f`

## 外部请求

- 禁止向未知域名发送数据
- API Key 只能通过环境变量读取
