# AI Mandrama Skills — Isolated Rewrite

这是一组用于多集 AI 剧情视频生产的 Agent Skills。它们把项目范围、故事、剧本、设计、镜头计划、时长预演、生成、后期和最终验收分开管理，重点解决版本混乱、越过授权、角色漂移、无诊断重试和“任务成功即成片成功”等问题。

本目录是从空白脚手架建立的隔离重写版，不会替换本机正在使用的 Skill。当前仍处于公开授权审查阶段，不是已获准公开发布的开源版本。

## 包含内容

| Skill | 责任 |
|---|---|
| `ai-mandrama-production` | 判断当前工作区、管理批准点、分派执行器、追踪版本与返修影响 |
| `emotion-performance-director` | 把人物行动意图转换成可观察、可生成、可复验的行为变化 |
| `mandrama-voice-director` | 维护角色声音护照，指导批准台词的逐句声音表演和试听 |
| `mandrama-lipsync-qc` | 评估画内对白风险，播放实际视频检查说话人与嘴部同步 |
| `seedance-batch-ops` | 在预算和授权范围内管理多镜任务、回执、重试、下载与文件检查 |
| `mandrama-final-qc` | 完整播放最终候选，汇总故事、连续性、声音、技术和权利结论 |

所有 Skill 当前版本均为 2.0.0。

## 协作关系

```text
SCOPE
  ↓
STORY → SCRIPT → DESIGN
                  ↓
                PLAN ── emotion-performance-director
                  ↓
               TIMING ─ mandrama-voice-director
                  ↓
              GENERATE ─ seedance-batch-ops
                  ↓
              ASSEMBLE
                  ↓
               VERIFY ─ mandrama-lipsync-qc
                        mandrama-final-qc
```

总控只协调输入、批准与交付物，不接管专项判断。平台上传、付费、真人肖像、声音复制和公开发布都需要独立授权。

## 安装

安装前确认目标 Skill 目录不存在同名文件夹。示例命令遇到同名目录会停止，不会覆盖正在使用的版本。

### Windows PowerShell

```powershell
git clone <PRIVATE_REPOSITORY_URL> ai-mandrama-skills
$sourceRoot = (Resolve-Path '.\ai-mandrama-skills\skills').Path
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
git clone <PRIVATE_REPOSITORY_URL> ai-mandrama-skills
source_root="$(cd ai-mandrama-skills/skills && pwd)"
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

## 外部能力

仓库不捆绑以下能力：

- 系列故事开发、单集剧本和独立审稿 Skill；
- `seedance-video-prompt` 或其他视频提示词编译器；
- 图片生成、TTS、视频平台和剪辑工具；
- FFmpeg 等可选媒体检查程序。

这些组件需在目标环境中独立安装、授权和核验。引用某个 Skill 名称不会自动安装它，也不会扩大素材上传或付费权限。

## 最小示例

启动一个项目：

```text
使用 $ai-mandrama-production 接收这个多集剧情项目。先完成 SCOPE 登记，区分事实、假设与未知项，在任何正式生成前列出需要我确认的费用和素材权利。
```

检查人物表演：

```text
使用 $emotion-performance-director 为已经批准的镜头建立表演卡。保持台词、道具结果和摄影任务不变，并给出镜头结束时可供下一镜继承的状态。
```

检查最终文件：

```text
使用 $mandrama-final-qc 完整播放最终候选。所有画内对白交给 $mandrama-lipsync-qc；无法完整观看时不要签发 ACCEPT。
```

## 兼容性与验证

- 文档编码：UTF-8。
- 目录遵循 `SKILL.md`、可选 `agents/`、`references/` 和 `assets/` 约定。
- Windows 上运行验证器时启用 UTF-8，避免默认代码页干扰中文读取。
- 平台模型、价格、规格和上传限制属于执行当天事实，不由本仓库固定。

## 权利边界

- 当前没有授予开源许可证；参见 [LICENSE-PENDING.md](LICENSE-PENDING.md)。
- 重写过程、已知来源和仍未解决的问题见 [THIRD_PARTY.md](THIRD_PARTY.md) 与 [REWRITE_AUDIT.md](REWRITE_AUDIT.md)。
- 本仓库不授予任何人物肖像、声音、音乐、字体、图形、品牌、客户内容或第三方 IP 的使用权。
- 本目录由曾接触旧版材料的同一执行环境重写，因此只能称为隔离重写，不能作为严格 clean-room 法律抗辩。
- 在最终权利审核和用户明确确认前，仓库应保持私有，不得 push 到公开远端或声明 MIT。
