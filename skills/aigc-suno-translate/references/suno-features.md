# Suno 模式 / 版本 / 限制 / 迭代工具

选模式、确认限制、调参救场时查这里。

## 目录

- [一、Simple vs Custom 模式](#一simple-vs-custom-模式)
- [二、版本时间线与能力](#二版本时间线与能力)
- [三、字符与时长限制](#三字符与时长限制)
- [四、迭代工具（出来不对怎么救）](#四迭代工具出来不对怎么救)
- [五、订阅 / credit 简要注意](#五订阅--credit-简要注意)
- [六、官方文档链接](#六官方文档链接)

---

## 一、Simple vs Custom 模式

在 suno.com/create 创作，两种模式：

| | Simple 模式 | Custom 模式（本 skill 默认假设） |
|---|---|---|
| 怎么填 | 一句话描述想听什么，Suno 自动配曲配词 | 分开填 **Style / Lyrics / Title**，可控性高 |
| 适合 | 快速碰灵感、随手玩 | 精确控制风格、用自己的歌词、做完整作品 |
| 歌词 | 系统自动生成 | 自写，或让 Suno 代写 |
| 其它 | 有"骰子"随机灵感 | 有 Instrumental 开关、Advanced Options（含 Exclude styles） |

> 本 skill 产出的 Title / Style / Lyrics 三段，正对应 **Custom 模式**的三个框，复制即用。

---

## 二、版本时间线与能力

Suno 版本迭代很快，**生成页通常可选版本**。下表为大致能力对照（按需向用户提示选当前最新主力版本）：

| 版本 | 关键能力 | 首次生成最长 |
|------|---------|------------|
| v3.5 | 更好的歌曲结构 | ~4 分钟 |
| v4 | 人声质量提升、更干净的音频、引入 Extend/Cover/Persona | ~4 分钟 |
| v4.5 | **更强提示词遵循**、更聪明的风格融合、更有表现力的人声、更丰富配器；引入 **Creative Prompt Boosting**（一键把简单 tag 扩成详细 Style） | **~8 分钟** |
| v4.5+ | 新增 Add Vocals / Add Instrumental 制作工具 | ~8 分钟 |
| v5 | 音质与结构连贯性更佳、专业过渡、处理更快 | ~8 分钟 |
| v5.5 | **Voices**（用自己的歌声）、**Custom Models**（上传自己的音乐个性化）、**My Taste**（学习偏好）、更丰富编曲 | ~8 分钟 |

实用建议：

- **优先选当前最新主力版本**（写作时为 v4.5 / v5 / v5.5），提示词遵循和音质最好。
- **Creative Prompt Boosting**：在 Style 框右上角点一下，Suno 会把简单提示扩成详细 Style——可用它的产出再人工微调（本 skill 已直接产出详细 Style，通常无需再 boost）。

---

## 三、字符与时长限制

- **Style 框 ≤ 240 字符**
- **Lyrics 框 ≤ 3000 字符**（含结构标签）
- **首次生成最长**：v4.5+ 约 8 分钟；更长用 **Extend** 续接拼到一首完整歌。

---

## 四、迭代工具（出来不对怎么救）

第一遍很少完美。**先在两版里挑底子更稳的那版**，再按现象用对应工具局部修，别推倒重来烧 credit。

| 工具 | 做什么 | 什么时候用 |
|------|--------|-----------|
| **Extend** | 在选定片段后续写、加长，可拼成完整歌 | 歌没唱完 / 想加段 / 想拼满整首；把原 Style 关键词带回去保持连贯 |
| **Replace Section / Quick Replace** | 只重新生成某一段（改该段歌词后重做） | 某段跑偏（如副歌不行），其余都满意——只修那段省 credit |
| **Cover** | 保留旋律，换一种风格/曲风重新演绎 | 旋律喜欢但想换风格；只能 Cover 自己创作的歌 |
| **Persona** | 捕捉某首歌的"声音气质/vibe"，在新歌里复用 | 想让系列作品保持同一种嗓音/气质；可与 Cover 组合 |
| **Stems / Stem Separation** | 把成品拆成分轨（Auto Split 多类；Advanced Split 可挑具体乐器，Premier） | 想拿走人声/伴奏、二次混音、进一步编辑 |
| **Remaster** | 在不改结构/歌词的前提下精修音质与平衡（v5+ 可选 Subtle/Normal/High 变化幅度） | 结构和演唱都满意，只想让音质更干净 |
| **Upload Audio** | 把哼唱/录音/片段变成成品的起点（免费 60 秒，订阅最长 8 分钟） | 有灵感哼唱或现成片段想接着做 |
| **Exclude styles（负面提示）** | 在 Custom 的 Advanced Options 里填**不想要**的元素，自然语言即可 | 总冒出不想要的乐器/风格/人声，如 `rap vocals, heavy drums` |
| **Remix / Suno Studio** | Remix 框架涵盖 Cover/Extend/Reuse 等；Suno Studio（Premier）是多轨编辑工作站，可导 MIDI | 需要更专业的多轨编排与导出 |

> 对症速查：**风格不对** → Cover；**只有一段烂** → Replace Section；**音质糙** → Remaster；**冒出不想要的乐器** → Exclude styles；**太短** → Extend。

---

## 五、订阅 / credit 简要注意

- 生成、Extend、Cover 等都消耗 **credit**；Cover、Advanced Split、Suno Studio、更长上传等部分能力需 **Pro / Premier** 订阅。
- **商用权益**：通常需在订阅状态下创作才具备商用资格；Remix/Cover **他人**作品一般不享商用权益，Remix 自己订阅期内的作品才可以。具体以官方条款为准。

---

## 六、官方文档链接

核心：

- 怎么做一首歌：https://suno.com/hub/how-to-make-a-song
- 版本时间线：https://help.suno.com/en/articles/5782721
- v4.5 详细 Style 写法：https://help.suno.com/en/articles/5782849
- Creative Prompt Boosting：https://help.suno.com/en/articles/5804417
- 歌词里的提示（v4.5）：https://help.suno.com/en/articles/5782977
- Music Glossary（术语表）：https://help.suno.com/en/articles/9010177
- 能不能用自己的歌词：https://help.suno.com/en/articles/2415873

迭代工具：

- 排除元素（负面提示）：https://help.suno.com/en/articles/3161921
- Cover：https://help.suno.com/en/articles/2872257
- Remaster：https://help.suno.com/en/articles/8105281
- 音频上传：https://help.suno.com/en/articles/6141569
- Remix FAQ：https://help.suno.com/en/articles/5663873
- 发布说明（最新功能）：https://suno.com/release-notes

> Suno 更新很快，具体限制/能力以官方页面当下为准；本文件用于快速决策，不替代官方条款。
