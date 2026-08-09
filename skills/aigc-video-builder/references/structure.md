# Prompt 结构 — 通用段落词汇表

这是组装工具箱。所有风格都由这些段落搭建而成。按场景需要选用，按下方规范顺序排列。用不到的直接跳过——一条简单的 oner 可能只用其中六个段落，一条完整的商业广告可能全部用上。

**注意：段落名称（STYLE、LIGHTING、CONSTRAINTS 等）和 prompt 正文一律保持英文**——这是给视频模型看的。中文只出现在交付给用户的解释部分。

## 规范顺序

1. **STYLE**（风格）— 画面的"长相"。渲染类型（8K photoreal / Pixar-quality 3D / UE5 in-engine / anamorphic film）、调色、颗粒感、情绪基调。游戏风格要明确写 NOT live-action / NOT film（不是实拍/不是电影）；写实风格要明确写 NOT 3D render / NOT game engine。这是整条 prompt 最重要的一行，必须放在开头。
2. **SCENE CONTEXT**（场景背景）— 一两句话：这是部什么片、总时长、分几段/几个镜头、画幅比例。
3. **ACTIVE REFERENCES / INPUT LOCK**（引用与输入锁定）— 逐条列出每个引用素材及其锁定的内容。图片用 `@image_1 — description. 100% matches the reference.` 视频合成用 `<<<video_1>>>` 加一条 INPUT LOCK 子句，点名所有原样保留的元素。（见下方"引用锁定"。）
4. **FORMAT MODE**（格式模式）— `Timed multishot, HARD CUTs on action`（定时多镜头，动作点硬切）或 `ONE CONTINUOUS TAKE, no cuts`（一镜到底无剪切）。声明摄影机不会自行剪切，剪切只发生在指定的时间点。
5. **LIGHTING**（灯光）— 光源、主光/轮廓光/点缀光、色温（用 Kelvin 标注白平衡）、体积光、场景内实用光源的合理性。当场景切换环境时，可按角色或段落分配各自的"光世界"。
6. **COLOR**（色彩）— 明确写出 60:30:10 的主色/辅色/点缀色分配。黑位压缩程度 / 饱和度水平 / 调色风格。
7. **CAMERA**（摄影机）— 镜头与运动语言：crash-zoom（急推）、macro probe（微距探针）、aerial drone（航拍）、snap-rack focus（快速变焦点）、dolly（轨道推拉）、steadicam（斯坦尼康）、FPV、chase-cam（追逐机位）、bullet-time orbit（子弹时间环绕）、speed-ramp（变速）。摄影机永远在运动。
8. **OPTICS**（光学参数，可选进阶）— 逐个剪切点标注焦段和角度，例如 `CUT 2 — ECU 14° HARD FAST ZOOM`。
9. **MATERIAL / SURFACES**（材质/表面）— 材质级写实：湿润的兽皮、藤壶、PBR 黏土、次表面散射的皮肤/毛发、珐琅、折射的水体、凝结的水珠。
10. **CHARACTER DESIGN**（角色设计）— 用具体细节描述原创设计。生物必须声明 "original, not based on any franchise"（原创，不基于任何 IP）。跨剪切锁定角色身份不漂移。
11. **SUBJECTS**（主体）— 具名实体及其行为；模型支持时使用 @handle 引用。
12. **PHYSICS**（物理）— 质量、重力、惯性、接触阴影、流体动力学、表面张力。明确写 "no floating props"（禁止悬浮道具）。
13. **ACTING / PERFORMANCE**（表演）— 微停顿、视线方向、呼吸、身体重量感、有表现力的表演。动画风格：卡通式夸张表情。有对白时：写出台词原文。
14. **COMPOSITION**（构图）— 三分法/黄金比例、走位调度、三层景深、"第一帧就有运动"。
15. **LOCATION / LOCATION MAP**（场景/场景地图）— 世界观设定，加一份前景/中景/背景拆解，以及摄影机穿越场景的路径。
16. **FIRST FRAME / BLOCKING**（首帧/走位）— 开场第一帧画面上到底有什么（并且必须已经有东西在动）。
17. **CONTINUITY**（连续性）— 每次剪切之间保持完全一致的元素（角色、道具、环境、HUD、那只特定的眼睛等）。写明 "No identity drift."（身份不漂移）。
18. **HUD LAYER**（HUD 层，仅游戏风格）— 每个 UI 元素、屏幕钉死（screen-pinned）、精确文字与颜色。见 styles.md → 游戏。
19. **ACTION / SHOT BREAKDOWN**（动作/镜头拆解）— 核心价值所在。逐镜头或逐节拍描述，带时间码。见下文。
20. **TECHNICAL**（技术参数）— 帧率、分辨率、"no jitter/aliasing"（无抖动/锯齿）、运动模糊快门。
21. **AUDIO**（音频）— 环境内真实音效（diegetic SFX）、配乐策略。默认 NO MUSIC，仅 SFX。
22. **CONSTRAINTS**（约束）— 画幅比例、硬性规则、比例锁定、绝对不允许发生的事。
23. **POSITIVE LOCKS**（正向锁定）— 最终重申不可打破的规则（引用保真度、logo、产品颜色、只出现一次的特效）。

