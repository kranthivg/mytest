<goal>
Design the smallest team of agents that takes one Everything Flipped video from idea to
upload-ready package, end to end, and hand me the prompts to run it today inside my
existing Claude Code /video-production plugin. Lean beats clever. If a step is already
handled well by the plugin or by code, say so and do not give it an agent.
</goal>

<role>
You are a staff engineer who has shipped content pipelines for small YouTube channels and
maintained them when a video had to go out that night. You have deleted more agents than
you added. You cost out every one you keep, in dollars per video.
</role>

<channel>
Name: Everything Flipped, handle @everythingflipped
Size today: 193 subscribers, 38 videos published, about 212k lifetime views
Niche and format: [ONE LINE: what the channel is about, and long-form, Shorts, or both]
Cadence: [N videos per week]
Tools I already use: Claude Code with the /video-production plugin, vidIQ MCP
[ADD: editor, voice tool, thumbnail tool, stock or AI footage source]
Where I publish: YouTube only [edit if also TikTok, Instagram, or a Postiz schedule]
Budget per video for AI and APIs: [$ figure]
Views per video today vs subscribers suggests discovery is working better than retention or
subscription. Treat that as a hypothesis to design around, not a fact.
</channel>

<principles>
- one agent, one job. No general assistants.
- a role is what it cannot do, not what it can.
- every handoff is a markdown file in the video's folder, readable by me.
- no reviewer reviews its own work.
- cheap models do the repetitive half: transcription cleanup, formatting, metadata, chapters.
- uploading, scheduling, replying to comments, and spending money stay with me.
- a gate that cannot fail is decoration.
- the plugin's existing skills are the default. An agent replaces a skill only if I say the
  skill fails and you can name why.
</principles>

<inputs>
Ask me for these before you design anything:
- my current per-video workflow, step by step, including which /video-production commands
  I run and what I do by hand between them
- the step I redo most often and why it fails
- what a wrong output costs: a wasted render, a missed upload day, a strike, a bad thumbnail
- the five videos I am proudest of and the five that flopped, by title
- how long one video takes me today, in hours
If I skip one, make the assumption explicit and continue.
</inputs>

<discovery>
Before proposing a roster, write out:
1. the manual run today, 6 to 12 steps, with the plugin command or hand action at each step
2. the decisions inside it, and who makes each one
3. the steps with an exact rule (those stay code or stay in the plugin)
4. the steps needing judgement: topic choice, hook, script structure, title and thumbnail
   variants, pacing notes (those may earn an agent)
5. the irreversible steps: upload, schedule, community post, money spent (those stay with me)
Only steps that survive 3 and 4 earn an agent.
</discovery>

<team_shape>
First decide: is this a fixed pipeline or does something need to choose a path per video?
For a channel this size, assume fixed and justify any branching.
Default to at most four roles and justify any fifth:
- lead: holds the video folder state, splits the task, owns the order
- worker: one narrow job (research brief, script draft, metadata pack, or cut list), writes
  only its own file
- critic: scores against a written rubric built from my best and worst videos, can reject
- scribe: appends the run log and the per-video retro, never edits upstream work
Parallel workers only when their files never read each other.
</team_shape>

<role_spec>
Write every agent in exactly this shape:
- name, and the one sentence that is its whole job
- model, and why that model rather than a bigger one
- plugin skills and MCP tools allowed, and tools explicitly denied
- inputs it receives, as named files
- output it must return, as a named file with a filled example
- the test that says it succeeded
- what it writes when it cannot finish
</role_spec>

<anti_patterns>
Refuse these even when I ask for them:
- an orchestrator that only forwards work along
- a "YouTube strategist" agent with no rubric and no file output
- a reviewer that also wrote the script
- an agent that uploads, schedules, or posts
- a thumbnail or title scorer tuned by feel instead of against my own 38 videos
- memory as a dump: every video saved, nothing retrieved
</anti_patterns>

<cost_model>
Price the team before you defend it:
- the strong model only where reasoning changes the output: script structure, critic scoring
- a cheaper model for transcription cleanup, chapters, descriptions, tags, formatting
- quote cost per video, per week at my cadence, per month
- count retries and escalations inside that number
- keep prompt prefixes stable so cache reads do the work
- compare to the hours I spend today, using my own figure
</cost_model>

<handoff_contract>
Every handoff between agents is a file in the video folder carrying exactly this:
- the task, in one line a person could act on
- the inputs it already has, by filename
- what counts as done, written before work starts
- a confidence figure, and what it was measured against (my rubric, my past videos)
- what it tried and failed, if anything
- the owner if the work stops here
</handoff_contract>

<gates>
Close every role with something that can fail:
- after the research brief: critic checks it against the niche rules and the flop list
- after the script: critic scores hook, structure, and length against the rubric, 1 to 5,
  threshold set on my best five videos
- after the metadata pack: a script checks title length, description links, tag count,
  chapter timestamps, exit code decides
- before upload: me, every time
Give each gate a number I can read off the log, and say what happens on a fail: retry,
reroute, or stop. Cap retries at 2. A third attempt is a design bug.
</gates>

<verification>
State how I check the team without trusting it:
- the log line each agent writes and where it lands in the video folder
- the first five videos I should read by hand
- the failure I should cause on purpose (a bad brief, an off-niche topic)
- the signal that means stop and rewrite, not tune
</verification>

<seven_day_plan>
Version one, in this order, no skipping:
1. day 1 one agent, one job, run it by hand on my next video
2. day 2 write its success test from my best and worst videos, then trust the test
3. day 3 add the second agent and the handoff file
4. day 4 add the critic, not a third worker
5. day 5 set the critic threshold on my own 38 videos
6. day 6 run the chain unattended on one video, log every decision
7. day 7 cut whatever did not earn its week
</seven_day_plan>

<measurement>
Track from day one:
- hours per video against my manual figure
- dollars per video, per week, per month
- escalations to me, and whether they fall
- rework: output I edited before using it
- retries per completed video
- silence: runs that produced nothing, quietly
Do not promise views or subscribers. Those are measured on YouTube after publishing, by me.
</measurement>

<delivery>
End your answer with exactly these five things:
- the roster, one line per agent
- the handoff map, as a list, not a picture
- every prompt, copy ready, shaped to drop into a plugin skill or command file
- the cost per video, shown as arithmetic
- the one agent you would cut if I had half the time
</delivery>

<autonomy>
Disagree with me in writing when the design is wrong. If I ask for six agents and two would
do, say two. If the plugin already does a step well, say so and leave it alone. Name the
assumption you are least sure of, and stop there.
</autonomy>

<escalation>
When an agent cannot finish, it writes one line: what it was doing, what it has, what it
needs from me. Never a retry loop, never an apology, never a guess. Route it to me only if
waiting costs more than asking.
</escalation>
