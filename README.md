# 🔐 密码保护的私密网站

这是一个使用 **StatiCrypt** (AES-256 加密) 保护的静态网站，托管在 GitHub Pages 上。

## 🌐 访问网站

**网站地址：** https://shiying-zhang.github.io/webpage/

## 🔑 演示密码

**密码：** `demo123`

## ✨ 为什么选择 StatiCrypt？

StatiCrypt 是一个强大的静态网页加密工具，具有以下优势：

- **🔒 真正的加密**：使用 AES-256-CBC 加密算法（军事级别）
- **🌐 浏览器端解密**：所有解密操作在你的浏览器中完成，无需服务器
- **💰 完全免费**：托管在 GitHub Pages，零成本
- **🎨 可定制界面**：自定义密码页面的样式和文案
- **💾 记住密码**：可选的"记住我"功能，30天免输入密码
- **🔐 安全可靠**：内容被真正加密，即使别人看到源码也无法解密

## 🚀 工作原理

1. 使用 StatiCrypt 将 `content.html` 加密成 `index.html`
2. 加密后的文件包含加密数据和密码验证界面
3. 用户访问网站时，输入密码
4. 密码正确后，内容在浏览器中实时解密并显示
5. **即使查看源代码，也只能看到加密后的乱码**

## 📝 如何更新内容？

### 步骤 1：编辑内容文件

编辑 `content.html` 文件，添加你想要展示的内容（HTML格式）。

### 步骤 2：重新加密

在终端运行以下命令：

```bash
# 使用你的密码替换 YOUR_PASSWORD
staticrypt content.html -p YOUR_PASSWORD --short --remember 30 \
  --template-title "私密内容访问" \
  --template-instructions "请输入密码以查看受保护的内容" \
  --template-color-primary "#667eea" \
  --template-color-secondary "#764ba2"

# 将加密后的文件移动到根目录
mv encrypted/content.html index.html
rmdir encrypted
```

### 步骤 3：推送到 GitHub

```bash
git add index.html
git commit -m "Update encrypted content"
git push origin main
```

### 步骤 4：完成

等待几分钟，GitHub Pages 会自动更新你的网站！

## 🛠️ 安装 StatiCrypt

如果你还没有安装 StatiCrypt：

```bash
npm install -g staticrypt
```

## 📋 文件说明

- `index.html` - 加密后的网页（这个会被推送到 GitHub）
- `content.html` - 原始内容文件（不应推送到公开仓库）
- `.staticrypt.json` - StatiCrypt 配置文件
- `encrypt-tool.html` - 旧的加密工具（已弃用）

## ⚠️ 重要提示

### 安全建议

- ✅ 使用强密码（建议 16 位以上，包含大小写字母、数字、符号）
- ✅ `content.html` 应该添加到 `.gitignore`，不要推送到公开仓库
- ✅ 定期更换密码并重新加密内容
- ✅ 不要在不安全的环境中输入密码
- ✅ GitHub Pages 默认使用 HTTPS，确保启用

### Git忽略原始内容

建议将 `content.html` 添加到 `.gitignore`：

```bash
echo "content.html" >> .gitignore
```

这样原始内容就不会被推送到 GitHub，只有加密后的 `index.html` 会被公开。

## 🔐 加密等级说明

StatiCrypt 使用的加密规格：

- **加密算法**：AES-256-CBC
- **密钥派生**：PBKDF2-SHA256
- **迭代次数**：600,000 次（符合 OWASP 安全标准）
- **盐值管理**：自动生成并保存在 `.staticrypt.json`

这意味着即使是最先进的计算机，在没有密码的情况下，也需要数千年才能暴力破解内容。

## 📚 更多信息

- [StatiCrypt GitHub 项目](https://github.com/robinmoisson/staticrypt)
- [StatiCrypt 在线工具](https://robinmoisson.github.io/staticrypt/)

## 📄 许可证

本项目使用 MIT 许可证。

---

**使用愉快！🎉** 如有问题，请查看 [StatiCrypt 文档](https://github.com/robinmoisson/staticrypt#readme)。
