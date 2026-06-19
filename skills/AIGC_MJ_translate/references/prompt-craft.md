# 提示词写作手艺 + 中→英视觉术语词表

SKILL.md Step 2/3 调用本文件。本文件讲"怎么把画面拆对、怎么把中文译成精准英文术语"，是本 skill 翻译精准度的核心。

---

## 一、提示词解剖（八要素 + 推荐排序）

一条结构完整的 MJ prompt 通常按这个顺序组织（不必每项都填，但越靠前权重越高）：

```
1. 主体 Subject       谁/什么 + 关键特征（数量、造型、姿态、表情）
2. 媒介 Medium        照片 / 油画 / 3D 渲染 / 插画 / 雕塑…
3. 环境 Environment   地点 + 布景 + 道具 + 天气粒子
4. 光照 Lighting      方向 + 光质 + 色温
5. 色彩 Color         主色板 + 饱和倾向
6. 情绪 Mood          一两个氛围词
7. 构图 Composition   景别 + 视角 + 镜头语言（焦段/景深）
8. 风格 Style         美学流派 / 参考艺术家或作品 / 时代
```

- **新手最小公式**：`主体 + 媒介 + 光照 + 画幅`，先把地基搭起来。
- **地基三要素**：主体、媒介、光照——缺了出图最不稳，尽量都给。
- **语序即权重**：最想要的元素放最前面。

---

## 二、最佳实践（让翻译"精准"的 7 条）

1. **具体词 > 笼统词**：`big` → `colossal / towering`；`beautiful` → 用具体的光/色/构图去定义"美"。
2. **去强度副词**：删掉 `very / really / so`，换更强的单词。`very tired` → `exhausted`，`very old` → `ancient / weathered`。
3. **具体名词 + 具体数量**：`furniture` → `mahogany writing desk`；`birds` → `a flock of starlings`；`几只猫` → `three cats`（数量越明确越可控）。
4. **正向描述**：只说"要什么"。要排除的东西交给 `--no`，别写 `no / without / not` 进描述句（MJ 易反向理解）。
5. **简洁，每词有信息**：删填充词；V8.1 偏自然语言，**别堆同义词**（堆砌反而更乱）。
6. **善用摄影/艺术术语**：`golden hour`、`85mm lens`、`chiaroscuro`、`bokeh` 这类术语对 MJ 是强信号，比形容词管用。
7. **媒介必须点明**：同一主体，`photograph` / `oil painting` / `3D render` 出来是三个世界。

---

## 三、中→英视觉术语词表（翻译时直接查）

> 原则：中文里的"感觉词"要落到这些**可成像的具体术语**上。机翻直译往往把"感觉词"原样译成形容词，那是无效信息。

### 媒介 / 风格 Medium & Style

| 中文 | 英文 |
|------|------|
| 写实摄影 / 照片感 | photograph, photorealistic, realistic photography |
| 电影感 | cinematic, cinematic still, movie scene |
| 油画 | oil painting |
| 水彩 | watercolor painting |
| 水墨 / 国风 | traditional Chinese ink painting, sumi-e |
| 3D 渲染 / CG | 3D render, octane render, CGI |
| 插画 | illustration, digital illustration |
| 动漫 / 二次元（配 `--niji`） | anime, manga style, cel shading |
| 吉卜力风 | Studio Ghibli style |
| 赛博朋克 | cyberpunk |
| 蒸汽朋克 | steampunk |
| 极简 | minimalist |
| 复古胶片 | vintage film, 35mm film, Kodak Portra |
| 概念设计 | concept art |
| 像素风 | pixel art |
| 黏土/定格 | claymation, stop-motion |

### 光照 Lighting

| 中文 | 英文 |
|------|------|
| 黄金时刻 / 暖阳 | golden hour, warm sunlight |
| 蓝调时刻 | blue hour |
| 逆光 | backlit, backlighting |
| 轮廓光 / 边缘光 | rim light |
| 柔光 | soft diffused light |
| 硬光 | hard light |
| 影棚光 | studio lighting |
| 霓虹光 | neon lighting |
| 丁达尔光 / 体积光 | volumetric light, god rays |
| 烛光 | candlelight |
| 月光 | moonlight |
| 明暗对比（伦勃朗/卡拉瓦乔式） | chiaroscuro, Rembrandt lighting |
| 暖色温 / 冷色温 | warm color temperature / cool color temperature |

### 镜头 / 构图 Composition & Camera

| 中文 | 英文 |
|------|------|
| 特写 | close-up |
| 大特写 | extreme close-up |
| 中景 | medium shot |
| 全景 / 远景 | wide shot |
| 大远景 | extreme wide shot |
| 仰拍 / 俯拍 | low angle / high angle |
| 鸟瞰 | bird's-eye view, aerial view |
| 斜角 | Dutch angle |
| 第一人称视角 | POV, first-person view |
| 景深虚化 / 背景虚化 | shallow depth of field, bokeh |
| 微距 | macro |
| 广角 | wide-angle lens |
| 长焦 | telephoto |
| 焦段 | 35mm / 50mm / 85mm lens |
| 对称构图 | symmetrical composition |
| 负空间 / 留白 | negative space |
| 三分法 | rule of thirds |

