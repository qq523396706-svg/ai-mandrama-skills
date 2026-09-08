<p align="center">
  <img src="assets/readme/ai-mandrama-workflow-hero.webp" alt="AI 漫剧从故事板、人物表演、声音波形、视频时间线到最终成片的完整生产链" width="100%" />
</p>

<h1 align="center">AI Content Pipeline Skills</h1>

<p align="center">
  <strong>把零散的 AI 创作能力，组织成可以持续运行的内容生产线。</strong><br />
  一套可恢复、可审计、可返修的 Agent Skills 系统；首发版本聚焦多集 AI 剧情作品的完整生产链。
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Skills-6-00B7FF?style=for-the-badge" alt="6 个 Agent Skills" />
  <img src="https://img.shields.io/badge/Pipeline-9_Stages-6366F1?style=for-the-badge" alt="9 个生产阶段" />
  <img src="https://img.shields.io/badge/Version-2.0.0-A855F7?style=for-the-badge" alt="版本 2.0.0" />
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-F59E0B?style=for-the-badge" alt="MIT License" /></a>
</p>

---

AI 视频真正困难的，通常不是某一个镜头能不能生成，而是：人物能否跨镜保持一致、台词与镜长是否匹配、付费任务是否越过授权、失败后该改哪一层，以及平台返回“成功”之后，最终文件是否真的能交付。

**AI Content Pipeline Skills 专门管理这些容易失控的环节。** 它不是一个越来越长的万能提示词，也不绑定某个视频平台；它把复杂制作拆成职责清楚的 Agent Skills、可恢复的阶段交付物和明确的批准点，让创作、执行、返修和验收各自有据可查。

当前 `2.0.0` 首发包包含 6 个 AI 漫剧专项 Skill。仓库名称为后续扩展预留空间，但不会把尚未发布的能力写成已经具备：小说自动化创作、自动化剪辑与跨平台内容运营只有在完成独立重写、测试和审计后，才会作为新的模块加入。

## 你能直接得到什么

| 能力 | 带来的改变 |
|---|---|
| **稳定推进** | 故事、剧本、角色、声音和镜头状态都有版本，不靠聊天记忆维持长项目 |
| **精准返修** | 问题会定位到剧本、表演、声音、口型、生成或剪辑责任层，不再整条盲目重做 |
| **费用可控** | 上传、付费、肖像和声音授权分别设门，批量任务有预算、回执与有限重试 |
| **成片可验** | 最终结论来自真实文件完整播放，不把任务成功、缩略图或抽帧当成交付成功 |

## 为什么它和普通工作流不一样

| 常见断点 | 本仓库的做法 | 实际价值 |
|---|---|---|
| 一个 Agent 同时写剧本、改表演、跑生成、做验收 | 总控只协调版本和批准点，专项 Skill 各守一层 | 减少角色混乱和越权修改 |
| 每次对话都重新解释人物、场景和上一集状态 | 使用项目登记、版本交付物和连续性记录 | 多集项目可暂停、恢复和交接 |
| 生成失败就换模型、换提示词、重复付费 | 先记录错误证据，再只改与证据相关的变量 | 降低无诊断重试和预算浪费 |
| 音频时长、嘴型和镜头节奏到最后才发现冲突 | 在正式生成前做声音路线和时长预演 | 把昂贵问题提前暴露 |
| 平台显示完成就视为成片通过 | 口型专项检查与最终文件完整验收分开进行 | 技术成功不再冒充内容成功 |
| 工作流被某个模型或工具锁死 | 平台、TTS、图片和剪辑能力通过接口接入 | 可以替换执行工具而保留治理链路 |

## 从故事到成片的九阶段生产链

