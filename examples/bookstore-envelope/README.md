# Fictional bookstore pilot / 虚构书店试片

**State: a 10-second final video made from AI-generated footage, with a documented local trim and QA limitation.** This is an original workflow pilot for the [production Skill](../../skills/seedance-production-workflow/SKILL.md), not a GoodCase prompt submission or evidence that the workflow improves video quality over another method.

| Character reference / 人物图 | Final storyboard / 最终四格分镜 |
| --- | --- |
| ![Fictional woman in a yellow raincoat holding one blue envelope](character-reference.png) | ![Four-shot bookstore storyboard with an inward-opening door](storyboard-4panel.png) |

The [12-second source prompt](video-prompt.txt) and [plan](plan.json) use those two images in that order. The character image controls identity and wardrobe; the storyboard controls location, composition, and shot order. Neither asks the video to reproduce the gray studio background or panel borders. The prompt describes one green door opening inward on both entry and exit, hand-to-brass-handle contact, and a single blue envelope left on the oak counter.

## Submitted video and source

- **[Submitted final video, 10.000 s, 854×480](dreamina-seedance-2.5-edited-10s-480p.mp4)** — AI-generated Dreamina footage, locally trimmed from 00:02.000 and re-encoded with FFmpeg. Dreamina did **not** directly generate a 10-second file.
- [Unedited source generation, 12.064 s, 854×480](dreamina-seedance-2.5-raw-12s-480p.mp4) — retained for provenance. Dreamina Seedance 2.5, Omni reference, 16:9, 480P; 180 credits consumed in one authorized run on 2026-09-25.
- [20-frame contact sheet of the final video](edited-10s-contact-sheet.jpg), [run manifest](run-manifest.json), and [timestamped QA](qa.md).

The generated video retains a small `AI` marker at the upper left despite the prompt's no-watermark request. Sampled frames support the door and envelope sequence; they do not establish that every frame is artifact-free. The run is presented as a traceable pilot with that limitation, not as a perfect output or a matched comparison against another Skill.

The characters and reference images were generated for this fictional project. No third-party creator's full prompt or media is copied here. The repository's upstream contribution is a hand-maintained Skill improvement; prompt-case submissions follow a separate review path.
