# Canaan Education — Consultant Portal
## CLAUDE.md — 项目完整记录

---

## 一、项目目标

为 **Canaan Education**（迦南教育）私人留学顾问公司构建一个内部使用的**大学申请管理系统**。

目标用户：6+ 名顾问，同时管理约 20 名高中生的大学申请全流程。

核心需求：
- 集中管理所有学生的学术、活动、申请信息
- 多顾问实时协作，数据同步共享
- AI 辅助分析、策略建议、家长报告生成
- 替代 Excel/手工跟踪，提升工作效率

---

## 二、已完成功能模块

### 🏠 Command Center（指挥中心 / 主控台）
- **紧急关注看板**：红/橙/绿三栏，自动识别需要立即关注的学生
- **全局统计**：学生总数、平均GPA、平均SAT、紧急人数
- **30天截止日历预览**：即将到期的申请/考试截止日
- **学生快速总览表**：GPA、测试分、A-G进度、文书进度、下一个截止日
- **⚡ Pre-Meeting Brief 按钮**：一键AI生成会前准备简报
- **团队动态 Activity Feed**：显示谁最近改了什么

### 👤 学生档案（Student Profile）
每个学生有独立档案页，包含以下标签页：

#### Overview（总览）
- 学术数据：GPA、加权GPA、SAT/ACT、目标院校梯度、Hook类型
- 活动列表（结构化展示）
- 即将到期的截止日
- 最近会议记录

#### 📋 Transcript & Audit（成绩单与学位审计）
- 按年级（9-12年级）分组录入课程
- **多国成绩系统支持**：
  - 🇺🇸 美国 A-F（标准4.0换算）
  - 🎓 IB（1-7分，7→4.0）
  - 🇬🇧 A-Level（A*→4.0, A→4.0, B→3.0...）
  - 🇨🇳 中国百分制（90+→4.0, 85+→3.7...）
- 自动计算**非加权GPA**和**加权GPA**（AP/IB +1.0, Honors +0.5）
- **UC A-G 要求审计**：9大类别进度条，自动标记已满足/进行中/缺失
- **学术强度评估**：AP/IB数量、Honors比例、按目标梯度评级
- **顾问预警系统**：自动生成需关注的学术红旗

#### 🏆 Activities（活动编辑器）
- 结构化卡片：活动名称、角色/职位、描述、每年小时数、活跃年级
- **AI Chat Box**：对话式输入，AI自动解析并整理成结构化格式
  - 支持口述、粘贴列表、更新单项等方式
  - 使用 Claude Sonnet API 解析

#### ☑ To-Do List（待办清单）
- 每个学生独立清单
- 字段：任务描述、优先级（高/中/低）、分类（文书/考试/申请等）、截止日
- 一键勾选完成，已完成任务自动归档
- 逾期/即将到期颜色预警
- 进度条显示完成百分比
- 悬停显示编辑/删除按钮

#### ✍ Essays（文书追踪）
- 追踪每篇文书：标题、类型（Common App/补充文书/奖学金）、学校、字数限制、截止日
- 状态流程：Not Started → Brainstorm → Drafting → Revising → Consultant Review → Final
- 下拉直接更新状态

#### 📝 Notes（会议记录）
- 按日期和分类（文书/学术/考试/家长等）记录会议内容
- 快速添加新记录

#### 🤖 AI Analysis（AI分析）
- 全面策略分析
- 学校列表建议（含ED/EA时机）
- 文书主题建议
- 时间线规划
- 成绩单深度解读

### ⇌ Cohort Compare（队列对比）
- 所有学生并排对比表
- 可排序列：GPA、加权GPA、SAT、AP数量、A-G完成度、文书进度、紧急程度
- 按年级筛选
- AI 队列整体分析

### 📅 Deadline Calendar（截止日历）
- 全团队所有截止日汇总视图
- 类型筛选：ED/EA/RD/考试/奖学金/其他
- 逾期警告、按学生分组视图
- 一键标记完成
- 添加/删除截止日

### ✍ Essay Tracker（全局文书追踪）
- 所有学生所有文书的统一视图
- 按状态统计（各阶段数量 + 总完成率）
- 按学生筛选
- 状态直接在表格下拉更新