### 色彩 / 情绪 Color & Mood

| 中文 | 英文 |
|------|------|
| 暖色调 | warm tones |
| 冷色调 | cool tones |
| 高级灰 / 低饱和 | muted palette, desaturated |
| 高饱和 / 鲜艳 | vibrant, saturated colors |
| 单色 | monochromatic |
| 黑白 | black and white |
| 撞色 / 互补色 | complementary colors |
| 粉彩 / 马卡龙 | pastel colors |
| 梦幻 | dreamy, ethereal |
| 治愈 / 宁静 | serene, soothing |
| 忧郁 | melancholic |
| 神秘 | mysterious |
| 史诗 / 震撼 | epic, grand |
| 温馨 / 亲密 | cozy, intimate |
| 阴郁 / 压抑 | gloomy, somber |
| 活力 / 欢快 | energetic, cheerful |

### 材质 / 质感 Texture & Material

| 中文 | 英文 |
|------|------|
| 金属质感 | metallic |
| 磨砂 | matte |
| 光泽 / 高光 | glossy |
| 通透 | translucent |
| 颗粒感 / 胶片颗粒 | film grain, grainy |
| 锈迹 | rusty, weathered |
| 丝绸 | silky |
| 粗糙 | rough, coarse texture |
| 水润 | dewy, glistening |
| 全息 | holographic, iridescent |

---

## 四、翻译范例（中文 → 反问 → 成品 + 说明）

### 范例 1：信息不足 → 先反问（写实人像）

**中文**：「帮我画一个很有气质的女生」

信息缺口：媒介不明、风格不定、用途/画幅未知 → **先反问**：

```
想要哪种"气质"？
A. 写实时尚摄影（杂志封面感）
B. 日系动漫插画（--niji）
C. 古典油画肖像
用途是头像(1:1) / 海报(2:3) / 手机壁纸(9:16)？
```

假设用户选 A + 海报，成品：

```
elegant young woman, fashion editorial photograph, minimalist studio backdrop,
soft diffused key light from the side, muted earth-tone palette, calm confident mood,
medium close-up, 85mm lens, shallow depth of field --ar 2:3 --v 8.1 --style raw
```

- **关键选词**：「气质」落到 `elegant + calm confident mood + fashion editorial`；用 `85mm + shallow depth of field` 给高级感。
- **参数**：`--ar 2:3`（海报竖构图）、`--style raw`（写实去 AI 味）、`--v 8.1`。

---

### 范例 2：动漫类 → 自动补 --niji

**中文**：「一个银发少女站在樱花树下，二次元，竖屏壁纸」

信息已足（主体/风格/画幅都清楚），直接翻：

```
silver-haired anime girl standing under a blooming cherry blossom tree,
petals drifting in the breeze, soft afternoon backlight, pastel pink and warm tones,
gentle dreamy mood, medium shot, detailed anime illustration --ar 9:16 --niji 6
```

- **关键选词**：「二次元」→ `detailed anime illustration` 并启用 `--niji 6`（动漫专用模型）；「樱花树下」补了 `petals drifting + backlight` 增强画面。
- **参数**：`--ar 9:16`（竖屏壁纸）、`--niji 6`。
- **AI 补充**：飘落花瓣、逆光是我加的氛围，可删。

---

### 范例 3：写实风光 → --style raw + 横画幅

**中文**：「清晨的雪山湖泊，很安静，要那种大片的感觉」

```
serene alpine lake at dawn, snow-capped mountains reflected on still water,
thin morning mist drifting over the surface, soft cool blue light,
muted palette, tranquil and majestic mood, extreme wide shot,
cinematic landscape photography --ar 16:9 --v 8.1 --style raw
```

- **关键选词**：「大片感」落到 `cinematic landscape photography + extreme wide shot`；「安静」→ `serene + tranquil + still water`。
- **参数**：`--ar 16:9`（大片横构图）、`--style raw`（写实）、`--v 8.1`。

---

### 范例 4：含排除项 → 用 --no，不写进描述

**中文**：「空荡荡的复古咖啡馆，暖色调，画面里不要有人」

```
empty vintage coffee shop interior, warm afternoon sunlight through large windows,
wooden furniture and brass details, cozy nostalgic mood, warm amber tones,
wide shot, 35mm film aesthetic --ar 3:2 --v 8.1 --no people
```

- **关键处理**：「不要有人」→ 末尾 `--no people`，**没有**写成 `no people` 进描述句（那样反而易出人）。
- **参数**：`--ar 3:2`、`--no people`、`--v 8.1`。

---

## 五、自检清单（产出前过一遍）

- [ ] 主体 + 媒介 + 光照三件套齐了吗？
- [ ] 笼统词都换成可成像的具体术语了吗？（没有 `beautiful / nice / cool` 这类空话）
- [ ] 有没有把"不要 XX"误写进描述句？（应进 `--no`）
- [ ] 短语 + 英文逗号分隔，最重要的在前？
- [ ] 参数格式合法（`--ar 16:9` 双连字符 + 空格，全英文标点）？
- [ ] 默认补了 `--v 8.1`（或动漫 `--niji 6`）和合适的 `--ar`？
- [ ] 输出是否包含"成品 prompt + 简要说明 + 微调提示"三段？