```mermaid
flowchart LR
    A["SCOPE<br/>范围 · 权利 · 预算"] --> B["STORY<br/>系列规则 · 人物选择"]
    B --> C["SCRIPT<br/>行动 · 台词 · 因果"]
    C --> D["DESIGN<br/>角色 · 场景 · 连续性"]
    D --> E["PLAN<br/>镜头 · 表演 · 状态"]
    E --> F["TIMING<br/>声音 · 时长预演"]
    F --> G["GENERATE<br/>任务 · 回执 · 重试"]
    G --> H["ASSEMBLE<br/>剪辑 · 音画整合"]
    H --> I["VERIFY<br/>口型 · 成片 · 权利"]

    classDef plan fill:#0F172A,stroke:#22D3EE,color:#F8FAFC,stroke-width:2px;
    classDef make fill:#161436,stroke:#8B5CF6,color:#F8FAFC,stroke-width:2px;
    classDef finish fill:#2A1607,stroke:#F59E0B,color:#FFF7ED,stroke-width:2px;
    class A,B,C,D plan;
    class E,F,G,H make;
    class I finish;
```

六个批准点把“内部规划”和“允许执行”分开：`STORY_ACCEPTED`、`SCRIPT_ACCEPTED`、`DESIGN_ACCEPTED`、`TIMING_ACCEPTED`、`GENERATION_ALLOWED`、`DELIVERY_ACCEPTED`。前一阶段没有得到具体版本批准，后一阶段不会自行越过。

## 六个 Skill，各自只做擅长的事

| Skill | 核心职责 | 解决的问题 |
|---|---|---|
| [`ai-mandrama-production`](skills/ai-mandrama-production/) | 判断当前阶段、管理批准点、分派执行器、追踪版本与返修影响 | 防止总控越俎代庖，让长项目始终知道“现在在哪、下一步是什么” |
| [`emotion-performance-director`](skills/emotion-performance-director/) | 把人物意图转换成可观察、可生成、可复验的行为变化 | 避免空泛的“更有情绪”，同时保护台词、道具结果和现实任务 |
| [`mandrama-voice-director`](skills/mandrama-voice-director/) | 维护角色声音护照，设计逐句语速、重音、停顿、气息与目标时长 | 保持角色声音身份，提前发现台词与镜长冲突 |
| [`mandrama-lipsync-qc`](skills/mandrama-lipsync-qc/) | 播放实际视频，检查说话人归属、开合时机、连续说话与音画偏移 | 区分“声音问题”和“嘴型问题”，给出可定位返修意见 |
| [`seedance-batch-ops`](skills/seedance-batch-ops/) | 管理批量任务、预算、授权、回执、有限重试、下载映射与文件检查 | 让外部生成任务可追踪、可复算，不因失败无限烧钱 |
| [`mandrama-final-qc`](skills/mandrama-final-qc/) | 完整播放最终候选，汇总故事、连续性、声音、技术与权利结论 | 只有真实最终文件通过，才签发 `ACCEPT` |

## 设计上的核心优势

### 1. 对长项目友好

所有关键决定落在磁盘交付物中，而不是只存在于聊天上下文。项目可以跨天、跨窗口、跨执行者恢复；修改某个版本时，也能追踪它会影响哪些下游产物。

### 2. 创意自由与执行边界并存

故事和表演允许探索，但上传、付费、真人肖像、声音克隆和公开发布不会被“顺手执行”。事实、假设和未知项分开记录，避免把推测逐轮固化成项目事实。

### 3. 返修责任清楚

剧本问题不会推给口型，口型问题不会靠改台词掩盖，生成失败也不会无诊断地换模型。每个专项 Skill 都输出问题位置、责任层、严重度和建议复验范围。

### 4. 把昂贵错误前移

正式生成前先检查声音路线、台词时长、人物动作负荷和镜头节奏。能够在文本或低成本预演阶段发现的问题，不拖到批量生成后处理。

### 5. 平台中立，可组合扩展

仓库定义输入、输出和批准契约，不捆绑具体模型、付费 API、TTS 或剪辑软件。你可以连接自己的故事开发、视频提示词、图片生成、声音和后期工具，而不必重建整条治理链。

### 6. 验收的是作品，不是任务状态

平台任务 ID、下载完成和技术可播放，只能证明流程走到某一步。最终 Skill 要完整播放候选文件，并对照批准剧本、镜头、声音、连续性、交付规格和权利边界后再作结论。

## 适合谁

