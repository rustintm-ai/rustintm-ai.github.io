# 新账户设置指南 (rustintm-ai)

## 第一步：创建 GitHub Pages 仓库

1. 登录 GitHub 账户 `rustintm-ai`
2. 创建新仓库，名称必须是：**`rustintm-ai.github.io`**
   - 仓库必须是公开的（Public）
   - 可以初始化 README（可选）

## 第二步：添加 SSH 密钥到新账户

### 你的 SSH 公钥

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICjThRlz4zKip3vzz/sr7br/cXGYnd//Hl4DSa0b9LpA rustin_meng@163.com
```

### 添加步骤

1. 登录 GitHub 账户 `rustintm-ai`
2. 进入 Settings → SSH and GPG keys
3. 点击 "New SSH key"
4. 标题：`MacBook Pro`（或任意描述性名称）
5. 密钥类型：`Authentication Key`
6. 粘贴上面的公钥
7. 点击 "Add SSH key"

## 第三步：测试 SSH 连接

```bash
ssh -T git@github.com
```

如果成功，会看到：
```
Hi rustintm-ai! You've successfully authenticated, but GitHub does not provide shell access.
```

## 第四步：推送代码

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git push -u origin master
```

如果推送成功，你会看到类似：
```
Enumerating objects: X, done.
Counting objects: 100% (X/X), done.
Writing objects: 100% (X/X), done.
To github.com:rustintm-ai/rustintm-ai.github.io.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

## 第五步：启用 GitHub Pages

1. 进入仓库 `rustintm-ai/rustintm-ai.github.io`
2. 进入 Settings → Pages
3. 在 "Build and deployment" → "Source" 中选择：
   - `Deploy from a branch`
   - Branch: `master`（或 `main`，取决于你的分支名）
   - Folder: `/ (root)`
4. 点击 "Save"

## 第六步：验证部署

等待 1-2 分钟让 GitHub Pages 更新，然后测试：

### 测试 OmniFocus
```
https://rustintm-ai.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
```

### 测试 Obsidian
```
https://rustintm-ai.github.io/redirect/?app=Obsidian&uri=obsidian%3A%2F%2Fadvanced-uri%3Fvault%3DRustWise%26filepath%3DProjects%2FMyProject.md%26uid%3Dabc123
```

## 当前仓库配置

- **远程仓库**: `git@github.com:rustintm-ai/rustintm-ai.github.io.git`
- **本地分支**: `master`
- **文件结构**:
  ```
  rustintm-ai.github.io/
  └── redirect/
      └── index.html
  ```

## 如果 SSH 连接失败

### 方案 A：使用 GitHub CLI

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
gh auth login
git push -u origin master
```

### 方案 B：使用 HTTPS + 个人访问令牌

1. 在 GitHub 创建个人访问令牌：
   - Settings → Developer settings → Personal access tokens → Tokens (classic)
   - 生成新令牌，勾选 `repo` 权限

2. 推送：
```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git remote set-url origin https://github.com/rustintm-ai/rustintm-ai.github.io.git
git push -u origin master
# 用户名：rustintm-ai
# 密码：粘贴个人访问令牌
```

