# GitHub 个人主页配置指南 🚀

本文件夹包含使用 OpenClaw 搭建个人学术主页的完整配置指南。

---

## 📁 文件清单

| 文件 | 说明 |
|------|------|
| `README.md` | 本文件，快速入门指南 |
| `github-homepage-setup-guide.md` | **完整配置指南**（主要文档） |
| `config.ini.example` | 配置文件模板（**不要直接修改**） |
| `github-homepage-management.md` | 管理经验总结 |

---

## ⚠️ 重要提示

**不要直接修改 `config.ini.example`！**

正确做法：
```bash
cp config.ini.example config.ini
nano config.ini  # 编辑这个文件
```

---

## 🚀 快速开始

### 第一步：确认是否已有 GitHub Pages 主页

**访问**: https://github.com/你的用户名？tab=repositories

**检查**: 是否有 `你的用户名.github.io` 仓库？

#### 情况 A：已有仓库 ✅
```bash
# 1. 复制配置文件
cp config.ini.example config.ini

# 2. 编辑配置
nano config.ini
```

修改：
```ini
[existing_site]
already_has_site = true
existing_repo_path = /path/to/your/repo  # 仓库路径
keep_existing_content = true  # 保留现有内容
```
→ 跳转到 **已有网站管理流程**

#### 情况 B：没有仓库 ❌
```bash
# 1. 复制配置文件
cp config.ini.example config.ini

# 2. 编辑配置
nano config.ini
```

修改：
```ini
[existing_site]
already_has_site = false
```
→ 跳转到 **新建网站流程**

---

## 📋 新建网站流程

### 1. 复制配置文件
```bash
cd ~/Downloads/Github-Homepage-Setup-Guide
cp config.ini.example config.ini
```

### 2. 编辑配置
```bash
nano config.ini
```

**必填项**：
```ini
[github]
username = 你的 GitHub 用户名
email = 你的邮箱
access_token = ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx  # GitHub Token

[user]
name_cn = 你的中文姓名
name_en = Your English Name
email = 你的邮箱

[links]
github = https://github.com/你的用户名
orcid = 你的 ORCID 链接
google_scholar = 你的 Google Scholar 链接
```

### 3. 安装技能
```bash
npx skills add github/awesome-copilot@gh-cli -g -y
npx skills add github/awesome-copilot@git-commit -g -y
npx skills add github/awesome-copilot@documentation-writer -g -y
```

### 4. 创建 GitHub Token

1. 访问 https://github.com/settings/tokens

2. 点击 **Generate new token (classic)**

3. 填写说明（Note）：如 "OpenClaw Homepage"

4. 设置过期时间（建议 90 天）

5. 选择权限：勾选 **`repo`**（完整仓库控制）

6. 点击 **Generate token**

7. **复制 Token**（只显示一次，格式：`ghp_xxxxxxxxxxxx`）

8. 粘贴到 `config.ini` 的 `access_token` 项

### 5. 创建仓库
1. 访问 https://github.com/new
2. Repository name: `你的用户名.github.io`
3. Visibility: Public
4. 不要勾选 "Add a README file"
5. 点击 Create repository

### 6. 查看详细指南
```bash
cat github-homepage-setup-guide.md
```

---

## 📋 已有网站管理流程

如果你已经有 `用户名.github.io` 仓库和主页：

### 1. 复制配置文件
```bash
cd ~/Downloads/Github-Homepage-Setup-Guide
cp config.ini.example config.ini
```

### 2. 编辑配置
```bash
nano config.ini
```

**修改以下配置**：
```ini
[github]
access_token = ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx  # 你的 Token

[existing_site]
already_has_site = true
existing_repo_path = /path/to/your/repo  # 填写你的仓库路径
keep_existing_content = true  # 保留现有内容
```

### 3. 安装技能
```bash
npx skills add github/awesome-copilot@gh-cli -g -y
npx skills add github/awesome-copilot@git-commit -g -y
```

### 4. 管理操作
```bash
cd /path/to/your/repo
git pull  # 拉取最新代码
# 进行修改...
git add -A
git commit -m "更新内容"
git push
```

---

## 📖 详细文档

| 文档 | 用途 |
|------|------|
| `github-homepage-setup-guide.md` | 完整的创建和部署指南 |
| `github-homepage-management.md` | 实际管理经验和最佳实践 |

---

## 📞 获取帮助

- OpenClaw 文档：https://docs.openclaw.ai
- 技能市场：https://clawhub.ai/
- 社区支持：https://discord.com/invite/clawd

---

*最后更新：2026-04-05*