- 正在制作多集 AI 漫剧、动态漫或连续剧情短视频的个人创作者；
- 需要多人或多个 Agent 协作、又担心版本和责任混乱的制作团队；
- 已经有生成工具，但缺少批准、预算、返修与最终验收闭环的工作流维护者；
- 想把现有模型替换为新平台，同时保留项目结构和生产记录的开发者。

## 快速开始

安装前确认目标 Skill 目录不存在同名文件夹。以下命令遇到同名目录会停止，不会覆盖你正在使用的版本。

### Windows PowerShell

```powershell
git clone https://github.com/qq523396706-svg/ai-content-pipeline-skills.git
$sourceRoot = (Resolve-Path '.\ai-content-pipeline-skills\skills').Path
$destinationRoot = Join-Path $env:USERPROFILE '.codex\skills'
New-Item -ItemType Directory -Path $destinationRoot -Force | Out-Null

Get-ChildItem -LiteralPath $sourceRoot -Directory | ForEach-Object {
    $destination = Join-Path $destinationRoot $_.Name
    if (Test-Path -LiteralPath $destination) {
        throw "Existing Skill will not be overwritten: $destination"
    }
    Copy-Item -LiteralPath $_.FullName -Destination $destination -Recurse
}
```

### macOS / Linux

```bash
git clone https://github.com/qq523396706-svg/ai-content-pipeline-skills.git
source_root="$(cd ai-content-pipeline-skills/skills && pwd)"
destination_root="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$destination_root"

for source_dir in "$source_root"/*; do
  name="$(basename "$source_dir")"
  destination="$destination_root/$name"
  if [ -e "$destination" ]; then
    echo "Existing Skill will not be overwritten: $destination" >&2
    exit 1
  fi
  cp -R "$source_dir" "$destination"
done
```

其他支持 Agent Skills 的宿主可能使用不同目录，请遵循对应产品文档。

## 三个最小调用示例

接收一个新项目：

```text
使用 $ai-mandrama-production 接收这个多集剧情项目。先完成 SCOPE 登记，区分事实、假设与未知项；在正式生成前列出需要我确认的费用、上传和素材权利。
```

把“演得更好”变成可执行表演：

```text
使用 $emotion-performance-director 为已批准镜头建立表演卡。保持台词、道具结果和摄影任务不变，写清人物的现实任务、注意力变化、可观察动作与镜尾状态。
```

检查真实最终文件：

```text
使用 $mandrama-final-qc 完整播放最终候选。所有画内对白交给 $mandrama-lipsync-qc；无法完整观看时不要签发 ACCEPT。
```

## 外部能力与边界

仓库不捆绑系列故事开发、单集剧本、图片生成、视频提示词编译、TTS、视频平台、剪辑软件或 FFmpeg。它们应在目标环境中独立安装、授权和核验。引用某个外部 Skill 或工具名称，不代表本仓库包含、安装、授权或认可它。

平台模型、价格、规格和上传限制属于执行当天事实。正式生成前应重新核验；本仓库不会把易变化的平台参数写成永久承诺。

## 验证与可信度

- 六个 Skill 当前版本均为 `2.0.0`，并通过官方 `quick_validate.py`。
- 总控路由、相对链接、frontmatter、敏感信息和发布边界均做过自动检查。
- 重写方法、来源范围和相似度结果记录在 [REWRITE_AUDIT.md](REWRITE_AUDIT.md)。
- 可执行验收场景见 [tests/acceptance-cases.md](tests/acceptance-cases.md)。

## 许可证与权利说明

- 本仓库内的原创表达按 [MIT License](LICENSE) 授权。
- 已知来源与第三方边界见 [THIRD_PARTY.md](THIRD_PARTY.md)。
- 本仓库不授予任何人物肖像、声音、音乐、字体、图形、品牌、客户内容或第三方 IP 的使用权。
- 本项目是由曾接触旧版材料的同一执行环境完成的隔离重写，不能作为严格 clean-room 法律抗辩。
- 发布审计降低了直接复制风险，但不构成法律意见或对任何司法辖区结果的保证。

---

<p align="center">
  <strong>让 AI 视频生产可创作、可控制、可恢复，也可真正验收。</strong>
</p>
