# Style 提示词写法 + 音乐术语中英词库 + 示例库

写 Suno 的 Style 框时查这里。Style 用**英文**、**只锚定一个主流派**、**≤240 字符**。

## 目录

- [一、Style 配方与原则](#一style-配方与原则)
- [二、音乐术语 中→英 词库](#二音乐术语-中英-词库)
  - [流派 Genres](#流派-genres)
  - [情绪 / 氛围 Mood](#情绪--氛围-mood)
  - [速度 / 节奏 Tempo & Rhythm（含 BPM 区间）](#速度--节奏-tempo--rhythm含-bpm-区间)
  - [乐器 Instrumentation](#乐器-instrumentation)
  - [人声 / 唱法 Vocals & Techniques](#人声--唱法-vocals--techniques)
  - [制作 / 效果 Production & Effects](#制作--效果-production--effects)
  - [动态 / 表达 Dynamics & Expression](#动态--表达-dynamics--expression)
- [三、各流派示例 Style 提示词](#三各流派示例-style-提示词)
- [四、"像某歌手的感觉" → 描述化替代](#四像某歌手的感觉--描述化替代)
- [五、字符限制与自检](#五字符限制与自检)

---

## 一、Style 配方与原则

**配方**（按需取用，不必全填）：

```
[anchor genre] + [mood 1-2 词] + [关键乐器] + [人声特征] + [节奏/BPM(可加 key)] + [制作质感] + (可选: 走向描述)
```

原则：

1. **一个主流派定盘**——anchor genre 决定整体走向，其余只做调味。
2. **从笼统走向具体**——`deep house, emotional` → `melodic emotional deep house with organic textures, hypnotic groove, soft ambient intro building to flowing synths`（官方推荐 v4.5+ 用连贯、有画面的描述）。
3. **情绪 1-2 个词**——别堆同义词稀释指令。
4. **写走向**——v4.5+ 读得懂 `starts sparse, builds to anthemic chorus, slow fade outro`；像 `lift before the chorus`、`drop at the second chorus` 这类方向提示很有用。
5. **BPM / key 可加**——`92 BPM`、`in F minor` 能稳定速度与情绪基调。
6. **不要的元素别写进 Style**——用 Exclude styles 负面排除（见 `suno-features.md`）。

> Suno 官方有一份 Music Glossary（help.suno.com/en/articles/9010177），把术语分成节奏、动态、结构、旋律和声、流派、配器、唱法、制作、进阶九类——下面的词库即按相近思路整理，方便中文创意快速映射成英文术语。

---

## 二、音乐术语 中→英 词库

把中文创意里的形容词换成下面 Suno 听得懂的专业英文。

### 流派 Genres

| 中文 | English |
|------|---------|
| 流行 / 华语流行 | pop / Mandarin pop / C-pop |
| 抒情慢歌 / 情歌 | ballad / pop ballad |
| 民谣 / 独立民谣 | folk / indie folk / acoustic folk |
| 摇滚 / 流行摇滚 / 朋克 | rock / pop-rock / punk rock |
| 嘻哈 / 说唱 / трэп | hip hop / rap / trap |
| R&B / 新灵魂乐 | R&B / contemporary R&B / neo-soul |
| 电子 / 浩室 / 深浩室 | EDM / house / deep house |
| 合成器流行 / 城市流行 | synth-pop / city pop |
| Lo-fi / study beats | lo-fi hip hop / lo-fi beats |
| 爵士 / 慵懒爵士 / 拉丁爵士 | jazz / smooth jazz / bebop / latin jazz |
| 蓝调 / 乡村 | blues / delta blues / country |
| 古典 / 电影配乐 | classical / orchestral / cinematic score |
| 国风 / 古风 | Chinese folk / guzheng-driven, traditional Chinese instrumentation, "guofeng" |
| 氛围 / 后摇 | ambient / post-rock |
| 金属 / 硬核 | metal / metalcore / hardcore |
| 雷鬼 / 电子舞曲 | reggae / dancehall / techno |

> 国风没有官方标准 tag，用**乐器 + 调式**去描述更稳：`traditional Chinese instrumentation (guzheng, erhu, dizi flute, pipa), pentatonic melody, cinematic, ethereal`。

### 情绪 / 氛围 Mood

| 中文 | English |
|------|---------|
| 治愈 / 温暖 | healing → warm, comforting, tender, soothing |
| 致郁 / 心碎 | melancholic, aching, heartbroken, sorrowful |
| 燃 / 热血 | anthemic, epic, uplifting, triumphant |
| 深夜 / 孤独 | late-night, intimate, lonely, introspective |
| 梦幻 / 空灵 | dreamy, ethereal, atmospheric |
| 慵懒 / 放松 | laid-back, chill, mellow, relaxed |
| 怀旧 | nostalgic, wistful, retro |
| 黑暗 / 阴郁 | dark, moody, brooding, eerie |
| 快乐 / 明亮 | upbeat, bright, joyful, feel-good |
| 性感 / 暧昧 | sultry, sensual, smooth |
| 励志 / 释怀 | hopeful, empowering, cathartic |
| 紧张 / 史诗 | tense, dramatic, epic, cinematic |

### 速度 / 节奏 Tempo & Rhythm（含 BPM 区间）

| 中文 | English | BPM 参考 |
|------|---------|---------|
| 极慢 / 抒情 | very slow, ballad tempo | 60–76 |
| 中慢板 | slow, downtempo | 76–96 |
| 中速 / 律动 | mid-tempo, groovy | 96–120 |
| 偏快 / 舞曲 | upbeat, danceable | 120–135 |
| 快 / 蹦迪 | fast, high-energy | 135–160 |
| 切分 / 律动感强 | syncopated, strong groove, shuffled beat | — |
| 四四拍 / 三拍子 | 4/4 time / waltz, 3/4 time | — |

### 乐器 Instrumentation

| 中文 | English |
|------|---------|
| 钢琴 / 大钢琴 | piano / grand piano / Rhodes (电钢) |
| 原声吉他 / 电吉他 | acoustic guitar / electric guitar |
| 贝斯 / 808 低音 | bass / electric bass / heavy 808 |
| 鼓 / 鼓机 / 军鼓 | drums / drum machine / punchy drums / snare |
| 弦乐 / 管弦 | strings / string section / orchestra |
| 合成器 / 合成器铺底 | synth / analog synth pads / arpeggios |
| 萨克斯 / 小号 / 铜管 | saxophone / trumpet / brass section |
| 小提琴 / 大提琴 | violin / cello |
| 古筝 / 二胡 / 笛子 / 琵琶 | guzheng / erhu / dizi flute / pipa |
| 口琴 / 手风琴 | harmonica / accordion |
| 黑胶噪声 / 磁带质感 | vinyl crackle / tape hiss / tape saturation |

### 人声 / 唱法 Vocals & Techniques

| 中文 | English |
|------|---------|
| 男声 / 女声 / 童声 | male vocals / female vocals / child vocals |
| 低沉 / 温柔 / 沙哑 | deep / tender, soft / raspy, gravelly |
| 气声 / 耳语 | breathy / whispered, intimate |
| 高亢 / 强声 / 飙高音 | powerful, belting / soaring high notes |
| 假声 | falsetto |
| 合唱 / 和声 | choir / gang vocals / layered harmonies |
| 颤音 | vibrato |
| 说唱 flow | rap flow / rhythmic spoken delivery |
| 无人声 / 纯音乐 | instrumental, no vocals |

### 制作 / 效果 Production & Effects

| 中文 | English |
|------|---------|
| 干净 / 精致 | clean, polished, radio-ready mix |
| 复古 / 模拟 | retro, analog, vintage |
| Lo-fi 颗粒感 | lo-fi, gritty, tape-saturated |
| 混响 / 空间感 | reverb, spacious, roomy |
| 大气 / 电影感 | cinematic, lush, wide |
| 极简 / 留白 | minimal, sparse, stripped-back |
| 厚 / 饱满 | full, rich, layered |
| 门控混响鼓（80 年代） | gated reverb drums |

### 动态 / 表达 Dynamics & Expression

| 中文 | English |
|------|---------|
| 渐强 / 渐弱 | crescendo / decrescendo |
| 层层递进 | builds gradually, rising intensity |
| 副歌爆发 | explosive / anthemic chorus, big drop |
| 慢慢淡出 | slow fade, gentle outro |
| 安静开场 | soft ambient intro, starts sparse |
| 断奏 / 连奏 | staccato / legato |

---

## 三、各流派示例 Style 提示词

可直接套用或改写（均 ≤240 字符，已锚定单一主流派）。

```
# Lo-fi 学习/咖啡馆 BGM（纯音乐）
lo-fi hip hop, chill and nostalgic, Rhodes piano, tape-saturated drums, warm
analog bass, vinyl crackle and soft rain, 72 BPM, instrumental, no vocals
```

```
# 80 年代复古 City Pop / 合成器流行
80s city pop, upbeat and nostalgic, polished male vocals, analog synth pads,
gated reverb drums, slap bass, shimmering arpeggios, bright radio-ready mix, 118 BPM
```

```
# 华语抒情情歌
heartfelt Mandarin pop ballad, intimate and aching, tender female vocals, grand
piano and warm strings, slow 68 BPM, builds to a soaring emotional chorus, cinematic
```

```
# 暗黑嘻哈
dark hip hop, moody and menacing, heavy 808 bass, punchy minimal drums, sparse
piano loop, raspy male rap flow, 92 BPM, gritty lo-fi mix
```

```
# 深浩室
deep house, groovy and hypnotic, filtered vocal chops, warm bass synth, crisp
hi-hats, shuffled beat, Rhodes stabs, spacious reverb, 122 BPM
```

```
# 钢琴抒情独唱
melancholic piano ballad, intimate and reflective, soft male vocals, solo grand
piano with subtle strings, very slow tempo, lots of space and reverb, cinematic
```

```
# 独立民谣
warm indie folk, wistful and hopeful, gentle female vocals, fingerpicked acoustic
guitar, soft brushed drums, light harmonies, mid-tempo, organic and intimate
```

```
# 国风 / 古风（纯器乐或可加人声）
cinematic Chinese folk, ethereal and epic, guzheng, erhu and dizi flute,
pentatonic melody, sweeping orchestral strings, slow build, lush and atmospheric
```

```
# 燃系流行摇滚
anthemic pop-rock, energetic and uplifting, powerful male vocals, driving electric
guitars, punchy drums, big sing-along chorus, polished arena mix, 128 BPM
```

```
# 慵懒 R&B / 新灵魂
contemporary R&B, sultry and smooth, breathy female vocals, mellow Rhodes, warm
bass, crisp finger snaps, lush harmonies, 90 BPM in F minor, late-night vibe
```

---

## 四、"像某歌手的感觉" → 描述化替代

**不要直接点名歌手**（如 `sing like Jay Chou`）——既不稳定也不合规。把"像谁的感觉"翻译成**该歌手的声音特征 + 制作风格**：

| 用户说"想要…的感觉" | 描述化写法（举例方向） |
|---------------------|----------------------|
| 周杰伦那种 | R&B-tinged Mandarin pop, half-sung half-rapped flow, mumbled intimate delivery, lush strings + hip hop beat |
| 泰勒·斯威夫特那种 | confessional pop storytelling, catchy melodic hooks, polished radio-ready production, emotional narrative |
| Billie Eilish 那种 | whispered intimate vocals, dark minimalist production, heavy sub-bass, eerie atmospheric textures |
| 林俊杰/抒情高音那种 | soaring Mandarin pop ballad, powerful clean male vocals with high belting, grand piano and strings |
| 城市夜晚日系那种 | 80s city pop, smooth vocals, lush synths, funky bass, nostalgic bright mix |

> 思路：把"风格 = 谁"换成"风格 = 哪几个可描述的声音特征"。这样 Suno 才能稳定复现，也避免直接模仿真人。

---

## 五、字符限制与自检

- **Style 框 ≤ 240 字符**——写完数一下；超了就先砍形容词、删重复信息，保留最有画面的词。
- 一个主流派？✅ 情绪 1-2 词？✅ 有乐器/人声/节奏/制作？✅ 不要的元素没写进来（留给 Exclude styles）？✅
- 全英文、用英文逗号分隔短语。
