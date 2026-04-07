# API Design Rules

路径: `src/api/**`, `**/routes/**`

## 请求处理

- 所有外部输入必须验证（使用 zod 或类似库）
- 错误响应统一格式：`{ error: { code: string, message: string } }`
- 成功响应统一格式：`{ data: T }`

## 端点设计

- RESTful 命名：资源用名词，动作用动词
- 版本化：`/api/v1/...`
- 分页：`?page=1&limit=20`

## 安全

- 所有端点需要认证（除了 public 白名单）
- 敏感操作需要二次验证
