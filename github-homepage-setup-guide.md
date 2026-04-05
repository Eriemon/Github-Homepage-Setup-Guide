# OpenClaw 个人主页配置指南

## 📋 项目概述

本指南帮助你使用 OpenClaw 快速搭建个人学术主页，部署到 GitHub Pages。

**技术栈**: HTML/CSS/JavaScript + GitHub Pages + 中英文双语支持

---

## ⚠️ 重要提示：配置文件使用说明

**不要直接修改 `config.ini.example`！**

正确做法：
```bash
# 1. 复制示例文件为实际配置文件
cp config.ini.example config.ini

# 2. 编辑实际配置文件
nano config.ini
# 或使用其他文本编辑器
```

**为什么？**
- `config.ini.example` 是模板文件，保持原样供参考
- `config.ini` 是你的个人配置，包含你的真实信息
- `config.ini` 应该被 `.gitignore` 忽略，不会提交到 Git

---

## 🔐 第一步：确认网站状态

### 检查是否已有 GitHub Pages 主页

1. 访问 https://github.com/你的用户名？tab=repositories
2. 查找是否有 `你的用户名.github.io` 仓库

### 根据情况选择流程

| 情况 | 操作 |
|------|------|
| **已有仓库** | 复制 `config.ini.example` → `config.ini`，设置 `already_has_site = true`，跳转到 [已有网站管理](#已有网站管理流程) |
| **没有仓库** | 复制 `config.ini.example` → `config.ini`，设置 `already_has_site = false`，继续 [新建网站流程](#新建网站流程) |

---

## 🔐 第二步：配置个人信息 (config.ini)

### 1. 复制配置文件

```bash
cp config.ini.example config.ini
```

### 2. 编辑配置文件

```bash
nano config.ini
```

### 3. 必填配置项

```ini
[github]
# GitHub 用户名（必须与你的 GitHub 账号一致）
username = zhangsan

# GitHub 邮箱
email = zhangsan@example.com

# Personal Access Token（重要！）
# 获取方式：https://github.com/settings/tokens
access_token = ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx

# 仓库名称（必须是 用户名.github.io 格式）
repo_name = zhangsan.github.io

[user]
# 中文姓名
name_cn = 张三

# 英文姓名
name_en = San Zhang

# 头衔/职位
title_cn = XX 大学 博士生
title_en = PhD Student @ XX University

# 邮箱
email = zhangsan@example.com

[links]
# 社交链接
github = https://github.com/zhangsan
orcid = https://orcid.org/XXXX-XXXX-XXXX-XXXX
google_scholar = https://scholar.google.com/citations?user=XXXXX
```

---

## 🛠️ 第三步：安装必要的技能

### 必装技能

```bash
# 1. GitHub CLI 技能（管理 GitHub 仓库）
npx skills add github/awesome-copilot@gh-cli -g -y

# 2. Git Commit 规范技能
npx skills add github/awesome-copilot@git-commit -g -y

# 3. 文档编写技能
npx skills add github/awesome-copilot@documentation-writer -g -y
```

### 可选技能

```bash
# 技术博客写作
npx skills add inferen-sh/skills@technical-blog-writing -g -y

# VitePress 静态站点
npx skills add sickn33/antigravity-awesome-skills@wiki-vitepress -g -y

# Vercel 部署
npx skills add vercel-labs/agent-skills@deploy-to-vercel -g -y
```

---

## 🔑 第四步：创建 GitHub Personal Access Token

### 1. 访问 Token 设置页面

访问：https://github.com/settings/tokens

### 2. 生成新 Token

1. 点击 **Generate new token (classic)**

2. 填写说明（Note）：如 "OpenClaw Homepage"

3. 设置过期时间（Expiration）：
   - 推荐：**90 天**
   - 或选择 **No expiration**（永不过期，安全性较低）

### 3. 选择权限（Select scopes）

✅ 勾选以下权限：
- **`repo`** - Full control of private repositories（完整仓库控制）

其他权限不需要勾选。

### 4. 生成并复制 Token

1. 点击 **Generate token**（绿色按钮）

2. **立即复制 Token**（格式：`ghp_xxxxxxxxxxxxxxxxxxxx`）

   ⚠️ **重要**：Token 只显示一次，关闭页面后无法再次查看！

3. 保存到安全位置（如密码管理器）

### 5. 配置到 config.ini

```bash
nano config.ini
```

在 `[github]` 部分填入 Token：
```ini
[github]
access_token = ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx  # 粘贴你的 Token
```

---

## 📁 第五步：新建网站流程

### 1. 在 GitHub 创建仓库

1. 访问 https://github.com/new

2. Repository name: `你的用户名.github.io`

3. Visibility: **Public**

4. **不要**勾选 "Add a README file"

5. 点击 **Create repository**

### 2. 本地初始化

```bash
cd ~/openclaw/workspace
git clone https://github.com/你的用户名/你的用户名.github.io.git
cd 你的用户名.github.io
```

首次推送时会提示输入用户名和密码：
- Username: 你的 GitHub 用户名
- Password: **粘贴你的 Personal Access Token**（不会显示）

### 3. 配置 Git

```bash
git config user.name "你的用户名"
git config user.email "你的邮箱@example.com"
```

---

## 📄 第六步：创建主页文件

### 基础项目结构

```
你的用户名.github.io/
├── index.html              # 主页面
├── style-academic.css     # 学术风格
├── style-natural.css      # 自然风格
├── script.js              # 交互脚本
├── README.md              # 项目说明
└── images/
    └── profile.jpeg       # 个人头像
```

### 核心功能清单

- [x] 中英文双语支持
- [x] 双风格切换（Academic/Natural）
- [x] 响应式设计
- [x] GitHub Pages 自动部署
- [x] 论文列表展示
- [x] 竞赛获奖展示（默认隐藏）
- [x] 新闻动态展示
- [x] 教育经历展示
- [x] 社交链接集成

---

## 🚀 第七步：推送部署

### 首次推送

```bash
cd ~/openclaw/workspace/你的用户名.github.io
git add -A
git commit -m "Initial commit: Personal homepage"
git branch -M main
git push -u origin main
```

推送时会提示：
```
Username for 'https://github.com': 你的用户名
Password for 'https://你的用户名@github.com': 
```
- Password 处**粘贴你的 Personal Access Token**（不会显示字符）

### 后续更新

```bash
# 方式一：手动推送
cd ~/openclaw/workspace/你的用户名.github.io
git add -A
git commit -m "描述性提交信息"
git push

# 方式二：使用自动推送脚本（需要先配置 Token）
~/github-push.sh ~/openclaw/workspace/你的用户名.github.io main
```

### 启用 GitHub Pages

1. 访问 https://github.com/你的用户名/你的用户名.github.io/settings/pages

2. **Source**: Deploy from a branch

3. **Branch**: main / (root)

4. 点击 **Save**

5. 等待 1-3 分钟部署完成

6. 访问：https://你的用户名.github.io

---

## 📋 已有网站管理流程

如果你已经有 `用户名.github.io` 仓库和主页：

### 1. 复制配置文件
```bash
cp config.ini.example config.ini
```

### 2. 配置现有仓库路径

编辑 `config.ini`：
```ini
[existing_site]
already_has_site = true
existing_repo_path = /path/to/your/repo
keep_existing_content = true
```

### 3. 克隆现有仓库（如果需要）

```bash
cd ~/openclaw/workspace
git clone https://github.com/你的用户名/你的用户名.github.io.git
cd 你的用户名.github.io
```

推送时使用 Token 认证。

### 4. 管理操作

```bash
# 拉取最新代码
git pull

# 进行修改（编辑文件、添加内容等）

# 提交并推送
git add -A
git commit -m "更新内容描述"
git push  # 使用 Token 认证
```

### 5. 常见管理任务

#### 添加论文
在 `index.html` 的 Publications 部分添加新条目

#### 更新个人信息
修改 `index.html` 中的对应部分

#### 添加新闻
在 `index.html` 的 News 部分添加

#### 检查部署状态
访问 https://github.com/你的用户名/你的用户名.github.io/actions

---

## 📝 内容管理

### 添加论文

```html
<article class="pub-card" data-year="2026">
    <div class="pub-year">2026</div>
    <div class="pub-content">
        <div class="pub-header">
            <h3 class="pub-title">论文标题</h3>
            <div class="pub-links">
                <a href="DOI 链接" class="pub-link">PDF</a>
                <a href="DOI 链接" class="pub-link">DOI</a>
            </div>
        </div>
        <p class="pub-authors"><strong>你的名字</strong>, 其他作者</p>
        <p class="pub-venue">期刊/会议名称，年份</p>
    </div>
</article>
```

### 添加竞赛获奖

```html
<div class="award-item">
    <div class="award-year">2026.01</div>
    <div class="award-content">
        <h3 class="award-title">竞赛名称</h3>
        <p class="award-level">奖项等级</p>
    </div>
</div>
```

### 添加新闻

```html
<div class="news-item">
    <div class="news-date">Jan 2026</div>
    <div class="news-content">
        <span class="news-badge">📢 类型</span>
        <span class="news-text">新闻内容</span>
    </div>
</div>
```

---

## ⚠️ 常见问题

### 1. GitHub Pages 不更新

**解决**:
- 强制刷新浏览器（Ctrl+Shift+R）
- 检查 GitHub Actions 部署状态
- 等待 3-5 分钟

### 2. Token 认证失败

**解决**:
- 检查 Token 是否正确
- 重新生成 Token：https://github.com/settings/tokens
- 确保勾选了 `repo` 权限

### 3. Token 过期

**解决**:
- 访问 https://github.com/settings/tokens
- 删除过期 Token
- 生成新 Token
- 更新 `config.ini` 中的 `access_token`

### 4. 语言切换不生效

**解决**:
- 清除浏览器缓存
- 检查浏览器控制台错误
- 强制刷新页面

### 5. 推送时提示认证失败

**解决**:
```bash
# 清除 Git 缓存的凭据
git config --global --unset credential.helper

# 重新推送，会提示输入用户名和 Token
git push
```

### 6. 找不到 config.ini 文件

**解决**:
```bash
# 确认你在正确的目录
pwd

# 复制配置文件
cp config.ini.example config.ini

# 检查文件是否存在
ls -la config.ini
```

---

## 🎯 快速检查清单

### 配置阶段
- [ ] **复制** `config.ini.example` → `config.ini`
- [ ] 确认是否已有网站
- [ ] 修改 `config.ini` 中的个人信息
- [ ] 创建 Personal Access Token
- [ ] 安装必要的技能

### 部署阶段（新建网站）
- [ ] 在 GitHub 创建仓库
- [ ] 克隆仓库到本地
- [ ] 配置 Git 用户信息
- [ ] 创建/修改主页文件
- [ ] 首次推送（使用 Token）
- [ ] 启用 GitHub Pages

### 管理阶段（已有网站）
- [ ] **复制** `config.ini.example` → `config.ini`
- [ ] 配置 `existing_site` 部分
- [ ] 克隆或定位现有仓库
- [ ] 拉取最新代码
- [ ] 进行修改
- [ ] 提交并推送（使用 Token）

### 维护阶段
- [ ] 定期更新内容
- [ ] 检查 Token 过期时间
- [ ] 备份重要文件

---

## 📞 获取帮助

### OpenClaw 文档
- 本地文档：`/opt/jvs-claw/base/lib/node_modules/openclaw/docs`
- 在线文档：https://docs.openclaw.ai

### 技能市场
- 查找技能：https://clawhub.ai/
- 技能 CLI: `npx skills find [关键词]`

### 社区支持
- Discord: https://discord.com/invite/clawd
- GitHub: https://github.com/openclaw/openclaw

---

*最后更新：2026-04-05*
