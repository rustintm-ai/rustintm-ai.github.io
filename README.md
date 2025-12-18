# GitHub Pages URL Scheme 重定向服务

这个项目提供了一个 GitHub Pages 重定向服务，用于将 HTTP 链接转换为 App 的 URL Scheme（如 `omnifocus://` 或 `obsidian://`）。

## 功能说明

当你点击类似这样的链接时：
```
https://rustinmiracle.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
```

页面会自动提取 `uri` 参数，解码后跳转到对应的 App URL Scheme。

## 部署步骤

### 1. 文件结构

将 `redirect/` 文件夹及其内容推送到你的 GitHub Pages 仓库（`rustinmiracle.github.io`）的根目录：

```
rustinmiracle.github.io/
└── redirect/
    └── index.html
```

### 2. 启用 GitHub Pages

1. 进入仓库的 Settings
2. 找到 Pages 设置
3. 在 "Build and deployment" -> "Source" 中选择：
   - `Deploy from a branch`
   - Branch: `main` (或你的主分支)
   - Folder: `/ (root)`

### 3. 等待部署

GitHub Pages 通常会在几分钟内更新。部署完成后，你的链接就会生效。

## 使用方法

### 生成重定向链接

将 App 的 URL Scheme 进行 URL 编码后，拼接到重定向链接后面：

**示例：OmniFocus 任务链接**

1. 原始 URL Scheme：
   ```
   omnifocus:///task/i5uauc17Jd4
   ```

2. URL 编码后：
   ```
   omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
   ```

3. 最终重定向链接：
   ```
   https://rustinmiracle.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
   ```

**示例：Obsidian 笔记链接**

1. 原始 URL Scheme：
   ```
   obsidian://open?vault=MyVault&file=Note
   ```

2. URL 编码后：
   ```
   obsidian%3A%2F%2Fopen%3Fvault%3DMyVault%26file%3DNote
   ```

3. 最终重定向链接：
   ```
   https://rustinmiracle.github.io/redirect/?app=Obsidian&uri=obsidian%3A%2F%2Fopen%3Fvault%3DMyVault%26file%3DNote
   ```

### 使用 JavaScript 生成链接

```javascript
function createRedirectLink(appName, urlScheme) {
    const encodedUri = encodeURIComponent(urlScheme);
    return `https://rustinmiracle.github.io/redirect/?app=${appName}&uri=${encodedUri}`;
}

// 示例
const omnifocusLink = createRedirectLink('omnifocus', 'omnifocus:///task/i5uauc17Jd4');
// 结果: https://rustinmiracle.github.io/redirect/?app=omnifocus&uri=omnifocus%3A%2F%2F%2Ftask%2Fi5uauc17Jd4
```

### 使用 iOS/macOS 快捷指令 (Shortcuts)

你可以创建一个快捷指令来生成这种链接：

1. **输入**：接受文本或 URL（作为输入）
2. **URL 编码**：对输入进行 `URL 编码` (URL Encode)
3. **组合文本**：
   - 文本内容：`https://rustinmiracle.github.io/redirect/?app=App&uri=`
   - 后面接上：`[编码后的 URL]`
4. **复制到剪贴板**

## 工作原理

1. 用户点击重定向链接
2. 浏览器加载 `index.html`
3. JavaScript 读取 URL 中的 `uri` 参数
4. 解码 URI（将 `%3A` 变回 `:` 等）
5. 自动跳转到解码后的 URL Scheme
6. 操作系统识别 URL Scheme 并打开对应的 App

## 注意事项

- 确保目标 App 已安装并支持对应的 URL Scheme
- URL 编码是必需的，因为 URL Scheme 中包含特殊字符（如 `:`、`/`、`?` 等）
- 如果自动跳转失败，页面会显示一个手动链接供用户点击