## ACTION / SHOT BREAKDOWN — 镜头怎么写

大部分价值都在这里。两种模式：

### Multishot（多镜头）

每个镜头是一个带时间码的标注块，以硬切结束：

```
SHOT 1 (0:00–0:05) — [camera framing + movement]: [what happens, action verb first]. [scale/detail beat]. Hard cut.
SHOT 2 (0:05–0:10) — ...
```

或者方括号分段风格：

```
[Section 1 — 0.0–2.0s] CHARACTER A, [framing matching @image_1]. [Action]. [Detail beat]. [Camera move that ends the section].
HARD CUT —
```

规则：每个镜头都要写明取景方式和摄影机运动。每个镜头以动作开头，不以环境描写开头。明确写出每个剪切点落在哪一秒。如果有特效（film burn、strobe、speed-ramp），要声明它只在指定时刻发生一次，硬进硬出（hard in/out）。

### Oner（一镜到底）

一整段连贯文字，节拍用时间戳区间标注，全程绝无剪切：

```
Single continuous shot 15s: [opening, already in motion]... at the three-second mark [beat]... [speed-ramp moment] time ramps into slow motion... [recovery] snaps back to full speed... before [closing motion] without ever pulling up or back.
```

规则：唯一允许的速度变化是明确点名的 speed-ramp / bullet-time 节拍，且必须回归正常速度。开头声明 "one take no cuts"，结尾声明 "never pulling up or back" / "no edits"。把摄影机当成一个飞行/追逐的存在来写。

## 引用锁定 — 精确措辞

- **图片引用（延展场景，不冻结画面）：**
  `@image_1 is the master STYLE REFERENCE, not a fixed keyframe. Match its look 100%. DO NOT use it as a frozen keyframe — set the scene in motion and let the world extend forward. Introduce no new characters, props or palette.`
  （中文含义：@image_1 是总风格参考，不是固定关键帧。100% 匹配其外观，但不许把它当冻结画面——让场景动起来、让世界向前延展，不引入新角色/道具/配色。）
- **图片引用（身份锁定）：**
  `@image_1 — [character]: [description]. 100% matches the reference.`
- **视频合成（输入锁定）：**
  `INPUT LOCK — <<<video_1>>> matches input 100%. The entire source clip is preserved UNCHANGED: [list every element]. Do NOT re-grade, re-time, smooth, or re-frame anything. The ONLY additions are [the new element and its physical effects].`
  （中文含义：源片 100% 原样保留，逐项列出保留的元素；禁止重新调色、变速、平滑、重新构图；唯一新增的只有新元素及其物理影响。）
- **产品/具名链接：** 当作产品引用处理——logo、颜色、摆放必须完全一致；重申锁定的文字（例如 logo 必须精确显示为 BEGIM；精华液保持绿色）。

## 变速与特效词汇

- **Speed-ramp（变速）：** 常速 → 慢动作 → 常速，由一个具名事件触发（颠簸、打击、险些相撞）。必须回归正常速度。
- **Bullet-time（子弹时间）：** 时间冻结的瞬间，摄影机环绕悬停的动作旋转。
- **Film burn（胶片灼烧）：** 一次性化学灼烧转场；声明只发生一次、在哪个时间码、硬进硬出、绝不渗入其他剪切。
- **Strobe flash / hard match-cut（频闪/硬匹配剪切）：** 动作点上的瞬间剪切，无叠化。

其余一切场合默认：**NO slow-motion**——除非某个节拍明确需要慢动作。

## 交付前自检清单

- [ ] STYLE 行位于开头，写明渲染类型（游戏/写实风格还要写明它"不是"什么）。
- [ ] 第一秒内摄影机已在运动；动作立即开始。
- [ ] 三层景深齐全；巨大物体旁有人物提供比例参照。
- [ ] 每个引用素材都有 100%-match / input-lock 锁定子句。
- [ ] 有物理段落（质量、接触阴影、禁止悬浮）。
- [ ] 剪切点（或"无剪切"）带时间码明确声明。
- [ ] 有 AUDIO 段落；配乐策略已声明。
- [ ] 画幅比例 + 总时长已声明。
- [ ] 从构建层面规避了内容政策风险（见 content-policy.md）。
- [ ] 格式符合用户规范：密集、指令式、按规范段落顺序。
- [ ] 英文 prompt 代码块之后附有逐段中文解释。