### 🏫 School Database（学校数据库）
- 内置16所顶尖大学基础数据
- **College Scorecard API 集成**（美国教育部官方数据）：
  - 实时搜索任意学校
  - 自动填入录取率、SAT 25-75分位
  - 一键刷新所有学校数据
  - 标注数据来源：🏛 Scorecard（官方）/ 估算
- 可编辑字段：GPA要求、ED加成、备注
- **Quick Match Calculator**：输入学生数据，自动计算每所学校的录取概率和 reach/match/safety 分类

### ⚡ Pre-Meeting Brief（会前简报）
- 点击任意学生的⚡按钮
- AI生成400字精准简报，包含：
  - 上次会议摘要
  - 本次必须讨论的紧急事项
  - 未完成的承诺/待确认事项
  - 本周快速行动建议
  - 需要深入了解的预警信号

### 📄 Parent Report（家长报告）
- 一键生成专业家长进度报告
- 涵盖：学术表现、A-G进度、文书状态、下一步行动、顾问专业建议
- 第一人称顾问视角，温暖专业语气
- 支持打印/保存为PDF

### 🔥 Firebase 实时协作
- Google 账号登录（公司账号 @canaanedu.com）
- 所有数据实时同步至 Firebase Firestore
- 在线成员头像显示（谁在线）
- 团队动态 Feed（谁更新了什么）
- 同步状态指示灯（绿=实时/橙=保存中/红=离线）
- 支持「Continue without sync」本地模式

---

## 三、技术架构

### 文件结构
```
college-consultant-v9.html    ← 当前最新版本（唯一文件）
CLAUDE.md                     ← 本文档
```

所有代码在**单个 HTML 文件**内，结构：
```
<head>
  Google Fonts (Cormorant Garamond + DM Sans + DM Mono)
  <style> — 全部 CSS（约600行）
</head>
<body>
  Auth Screen（Firebase登录界面）
  Presence Bar（在线成员栏）
  Sidebar（学生列表 + 导航）
  Main Content（各页面）
  Modals（弹窗：添加学生/文书/截止日/活动编辑/待办/家长报告/会前简报）
  <script> — 全部 JavaScript（约2400行）
</body>
```

### 核心技术栈
| 技术 | 用途 |
|------|------|
| 纯 HTML/CSS/JS | 无框架，单文件部署 |
| Firebase Firestore | 实时数据库，多端同步 |
| Firebase Auth | Google OAuth 登录 |
| Anthropic Claude API | AI分析、简报生成、活动整理 |
| College Scorecard API | 美国教育部官方学校数据 |
| Google Fonts | Cormorant Garamond + DM Sans |

### Firebase 配置（已内置）
```javascript
apiKey:    "AIzaSyBOCbEF_nlvUh-NT2x_L4-C3RVfI1M1TZ8"
authDomain:"canaanedu-consultant-portal.firebaseapp.com"
projectId: "canaanedu-consultant-portal"
appId:     "1:25438024590:web:2573880b7683cc801c2adf"
```
Firebase 项目：**Canaanedu Consultant Portal**
Firestore 位置：nam5
支持邮箱：chloe@canaanedu.com

### 数据模型
```javascript
// Firestore: /students/{studentId}
{
  id, firstName, lastName, grade, gpa, sat, act,
  major, tier, hook, color, activities, activitiesList[],
  transcript[],   // 每门课：subject, ag, level, grade, gradeSystem, year, credits, sem
  essays[],       // 每篇文书：title, type, school, wordLimit, due, status, drafts
  todos[],        // 每个待办：text, priority, category, due, done, createdAt
  meetings[],     // 每次会议：date, content, tag
  createdAt, updatedAt, updatedBy
}

// Firestore: /activityFeed/{docId}
{ user, uid, color, action, ts }

// Firestore: /presence/{uid}
{ uid, name, email, photo, lastSeen, currentPage }
```

