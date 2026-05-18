# AIGC 视频工具 Prompt 适配指南

> 用法：阶段 7「Prompt 输出」中需要根据用户选择的工具调整 prompt 语法时调取此文件。
> 这是 seedance-storyboard skill 的功能扩展和替代。

---

## 工具速查表

| 工具 | 出品方 | 强项 | 短板 | Prompt 语言偏好 |
|------|--------|------|------|---------------|
| **Seedance 2.0** | 豆包/字节 | 中文友好、角色一致性、物理理解 | 写实人脸审核严 | 中文 / 英文均可 |
| **Sora 2** | OpenAI | 物理表现最强、长镜头稳 | 价格贵、中文支持弱 | 英文优先 |
| **Kling 2.1** | 快手可灵 | 国产强模型、性价比高、运镜灵活 | 极端写实弱于 Sora | 中文 / 英文均可 |
| **Runway Gen-4** | Runway | 运镜参数化、角色一致性强 | 静态画面感、动作弱 | 英文 |
| **Veo 3** | Google | 物理顶级、音频同步生成 | 价格最贵、地区限制 | 英文优先 |
| **Hailuo 02** | MiniMax | 动态丰富、人物表演好 | 一致性较弱 | 中文 / 英文均可 |
| **Pika 2.2** | Pika Labs | 创意特效、风格化强 | 写实弱 | 英文 |

**注：以上信息为 2026 年初的状态，工具迭代快，使用前建议 web_search 验证最新能力。**

---

## 通用 Prompt 黄金结构

不管哪个工具，这个结构都适用：

```
[镜头景别] + [主体描述（含角色参考）] + [主体动作]
+ [环境与背景] + [光线方向与质感] + [色调]
+ [镜头运动] + [画幅与风格]
```

**通用规则：**
- 短句 + 逗号分隔，不要写散文
- 关键元素重复 2-3 次（AI 会强化关注）
- 负面提示词每镜都加
- 角色参考用工具支持的语法（@图片1、`--cref`、reference image）

---

## Seedance 2.0 适配

### 提示词偏好

- 中文友好，能直接用中文写
- 喜欢"短句 + 逗号"结构，不要长段散文
- 对"镜头运动"指令理解精准
- 支持 `@素材名` 引用上传的素材

### 提示词模板

```
@图片1 作为角色参考。
[景别]镜头。[主体]在[环境]中[动作]。
[关键细节描述]。
[光线方向]。[色调]。
镜头[运动方式]。
[画幅]，[风格关键词]。
```

### 实例（蒙考拉冷玩风）

```
@图片1 作为角色参考。
中景固定机位镜头。方源单膝跪在血红色西漠沙地中，
长发湿透垂地，墨绿血衣被风沙撕裂。
背景是巨大的暗红色落日（铁锈红，不要橙黄色），风沙漫天。
逆光剪影构图。低饱和度，墨红与铁灰主导。
镜头完全静止。
2.39:1 宽银幕，Anamorphic 镜头质感。
```

### 关键功能

| 功能 | 使用方式 |
|------|---------|
| 图片参考 | `@图片1` 标注 |
| 首尾帧入口 | 上传首帧图 + prompt |
| 全能参考入口 | 多图 + 文本组合（推荐） |
| 视频延长 | 长镜头分段生成后拼接 |
| 视频音频 | **抽卡阶段必关，浪费额度** |

### 注意事项

⚠️ **写实人脸审核：** 高度写实的人脸有概率被拦截。应对方案：
1. 先试（AI 写实风可能过审）
2. Midjourney/Flux 风格化处理后再用
3. 多用背影、侧脸、剪影规避
4. 完全纯文本描述

⚠️ **画幅：** 默认 16:9，2.39:1 需要后期裁切。Prompt 加入：
```
2.39:1 宽银幕电影构图，主体置于画面中部纵向带，便于后期裁切上下黑边
```

---

## Sora 2 适配

### 提示词偏好

- 英文优先（中文支持有但效果不如英文）
- 喜欢"自然语言描述"，可以写一小段散文
- 对物理规律理解极强（光、水、动力学）
- 对镜头运动术语理解精准（dolly、pan、tilt、tracking）

