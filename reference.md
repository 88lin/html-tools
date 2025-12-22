# 参考文档

## 设计原则

### 核心设计原则

#### 1. 单文件 HTML
- 将 HTML、CSS 和 JavaScript 都写在一个文件中
- 方便复制粘贴和部署
- 无需构建步骤

#### 2. 避免 React
- React 的 JSX 需要构建步骤，增加复杂性
- 使用纯 JavaScript 或从 CDN 加载轻量级框架
- 更快的渲染和更少的 Bug

#### 3. CDN 依赖
- 使用 cdnjs 或 jsDelivr 加载第三方库
- 优先选择知名库
- 使用带版本号的 URL 确保稳定性

#### 4. 保持精简
- 每个工具控制在几百行代码
- 便于 LLM 理解和修改
- 易于维护和重新编写

### 功能模式

#### 剪贴板操作
- 支持粘贴内容（文本、富文本、图片、文件）
- 一键复制结果到剪贴板
- 利用剪贴板的多格式支持

#### URL 状态持久化
- 将状态保存在 URL 中
- 方便书签和分享
- 无需服务器存储

#### localStorage 存储
- 用于存储较大的状态或敏感信息（如 API 密钥）
- 数据不离开用户设备
- 适合自动保存功能

#### CORS API 调用
- 利用支持 CORS 的公开 API
- 常用的 CORS API：
  - GitHub (公开仓库)
  - 各类公开数据接口

#### 文件处理
- 使用 `<input type="file">` 直接读取文件
- 无需上传到服务器
- 支持浏览器内处理库

#### 文件下载
- 使用 JavaScript 生成可下载文件
- 支持多种格式（PNG、JPEG、ICS 等）

---

## 本项目的实现

<div style="background: #f8f9fa; padding: 20px; border-radius: 12px; margin-top: 20px;">

<h3 style="color: #333; margin-bottom: 15px;">项目特色</h3>

<ul style="list-style: none; padding: 0;">
  <li style="padding: 10px 0; border-bottom: 1px solid #e0e0e0;">
    <strong style="color: #667eea;">📁 标准化目录结构</strong> - 每个工具独立文件夹，包含 index.html 和 app.html
  </li>
  <li style="padding: 10px 0; border-bottom: 1px solid #e0e0e0;">
    <strong style="color: #667eea;">📋 索引系统</strong> - 使用 index.json 管理工具元数据
  </li>
  <li style="padding: 10px 0; border-bottom: 1px solid #e0e0e0;">
    <strong style="color: #667eea;">🔍 搜索和过滤</strong> - 前端实现的多维度搜索
  </li>
  <li style="padding: 10px 0; border-bottom: 1px solid #e0e0e0;">
    <strong style="color: #667eea;">🤝 提交流程</strong> - 通过 GitHub Issues 提交工具
  </li>
  <li style="padding: 10px 0;">
    <strong style="color: #667eea;">🌐 GitHub Pages 部署</strong> - 静态托管，无服务器成本
  </li>
</ul>

</div>

---

## 工具分类

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-top: 20px;">

<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 20px; border-radius: 12px;">
  <div style="font-size: 2rem; margin-bottom: 10px;">🔄</div>
  <div style="font-weight: 600;">格式转换</div>
  <div style="font-size: 0.9rem; margin-top: 5px;">7 个工具</div>
</div>

<div style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); color: white; padding: 20px; border-radius: 12px;">
  <div style="font-size: 2rem; margin-bottom: 10px;">👨‍💻</div>
  <div style="font-weight: 600;">开发者工具</div>
  <div style="font-size: 0.9rem; margin-top: 5px;">6 个工具</div>
</div>

<div style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); color: white; padding: 20px; border-radius: 12px;">
  <div style="font-size: 2rem; margin-bottom: 10px;">📝</div>
  <div style="font-weight: 600;">文本处理</div>
  <div style="font-size: 0.9rem; margin-top: 5px;">6 个工具</div>
</div>

<div style="background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); color: white; padding: 20px; border-radius: 12px;">
  <div style="font-size: 2rem; margin-bottom: 10px;">🖼️</div>
  <div style="font-weight: 600;">图片处理</div>
  <div style="font-size: 0.9rem; margin-top: 5px;">2 个工具</div>
</div>

<div style="background: linear-gradient(135deg, #fa709a 0%, #fee140 100%); color: white; padding: 20px; border-radius: 12px;">
  <div style="font-size: 2rem; margin-bottom: 10px;">🧰</div>
  <div style="font-weight: 600;">实用工具</div>
  <div style="font-size: 0.9rem; margin-top: 5px;">4 个工具</div>
</div>

</div>

---

## 开发指南

### 工具开发流程

1. **需求分析** - 确定工具功能和用户需求
2. **原型设计** - 使用 HTML/CSS/JS 快速原型
3. **功能实现** - 保持精简，专注核心功能
4. **测试验证** - 多浏览器兼容性测试
5. **提交审核** - 通过 GitHub Issues 或 PR 提交

### 工具规范

每个工具必须包含：

```
tools/
  └── your-tool/
      ├── index.html    # 工具详情页（介绍页面）
      └── app.html      # 工具实体页（实际运行的工具）
```

**设计原则：**

- 单文件 HTML，内联 CSS/JS
- 不使用 React 或需要构建的技术
- 从 CDN 加载第三方库
- 保持精简（建议 500 行以内）
- 数据本地处理，保护隐私

### 提示词模板

```
Build an HTML tool that [描述功能需求].
No React.
Use [特定库名] from CDN if needed.
Include [特定功能要求].
```
