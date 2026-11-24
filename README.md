**English** | [简体中文](README.zh-CN.md)

# Character Motion Recreation Director

### Turn “make this character do that” into a production plan your team can execute.

**person-video-remake** transforms a motion reference, a target character image, and production requirements into a timed action breakdown, identity constraints, shot prompts, a RunningHub handoff, and an output review checklist. Use it for fictional character demonstrations, authorized model video adaptations, and character-led short videos.

![Four sampled frames from the 4-second motion recreation demo](preview.jpg)

**[Watch the 4-second demo](https://github.com/ultimatech-cn/person-video-remake/raw/refs/heads/main/demo.mp4)** · **[Download the Skill](https://github.com/ultimatech-cn/person-video-remake/releases/latest)** · [Detailed case · 中文](EXAMPLE.md) · [Agent instructions · 中文](SKILL.md)

> A useful motion reference has a starting pose, direction, range, pauses, and an ending pose—not just “copy this.” The application renders the video; the Skill helps an agent describe, hand off, and review the requirements.

## What you get

| Production stage | What the Skill helps the agent do | Deliverable |
|---|---|---|
| Understand the reference | Break down actions, camera, occlusion, and pauses; define left/right consistently | Timestamped action table |
| Define the character | Separate identity features, wardrobe, and permitted styling changes | Hair, clothing, and visible facial feature checklist |
| Write the brief | Organize subject, action order, camera, setting, and pacing | Shot prompts and appearance constraints |
| Hand off to an operator | Map files to fields actually present in the application | Upload and parameter mapping table |
| Review the result | Evaluate character, movement, timing, hands/feet, and sound separately | Timestamped findings and rerun recommendations |

This is an **agent-assisted directing and review workflow**. It is not a standalone video model, unrestricted face-swapping tool, or automatic generation client. Cloud generation is performed by the application; website operation requires authorization and suitable tools.

## A real completed example

The inputs were a simple stepping reference and a generated **fictional adult character** with shoulder-length dark hair, a blue blazer, white top, dark trousers, and white shoes. The output is a **4-second, 720×1280** portrait video.

- The alternative China-site application completed upload, generation, download, and local decoding.
- The main raise-hands → lower-hands events occurred near the reference intervals; the clothing colors remained recognizable.
- Facial details and body shape were only partially consistent, and subtle footwork was weak. This is not a claim of frame-exact motion transfer.
- The original input had no audio track, causing `KeyError: waveform`. Adding a silent AAC compatibility track allowed the same visual inputs to generate successfully.

The [full case · 中文](EXAMPLE.md) documents results, timing evidence, and the repair. The motion reference is by Secarver7 under CC BY 3.0. See [ATTRIBUTION.md](ATTRIBUTION.md) for the source, modifications, and attribution for the adapted output.

## Good use cases

- **Character short-video planning:** replace a vague “same movement” request with reviewable action events.
- **Fictional character demonstrations:** use a fictional adult image and attempt to preserve reference timing and recognizable wardrobe features.
- **Production handoffs:** specify exactly which file belongs in each field and avoid mismatches between prompts and application capabilities.
- **Troubleshooting and review:** distinguish audio compatibility issues, weak movement, and identity drift.

Use target-person material with authorization covering generation and the intended sharing. Reference analysis can proceed while authorization is being obtained; a visible photograph alone is not permission to use someone's likeness.

## Two application routes, different fields

The table reflects the **November 13, 2026 historical field check**. Recheck the live page and fees before running.

| Route | Input fields | Historical status |
|---|---|---|
| [Instagram Influencer Video Recreation](https://www.runninghub.ai/zh-cn/AI-DETAIL/2093879380232998913) | `Reference video`, `image`, `Supplementary prompts` | Public fields inspected; this international route was not run |
| [China site: video recreation / person, face, and clothing replacement](https://www.runninghub.cn/ai-detail/2063185999106236418) | Original video, model image, frame rate, start, duration, replacement target, size, etc. | Used for the completed 4-second demo |

The China-site application **does not have a general action-prompt field**. Prompts support planning and review; do not paste them into the custom-object-name field. The two applications are not mirrors, and one test does not validate both. Parameter details are in the [operator handoff · 中文](references/operator.md).

## Install and invoke

Download the release ZIP and place the extracted `person-video-remake` directory in your host's Skill directory. It must contain `SKILL.md` directly.

| Host | Location or entry point | Recorded status |
|---|---|---|
| Codex | `~/.codex/skills/person-video-remake/` | Historical fresh-session explicit invocation produced a plan |
| DeepSeek Harness | Project `.dsh/skills/person-video-remake/` | Directory adaptation provided; target-session triggering not tested |
| WorkBuddy | Upload Skill ZIP in the client's skill manager | Client import/triggering not tested |

The agent instructions and detailed operator documents are currently in Chinese. You can request an English plan with this prompt:

```text
Use person-video-remake. Reply and deliver the plan in English.
Reference: /absolute/path/reference.mp4
Target character: /absolute/path/authorized-person.png
Authorization: this generation and demonstration sharing are permitted.
Preserve the action order and pauses; keep the target image's clothing.
Output: 4-second portrait video.
First analyze action events, character consistency features, and real
application fields, then prepare an operator handoff.
After generation, review identity, motion, and timing separately;
do not promise pixel-exact matching.
```

The Skill itself requires no Python packages. Local media access, frame extraction, and website operation depend on host tools. This repository contains no built-in API caller, model weights, or automatic paid-task runner.

## Example files

| File | Purpose |
|---|---|
| [demo.mp4](demo.mp4) | Historical application output: 4-second portrait video |
| [target-person.png](target-person.png) | Fictional adult character image used in this case |
| [reference.mp4](reference.mp4) | 4-second CC BY 3.0 reference with silent AAC compatibility track |
| [preview.jpg](preview.jpg) | Output contact sheet sampled at 0.5 / 1.5 / 2.5 / 3.5 seconds |
| [EXAMPLE.md](EXAMPLE.md) | Detailed actions, application route, repair, and review · 中文 |
| [VERIFICATION.md](VERIFICATION.md) | Publication checks and their scope · 中文 |

## License

Original instructions and documentation use the [MIT License](LICENSE). Attribution, licensing, and modification notes for the third-party motion reference and adapted demo are listed in [ATTRIBUTION.md](ATTRIBUTION.md). AI images and outputs are not guaranteed to carry exclusive copyright or likeness/commercial-use rights. RunningHub and other services have their own terms and fees.