### 提示词模板

```
[Shot type] of [subject] [action] in [environment].
[Detailed lighting description].
[Color palette].
Camera [movement description].
[Aspect ratio], [style references], [film stock or lens reference].
```

### 实例（与上面同一镜头）

```
Medium shot, static camera. A lone wandering swordsman kneels on red 
desert sand, his long black hair soaked and dripping, dark green 
blood-stained robe torn by sandstorm winds.

Behind him: a massive rust-red setting sun (deep blood red, NOT 
orange-yellow), heavy sand particles drifting through the air.

Backlit silhouette composition. Desaturated colors with rust red 
and iron grey dominant. Static camera, no movement.

2.39:1 widescreen anamorphic. Shot on Arri Alexa with anamorphic lens, 
35mm film grain. Roger Deakins cinematography style.
```

### Sora 独有的优势用法

**长镜头运动描述：**
```
"Camera slowly dollies forward from 20 meters to 5 meters over 8 seconds,
maintaining the subject in the lower-right third of the frame"
```

**物理细节描述：**
```
"Sand particles realistically affected by wind direction from camera left to right.
The robe fabric responds to wind with natural cloth simulation."
```

### 注意事项

- 不接受 `@image` 语法，参考图通过 UI 上传
- 角色一致性靠 prompt 描述 + reference image
- 价格按秒计费，5 秒以下尽量优化

---

## Kling 2.1 适配

### 提示词偏好

- 中英文均可
- 喜欢"短句 + 逗号"，类似 Seedance
- 对"镜头景别"理解精准
- 支持参考图（"参考图像"功能）

### 提示词模板

```
[景别] [主体描述]
[主体动作]
[环境]
[光线 + 色调]
[镜头运动]
[风格关键词]
```

### Kling 独有特点

- **运动幅度参数**（可调，1-10）：用于控制画面动态强弱
- **专业模式**：支持负面提示词、运动笔刷等
- **首尾帧**：支持指定开始和结束画面

### 实例

```
中景固定机位
苍白男子单膝跪地，黑发湿润垂地，破损墨绿长袍
风沙吹拂衣摆，身侧插满断剑
血红色沙漠，铁锈红落日剪影，漫天风沙
逆光剪影构图，低饱和度，墨红色调
镜头完全静止
2.39:1 宽银幕，电影感，Roger Deakins 摄影风格
```

### 运动幅度建议

| 镜头类型 | 推荐运动幅度 |
|---------|------------|
| 固定机位 | 1-2 |
| 缓慢推拉 | 3-4 |
| 中速跟拍 | 5-6 |
| 快速运镜 | 7-8 |
| 极端动作 | 9-10 |

---

## Runway Gen-4 适配

### 提示词偏好

- 英文为主
- 强调"reference image"逻辑
- 支持运镜参数（在 UI 里调，不是 prompt）
- 喜欢简洁的英文描述

### Runway 独有功能

- **Camera Motion**：通过参数（Pan、Tilt、Zoom、Roll、Tracking）控制运镜
- **Motion Brush**：可以画出运动的区域和方向
- **Director Mode**：详细控制镜头参数

### 提示词模板

```
[Shot type] of [subject], [action].
[Environment].
[Lighting].
[Aspect ratio], [style].
```

**注：复杂的镜头运动通过 UI 参数控制，不写在 prompt 里。**

### 实例

```
Medium static shot of a lone swordsman kneeling on red desert sand,
long black hair wet and tangled, dark green torn robe stained with blood.
Behind him: massive rust-red setting sun, sand particles drifting.
Backlit silhouette, desaturated rust and grey palette.
2.39:1 widescreen, cinematic anamorphic, Roger Deakins style.
```

然后在 UI 里设置：
- Camera Motion: None
- Motion Strength: 2/10

---

## Veo 3 适配

### 提示词偏好

- 英文优先
- 自然语言长描述（类似 Sora）
- 物理规律最强
- **可同时生成音频**（这是 Veo 3 的杀手锏）

### Veo 独有优势

- 自动生成与画面同步的音效（脚步、环境音、人声等）
- 物理表现最接近真实

### 是否用音频生成？

