# Fictional bookstore test / 虚构书店试片

**State: `assets-ready`.** The two references, four-shot plan, and video prompt are ready. The video has not been generated or reviewed.

On 2026-09-23, Dreamina showed Seedance 2.5 with Omni reference. The 12-second, 16:9, 480P option was quoted at 180 credits. The reference upload and generation are still pending; no credits have been spent on this example.

| Character reference / 人物图 | Four-panel storyboard / 四格分镜 |
| --- | --- |
| ![Fictional woman in yellow raincoat holding a blue envelope](character-reference.png) | ![Numbered storyboard for the four shots](storyboard-4panel.png) |

This fictional test checks four observable points: the same woman across shots; the envelope stays in her right hand through Shot 2; she places it on the counter in Shot 3; she leaves it on the counter in Shot 4. The plan sets four three-second shots within 12 seconds.

## Dreamina / 即梦交接

1. In AI Video, check which Seedance model, reference mode, duration, ratio, and resolution your account actually offers. If Seedance 2.5 and Omni reference are available, select them.
2. Upload `character-reference.png` first and `storyboard-4panel.png` second. Insert their actual `@` tags with the UI picker. Replace the textual `Image 1` and `Image 2` labels in [`video-prompt.txt`](video-prompt.txt) with those tags.
3. If 12 seconds is available, use 12 seconds at 16:9. If not, adjust [`plan.json`](plan.json) and the shot times in the prompt before generation. Select resolution using the available UI options.
4. Fill in the [run notes](run-notes.md) with the actual model, mode, settings, cost, task ID, date, and video. Inspect the returned video with the [QA rubric](../../skills/seedance-production-workflow/references/qa-rubric.md). Record the second of every failure before a retry.

Reference images were generated for this fictional example on 2026-09-23. The prompt and shot plan are original to this project. No third-party creator video or complete case prompt is included. The [Dreamina guide](https://dreamina.capcut.com/seedance/how-to-use-seedance-2-5) describes Omni reference and `@` tags; this example has not yet been run through that interface.
