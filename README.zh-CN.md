# Seedance Awesome Director

这是一个把 Seedance 视频从想法推进到实际成片检查的独立 Agent Skill：规划参考图和镜头、校验时间轴、准备生成交接包，并按时间点检查和修复结果。

**当前状态：公开试片。** [虚构书店试片](examples/bookstore-envelope/README.md)提交展示的成片是[即梦 AI 生成画面的 10 秒最终版](examples/bookstore-envelope/dreamina-seedance-2.5-edited-10s-480p.mp4)：从[未经剪辑的约 12 秒原片](examples/bookstore-envelope/dreamina-seedance-2.5-raw-12s-480p.mp4)裁去开头 2 秒，原片作为来源证据保留。试片还包含两张参考图、实际提交的提示词和[核对记录](examples/bookstore-envelope/qa.md)。成片左上角仍有 `AI` 标记；目前不宣称比其他工作流画质更好。

[English](README.md)

![虚构书店试片的四格编号分镜](examples/bookstore-envelope/storyboard-4panel.png)

## 仓库内容

- [可安装的 Skill](skills/seedance-production-workflow/SKILL.md)
- [可修改的制作模板](skills/seedance-production-workflow/references/editable-template.md)：brief、参考图、分镜与视频提示词字段
- [时间轴预检脚本](skills/seedance-production-workflow/scripts/validate_plan.py)：检查镜头顺序、时长、必填字段和参考图 ID
- [成片检查表](skills/seedance-production-workflow/references/qa-rubric.md)：按时间点定位失败并决定最小改动
- [书店试片示例](examples/bookstore-envelope/README.md)：原创四镜头情境、两张图、计划、提示词、10 秒最终版、原片与来源记录

Skill 会按任务选控制件。单镜头可以只用时间轴；需要严格镜头顺序时用编号分镜；需要人物或产品一致性时再加主参考图。参考图只能提供控制信号，最终是否稳定要看真实成片。

## 安装到 Codex

```bash
npx skills add pursurer/seedance-awesome-director --skill seedance-production-workflow -g -a codex
```

[skills CLI](https://github.com/vercel-labs/skills)支持从 GitHub 选择一个 Skill 并全局安装到 Codex。也可以手工复制：

```bash
git clone https://github.com/pursurer/seedance-awesome-director.git
mkdir -p ~/.codex/skills
cp -R seedance-awesome-director/skills/seedance-production-workflow ~/.codex/skills/
```

在新任务中说：`请用 $seedance-production-workflow 为一个 12 秒四镜头视频准备参考图、分镜、视频提示词和成片检查表。`

准备阶段不需要付费 API。真正提交 Seedance 时，以你账号中可用的模型、时长、参考模式和费用为准，并记录任务 ID、参数和结果。

## 查看或复现本仓库试片

1. 看 [brief](examples/bookstore-envelope/brief.md)、[参考图职责](examples/bookstore-envelope/reference-map.md) 和 [四镜头计划](examples/bookstore-envelope/plan.json)。
2. 运行 `python3 skills/seedance-production-workflow/scripts/validate_plan.py examples/bookstore-envelope/plan.json`。
3. 查看[提交展示的 10 秒最终版](examples/bookstore-envelope/dreamina-seedance-2.5-edited-10s-480p.mp4)、[运行清单](examples/bookstore-envelope/run-manifest.json)及[核对记录](examples/bookstore-envelope/qa.md)。[未经剪辑的生成原片](examples/bookstore-envelope/dreamina-seedance-2.5-raw-12s-480p.mp4)用于核对来源；最终版删除了原片 00:00–00:02，即梦没有直接输出 10 秒文件。
4. 如要在自己的即梦账号复现，先核对当前模型、参考模式、时长、画幅、分辨率与积分价格；按[检查表](skills/seedance-production-workflow/references/qa-rubric.md)检查自己的成片，不把本次单样本当作必然结果。

运行 `python3 -m unittest discover -s skills/seedance-production-workflow/scripts -p 'test_*.py'` 可检查预检脚本。本仓库的试片提示词、图片和 Skill 文本为此次项目制作；Skill 只链接 [awesome-seedance](https://github.com/LearnPrompt/awesome-seedance) 的相关结构模板，没有转载创作者的完整案例提示词或媒体。

本项目独立于字节跳动、即梦和 LearnPrompt。模型能力及账号入口可能变化，实际生成前须核对当前界面。

## 许可

MIT，见 [LICENSE](LICENSE)。