虽然 Veo 3 能生成音频，但**对于多镜头剪辑的宣传片，依然建议关闭**——
理由同 Seedance：音频绑定视频，后期剪辑会被锁死。

只在做"单镜头独立短片"时开启。

### 实例

同 Sora 实例的英文 prompt，加上：
```
Audio: minimal wind sound, distant low rumble, no music, no dialogue.
```

---

## Hailuo 02 适配

### 提示词偏好

- 中英文均可
- 对人物表演（表情、微动作）理解最好
- 喜欢"动作描写"密集的 prompt

### Hailuo 的优势

- 微表情、眼神变化、嘴唇动作生成最自然
- 适合"角色表演为主"的镜头

### 注意

- 一致性较弱，不要用于跨多镜头的角色锁定
- 适合插入"单一表演特写"镜头

---

## Pika 2.2 适配

### 提示词偏好

- 英文为主
- 喜欢"风格化关键词"
- 适合非写实风格

### Pika 适合场景

- 风格化短片（漫画、油画、像素风）
- 创意特效（变形、转换、过渡）

### 不适合

- 写实电影感（用 Sora / Veo / Seedance）
- 角色一致性强的多镜头叙事

---

## 跨工具通用要点

### 1. 角色一致性的核心策略

不管什么工具，角色一致性都靠：

```
1. 第一步：建立"角色锚点图"（Midjourney/Flux 生成的高质量参考图）
2. 第二步：在视频生成时把锚点图作为参考输入
3. 第三步：在 prompt 里反复强调角色特征
4. 第四步：每个生成成功的镜头保存最后一帧作为下一镜的"二级参考"
```

**最关键：所有镜头都用同一张角色锚点图。**

### 2. 负面提示词的通用模板

```
（按风格调整）
低质量、模糊、畸形、变形、五官扭曲、额外肢体、错误手指、
不一致的角色、风格断裂、过度饱和、卡通风格（如果要写实）、
水印、文字、字幕（除非需要）
```

英文版：
```
low quality, blurry, deformed, distorted, mutated face,
extra limbs, wrong fingers, character inconsistency,
style break, oversaturated, cartoon style (if realistic),
watermark, text, subtitles
```

### 3. 画幅控制

| 画幅 | Prompt 关键词 |
|------|-------------|
| 1:1 | "1:1 square composition" |
| 16:9 | "16:9 widescreen" |
| 9:16 | "9:16 vertical / portrait" |
| 2.39:1 | "2.39:1 anamorphic widescreen" + "主体置于画面中部，便于后期裁切" |

### 4. 帧率与时长

| 工具 | 单次生成最长 | 帧率 |
|------|------------|------|
| Seedance 2.0 | 5-10s | 24fps |
| Sora 2 | 20s | 24fps |
| Kling 2.1 | 10s | 30fps |
| Runway Gen-4 | 16s | 24fps |
| Veo 3 | 8s | 24fps |
| Hailuo 02 | 10s | 25fps |

**注：超过这个时长建议分段生成 + 后期拼接。**

### 5. 抽卡心法

不管什么工具：
- 一个镜头**至少抽 3-5 次**取最佳
- 关键镜头（面部特写、复杂动作）**抽 15-30 次**
- **记录种子和参数**，好的镜头要能复现
- **每个镜头多生 2 个备选版本**，剪辑时会感谢自己

### 6. 关于音频

**通用规则：抽卡阶段全程关闭 AI 视频的音频生成。**

理由：
- AI 音频质量达不到电影级
- 音频绑定视频，剪辑无法独立调整
- 浪费额度

正确流程：
```
1. 视频抽卡（无音频）
2. 剪辑成片
3. Suno AI 生成主音乐
4. freesound / Splice / Epidemic Sound 加音效
5. DaVinci Resolve Fairlight 混音
```

唯一例外：单镜头作品（不剪辑）可以试 Veo 3 的同步音频。

---

## 工具选择决策树

