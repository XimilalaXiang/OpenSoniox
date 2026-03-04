# 快速入门指南

## 第一步：获取 Soniox API Key

1. 访问 [Soniox Console](https://soniox.com/console)
2. 创建账户或登录
3. 创建新项目（如果没有）
4. 在项目中创建 API Key
5. 复制 API Key 备用

## 第二步：部署应用

### 使用一键脚本（推荐）

```bash
# 克隆项目
git clone https://github.com/XimilalaXiang/OpenSoniox.git
cd OpenSoniox

# 首次配置环境变量
cp .env.example .env
# 编辑 .env，至少设置 SECRET_KEY（ACCESS_PASSWORD 默认 opensoniox123，建议修改）

# 运行启动脚本（自动拉取镜像并启动）
./start.sh
```

### 或使用 Docker Compose

```bash
# 首次使用先准备 .env
cp .env.example .env
# 编辑 .env，至少设置 SECRET_KEY（ACCESS_PASSWORD 默认 opensoniox123，建议修改）

# 拉取预构建镜像
docker compose pull

# 启动服务
docker compose up -d

# 查看日志
docker compose logs -f
```

## 第三步：配置应用

1. 打开浏览器访问 `http://localhost:17881`
2. 输入访问密码（默认 `opensoniox123`；若 `.env` 里留空 ACCESS_PASSWORD，则会先进入初始化密码页面）
3. 点击右上角"配置"按钮
4. 输入你的 Soniox API Key
5. （可选）配置 OpenAI API 用于 AI 助手功能
6. 点击"保存配置"

## 第四步：开始使用

1. 点击"开始录音"按钮
2. 允许浏览器访问麦克风
3. 开始说话，转录内容会实时显示
4. 点击"停止录音"结束转录

## 第五步：使用 AI 助手（可选）

如果配置了 OpenAI API：

1. 完成录音后，在 AI 助手面板
2. 点击快捷操作按钮（总结、提取待办等）
3. 或输入自定义问题

## 常见问题

### Q: 无法访问麦克风
A: 确保：
- 浏览器有麦克风权限
- 使用 HTTPS 或 localhost
- 系统麦克风正常工作

### Q: 连接失败
A: 检查：
- Docker 容器是否正常运行：`docker ps`
- 查看后端日志：`docker logs opensoniox-backend`
- 防火墙是否允许端口访问

### Q: 如何修改访问密码
A: 修改 `.env` 里的 `ACCESS_PASSWORD`，然后重启容器：
- `docker compose up -d`
- 或 `docker compose -f docker-compose.dev.yml up -d`

### Q: Soniox API 报错
A: 确认：
- API Key 是否正确
- 账户是否有可用配额
- 网络连接是否正常

## 获取帮助

- 查看完整文档：[README.md](./README.md)
- 查看 Soniox 文档：https://soniox.com/docs
- 提交 Issue：[GitHub Issues](https://github.com/XimilalaXiang/OpenSoniox/issues)

## 下一步

- 尝试不同的转录场景
- 探索 AI 助手的各种功能
- 查看高级配置选项
- 自定义 UI 主题和样式
