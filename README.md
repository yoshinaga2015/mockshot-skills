# Store screenshot planner

An agent skill that plans store screenshots from your app's own code. It reads your README and screens, picks the 5 to 8 benefits worth showing, writes short headlines for each slide, and lists the exact sizes and counts each store needs.

Works with Claude Code, Cursor, Codex and other agents that support [skills](https://skills.sh).

```sh
npx skills add yoshinaga2015/mockshot-skills
```

Then ask your agent something like:

- "Plan our App Store screenshots."
- "Write screenshot captions for the Play Store listing."
- "Our screenshots are just raw UI. Redo the order and copy."

## What you get

1. **Benefits**: features from the code, rewritten as what the user gets, each traced to a file.
2. **Slide plan**: one headline per slide, the screen to capture, and the order. Slide 1 says why the app exists, and slide 2 proves it with the real UI.
3. **Spec sheet**: sizes, counts and format rules for App Store (iPhone, iPad, iPhone Duo), Mac App Store and Google Play, with the date they were last checked.

The copy follows the **2-13-2 rule**: most people stop after **2** screenshots, keep the why to about **13** characters (a short punchline in English), and make the **2**nd shot the proof.

## Design and export

The plan works with any design tool. If you use [MockShot Studio](https://mockshot.studio) (Mac app, plus a browser editor), the agent can also write the plan as a `.mockshot` project that you open directly, so you start with the slides and headlines already in place. Format: [`references/mockshot-format.md`](store-screenshot-planner/references/mockshot-format.md).

## Files

```
store-screenshot-planner/
  SKILL.md                     # the workflow the agent follows
  references/store-specs.md    # store sizes and rules, with sources and check date
  references/mockshot-format.md
  references/example.mockshot
```

## Keeping the specs current

Apple and Google change their screenshot rules from time to time. `store-specs.md` lists its sources and the date it was last checked. Pull requests with a link to the official page are welcome.

## License

MIT