```
你的核心需求是？
├─ 中文项目 / 国内访问
│   ├─ 强角色一致性 → Seedance 2.0
│   ├─ 灵活运镜 → Kling 2.1
│   └─ 人物表演 → Hailuo 02
│
├─ 全球项目 / 不限地区
│   ├─ 最强物理表现 → Veo 3 / Sora 2
│   ├─ 运镜精确控制 → Runway Gen-4
│   └─ 风格化特效 → Pika 2.2
│
└─ 预算敏感
    ├─ 性价比首选 → Kling 2.1
    └─ 免费试用 → Pika / Runway 试用版
```

---

## 完整制作流程的工具组合

实际项目通常**多工具组合**，不只用一个：

```
角色 / 概念图生成：Midjourney / Flux
       ↓
视频生成：Seedance / Kling / Sora / Veo（按需选）
       ↓
关键单镜表演：Hailuo（如需）
       ↓
特效插入：Pika（如需）
       ↓
音乐生成：Suno AI
       ↓
音效素材：Splice / Epidemic Sound / freesound
       ↓
剪辑 + 调色：DaVinci Resolve
```

---

## 后期工作流详解

### 调色配方（DaVinci Resolve）

按选择的风格调整。以下是几种常见风格的节点配方。

**蒙考拉冷玩配方：**

```
节点1：基础校准 — 拉低饱和度至 60%
节点2：色彩平衡 — 阴影推青蓝（青+15，蓝+10）
                  中间调推青（青+8）
                  高光略推蓝（蓝+5）
节点3：曲线 — S 型曲线增加对比度，压暗阴影
节点4：色相 vs 饱和度 — 单独压低橙色和黄色饱和度（-30）
节点5：LUT — 套一个 Sicario / Deakins 风格的 LUT 微调
节点6：颗粒 — 加 35mm 胶片颗粒质感（强度 15-20%）
```

**沙丘古黑配方：**

```
节点1：拉低饱和度至 50%
节点2：阴影推土黄（黄+12，红+5）
        中间调推暖（红+8，黄+5）
        高光略推红（红+10）
节点3：曲线 — 重压阴影，提中间调
节点4：减弱蓝色和绿色饱和度
节点5：套 Dune 风格 LUT
节点6：重颗粒（强度 25-30%）
```

**栖地东方幻配方：**

```
节点1：拉低饱和度至 65%
节点2：阴影推墨绿（绿+8，蓝+5）
        中间调推青（青+10）
        高光保持中性
节点3：S 曲线但压制更柔
节点4：去除红色饱和（-50）
节点5：加水墨纸质感叠加（10% 透明度）
节点6：轻颗粒（强度 10-15%）
```

### 剪辑节奏表

为每个镜头切点标注处理方式：

```
| 切点 | 处理 |
|------|------|
| 慢 → 慢 | 缓淡入 0.5-1s |
| 慢 → 快 | 硬切 + 闪白 0.15s |
| 快 → 快 | 硬切，无过渡 |
| 快 → 慢 | 慢淡入 1s |
| 高潮起始 | 一声低频「咚」配合硬切 |
| 关键回响 | 眼神匹配剪辑 / 动作匹配剪辑 |
| 情绪转折 | 0.3 秒黑屏过渡 |
| 时间跳跃 | 闪白 + 模糊过渡 |
```

### 字幕字体推荐

| 用途 | 中文推荐 | 英文推荐 |
|------|---------|---------|
| 电影感主标题 | 思源宋体 Heavy | Bodoni / Didot |
| 手写苍劲感 | 汉仪尚巍手书 / 字魂龙吟手书 | Pacifico (轻量) |
| 古风 | 思源宋体 / 方正瘦金书 | Trajan Pro |
| 现代极简 | 思源黑体 Light / OPPO Sans | Helvetica Neue / Inter |
| 赛博朋克 | 阿里巴巴普惠体 Bold | Orbitron / Audiowide |
| 商业宣传 | 思源黑体 Bold | Montserrat Bold |

字幕颜色：纯白 #FFFFFF 或 微冷灰 #E8ECF0

### 输出格式

| 用途 | 分辨率 | 编码 | 帧率 |
|------|--------|------|------|
| 个人作品集 | 4K (3840x2160) | H.264 高码率 | 24fps |
| 社交媒体 | 1080p | H.264 标准 | 30fps |
| 提案演示 | 1080p | H.264 高码率 | 24fps |
| 网页展示 | 1080p | H.265 | 30fps |