### GPA 换算逻辑
```javascript
// 美国制
A+/A=4.0, A-=3.7, B+=3.3, B=3.0, B-=2.7...

// IB制
7=4.0, 6=3.7, 5=3.3, 4=3.0, 3=2.0, 2=1.0, 1=0.0

// A-Level
A*=4.0, A=4.0, B=3.0, C=2.0, D=1.0, E=0.0

// 中国百分制
90+=4.0, 85+=3.7, 80+=3.3, 75+=3.0, 70+=2.7, 65+=2.3, 60+=2.0, <60=0.0

// 加权加成
AP/IB: +1.0, Honors/College: +0.5, 上限5.0
```

### 设计风格
- **主题**：深色豪华风（Navy + Gold）
- **字体**：Cormorant Garamond（标题）+ DM Sans（正文）+ DM Mono（数据）
- **主色**：`--bg:#080f1e` / `--gold:#c9a84c` / `--cream:#f0ece4`

---

## 四、版本历史

| 版本 | 主要新增内容 |
|------|-------------|
| v1 | 基础学生档案、学校列表、AI策略分析 |
| v2 | 置信度指标、学校数据库、Enhanced AI提示 |
| v3 | 成绩单模块、UC A-G审计、成绩单AI分析 |
| v4 | 紧急看板、队列对比、截止日历、文书追踪、家长报告、会前简报 |
| v5 | College Scorecard API集成、学校实时数据拉取 |
| v6 | 多国成绩系统（IB/A-Level/中国百分制）、活动AI编辑器 |
| v7 | To-Do List（每学生独立清单，勾选/优先级/分类/截止日） |
| v8 | Firebase实时协作框架（登录/同步/在线成员/动态Feed） |
| v9 | Firebase配置内置（无需手动输入），直接Google登录 |

**当前最新版：`college-consultant-v9.html`**

---

## 五、当前进行到哪一步

### ✅ 已完成
- 所有核心功能模块开发完毕
- Firebase Firestore 数据库已创建（nam5）
- Firebase Authentication 已启用 Google 登录
- Firestore 安全规则已配置（仅登录用户可读写）
- Firebase 配置已内置到 v9 文件
- v9 文件已生成，待部署

### 🔄 进行中
- **Firebase Hosting 部署**：正在引导用户通过命令行部署
  - Node.js v24.14.0 已确认安装 ✅
  - 下一步：安装 Firebase CLI（`npm install -g firebase-tools`）

---

## 六、下一步计划

### 立即（部署阶段）
1. 安装 Firebase CLI：`npm install -g firebase-tools`
2. 登录：`firebase login`
3. 初始化 Hosting：`firebase init hosting`
4. 部署：`firebase deploy`
5. 获得永久网址：`https://canaanedu-consultant-portal.web.app`
6. 分享网址给全团队，每人用公司 Google 账号登录

### 短期优化建议
- [ ] 添加学生照片上传功能
- [ ] 文书版本历史追踪（Draft 1, 2, 3 对比）
- [ ] 申请进度追踪（已提交/等待/录取/拒绝/Waitlist）
- [ ] 邮件/微信通知（截止日临近提醒）
- [ ] 数据导出（PDF报告、Excel汇总）
- [ ] 移动端适配优化

### 中期功能扩展
- [ ] 学生自助门户（学生登录查看自己的任务和进度）
- [ ] 家长门户（只读查看子女进度）
- [ ] 面试准备模块
- [ ] 奖学金追踪

---

## 七、使用说明

### 顾问如何开始使用
1. 打开网址（Firebase Hosting部署后提供）
2. 点「Sign in with Google」，用 `@canaanedu.com` 账号登录
3. 首次登录会自动加载示例学生数据
4. 在侧边栏点击学生名字进入档案
5. 顶部绿色指示灯表示实时同步正常

### AI功能使用
- 所有 AI 功能使用 **Claude claude-sonnet-4-20250514** 模型
- 活动编辑器中的 AI Chat 支持中英文输入
- 会前简报和家长报告约需5-10秒生成

### College Scorecard API
- 在「School Database」页面顶部粘贴 API Key
- 免费申请：api.data.gov/signup
- 搜索学校名称，点「+ Add」自动填入官方数据

---

*最后更新：2026年3月 | 当前版本：v9 | 维护：Chloe @ Canaan Education*
