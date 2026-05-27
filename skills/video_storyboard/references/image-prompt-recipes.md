# ChatGPT-Images 2 出图配方

SKILL.md Step 3 调用本文件。本文件只讲"如何让 ChatGPT 网页出一张可用的分镜首帧图"，不涉及视频。

---

## 写作要点

1. **中英文混写没问题**——ChatGPT-Images 2 对中文理解到位，但**光学术语、风格词、画幅术语用英文更准**（如 `anamorphic`, `chiaroscuro`, `35mm`, `bokeh`, `volumetric light`）。
2. **短句 + 逗号分隔**，不要写散文段落。
3. **关键元素重复 2–3 次**——色板、光源方向、风格关键词是最容易被稀释的，重复强化。
4. **永远写 Negative**——单独一行 `Negative:` 列出本镜不能出现的东西。
5. **一张图只描述一帧**——不要写"她转过身然后……"，那是视频 prompt 的事。

---

## 出图 prompt 黄金结构

```
[景别] + [主体造型/服装/表情/姿态]
+ [环境布景与道具]
+ [光源方向 + 光质 + 色温]
+ [色板 / 调色]
+ [画幅 + 风格关键词]
+ Negative: [全局负面词 + 本镜专属负面词]
```

---

## 构图术语词典（英文最稳）

| 类别 | 术语 |
|------|------|
| 景别 | extreme close-up / close-up / medium shot / wide shot / extreme wide shot |
| 视角 | low angle / high angle / Dutch angle / bird's eye / worm's eye / POV |
| 镜头 | 35mm / 50mm / 85mm / wide-angle / telephoto / anamorphic / macro |
| 景深 | shallow depth of field / deep focus / bokeh / rack focus |
| 光质 | hard light / soft light / volumetric light / rim light / backlight / chiaroscuro / godrays |
| 色温 | warm (3200K) / neutral (5500K) / cool (7500K) |
| 风格 | cinematic / documentary / fashion editorial / film noir / oil painting / sumi-e |
| 胶片 | 35mm Kodak Portra / Fuji Pro 400H / Ilford HP5 black and white |

---

## 角色一致性三策略（按难度升序）

### 策略 A：阴影遮脸 / 剪影（最稳）
- 让角色 80% 时间脸在阴影里、戴帽子、背对镜头
- prompt 里写 `face obscured by shadow / silhouette against bright background / hood covering eyes`
- 适合：暗黑系、悬疑、概念片

### 策略 B：背影 + 侧脸为主（稳）
- 只在 1–2 个关键镜头给正脸
- 其他镜头用背影、侧脸、过肩
- 服装、发型、配饰必须每镜复述同一套描述

### 策略 C：上传参考图保持一致（最常用）
- **先生成一张"角色档案图"**：在 ChatGPT 里 prompt：
  > Character reference sheet: front view, side view, back view of [角色描述]. Same character across all three views, consistent face, hair, outfit. Neutral gray background, even soft lighting, full body, fashion design illustration style.
- 存为 `character-ref.png`
- **后续每镜**：在 ChatGPT 对话中**上传 character-ref.png**，然后 prompt：
  > Using the attached character reference, keep face, hair, and outfit identical. Now show this character: [本镜场景 + 姿态 + 表情 + 环境]. [光源/色板/风格关键词]. Negative: ...

**注意**：ChatGPT-Images 2 即使有参考图也会漂移，每 3–5 镜重新上传一次参考图，并在 prompt 开头强调 `match the attached reference exactly`。

---

## 5 种常见镜头类型的出图模板

### ① 人物面部特写（难度 ⭐⭐⭐⭐⭐）

```
Extreme close-up portrait, [角色: 上传 character-ref.png 保持一致],
[表情: 眼神向左下方 / 紧抿嘴唇 / 微微皱眉],
[光源: 单一硬侧光从左上 45°, 右侧 70% 阴影],
[色板: 墨青 + 一点暖橘高光],
shallow depth of field, 85mm lens, anamorphic,
cinematic, film grain, [风格关键词].
Negative: smile, cartoon, anime face, soft diffused light, multiple light sources,
distorted features, plastic skin, HDR.
```

### ② 大远景环境镜（难度 ⭐⭐）

```
Extreme wide shot, [环境: 雾气弥漫的群山 / 霓虹雨夜的赛博都市 / 黄昏沙漠],
[主体: 微小的人物剪影站在画面右下 1/3 处],
[光源: 逆光、godrays 穿透雾气],
[色板: 单色调以 X 为主 + 一点 Y 作点缀],
massive scale, negative space, 21:9 aspect ratio,
cinematic, atmospheric, IMAX, [风格].
Negative: 主体过大, 居中构图, 杂乱前景.
```

### ③ 道具特写（难度 ⭐⭐）

```
Macro close-up of [道具: 一柄锈迹斑斑的青铜剑 / 一只翡翠戒指 / 一本翻开的古书],
extreme detail, surface texture visible (rust / fabric weave / paper fiber),
[光源: 单一侧光勾边, 背景全黑],
shallow depth of field, 100mm macro lens,
[色板], cinematic still life, museum quality.
Negative: 杂乱背景, 多个物体, 卡通感.
```

### ④ 多人群像（难度 ⭐⭐⭐⭐）

```
Medium-wide shot, [N 人: 描述各自位置、姿态、关系],
[主角在 X 位置, 配角 Y 在 Z 位置],
[环境], [光源: 主光从 A 方向, 整体阴影占 60%],
[色板], cinematic ensemble framing, [风格].
Negative: 人物面部模糊, 多余的人, 重复的脸, 人物比例失调.
```

**多人一致性**：把每个角色档案图都上传，prompt 里编号指代（"the character on the left matches reference image 1, the one on the right matches reference image 2"）。

### ⑤ 环境氛围镜（无主角，难度 ⭐⭐）

```
[场景: 空荡荡的长廊 / 风沙中的废墟 / 烛火摇曳的房间],
no people, atmospheric, [天气/粒子: 飘雪 / 烟雾 / 飞舞的灰烬],
[光源], [色板], [画幅], cinematic establishing shot, [风格].
Negative: 人物, 文字, 标志.
```

---

## 五大避坑清单

| 坑 | 规避 |
|----|------|
| **人物五官畸变** | Negative 里必加 `distorted features, asymmetric eyes, melted face` |
| **手指畸形** | 能避免手就避免；非画不可时 prompt 写 `hands hidden in sleeves / holding object that occupies most of the hand` |
| **图里出现乱码文字** | Negative 必加 `text, letters, watermark, logo, signature` |
| **风格漂移** | 每 3–5 镜重新上传 character-ref，且 prompt 开头复述风格关键词 |
| **画幅不对** | 直接在 prompt 末尾写 `21:9 aspect ratio` 或 `9:16 vertical`，ChatGPT-Images 2 对这个识别准 |

---

## 抽卡建议

- 一镜先抽 3 张选最接近的，再基于"那张已经对了的"做微调（在 ChatGPT 里继续对话，说"keep everything, change only X"）。
- 不要一上来就追求完美，先把构图、色调、光源对了，细节漂移后期可以用 PS / Photoshop generative fill 修。
- **存好种子提示词**：一旦某镜出来了，把完整 prompt 存到工作手册里，下次系列项目可以套用。
