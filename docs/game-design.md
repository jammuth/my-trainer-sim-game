# Trainer Sim — Game Design Document

Oct 24, 2026 · @James

> This file is the source of truth for the game design — edit it here. It was imported from an earlier [online draft](https://claude.ai/artifact/61v4w8wRktjBdRfxxPY6nP) on Oct 24, 2026, which is no longer kept in sync.

## Overview

A single-character training sim: the player is a guild trainer who takes on one trainee under a fixed contract, schedules every day, and is graded on the result when the contract ends.

- **Genre:** stat-raising management sim with branching endings
- **Inspirations:** Slave Maker 1–3 (structure, guild contracts, moddability) and Princess Maker 2 (scheduling and stat trade-offs)
- **Audience and rating:** adults only, 18+. Every character is an original creation and clearly adult.
- **Setting: high fantasy**

## Core loop

The player accepts a contract, then plans each day slot by slot until the deadline triggers the evaluation.

```text
Accept contract
  └─> Each day (×70):
        Day block     — trainee runs 8 slots (assistant supervises) | player runs own 8 hours
        Evening block — 4 slots together: lessons, talks, praise/punishment, rewards
        Night         — sleep and recovery
  └─> Contract end (day 70) → evaluation: ending + guild grade + gold payout
```

A contract runs 10 weeks (70 days). Each day has 8 time slots, and an activity can fill more than one slot, so a long job trades breadth for depth.

Each day has an 8-hour day block and a 4-hour evening block, with the rest for sleep:

| Block | Who | What happens |
| --- | --- | --- |
| Day block | Trainee, watched by the player's assistant | The trainee's 8 slots of skills, jobs and rest |
| Day block (same hours) | Player | The player runs a separate 8-hour schedule of their own |
| Evening block | Player, assistant and trainee together | Special lessons and talks, corrective training, punishments and praise |
| Night | Everyone | Sleep and recovery |

## Systems

Every action raises some stats and costs others, so no schedule is free.

| System | What it does | Draft notes |
| --- | --- | --- |
| Stats | Classic set: obedience, mood, fatigue, health, plus skill stats such as refinement and cooking | Final list to be decided |
| Actions | Each fills one time slot and changes several stats | Some unlock via items or assistants |
| Fatigue and mood | No hard fail: poor values only lower the final grade | Rest actions recover them |
| Economy | Jobs earn gold; gold buys items, clothes and lessons | Gold buys clothes, gifts and better lessons; version 1 starts with plenty of gold for testing, then tune so money is tight |
| Shop and inventory | Stat-boosting items, gifts, outfits | Stock may rotate or unlock over time |
| Events | Random and scripted: visitors, rival trainers, guild check-ins | Main source of story; version 1 includes her old bandit gang trying to recruit her back, plus random visitors whose conversation choices grant stats or miss opportunities |
| Assistants | Optional helpers who unlock extra actions | Hired for a few weeks at a time; see Assistants |
| Personality | Each trainee reacts differently to the same action | Drives replay value |

## Activities

Skills take 1 slot and jobs take 2, so an 8-slot day might be one job plus six lessons, or two jobs plus rest.

| Activity | Slots | Type | Main effect |
| --- | --- | --- | --- |
| Cooking lesson | 1 | Skill | Cooking up, fatigue up |
| Cleaning lesson | 1 | Skill | Cleaning up, fatigue up |
| Singing lesson | 1 | Skill | Singing up, fatigue up |
| Etiquette lesson | 1 | Skill | Refinement up, mood down slightly |
| Dancing lesson | 1 | Skill | Grace up, fatigue up |
| Rest | 1 | Recovery | Fatigue down, mood up |
| Barmaid shift | 2 | Paid job | Gold, small singing gain |
| Inn staff shift | 2 | Paid job | Gold, small cleaning and cooking gain |
| Bathhouse shift | 2 | Paid job | Most gold, most fatigue |

## Mood

Wren's mood scales how fast she learns: high mood speeds up skill gains, low mood slows them.

- **Raises mood:** rest, varied days, praise, and letting her keep a small share of wages
- **Lowers mood:** the same activity three or more days running, high fatigue, and harsh treatment
- **Guilt:** because she knows she messed up, fair and consistent treatment also builds obedience over time

## Player day block

While the assistant watches the trainee, the player spends their own 8 hours improving how well they can train her.

- **Visit** people, shops and places around the city
- **Train player stats**, using day-block hours and gold, which raise the player's training bonuses
- **Buy tools**, new or better equipment for training

| Type | Example | Effect |
| --- | --- | --- |
| Player stat | Charisma | Boosts praise and talks |
| Player stat | Discipline | Boosts corrective training |
| Tool | Better cooking utensils | Faster cooking gains |
| Tool | Music box | Faster singing gains |
| Place | Market | Shops for tools, clothes and gifts |
| Place | Guild hall | Contracts and hiring assistants |
| Place | Tavern | Rumours and people to meet |
| Place | Courtesan Guild | Contacts for the courtesan ending |

## Assistants

Assistants are hired, have a skill value, and each offers different training, so who you hire shapes what the trainee can learn.

- Spend gold to improve an assistant's skill, or hire a different one
- Each has strengths, such as a singing coach or a sword master
- An assistant may only stay a few weeks before a new one is needed

| Assistant | Cost | Teaches best |
| --- | --- | --- |
| Housekeeper (starting hire) | Cheap | General chores: cleaning, cooking |
| Noblewoman | Expensive | Refinement and manners |
| Adventurer | Moderate | Self defence (adds a self-defence skill that helps in the bandit-gang event) |

## Evening options

The 4-hour evening block (4 slots) mixes lessons, talks, discipline and rewards.

- **Praise** raises mood but can lower obedience
- **Punishment** raises obedience but lowers mood
- **Rewards** unlock from praise or high mood: a meal together when praised, or a bath together when she is happy enough

## Future plans

Not in version 1, kept here for later.

- **Best ending:** the trainee falls in love with the player and becomes their assistant
- **Adventuring:** possible combat, such as fighting goblins, if a sword master or similar assistant makes it worthwhile
- **Player starts:** different player backgrounds for variety

## Endings and scoring

The ending is chosen from the trainee's final stats when the contract closes.

- Each career path has stat thresholds; the highest-priority match wins
- A guild grade (e.g. S to F) and a gold payout reward the player
- No early fail endings; a bad run ends on a low grade
- Version 1 has 3 endings: noble's maid, courtesan with the Courtesan Guild, or a bad ending (back to prison or sent to the brothel)

| Ending | Driven by |
| --- | --- |
| Noble's maid | Cleaning, cooking, obedience |
| Courtesan with the Courtesan Guild | Singing, dancing, refinement |
| Bad ending: prison or brothel | Neither path's thresholds met |

## Content and modding

Characters, events and art load as drop-in content packs, so the community can extend the game.

Version 1 trainee: Wren (alternatives: Kess, Sable, Tamsin, Mira), an adult captured bandit. She was the gang's honeypot, used to cause distractions rather than fight, and was caught stealing. The city sentenced her to 5 years' service, and the guild contract is part of that. She is street smart and tough, and she knows she messed up.

- One data file per character: stats, personality, events, endings, art references
- Base game ships with a small cast of original characters, text-only at first; art is added later
- Mod rules require original or properly licensed characters, all adults

## Tech, platform and distribution

To be decided; see the open questions below.

- Engine: Godot
- Platforms: Linux for version 1
- Release: personal use at first, no public store yet

## Open questions

- [ ] One-line pitch
- [ ] Exact praise and punishment effects
- [ ] Final stat list
- [ ] Art style and artist for the later art pass
- [ ] Final pick of the trainee's name
- [ ] Exact threshold numbers for each ending
- [ ] Exact numbers for stat gains and job pay
