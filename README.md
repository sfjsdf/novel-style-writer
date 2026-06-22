# Novel Style Writer

> 🖊️ 基于 Claude Skill 的网络小说全流程创作系统

一个覆盖从风格分析到逐章审校的六阶段小说创作工作流，将专业网文创作方法论系统化封装为可复用的 AI Skill。

## 快速开始

### 环境要求

- [Claude](https://claude.ai)（推荐 Claude Pro/Team 以获得更长上下文）
- 支持 Skill 的 Claude 客户端（Claude.ai、Claude Desktop、Claude Code 等）

### 安装配置

**方式一：直接下载**

```bash
git clone https://github.com/sfjsdf/novel-style-writer.git
```

**方式二：手动安装**

1. 下载本仓库所有文件
2. 保持目录结构不变（`assets/`、`references/` 文件夹必须完整）

### 注册为 Claude Skill

#### Claude.ai / Claude Desktop

1. 进入 **Settings** → **Skills**
2. 点击 **Create Skill**
3. 将 `SKILL.md` 的完整内容粘贴到 Skill 编辑器中
4. Skill 名称填写 `novel-style-writer`
5. 保存即可

#### Claude Code

将整个 `novel-style-writer/` 文件夹放入项目的 `.claude/skills/` 目录下：

```bash
cp -r novel-style-writer/ your-project/.claude/skills/
```

### 使用方法

注册完成后，在对话中输入以下任意关键词即可触发：

```
写小说、仿写、小说大纲、小说创作、章纲、卷纲、风格分析、网文、
网络小说、力量体系、人物设定、世界观、玄幻、仙侠、都市异能、
悬疑推理、武侠
```

### 使用示例

**示例 1：仿写现有风格**

```
我想仿照《诡秘之主》的风格写一本克苏鲁+蒸汽朋克的小说，
大概 200 万字，帮我从风格分析开始。
```

**示例 2：从零创作**

```
我想写一本都市异能小说，核心爽点是打脸和升级，
主角金手指是能看到物品的隐藏属性，帮我从核心概念开始构建。
```

**示例 3：只做大纲**

```
我已经有人设和世界观了，帮我细化大纲，
从总纲开始，然后卷纲和章纲。
```

### 六阶段工作流说明

| 阶段 | 内容 | 预计时长 | 产出文件 |
|------|------|---------|---------|
| Phase 1 | 风格分析（9 维度） | 1-3 天 | `style-profile.md` |
| Phase 2 | 核心概念定型 | 3-7 天 | `concept.md` |
| Phase 3 | 世界观构建 | 1-2 周 | `world-building.md` |
| Phase 4 | 人物体系设计 | 3-7 天 | `characters/` |
| Phase 5 | 大纲五层细化 | 1-2 周 | `outline/` |
| Phase 6 | 逐章创作与审校 | 持续进行 | `chapters/` |

> 每个阶段完成后需要用户确认才进入下一阶段，确保创作方向符合预期。

### 文件输出说明

每阶段完成后，所有文件自动保存到当前工作目录。建议为每本小说创建独立文件夹：

```
my-novel/
├── style-profile.md
├── concept.md
├── world-building.md
├── characters/
│   ├── protagonist-xxx.md
│   ├── antagonist-xxx.md
│   └── supporting-cast.md
├── outline/
│   ├── 总纲.md
│   ├── 卷纲/
│   ├── 章纲/
│   ├── 节点纲.md
│   └── 日常纲.md
├── trackers/
│   ├── 人物状态.md
│   ├── 伏笔追踪.md
│   └── 扩展元素.md
├── chapters/
│   ├── 第001章-xxx.txt
│   └── ...
└── review/
    └── 整体审校.md
```

---

## 核心亮点

- **六阶段完整工作流**：风格分析 → 核心概念 → 世界观 → 人物体系 → 五层大纲 → 逐章创作
- **风格仿写引擎**：9 维度风格分析，生成风格画像作为全程创作锚点
- **五层大纲体系**：总纲 → 卷纲 → 章纲 → 节点纲 → 日常纲，逐层细化
- **一致性保障**：伏笔追踪、人物状态追踪、世界观扩展追踪，每章自动更新
- **网文商业标准**：黄金三章、爽点分布、章末钩子、节奏控制等内置规则

## 工作流架构

```
Phase 1: 风格分析          → style-profile.md
Phase 2: 核心概念定型       → concept.md
Phase 3: 世界观构建         → world-building.md + trackers/expansion.md
Phase 4: 人物体系构建       → characters/
Phase 5: 大纲五层细化       → outline/
  ├ 5.1 总纲              → outline/总纲.md
  ├ 5.2 卷纲              → outline/卷纲/
  ├ 5.3 章纲              → outline/章纲/
  ├ 5.4 节点纲            → outline/节点纲.md
  └ 5.5 日常纲            → outline/日常纲.md
Phase 6: 逐章创作与审校     → chapters/ + trackers/
```

## 项目结构

```
novel-style-writer/
├── SKILL.md                              # Skill 主文件（执行指令）
├── assets/
│   ├── style-profile-schema.json         # 风格画像数据结构
│   ├── chapter-outline-schema.json       # 章纲数据结构
│   └── volume-outline-schema.json        # 卷纲数据结构
└── references/
    ├── style-analysis-guide.md           # 风格分析 9 维度详解
    ├── character-template.md             # 人物卡片模板
    ├── world-building-guide.md           # 世界观构建清单
    ├── outline-structure-guide.md        # 大纲写作指南
    ├── node-outline-guide.md             # 节点纲指南
    ├── daily-outline-guide.md            # 日常纲指南
    ├── quality-checklist.md              # 审校清单
    ├── character-state-tracker.md        # 人物状态追踪模板
    ├── foreshadowing-tracker.md          # 伏笔追踪模板
    ├── expansion-tracker.md              # 扩展元素追踪模板
    ├── world-expansion-guide.md          # 世界观扩展指南
    └── world-building-guide.md           # 世界观构建指南
```

## 设计理念

### 纲要一致性准则

当修改任何设定时，系统自动检查并同步更新所有关联文件，确保长篇创作中的前后一致性。

### 按需加载机制

15+ 个结构化参考文档按需读取，避免一次性加载导致上下文溢出，每个 Phase 只在需要时读取对应文档。

### 结构化数据定义

通过 JSON Schema 定义章纲、卷纲、风格画像的数据结构，确保输出格式稳定、可解析、可复用。

## 适用场景

- 仿照某部小说的风格写新小说
- 从零构建一部长篇网络小说
- 系统化的小说大纲和章节规划
- 力量体系 / 势力分布 / 人物关系设计
- 黄金三章和章末钩子规划

## 技术栈

- **AI 平台**：Claude (Anthropic)
- **技术领域**：Prompt Engineering、Skill 架构设计、多轮对话管理
- **数据格式**：JSON Schema、Markdown

## License

MIT
