# Claude AI Production Studio

**Original by Francesco (@francescoinweb3)**  
**Sources**:  
- [Main Article (X)](https://x.com/francescoinweb3/status/2108882188624121896)  
- [6 Small Jobs Workflow (X)](https://x.com/francescoinweb3/status/2111393917899808880)  
- Article ID: 2108867565233614848

> Most people use Claude to write. A smaller group figured out how to turn it into an AI production studio.

---

## Core Idea

Don’t ask Claude to “make a video” in one big prompt.  
Treat Claude as a **production studio made of rooms**, and break the work into small, checkable jobs. Each job produces one file; the next job starts from that file.

This is not a prompt trick. It’s a way of working.

---

## Part 1 – The Mental Model: Claude is the Studio, Not the Tool

A real production studio isn’t one machine. It’s a set of specialized rooms, each with its own job, connected by a workflow.

- **Data room**: raw numbers become honest charts.
- **Motion room**: charts and ideas become movement.
- **Edit room**: clips, decks, and documents get assembled and shipped to a human.

Claude now has a working version of each of those rooms, plus an open ecosystem of skills that upgrade them.

When the studio lives in one assistant, there are no handoffs between apps, no exported files that go stale, no “I changed the number in the spreadsheet but forgot to update the chart.” Everything downstream knows when something upstream changed.

---

## Part 2 – The Data Room: Claude Dashboards

Every good video that contains a number lives or dies on whether that number is true. The data room is where you make it true before you make it pretty.

**What it does**  
You connect a data platform or a CRM, then ask a question in plain language. Claude writes the query, runs it, and builds a dashboard. As the underlying data changes, the dashboard updates. Crucially, every chart carries the query that produced it — so a reviewer (or future-you) can see exactly how a number was derived. No mystery figures.

**Why it belongs in a studio**  
The dashboard is the source of truth the motion room reads from. When you animate a chart later, you’re not re-typing numbers into an animation — you’re pointing the animation at a figure that’s already been checked. The video inherits the honesty of the data room.

**How to use it well**
- Ask the real question, not the chart you think you want. (“Which of our stations run empty before 9am on weekdays” beats “make me a bar chart.”)
- Make it name its assumptions (date range, filters, what was excluded).
- Find the one number the video is about before you animate anything.

---

## Part 3 – The Motion Room: Claude Motion

This is the room people came for, and the one most misunderstood.

**What it does**  
Point Claude at a report, a chart, or a product walkthrough, and it produces a short animation: animated titles, a chart that draws on, a camera move, cuts timed to a beat. Then it exports an MP4.

**The part that changes everything**: it writes the animation **as code**. There is no video model in the loop. The titles, the timings, the colors, the chart draw-on — all of it is text Claude writes and you can read.

### Why “animation as code” is the whole game

Most people’s model of “AI video” is a generator: you write a prompt, you get a finished clip, and if the clip is wrong you re-prompt and hope. You’re negotiating with a black box.

Claude Motion inverts that. Because the animation is code, you get four properties a generator can never give you:

1. **Every value is editable.** The number on screen is a variable, not baked pixels.
2. **Revisions are instant and precise.** “Draw the chart half a second slower” is a one-line change.
3. **It’s deterministic.** The same input produces the same output.
4. **It composes.** The same values can feed a chart, a title card, and a lower-third, all staying in sync.

You’re not generating video. You’re **compiling** it.

Availability: Motion is in beta on Team and Enterprise plans.

---

## Part 4 – The Edit Room: Docs, Slides, Design

The quietest upgrade, and the one you can use today on any plan.

Docs, Slides, and Design are out of beta and available on every plan (including Free). You and Claude edit the same document, deck, or design together in real time.

This is where the clips from the motion room and the numbers from the data room get assembled into something a human receives: an article with the video embedded, a deck that walks a client through the data, a design that packages the whole thing.

**Pipeline tip**: build the narrative here first, leave holes where the video and the charts go, then fill them from the other two rooms. Writing the story before you animate keeps you from making beautiful clips that don’t serve a point.

---

## Part 5 – The Skills Layer: Open-Source Repos That Teach Claude Motion

This is what turns “Claude can animate” into “Claude animates well.”

Skills are packaged instruction sets that teach Claude the craft (easing, timing, the order elements appear) and how to drive a real animation library end to end.

You do not need all ten. You need the two or three that match the video you’re making.

### Group A – Rendering full videos in code

1. **Remotion** – Build entire videos in React: animated titles, charts, transitions, synced audio. The workhorse when the final output is a video file.  
   https://github.com/remotion-dev/remotion

2. **Remotion Agent Skills** – Ready-made instructions that take Claude from an empty Remotion project to a finished render.  
   https://github.com/remotion-dev/skills

3. **HyperFrames** – Turns AI-generated scenes into a finished piece (promo, explainer, animation cut to music).  
   https://github.com/heygen-com/hyperframes

4. **HyperFrames Student Kit** – The edit-room skill for your own footage: kills dead pauses, cuts stumbles, assembles a Reel, drops in subtitles.  
   https://github.com/nateherkai/hyperframes-student-kit

### Group B – Moving the web and the interface

5. **Motion (motiondivision)** – Brings a site to life: blocks that fade in, hover reactions, scroll-triggered effects.  
   https://github.com/motiondivision/motion

6. **Lottie Web (Airbnb)** – Embeds lightweight animated icons, logos, illustrations, and loaders.  
   https://github.com/airbnb/lottie-web

7. **GSAP (GreenSock)** – Complex, synchronized sequences where text, images, and other elements move together on a shared timeline.  
   https://github.com/greensock/GSAP

### Group C – Teaching Claude taste, not just syntax

8. **Motion Design Skill (LottieFiles)** – Teaches the model the craft decisions: how fast things should move, how they accelerate, what order elements enter in. Most underrated.  
   https://github.com/LottieFiles/motion-design-skill

9. **Motion Graphics (Barty-Bart)** – Builds animated cards, diagrams, and charts that appear on cue under the specific words a speaker says.  
   https://github.com/Barty-Bart/motion-graphics

10. **Claude Motion Design (howseen-ai)** – A full promo pipeline for Claude: transitions, camera moves, music-synced cuts, sound effects.  
    https://github.com/howseen-ai/claude-motion-design

**Index**: [Mort1d/motion-graphics-skills](https://github.com/Mort1d/motion-graphics-skills) – running index of motion-design skills.

**Honest recommendation**: Most people should start with #8 (taste) plus one pipeline skill (#2 or #10). A taste skill + a pipeline skill gets you 80% of the result.

---

## Part 6 – The Workflow: From Reference to Finished Clip

The move almost nobody uses: Claude is also your reference desk. You don’t describe the style you want — you show it, and let Claude reverse-engineer what makes it work.

1. **Feed it the reference, not a description.** Drop in the video you’re matching. Ask Claude to break down why it works: pacing, where the first motion lands, how the text enters, when the payoff hits. You get a **spec**, not a vibe.
2. **Build the data room first.** If the video has numbers, start in Dashboards. Get the real figures before you animate anything.
3. **Write the story in the edit room.** Lay out the narrative with holes where the video and charts go.
4. **Hand the spec and the chart to the motion room.** Claude writes it as code, matching the reference’s timing.
5. **Direct it in words.** “The title’s a beat late.” “Draw the line slower.” Each is a one-line edit.
6. **Assemble and ship.** Pull the clip into Slides/Doc or export the MP4.

---

## The 6 Small Jobs Version (Practical Pipeline)

From the later post (2026-10-17):

I don’t ask Claude to “make a video” anymore.  
I give it 6 small jobs. Each one produces one file, and the next job starts from that file.

> **reference** → `spec.md`  
> It watches a video I like and writes down why it works: pacing, first motion, cut rhythm.

> **data** → `data.json`  
> It pulls the real numbers and keeps the source next to every figure.

> **story** → `story.md`  
> One point, one hero number, three beats. Before anything moves.

> **motion** → `Scene.tsx`  
> It writes every frame as code with Remotion and a motion-design skill.

> **direct** → `timing.ts`  
> I give notes in plain words. “title is a beat late” → one line changes.

> **ship** → `final.mp4`  
> It renders stills, checks them against the spec and the data, then waits for my approval.

### Why small jobs work better

- Each step has one clear output, so it’s easy to check.
- If something looks off, you know exactly which file to fix.
- Nothing gets re-rolled, so the rest of the video stays the same.

One big prompt gives you a guess.  
Six small jobs give you a video you can actually edit.

---

## Part 7 – Common Mistakes

- Animating before the number is checked.
- Describing a style instead of showing one.
- Reaching for a rendering library when a taste skill was the real gap.
- Skipping the story.
- Treating a generated clip as final (the whole advantage is that it’s editable).

---

## Part 8 – Your First Week (On-Ramp)

- **Day 1** – Edit room. Open Docs/Slides/Design and co-edit one piece with Claude.
- **Day 2** – Reference desk. Feed a video you admire, get a written spec of why it works.
- **Day 3** – Taste skill. Install Motion Design Skill (#8) + one pipeline skill. Make one short animation from the spec.
- **Day 4** – Data room. Build one chart from a plain-language question (or mock numbers).
- **Day 5** – Full pass. Run the whole workflow once on something real and small. Ship it.

One real video beats ten tutorials.

---

## Availability Summary

| Component              | Status                          |
|------------------------|---------------------------------|
| Dashboards             | Beta, paid plans                |
| Motion                 | Beta, Team & Enterprise         |
| Docs / Slides / Design | Live on every plan (incl. Free) |
| Open-source skills     | Free, usable on any plan        |

The “studio” is really two layers: the native rooms Anthropic is rolling out, and the open skills shelf that’s already here. You don’t need the first to start building with the second.

---

## One Line to Remember

You’re not generating video anymore.  
You’re **compiling** it — from real data, against a real reference, in code you can change.  
That’s what turns an assistant into a studio.

---

*Archived for personal reference in signal-lab. Original content by @francescoinweb3.*
