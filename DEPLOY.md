# 部署指南

## 当前状态

- ✅ 文件已准备就绪：`redirect/index.html` 和 `README.md`
- ✅ 已提交到本地 Git 仓库
- ⚠️ 需要推送到 GitHub（需要身份验证）

## 推送选项

### 选项 1：使用 GitHub CLI（推荐）

如果你安装了 GitHub CLI：

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
gh auth login
git push -u origin master
```

### 选项 2：启用 1Password SSH Agent

你的 SSH 配置使用了 1Password 作为 IdentityAgent。需要：

1. 打开 1Password 应用
2. 进入 Settings → Developer
3. 启用 "Use the SSH agent"
4. 确保你的 SSH 密钥已添加到 1Password

然后重试推送：

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git push -u origin master
```

### 选项 3：使用 HTTPS + 个人访问令牌

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git remote set-url origin https://github.com/rustintm-ai/rustintm-ai.github.io.git
git push -u origin master
# 用户名：rustintm-ai
# 密码：粘贴个人访问令牌（在 GitHub Settings → Developer settings → Personal access tokens 创建）
```

### 选项 4：手动添加 SSH 密钥到 ssh-agent

```bash
# 启动 ssh-agent
eval "$(ssh-agent -s)"

# 添加密钥（需要输入密钥密码）
ssh-add ~/.ssh/id_ed25519

# 测试连接
ssh -T git@github.com

# 推送
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git push -u origin master
```

## 验证部署

推送成功后，等待几分钟让 GitHub Pages 更新，然后测试：

### 测试 OmniFocus 链接
```
https://rustintm-ai.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
```

### 测试 Obsidian 链接
```
https://rustintm-ai.github.io/redirect/?app=Obsidian&uri=obsidian%3A%2F%2Fadvanced-uri%3Fvault%3DRustWise%26filepath%3DProjects%2FMyProject.md%26uid%3Dabc123
```

## 你的 SSH 公钥

如果需要将 SSH 密钥添加到 GitHub：

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICjThRlz4zKip3vzz/sr7br/cXGYnd//Hl4DSa0b9LpA rustin_meng@163.com
```

在 GitHub Settings → SSH and GPG keys → New SSH key 中添加此公钥。

