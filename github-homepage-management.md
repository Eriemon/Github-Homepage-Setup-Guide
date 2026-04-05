# GitHub 个人主页管理经验总结

## 📋 项目概述

**项目名称**: 用户名.github.io  
**访问地址**: https://用户名.github.io  
**技术栈**: 静态 HTML/CSS/JavaScript + GitHub Pages + 中英文双语支持

---

## 🛠️ 技术栈

- **框架**: 静态 HTML/CSS/JavaScript（无构建工具）
- **样式**: 双风格支持（Academic/Natural）
- **部署**: GitHub Pages
- **认证**: Personal Access Token（推荐）
- **语言**: 中英文双语支持

---

## 📁 项目结构

```
用户名.github.io/
├── index.html              # 主页面（含中英文翻译）
├── style-academic.css     # 学术风格样式
├── style-natural.css      # 自然风格样式
├── script.js              # 交互脚本（主题/风格/语言切换）
├── README.md              # 项目说明
└── images/
    ├── profile.jpeg       # 个人头像
    └── xxx.png            # 其他图片
```

---

## 🚀 部署流程

### 新建网站

1. **创建 Token**: https://github.com/settings/tokens
2. **创建仓库**: GitHub 创建 `用户名.github.io`
3. **本地克隆**: `git clone https://github.com/用户名/用户名.github.io.git`
4. **配置 Git**: `git config user.name "用户名"` 和 `git config user.email "邮箱"`
5. **推送部署**: `git add -A` → `git commit -m "描述"` → `git push`（使用 Token）
6. **启用 Pages**: Settings → Pages → Deploy from branch → main

**部署时间**: 通常 1-3 分钟

### 已有网站管理

1. **定位仓库**: 找到现有仓库路径
2. **拉取代码**: `git pull`
3. **进行修改**: 编辑文件、添加内容
4. **提交推送**: `git add -A` → `git commit -m "描述"` → `git push`（使用 Token）

---

## 🔐 Token 认证配置

### 创建 Personal Access Token

1. 访问 https://github.com/settings/tokens

2. 点击 **Generate new token (classic)**

3. 填写说明（Note）：如 "OpenClaw Homepage"

4. 设置过期时间：推荐 **90 天**

5. 选择权限：勾选 **`repo`**（完整仓库控制）

6. 点击 **Generate token**

7. **复制 Token**（格式：`ghp_xxxxxxxxxxxx`）

### 保存 Token

```bash
mkdir -p ~/.github-config
echo "ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx" > ~/.github-config/token
chmod 600 ~/.github-config/token
```

### 使用 Token 推送

```bash
# 方式一：推送时手动输入
git push
# Username: 你的用户名
# Password: 粘贴 Token（不会显示）

# 方式二：使用自动脚本
~/github-push.sh /path/to/repo main
```

---

## 📝 内容管理最佳实践

### 1️⃣ 论文列表管理
- **数据来源**: 使用 CrossRef API 获取真实作者信息
- **格式规范**: 第一作者加粗显示 `<strong>你的名字</strong>`
- **链接完整**: 每篇论文提供 DOI、PDF 链接

### 2️⃣ 新闻时间排序
- 按日期倒序排列（最新在前）
- 每条 News 包含：日期、徽章、标题

### 3️⃣ 中英文翻译
- 使用 `data-i18n` 属性标记可翻译内容
- 翻译对象存储在 JavaScript 中
- 用户偏好保存到 localStorage

---

## 🎨 设计决策

### 1️⃣ 双风格支持
| 风格 | 特点 | 适用场景 |
|------|------|----------|
| Academic | 传统学术、正式、紧凑 | 学术会议、正式场合 |
| Natural | 现代自然、亲和、宽松 | 日常浏览、非正式场合 |

**默认风格**: Academic

### 2️⃣ 响应式设计
- 适配桌面、平板、手机
- 使用 Flexbox 和 Grid 布局
- 图片使用 `max-width: 100%`

---

## 📊 内容清单模板

### 个人信息
- 姓名：张三 / San Zhang
- 头衔：XX 大学 博士生 / PhD Student @ XX University
- 邮箱：zhangsan@example.com

### 社交链接
- GitHub: https://github.com/用户名
- ORCID: https://orcid.org/XXXX-XXXX-XXXX-XXXX
- Google Scholar: https://scholar.google.com/citations?user=XXXXX

### 教育经历
- 202X-Present: PhD, XX University
- 202X-202X: Master, XX University
- 202X-202X: Bachelor, XX University

### 研究方向
- Research Direction 1
- Research Direction 2
- Research Direction 3

---

## 🔄 更新流程

### 新增论文
1. 在 `index.html` 的 Publications 部分添加新条目
2. 更新 Hero 区域的论文统计数字
3. 提交并推送

### 更新个人信息
1. 修改 `index.html` 对应部分
2. 检查中英文翻译是否同步更新
3. 提交并推送

### 添加新页面
1. 创建 `.html` 文件
2. 在主页添加链接
3. 提交并推送

---

## ⚠️ 常见问题与解决方案

### GitHub Pages 不更新
- 强制刷新浏览器（Ctrl+Shift+R）
- 检查 GitHub Actions 部署状态
- 等待 3-5 分钟部署完成

### Token 认证失败
- 检查 Token 是否正确
- 重新生成 Token：https://github.com/settings/tokens
- 确保勾选了 `repo` 权限

### Token 过期
- 访问 https://github.com/settings/tokens
- 删除过期 Token
- 生成新 Token
- 更新 `~/.github-config/token`

### 语言切换不生效
- 清除浏览器缓存
- 检查浏览器控制台错误
- 强制刷新页面

### HTML 标签显示为文本
- 使用 `innerHTML` 而非 `textContent`
- 检查翻译字符串中的引号转义

### 推送时提示认证失败
```bash
# 清除 Git 缓存的凭据
git config --global --unset credential.helper

# 重新推送，会提示输入用户名和 Token
git push
```

---

## 📚 学习要点

### Git 操作
- 基础：clone, add, commit, push
- 远程管理：remote add/set-url
- 分支管理：branch, checkout
- HTTPS 认证：使用 Token 而非密码

### GitHub Pages
- 自动部署机制
- 自定义域名（可选）
- 部署状态查看

### 前端技术
- HTML5 语义化标签
- CSS Variables 主题切换
- JavaScript 国际化 (i18n)
- localStorage 用户偏好保存

---

## 🎯 未来改进方向

### 短期
- 添加暗色模式支持
- 优化移动端体验
- 添加论文引用统计

### 中期
- 集成 BibTeX 引用导出
- 添加博客功能
- 支持更多语言

### 长期
- 使用静态站点生成器（如 Hugo/Jekyll）
- 添加 CI/CD 自动化
- 集成分析工具（如 Google Analytics）

---

## 🔒 安全提示

### Token 安全
- ✅ 不要将 Token 提交到 Git 仓库
- ✅ 使用 `~/.github-config/token` 保存（权限 600）
- ✅ 设置 Token 过期时间（90 天）
- ✅ 定期更换 Token
- ❌ 不要在公开场合分享 Token
- ❌ 不要使用永不过期的 Token（除非必要）

### 仓库安全
- ✅ 定期备份重要文件
- ✅ 使用 `.gitignore` 忽略敏感文件
- ✅ 检查推送内容不包含隐私信息

---

*最后更新：2026-04-05*
