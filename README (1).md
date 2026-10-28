# The three-part finish line

**How to use this:** Before you type `/goal`, fill in these three parts on paper or in a scratch doc first. A finish line you wrote in your head isn't a finish line the referee model can check. Copy the three headers below into your prompt and fill each one in.

## The template

```
DONE WHEN: [the condition, specific enough that a stranger could check it]

VERIFY: [the command or check that proves the condition is true]

OUTPUT: [what gets printed or written, so the referee can confirm]
```

Write only "Done When" and the referee judges on vibes. All three parts is what makes the run stoppable and honest.

## The 30-second stranger test

If a stranger couldn't verify your finish line in 30 seconds without reading the code, it isn't a finish line yet. Read it out loud to someone who's never seen the project. If they'd have to ask "wait, what counts as done?", rewrite it.

## The two failure modes to avoid

**1. The vague condition.** "Production-ready" burned 30 turns at full-rate token costs before it got killed for being unmeasurable. Fix: name the artifact, the state, the test, and the printed proof. Not "make it good". "the file exists, the test passes, and the count prints."

**2. The compound goal.** "Redesign auth, add OAuth, write tests, update docs" is four goals wearing one prompt. Sequential goals beat compound goals every time: run one, confirm it, then start the next. A goal that's actually four goals fails all four at once when it fails.

## The cost, honestly

Expect 10-20x the tokens of a single prompt. You're buying back your own checking hours, not saving tokens. If the task doesn't have real hours of checking behind it, a plain prompt is cheaper and just as good.
