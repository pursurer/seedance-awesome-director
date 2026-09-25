# Seedance Awesome Director

An independent Agent Skill for taking a Seedance video from a brief to a checked result. It plans references and shots, validates timing, prepares a generation handoff, and reviews the returned video shot by shot.

**Status:** public pilot. The submitted video for the [fictional bookstore example](examples/bookstore-envelope/README.md) is the [10-second final cut of AI-generated Dreamina footage](examples/bookstore-envelope/dreamina-seedance-2.5-edited-10s-480p.mp4). It removes the first 2 seconds of the [unedited 12-second generation](examples/bookstore-envelope/dreamina-seedance-2.5-raw-12s-480p.mp4), which is retained for provenance. The example also includes the reference images, exact submitted prompt, and [QA notes](examples/bookstore-envelope/qa.md). The video retains an `AI` marker; no quality improvement over another workflow is claimed.

[简体中文](README.zh-CN.md)

![Four numbered panels for the fictional bookstore test](examples/bookstore-envelope/storyboard-4panel.png)

## What is included

- [`seedance-production-workflow`](skills/seedance-production-workflow/SKILL.md): the installable Skill.
- [Editable production template](skills/seedance-production-workflow/references/editable-template.md): brief, image references, storyboard, and video prompt fields.
- [Plan validator](skills/seedance-production-workflow/scripts/validate_plan.py): checks shot timing, order, required fields, and reference IDs before generation.
- [QA rubric](skills/seedance-production-workflow/references/qa-rubric.md): checks the actual output and records a precise repair.
- [Bookstore example](examples/bookstore-envelope/README.md): an original four-shot test with references, plan, prompt, final 10-second video, source output, and run provenance.

The Skill chooses the production controls that fit the request. A single continuous shot may need only a time plan. Exact multi-shot order may benefit from a numbered storyboard. Identity-sensitive work may also need a master character or product reference. The video model's response to those controls must be checked on the generated result.

## Install in Codex

```bash
npx skills add pursurer/seedance-awesome-director --skill seedance-production-workflow -g -a codex
```

The [skills CLI](https://github.com/vercel-labs/skills) supports GitHub repositories, selecting one Skill, and global Codex installation. Manual copy is also possible:

```bash
git clone https://github.com/pursurer/seedance-awesome-director.git
mkdir -p ~/.codex/skills
cp -R seedance-awesome-director/skills/seedance-production-workflow ~/.codex/skills/
```

Start a new Codex task and ask: `Use $seedance-production-workflow to plan a 12-second four-shot Seedance video. Prepare references, a storyboard, a prompt, and a QA checklist.`

This Skill does not require a paid API to prepare the package. Video submission uses the Seedance entry point available to the user and may consume credits. The Skill records the actual model, settings, cost, and result when that step is run.

## Inspect or reproduce the pilot

1. Inspect the [example brief](examples/bookstore-envelope/brief.md), [reference map](examples/bookstore-envelope/reference-map.md), and [four-shot plan](examples/bookstore-envelope/plan.json).
2. Run `python3 skills/seedance-production-workflow/scripts/validate_plan.py examples/bookstore-envelope/plan.json`.
3. Inspect the [submitted 10-second final video](examples/bookstore-envelope/dreamina-seedance-2.5-edited-10s-480p.mp4), [manifest](examples/bookstore-envelope/run-manifest.json), and [QA notes](examples/bookstore-envelope/qa.md). The [unedited generation](examples/bookstore-envelope/dreamina-seedance-2.5-raw-12s-480p.mp4) documents its source. The final video removes 00:00–00:02 of that source; Dreamina did not directly output a 10-second file.
4. If you run the prompt in your own Dreamina account, check its current model, reference mode, duration, ratio, resolution, and credit price first. Review your result against the [QA rubric](skills/seedance-production-workflow/references/qa-rubric.md); the recorded output is one run, not a guaranteed result.

## Verification and provenance

Run `python3 -m unittest discover -s skills/seedance-production-workflow/scripts -p 'test_*.py'` to check the plan validator. The example prompt, reference images, and Skill text were created for this project. The Skill links to relevant [awesome-seedance templates](https://github.com/LearnPrompt/awesome-seedance) for prompt structures; it does not republish a creator's complete case prompt or media.

This project is independent of ByteDance, Dreamina, and LearnPrompt. Model capabilities and account availability can change; the Skill points to provider documentation and requires the actual interface to be checked before generation.

## License

MIT. See [LICENSE](LICENSE).
