# 歌词排版 + Meta Tag 全表 + 示例歌词

写 Suno 的 Lyrics 框时查这里。歌词框只放**要被唱出来的字 + 结构标签**，语言跟随用户需求，**≤3000 字符**。

## 目录

- [一、歌词排版最佳实践](#一歌词排版最佳实践)
- [二、Meta Tag 全表（官方 vs 社区）](#二meta-tag-全表官方-vs-社区)
- [三、完整示例歌词](#三完整示例歌词)
- [四、纯音乐 / 无人声写法](#四纯音乐--无人声写法)
- [五、注意事项与已知边界](#五注意事项与已知边界)

---

## 一、歌词排版最佳实践

1. **用结构标签搭骨架**：每段前用 `[Verse] [Chorus] [Bridge]` 等标签，**标签独占一行**，AI 才认得出段落转换。
2. **常见曲式**：
   ```
   [Intro] →（可选，气氛铺垫）
   [Verse 1] → 主歌，叙事 8-16 行
   [Pre-Chorus] →（可选，蓄力 2-4 行）
   [Chorus] → 副歌，钩子 1-4 行
   [Verse 2] → 主歌，推进剧情
   [Chorus]
   [Bridge] → 桥段，情绪/旋律对比 2-4 行
   [Chorus] → 收尾常把副歌重复或升 key
   [Outro] →（可选，收束）
   ```
3. **副歌短而重复**：副歌是全曲记忆点，保持 1-4 行、每次出现尽量一致（重复才抓耳）。
4. **主歌负责叙事**：8-16 行讲故事/铺画面，每段歌词可不同。
5. **一行一个意思**：一行别塞太多字，否则人声唱得赶、咬字糊。中文一行通常别超过十来个字。
6. **控制音节**：英文一行 4-6 个重音节奏感最好；中文按"一句话能顺口唱完"为准。需要把一个字唱长，可用连字符提示（英文 `to-night`）。
7. **押韵自然就好**：别为押韵硬凑绕口倒装的句子，AI 唱出来会别扭；顺口 > 工整。
8. **括号做和声/衬词**：副歌里 `(oh oh oh)`、`(don't let go)` 这类括号常被当作背景和声/ad-lib 处理。

---

## 二、Meta Tag 全表（官方 vs 社区）

> **重要区分**：下面 **A 组结构标签**是官方文档明确提到、识别最稳的；**B 组扩展标签**主要来自社区实践与用户示例，能起作用但官方未给出严格语法，**属"锦上添花"，别依赖它做精确控制**。Suno 官方对标签的换行、大小写等细则着墨很少（实践中大小写不敏感、建议独占一行）。

### A 组 · 官方结构标签（优先用这些）

| 标签 | 作用 |
|------|------|
| `[Intro]` | 前奏 / 开场铺垫 |
| `[Verse]` / `[Verse 1]` `[Verse 2]` | 主歌，叙事主体 |
| `[Pre-Chorus]` | 预副歌，进副歌前的蓄力 |
| `[Chorus]` | 副歌，核心钩子 |
| `[Post-Chorus]` | 副歌后小段（社区常用） |
| `[Bridge]` | 桥段，情绪/旋律对比 |
| `[Hook]` | 抓耳的反复句 |
| `[Refrain]` | 反复句，常在段尾 |
| `[Outro]` | 尾奏 / 收束 |
| `[Instrumental]` | 无人声器乐段 |

### B 组 · 社区扩展标签（点缀用，不保证精确生效）

**段落/器乐类**：

```
[Instrumental Break]   [Guitar Solo]   [Saxophone Solo]   [Piano Solo]
[Percussion Break]     [Drum Break]    [Break]            [Build]   [Drop]   [Breakdown]
```

**人声/表演类**（写在段落里或段标签下面）：

```
[Whisper]      [Belting]        [Breathy]       [Raspy]
[Harmonies]    [Gang Vocals]    [Choir]         [Falsetto]
[Spoken Word]  [Ad-libs]        [Vocal Run]
```

**情绪/能量类**：

```
[Energy: High] / [Energy: Low]    [Mood: melancholic]    [Soft]   [Intense]
[Emotional Swell]    [Crescendo]    [Atmospheric]
```

> 用法：把 A 组标签当骨架，B 组标签在需要时插一两个点缀（如副歌前加 `[Build]`、桥段标 `[Whisper]`）。**别整首堆满 B 组标签**——过多反而让 AI 困惑。

---

## 三、完整示例歌词

### 示例 1 · 中文流行情歌（女声，异地恋深夜想念）

```
[Intro]

[Verse 1]
凌晨三点 手机还亮着
你那边的天 是不是刚破晓
我数着时差 数着想你的秒
一整座城市 只剩我醒着

[Pre-Chorus]
多想一伸手 就碰到你的脸
可屏幕这端 只有我的倒影

[Chorus]
隔着一整个时差想你
把晚安 寄到你的清晨里
我们活在 不同的天气
却共享 同一颗 想念的心

[Verse 2]
你发的照片 是陌生的街
我收藏起来 假装也在场
时间偷走了 拥抱的温度
留下两个 倔强的方向

[Chorus]
隔着一整个时差想你
把晚安 寄到你的清晨里
我们活在 不同的天气
却共享 同一颗 想念的心

[Bridge]
再远的距离 也有尽头
等季节转过 等航班落地
(等你 等你)

[Chorus]
隔着一整个时差想你
把晚安 寄到你的清晨里

[Outro]
晚安 我的清晨
```

### 示例 2 · 英文流行（明亮、励志）

```
[Verse 1]
Woke up to a quiet kind of grey
Footsteps heavy, words I couldn't say
But there's a light beneath the door
Telling me there's something more

[Pre-Chorus]
So I'm lacing up my shoes
Got nothing left to lose

[Chorus]
I'll run into the morning
Let the old me fall behind
I'm done with all the waiting
This is my time, this is my time

[Verse 2]
Every scar's a story that I own
Every crack is how the light gets thrown
I'm not the person that I was
I'm rising up, and that's because

[Chorus]
I'll run into the morning
Let the old me fall behind
I'm done with all the waiting
This is my time, this is my time

[Bridge]
(Oh oh oh)
No more looking back
(Oh oh oh)
I'm never going back

[Chorus]
I'll run into the morning
This is my time, this is my time

[Outro]
This is my time
```

---

## 四、纯音乐 / 无人声写法

要 BGM / 纯音乐时：

- 在 Style 框写明 `instrumental, no vocals`，并在生成页打开 **Instrumental** 开关。
- 歌词框可**留空**，或用器乐段落标签搭出结构与走向：

```
[Intro]
[soft ambient pads, gentle rain]

[Build]
[layered Rhodes piano, warm bass enters]

[Main Theme]
[melodic lead, steady lo-fi drums]

[Breakdown]
[strip back to piano and vinyl crackle]

[Outro]
[slow fade]
```

> 段落里的方括号描述是给 AI 的氛围/配器提示，不会被当歌词唱出来。

---

## 五、注意事项与已知边界

- **标签独占一行**：`[Chorus]` 单独一行，下一行才是歌词。
- **大小写**：实践中不敏感（`[Chorus]` 与 `[chorus]` 都认），但建议统一首字母大写更清晰。
- **歌词 ≤ 3000 字符**：含标签在内。太长就精简段落或减少重复次数。
- **官方语法留白**：Suno 官方没有公布"标签必须怎么写、重复几次、非标准标签如何解析"的硬规则——B 组扩展标签效果因版本和运气而异，**当点缀别当开关**。
- **Style 与歌词别串味**：风格/情绪/乐器描述放 Style 框；这里只放要唱的字 + 结构标签。
- **语言一致**：整首歌词尽量用同一种语言（除非用户明确要双语）；不要把中文歌词擅自译成英文。
