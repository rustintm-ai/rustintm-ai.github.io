# 添加新 SSH 密钥到 GitHub

## ✅ 新密钥已生成

已为你生成新的 SSH 密钥对：
- **私钥**: `~/.ssh/id_ed25519_rustintm_ai`
- **公钥**: `~/.ssh/id_ed25519_rustintm_ai.pub`

## 📋 你的新 SSH 公钥

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIAUOpa3nNOP1+BtKMUHm2ZpLoNQV36+row4cXS64vMej rustintm-ai@github
```

**✅ 公钥已自动复制到剪贴板！**

## 🔧 添加步骤

### 1. 登录 GitHub

访问 https://github.com/settings/keys 并登录账户 `rustintm-ai`

### 2. 添加 SSH 密钥

1. 点击 **"New SSH key"** 按钮
2. **Title（标题）**: 输入描述性名称，如 `MacBook Pro - rustintm-ai`
3. **Key type（密钥类型）**: 选择 `Authentication Key`
4. **Key（密钥）**: 粘贴上面的公钥（已复制到剪贴板，直接 Cmd+V）
5. 点击 **"Add SSH key"**

### 3. 验证添加

运行以下命令测试连接：

```bash
ssh -T git@github.com
```

如果成功，你会看到：
```
Hi rustintm-ai! You've successfully authenticated, but GitHub does not provide shell access.
```

## 🚀 推送代码

SSH 密钥添加成功后，就可以推送代码了：

```bash
cd /Users/one/MySpace/50_Development/lifeDNA/projects/github-pages-redirect
git push -u origin master
```

## 📝 SSH 配置已更新

你的 `~/.ssh/config` 已更新，GitHub 现在会使用新密钥：
- 密钥文件：`~/.ssh/id_ed25519_rustintm_ai`
- 标识：`rustintm-ai@github`

## ⚠️ 如果使用 1Password SSH Agent

如果你的 SSH 配置使用 1Password 作为 IdentityAgent，你可能需要：

1. 打开 1Password 应用
2. 将新密钥添加到 1Password 的 SSH 密钥管理
3. 或者临时禁用 1Password agent，直接使用系统 ssh-agent

临时禁用 1Password agent（仅用于测试）：
```bash
# 备份原配置
cp ~/.ssh/config ~/.ssh/config.backup

# 临时注释掉 IdentityAgent 行
sed -i '' 's/IdentityAgent/#IdentityAgent/' ~/.ssh/config

# 测试连接
ssh -T git@github.com

# 恢复配置（如果需要）
# mv ~/.ssh/config.backup ~/.ssh/config
```

