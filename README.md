# Novel Style Writer

> 🖊️ 基于 Claude Skill 的网络小说全流程创作系统

一个覆盖从风格分析到逐章审校的六阶段小说创作工作流，将专业网文创作方法论系统化封装为可复用的 AI Skill。

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
