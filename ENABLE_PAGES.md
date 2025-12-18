# 启用 GitHub Pages

## ✅ 代码已成功推送！

你的代码已经推送到：`rustintm-ai/rustintm-ai.github.io`

## 📋 下一步：启用 GitHub Pages

### 1. 进入仓库设置

访问：https://github.com/rustintm-ai/rustintm-ai.github.io/settings/pages

### 2. 配置 Pages 设置

在 "Build and deployment" 部分：

1. **Source（源）**: 选择 `Deploy from a branch`
2. **Branch（分支）**: 
   - 选择 `master`
   - Folder（文件夹）: `/ (root)`
3. 点击 **"Save"** 按钮

### 3. 等待部署

GitHub Pages 通常会在 1-2 分钟内完成部署。你可以：
- 在仓库的 Settings → Pages 页面查看部署状态
- 看到绿色的 ✅ 表示部署成功

## 🧪 测试重定向服务

部署完成后（等待 1-2 分钟），测试以下链接：

### 测试 OmniFocus 链接
```
https://rustintm-ai.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
```

### 测试 Obsidian 链接
```
https://rustintm-ai.github.io/redirect/?app=Obsidian&uri=obsidian%3A%2F%2Fadvanced-uri%3Fvault%3DRustWise%26filepath%3DProjects%2FMyProject.md%26uid%3Dabc123
```

### 测试页面本身
```
https://rustintm-ai.github.io/redirect/
```

如果页面显示 "错误：链接中没有包含目标 URI"，说明部署成功！

## 📝 使用示例

### JavaScript 函数生成链接

```javascript
function createRedirectLink(appName, urlScheme) {
    const encodedUri = encodeURIComponent(urlScheme);
    return `https://rustintm-ai.github.io/redirect/?app=${appName}&uri=${encodedUri}`;
}

// OmniFocus 示例
const ofLink = createRedirectLink('omnifocus', 'omnifocus:///task/i5uauc17Jd4');

// Obsidian 示例
const obsLink = createRedirectLink('Obsidian', 'obsidian://advanced-uri?vault=RustWise&filepath=Projects/MyProject.md&uid=abc123');
```

## 🎉 完成！

一旦 GitHub Pages 部署完成，你的重定向服务就可以使用了！

