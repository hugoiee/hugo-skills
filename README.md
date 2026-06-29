# hugo-skills

hugo 维护的 Claude Code / Claude.ai Skills 仓库。开箱即用，clone 下来就能让你的 Claude 多出一组专业能力。

## 仓库里有什么

| Skill | 适用场景 |
|-------|---------|
| [video_storyboard](skills/video_storyboard/) | 想用 AIGC 做视频但没思路 / 要把 IP 改成宣传片 / 需要一份可执行的分镜手册时调用。覆盖项目定位 → 调研 → 创意收敛 → 视觉锁定 → 分镜 → 迭代 → Prompt 输出全流程，工具中立（Seedance / Sora / Kling / Runway / Veo 通用） |
| [AIGC_Podcast_Script](skills/AIGC_Podcast_Script/) | 做**双人 AI 对话播客**（两人对谈/数字人对谈视频）时调用。把剪辑决策前置到写稿之后：从 A/B 对话稿直接算出一张精确到秒的剪辑决策表（cut plan / EDL）+ 反应镜头素材库需求清单 + 每个片段的生成 prompt，让最后在剪映/CapCut 里的拼接退化成照表拼装。核心机制是"说话片段音画一体进主轨、静音反应片段进上层覆盖轨做盖画面不盖声音的 cutaway 叠加"，并给出可判定的反应镜头触发规则与（可选）pyJianYingDraft 一键生成剪映草稿。针对即梦 / 可灵 / Vidu + 剪映。与 video_storyboard 分工：后者是单人/通用 AIGC 分镜，本 skill 专攻双人对话的剪辑前置 |
| [AIGC_MJ_translate](skills/AIGC_MJ_translate/) | 把中文创意/提示词翻译成精准、符合 Midjourney 规范的英文 prompt 时调用。按"解析意图（缺信息先反问）→ 八要素拆解 → 专业术语选词 → 智能补参数 → 成品 + 说明"五步，产出可直接出图的 prompt。内置 MJ 参数速查与中→英视觉术语词表，默认 V8.1。专用于 Midjourney |
| [AIGC_Suno_Music](skills/AIGC_Suno_Music/) | 用 Suno 做歌时调用。把一句音乐创意/主题变成可直接粘贴进 Suno 的成品——英文 Style 提示词（≤240 字符）+ 带 [Verse]/[Chorus] 结构标签的歌词（≤3000 字符）+ 标题 + 调参建议。按"厘清意图 → 写 Style → 写结构化歌词 → 选模式/版本 → 调参迭代"五步，只锚定一个主流派避免风格打架；Style 用英文、歌词随用户语言。内置音乐术语中→英词库、各流派示例提示词、meta tag 全表与迭代工具速查。专用于 Suno |
| [coding_new_project](skills/coding_new_project/) | 从零搭新项目时调用。在空目录里按"技术选型 → 项目骨架 → 工具链配置 → 首个页面 + CLAUDE.md"四步法，让 AI 干体力活（初始化、装依赖、写配置、搭样板），你做脑力活（技术选型、架构决策、目录规划），先求可运行、可解释、可继续扩展，不一步到位堆功能。工具中立 |
| [coding_new_feat](skills/coding_new_feat/) | 开发新功能时调用。把一个模糊的功能需求按"需求分析 → 任务拆解 → 逐步实现 → 每步验证 → 集成测试"五步法拆成 5-7 个可验证的小任务，一次只做一步、做完就验，避免一把梭到底反复翻车。工具中立 |
| [coding_fix_bug](skills/coding_fix_bug/) | 修 bug 时调用。按"收集线索 → 缩小范围 → 定位根因 → 安全修复"四步定位法，从异常现象倒推原因，给 AI 精确线索而不是让它猜，先诊断再动手、最小改动、改完防回归。覆盖 runtime error / 逻辑 bug / 类型错误 / 状态不同步等。工具中立 |

每个 skill 都是一个独立目录，包含 `SKILL.md`（主流程）和 `references/`（按需加载的支撑文档）。Claude 会读 `SKILL.md` frontmatter 里的 `description` 自动判断何时触发，你不需要手动 `/调用`。

---

## 反馈与贡献

- 用得顺手 / 用得不顺手都欢迎开 issue。

License: [MIT](LICENSE)。
