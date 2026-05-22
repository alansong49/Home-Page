# 部署到 Vercel 指南

## 前置准备

1. 创建一个 GitHub 仓库，将此项目推送到仓库
2. 在 Vercel 上注册账号并连接 GitHub
3. 创建一个 GitHub Personal Access Token (PAT)

## 部署步骤

### 1. 准备项目

确保项目结构包含以下文件：
```
Home_Page/
├── app.py
├── requirements.txt
├── vercel.json
├── .gitignore
├── templates/
│   └── index.html
├── default/
│   ├── default_config.json
│   └── background.jpg
└── Introduction.md
```

### 2. 推送到 GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

### 3. 在 Vercel 上部署

1. 访问 https://vercel.com/new
2. 选择你的 GitHub 仓库
3. 配置环境变量：
   - 点击 "Environment Variables"
   - 添加以下变量：
     - `GITHUB_URL`: 你的 GitHub 主页 URL（例如：https://github.com/alansong49）
     - `GITHUB_TOKEN`: 你的 GitHub Personal Access Token
     - `NAME`: 你的名字（可选）
     - `BIO`: 你的个人简介（可选）
4. 点击 "Deploy" 开始部署

### 4. 配置自定义域名（可选）

部署成功后，在 Vercel 项目设置中可以配置自定义域名。

## 环境变量说明

| 变量名 | 说明 | 是否必需 |
|--------|------|----------|
| `GITHUB_URL` | 你的 GitHub 主页链接 | 是 |
| `GITHUB_TOKEN` | GitHub Personal Access Token | 是 |
| `NAME` | 显示的名字 | 否 |
| `BIO` | 个人简介 | 否 |
| `DARK_MODE` | 深色模式设置 (`auto`, `light`, `dark`) | 否 |

## 创建 GitHub Personal Access Token

1. 访问 https://github.com/settings/tokens
2. 点击 "Generate new token (classic)"
3. 选择 `repo` 权限（或只读权限即可）
4. 生成并复制令牌

## 本地开发

本地开发时，可以使用 `config.json` 文件配置：

```bash
# 复制默认配置
cp default/default_config.json config.json

# 编辑配置
# 修改 config.json 中的内容

# 运行应用
python app.py
```

## 注意事项

- 不要将 `config.json` 或 `github_token.txt` 提交到仓库（已在 .gitignore 中）
- Vercel 部署时使用环境变量配置，更安全
- GitHub Token 需要定期更新