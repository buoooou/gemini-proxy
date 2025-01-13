# Gemini Proxy Worker

这是一个利用Cloudflare Workers作为中转的Gemini代理。

## 功能

- 代理Gemini请求
- 支持多种API端点
- 处理跨域请求

## 文件结构

- `worker.js`: 主Worker脚本，包含代理逻辑

## 部署步骤

1. 确保你已经安装了Cloudflare Wrangler CLI。
2. 登录到Cloudflare账户：
    ```sh
    wrangler login
    ```
3. 初始化一个新的Cloudflare Workers项目：
    ```sh
    wrangler init
    ```
4. 将`worker.js`文件复制到项目目录中。
5. 在`wrangler.toml`文件中配置你的项目：
    ```toml
    name = "gemini-proxy-worker"
    type = "javascript"
    account_id = "你的Cloudflare账户ID"
    workers_dev = true
    ```
6. 部署你的Worker：
    ```sh
    wrangler publish
    ```

## 使用方法

部署完成后，你可以通过以下端点访问你的Gemini代理：

- `/chat/completions`
- `/embeddings`
- `/models`

## 示例请求

```sh
curl -X POST https://your-worker-url/chat/completions -H "Authorization: Bearer YOUR_API_KEY" -d '{
  "model": "gemini-1.5-pro-latest",
  "messages": [{"role": "user", "content": "Hello, world!"}]
}'