# hugo-skills

hugo 维护的 Claude Code / Claude.ai Skills 仓库。开箱即用，clone 下来就能让你的 Claude 多出一组专业能力。

## 仓库里有什么

### AIGC 播客视频（两条写稿 → 出片流水线）

单人和双人各是一条「先写稿、再出片」的流水线：`*-writing` 用"小林说式"方法论把选题写成定稿/对话稿，产出的稿子直接喂给同名 `*-script` 切段并生成图生视频 prompt。

| Skill | 适用场景 |
|-------|---------|
| [aigc-podcast-solo-writing](skills/aigc-podcast-solo-writing/) | 写**单人口播文案**时调用。用"小林说式"方法论把一个选题按"选题打分 → 结构选型 → 悬念地图 → 开场 60 秒 → 正文填充 → 口语化 → 收尾"产出可直接朗读的口播定稿。面向知识解释类（财经/科技/历史/社会事件"把复杂东西讲明白"）。定稿可直接作为下游 `aigc-podcast-solo-script` 的输入。不适用于双人对谈稿、带货、vlog/测评/情绪共鸣类 |
| [aigc-podcast-solo-script](skills/aigc-podcast-solo-script/) | 把写好的**单人口播稿做成视频**时调用。前置切成偏 10–15s 的段（4–15s 内）、按念出字数（数字按读法）估时卡死总时长（如 ≤90s），锁一张固定机位首帧 host_solo.png，逐段产出**可直接复制**的图生视频说话 prompt。专治单人口播两大坑：镜头切太碎、以及台词短但生成时长设太长导致人物"傻坐着发呆"（修法：时长=台词实长 + "连贯讲话不发呆" + 合并镜头）。针对即梦/可灵/Vidu |
| [aigc-podcast-double-writing](skills/aigc-podcast-double-writing/) | 写**双人对谈稿**时调用。用"小林说式"方法论把单人爆款技巧拆成两个声部（自问自答→A 问 B 答、替观众提问→A 的人设、虚拟对白→真实交锋、大悬念两人共同揭开），按"选题打分 → 双人设定 → 结构与悬念地图 → 逐块写台词 → 口语化"产出带 T1/T3/T4 反应镜头触发点备注的六字段 A/B 行表。行表可直接作为下游 `aigc-podcast-double-script` 的输入 |
| [aigc-podcast-double-script](skills/aigc-podcast-double-script/) | 把**双人对话稿做成视频 + 剪辑决策表**时调用。生成双人/A 单人/B 单人三视图固定机位首帧、逐人图生视频出音画一体说话片段，把剪辑决策前置成一张精确到秒的剪辑决策表（cut plan / EDL）+ 反应镜头素材库需求清单，让剪映/CapCut 里的拼接退化成照表拼装。核心机制是"说话片段音画一体进主轨、静音反应片段进上层覆盖轨做盖画面不盖声音的 cutaway 叠加"，逐行给出起点/时长/用哪条反应片段/转场，并可选 pyJianYingDraft 一键生成剪映草稿。针对即梦/可灵/Vidu + 剪映 |

### 出图 / 出歌 / 出视频

| Skill | 适用场景 |
|-------|---------|
| [aigc-video-builder](skills/aigc-video-builder/) | 写**AI 视频生成 prompt** 时调用。为任意风格构建专业、可直接投产的英文视频 prompt——实拍电影感、3D 动画长片、3A 游戏过场、游戏实机、FPV 一镜到底、产品广告、源视频 VFX 合成、怪兽大片全覆盖。五大硬性原则（第一帧就有运动、三层景深、引用锁定、真实物理与实用光源、构建层面规避内容政策风险）+ 23 段通用结构词汇表 + 8 套风格配方。交付永远是"英文 prompt 成品块 + 逐段中文解释"双份，不是写法说明 |
| [aigc-mj-translate](skills/aigc-mj-translate/) | 把中文创意/提示词翻译成精准、符合 Midjourney 规范的英文 prompt 时调用。按"解析意图（缺信息先反问）→ 八要素拆解 → 专业术语选词 → 智能补参数 → 成品 + 说明"五步，产出可直接出图的 prompt。内置 MJ 参数速查与中→英视觉术语词表，默认 V8.1。专用于 Midjourney |
| [aigc-suno-translate](skills/aigc-suno-translate/) | 用 Suno 做歌时调用。把一句音乐创意/主题变成可直接粘贴进 Suno 的成品——英文 Style 提示词（≤240 字符）+ 带 [Verse]/[Chorus] 结构标签的歌词（≤3000 字符）+ 标题 + 调参建议。按"厘清意图 → 写 Style → 写结构化歌词 → 选模式/版本 → 调参迭代"五步，只锚定一个主流派避免风格打架；Style 用英文、歌词随用户语言。专用于 Suno |

### 编程

| Skill | 适用场景 |
|-------|---------|
| [coding_new_project](skills/coding-new-project/) | 从零搭新项目时调用。在空目录里按"技术选型 → 项目骨架 → 工具链配置 → 首个页面 + CLAUDE.md"四步法，让 AI 干体力活（初始化、装依赖、写配置、搭样板），你做脑力活（技术选型、架构决策、目录规划），先求可运行、可解释、可继续扩展，不一步到位堆功能。工具中立 |
| [coding_new_feat](skills/coding-new-feat/) | 开发新功能时调用。把一个模糊的功能需求按"需求分析 → 任务拆解 → 逐步实现 → 每步验证 → 集成测试"五步法拆成 5-7 个可验证的小任务，一次只做一步、做完就验，避免一把梭到底反复翻车。工具中立 |
| [coding_fix_bug](skills/coding-fix-bug/) | 修 bug 时调用。按"收集线索 → 缩小范围 → 定位根因 → 安全修复"四步定位法，从异常现象倒推原因，给 AI 精确线索而不是让它猜，先诊断再动手、最小改动、改完防回归。覆盖 runtime error / 逻辑 bug / 类型错误 / 状态不同步等。工具中立 |

每个 skill 都是一个独立目录，包含 `SKILL.md`（主流程）和 `references/`（按需加载的支撑文档）。Claude 会读 `SKILL.md` frontmatter 里的 `description` 自动判断何时触发，你不需要手动 `/调用`。

---

## 反馈与贡献

- 用得顺手 / 用得不顺手都欢迎开 issue。

License: [MIT](LICENSE)。
