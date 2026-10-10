# 船长AI视界 · AI 短剧制作技能集

把小说或故事素材整理成可检查、可修改、可交接的短剧制作资料。六个技能覆盖改编大纲、角色、角色参考图、场景道具、剧本和分镜；各阶段提供结构化 JSON、Markdown 或 HTML 报告，并用脚本检查关键质量要求。

> 本仓库发布的是技能与示例，不包含《开局签到荒古圣体》的小说原文或制作项目文件。技能中的示例素材仅用于演示和自测。

## 六个技能

| 技能 | 用途 | 主要交付物 |
| --- | --- | --- |
| [船长大纲](skills/chuanzhang-dagang/README.md) `chuanzhang-dagang` | 小说改编、分集梗概与爽点规划 | 大纲五件套、质量检查、评审报告 |
| [船长角色](skills/chuanzhang-juese/README.md) `chuanzhang-juese` | 角色梳理、人物画像、形象与音色提示词 | 角色表、设定提示词、评审报告 |
| [船长角色引用](skills/chuanzhang-jueseyinyong/README.md) `chuanzhang-jueseyinyong` | 以正面全身锚点制作同一角色的多视图参考图 | 图像资产记录、多视图、检查报告 |
| [船长场景](skills/chuanzhang-changjing/README.md) `chuanzhang-changjing` | 场景与叙事道具设定 | 美术设定、提示词、评审报告 |
| [船长小说脚本](skills/chuanzhang-xiaoshuojiaoben/README.md) `chuanzhang-xiaoshuojiaoben` | 分集梗概转场次、动作节拍和台词 | 结构化剧本、时长检查、评审报告 |
| [船长故事板](skills/chuanzhang-gushiban/README.md) `chuanzhang-gushiban` | 剧本转视频段落、镜头、关键帧与视频提示词 | 分镜、视频提示词、评审报告 |

推荐顺序：**大纲 → 角色 → 场景 → 剧本 → 故事板**。角色引用可在角色设定确认后制作，与场景设定并行。文本环节可先完成；参考图环节需要可用的生图模型或自定义出图命令。

## 安装

需要支持本地技能的 Codex 环境，以及 **Node.js 18 或更新版本**。本仓库脚本只使用 Node.js 标准库，无需 `npm install`。克隆仓库后，把 `skills` 下需要的文件夹复制到你的技能目录，并重新加载技能列表。

Windows PowerShell 示例（目标目录显式设在 E 盘）：

```powershell
git clone https://github.com/zhangxiansheng-888/chuanzhang-ai-shortdrama-skills.git E:\视频生成\chuanzhang-ai-shortdrama-skills
$source = 'E:\视频生成\chuanzhang-ai-shortdrama-skills\skills'
$target = 'E:\视频生成\.codex\skills'
New-Item -ItemType Directory -Force -Path $target | Out-Null
Get-ChildItem -LiteralPath $source -Directory | Where-Object Name -like 'chuanzhang-*' | ForEach-Object {
  Copy-Item -LiteralPath $_.FullName -Destination $target -Recurse -Force
}
```

已有同名技能时，请先备份个人修改再更新。其他系统可将这六个目录复制到自己的技能目录。安装位置由你的 Codex 配置决定。

## 怎么用

在 Codex 中给出小说或故事文本，并说明目标，例如：

> 使用 `chuanzhang-dagang` 把这部小说改编成 3 集短剧，每集约 2 分钟；接着运行 `chuanzhang-juese`、`chuanzhang-changjing`、`chuanzhang-xiaoshuojiaoben` 和 `chuanzhang-gushiban`，逐阶段检查并输出可查看的报告。角色定稿后再用 `chuanzhang-jueseyinyong` 制作参考图。

也可以只使用单个技能，例如“用 `chuanzhang-dagang` 体检已有大纲”。每个技能的 `SKILL.md` 是给智能体执行的说明，`README.md` 提供该技能的详细用法和命令示例。质量检查、数据整理和报告生成由本地脚本完成；故事取舍、人物设计、分场写作仍需智能体处理。参考图生成依赖所选模型的可用性、额度与输出路径配置。

## 关注船长AI视界

扫码关注 **船长AI视界** 公众号，获取 AI 短剧制作教程、技能更新和实际案例。

<img src="assets/chuanzhang-wechat-qr.jpg" alt="船长AI视界公众号二维码" width="220">

二维码由船长AI视界提供。

## 来源与许可

本仓库是基于 [shuohao-skills](https://github.com/eternityspring/shuohao-skills) 的定制版本，调整了技能名称、界面配色、品牌文案和部分说明。原项目采用 Apache License 2.0。各技能目录保留原许可文件和 NOTICE，并记录本地修改；请在再分发时一并保留。
