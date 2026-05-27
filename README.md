# hugo-skills

hugo 维护的 Claude Code / Claude.ai Skills 仓库。开箱即用，clone 下来就能让你的 Claude 多出一组专业能力。

## 仓库里有什么

| Skill | 适用场景 |
|-------|---------|
| [video_storyboard](skills/video_storyboard/) | 想用 AIGC 做视频但没思路 / 要把 IP 改成宣传片 / 需要一份可执行的分镜手册时调用。覆盖项目定位 → 调研 → 创意收敛 → 视觉锁定 → 分镜 → 迭代 → Prompt 输出全流程，工具中立（Seedance / Sora / Kling / Runway / Veo 通用） |
| [coding_new_feat](skills/coding_new_feat/) | 开发新功能时调用。把一个模糊的功能需求按"需求分析 → 任务拆解 → 逐步实现 → 每步验证 → 集成测试"五步法拆成 5-7 个可验证的小任务，一次只做一步、做完就验，避免一把梭到底反复翻车。工具中立 |
| [coding_fix_bug](skills/coding_fix_bug/) | 修 bug 时调用。按"收集线索 → 缩小范围 → 定位根因 → 安全修复"四步定位法，从异常现象倒推原因，给 AI 精确线索而不是让它猜，先诊断再动手、最小改动、改完防回归。覆盖 runtime error / 逻辑 bug / 类型错误 / 状态不同步等。工具中立 |

每个 skill 都是一个独立目录，包含 `SKILL.md`（主流程）和 `references/`（按需加载的支撑文档）。Claude 会读 `SKILL.md` frontmatter 里的 `description` 自动判断何时触发，你不需要手动 `/调用`。

---

## 快速开始

### 前置条件

- 已安装 [Claude Code](https://claude.com/claude-code)（CLI / Desktop / IDE 插件任一），或在用 Claude.ai。
- 本机有 `git`。

### 安装方式 A：克隆整个仓库（推荐）

一次性拿到所有 skill，后续 `git pull` 就能跟进更新。

```bash
# 1. 克隆到任意位置
git clone https://github.com/<owner>/hugo-skills.git ~/hugo-skills

# 2. 把需要的 skill 软链到 Claude Code 的 skills 目录
mkdir -p ~/.claude/skills
ln -s ~/hugo-skills/skills/video_storyboard ~/.claude/skills/video_storyboard
```

> 把 `<owner>` 换成本仓库实际的 GitHub 用户名。

只想给某个项目用，不想全局生效？把软链放到项目内即可：

```bash
mkdir -p <你的项目>/.claude/skills
ln -s ~/hugo-skills/skills/video_storyboard <你的项目>/.claude/skills/video_storyboard
```

更新：

```bash
cd ~/hugo-skills && git pull
```

### 安装方式 B：作为 git submodule

适合你自己也有 `.claude/` 仓库、想把外部 skill 当依赖管理的场景。

```bash
cd ~/.claude
git submodule add https://github.com/<owner>/hugo-skills.git hugo-skills
ln -s ../hugo-skills/skills/video_storyboard skills/video_storyboard
```

### 安装方式 C：只下载单个 skill

不想要整个仓库：

```bash
cd ~/.claude/skills
git clone --depth=1 https://github.com/<owner>/hugo-skills.git _tmp
mv _tmp/skills/video_storyboard .
rm -rf _tmp
```

### 安装方式 D：Claude.ai / Claude Desktop（无命令行）

1. 在 GitHub 页面点 `Code → Download ZIP`，解压。
2. 把 `skills/video_storyboard/` 整个文件夹重新压缩成 zip。
3. 打开 Claude.ai 或 Claude Desktop → Settings → Capabilities → Skills → Upload skill，选择上一步的 zip。

---

## 验证安装

随便新开一个 Claude Code / Claude.ai 会话，输入：

> 我想用 AI 做个 60 秒的 IP 宣传片，但还没想好怎么搞

如果 Claude 自动按"七阶段流程"开始引导（先问 **是什么 / 用途 / 时长** 三问），说明 video_storyboard 已正确加载。

没触发？检查清单：

- [ ] skill 目录名是 `video_storyboard`（**不能改名**，要和 `SKILL.md` frontmatter 里的 `name` 一致）
- [ ] `SKILL.md` 在 skill 根目录，没多嵌一层
- [ ] 软链路径正确：`ls -l ~/.claude/skills/video_storyboard` 能看到指向源文件
- [ ] 重启了 Claude Code / Claude Desktop，或新开了一个会话

---

## 目录结构

```
hugo-skills/
├── LICENSE
├── README.md
└── skills/
    ├── video_storyboard/
    │   ├── SKILL.md              # 主流程入口，Claude 会先读这个
    │   └── references/           # 按需加载的支撑文档
    │       ├── image-prompt-recipes.md
    │       ├── style-quickpick.md
    │       └── video-prompt-recipes.md
    ├── coding_new_feat/
    │   └── SKILL.md              # 新功能开发五步法
    └── coding_fix_bug/
        └── SKILL.md              # Bug 修复四步定位法
```

想把仓库里的 skill 改成自己用的版本？fork 一份，改 `SKILL.md` 里的 `description` 和具体步骤即可——Claude 完全按 frontmatter 描述来判断何时触发。

---

## 反馈与贡献

- 用得顺手 / 用得不顺手都欢迎开 issue。
- 想加新的 skill 或改进现有 skill，欢迎 PR：放到 `skills/<your-skill-name>/SKILL.md`，frontmatter 写清 `name` 和触发场景即可。

License: [MIT](LICENSE)。
