# i-have-asd

**Predictable output for autistic readers. You can see what is coming, and every switch happens the same announced way.**

[日本語](.github/readme/README.ja.md)

> **Not medical advice.** This is an output-style skill for AI coding assistants. It is not a diagnosis, a treatment, a therapy, or a medical device, and it has not been clinically tested. Autistic people differ from each other; nothing here describes any individual, and no diagnosis is needed to use it.

## What it does

A skill for your coding assistant. When it is on, the assistant stops improvising its shape. It uses four fixed patterns and literal wording.

| Pattern | What the assistant does |
| --- | --- |
| 1. Fixed reply frame | Every reply has the same four parts in the same order: `Now` / `This reply` / body / `Next`. |
| 2. Preview | Before anything happens: the goal, the number of steps, what will change and what will not. Sizes in concrete units. |
| 3. Fixed change notice | When the plan changes: `Change` / `Reason` / `Was` / `Now` / `Unchanged`. Old and new shown together. Never a silent change. |
| 4. Fixed switch | Moving between topics: `Closing: … — state` then `Switching to: …`. New items raised mid-task are parked, not jumped to. |

Plus:

- **Wording**: literal and concrete. No metaphor, idiom or sarcasm. One name per thing. Rules stated with their reason.
- **Questions**: one per reply, closed, with 2 or 3 options and a labelled recommendation. "No need to decide now" when that is true.
- **Predictable, not rigid**: the reader can change any pattern, and the changed pattern then stays fixed.

Full text: [skills/i-have-asd/SKILL.md](./skills/i-have-asd/SKILL.md). It is one file, and it is the only place the rules live.

### Example

Before:

> Sure! So I looked into it and actually I think we should probably take a slightly different approach here — I went ahead and tweaked the config a bit too. Let me know what you think!

After:

> Now: step 2 of 3 is finished. The test passes.
> This reply: 1 change notice, 1 question.
>
> Change: step 3.
> Reason: the planned command does not exist in this version.
> Was: run `build --fast`.
> Now: run `build`.
> Unchanged: steps 1 and 2, and the goal.
>
> Question: apply this change?
> 1. Yes, use `build` (recommended: it is the only command that exists).
> 2. No, keep the plan and stop here.
>
> Next: you choose 1 or 2. I have not changed any file.

## On and off

There is no configuration. The skill is on or off.

- `/i-have-asd` turns it on for the session.
- `stop asd mode` (or `normal mode`) turns it off.
- Always on: create the empty flag file `~/.claude/.i-have-asd-always`. Delete the file to go back to on-demand.

See [INSTALL.md](INSTALL.md).

## Sources

The rules are design choices for how an assistant should write. They are informed by the sources below, but they are not taken from them as clinical recommendations, and none of the sources evaluated an AI assistant.

Only pages that were actually opened and read while writing this (2026-11-13) are listed.

### NICE guideline CG142

Autism spectrum disorder in adults: diagnosis and management. Published 27 June 2012, last updated 14 June 2021.
https://www.nice.org.uk/guidance/cg142/chapter/Recommendations

| Recommendation | What it says | Used in |
| --- | --- | --- |
| 1.3.2 | When discussing care, take into account the "importance of predictability, clarity, structure and routine for autistic people" and the "increased propensity for elevated anxiety about decision-making". | Patterns 1 to 4; Questions |
| 1.6.3 | Adaptations include "a more concrete and structured approach with a greater use of written and visual information", "making rules explicit and explaining their context", "using plain English and avoiding excessive use of metaphor, ambiguity and hypothetical situations", and "offering regular breaks". | Wording; Pace and breaks |
| 1.8.14 | Staff should "be consistent and predictable, but with some flexibility to allow change and choice". | "Predictable, not rigid" |
| 1.2.2 | Lists "stereotypic (rigid and repetitive) behaviours, resistance to change or restricted interests" among the features that should prompt considering an assessment. | Patterns 3 and 4 |

These recommendations are written for health and social care staff. 1.6.3 is about adapting cognitive and behavioural interventions for coexisting mental disorders, and 1.8.14 is about residential care. The skill borrows only the communication adaptations. It is not an intervention.

### Japanese public guidance: 国立障害者リハビリテーションセンター 発達障害情報・支援センター

- 各障害の定義: https://www.rehab.go.jp/ddis/understand/definition
- 支援方法の学習: https://www.rehab.go.jp/ddis/howto/study/support
- 支援原則の学習: https://www.rehab.go.jp/ddis/howto/study/principle
- 自閉スペクトラム症 (発達障害情報のポータルサイト, linked from the centre's definition page): https://hattatsu.go.jp/supporter/healthcare_health/about-asd-2/

What these pages say:

- Numbered procedure sheets, and calendars or schedules that give a view of what is ahead, are described as often effective. A change from the usual is easier to understand when it is shown visually, either corrected on the same sheet or presented on a new one. → Patterns 2 and 3.
- Many people with pervasive developmental disorder traits are said to understand visual information more easily than spoken. → written structure.
- Abstract instructions, tacit understandings, figurative expressions, sarcasm and jokes can be hard to understand; use expressions that are as concrete as possible; explain rules properly. → Wording.
- For decisions, start by setting out a few options and make the merits and risks of each explicit. → Questions.
- The portal page notes that first-time situations and changes of schedule may be disliked (in its description of early childhood) and that adults may struggle with work that needs improvisation. → Patterns 2 to 4.

The centre's pages mostly describe support for children and for developmental disabilities in general. The skill applies the same ideas to written output for adults, which is a design choice.

## What it deliberately does not do

- It does not assess, diagnose, or describe the reader.
- It does not try to change how the reader communicates.
- It does not give advice on diagnosis, medication or therapy, and tells the assistant to decline if asked.
- It does not mention autism unless the reader does.

## Credits

Modelled on [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd) by Ayoub Ghriss (MIT). The repository layout, the `SessionStart` hooks, the Pi/OMP extension, the OpenCode plugin and the runtime manifests are adapted from that project; the original copyright notice is kept in [LICENSE](LICENSE) and in the adapted files. The rules in `SKILL.md` are new.

This project is not affiliated with the original author, and the original author has not reviewed or endorsed it.

## License

[MIT](LICENSE).
